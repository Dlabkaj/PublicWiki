# Sweet Home 3D — plug-in vývoj a API

Fakta na této stránce vychází z vlastní oficiální dokumentace projektu (sweethome3d.com — plug-in developer's guide, documentation, javadoc) — subjekt dokumentuje sám sebe, tagy `*(unverified)*` proto nejsou u faktů z těchto zdrojů použity.

## Základní údaje

Sweet Home 3D je bezplatná aplikace pro interiérový design (kreslení půdorysu domu a jeho prohlížení ve 3D). Aktuální verze dle webu je 7.5 (poslední aktualizace 5. května 2025). Je dostupná ve 29 jazycích, jde o open-source projekt na SourceForge.net, distribuovaný pod GNU General Public License. (source: https://www.sweethome3d.com/documentation/)

## Plug-in architektura

Od verze 1.5 lze do Sweet Home 3D přidávat nové funkce pomocí plug-in souborů umístěných ve složce plug-ins. Umožňuje to Java programátorům vyvíjet a distribuovat nové funkce bez úpravy zdrojových souborů aktuální verze a bez nutnosti dodávat plnou verzi programu. (source: https://www.sweethome3d.com/plug-in-developers-guide/)

Vývoj plug-inu vyžaduje znalost programování v Javě (s IDE, např. Eclipse) — Sweet Home 3D sám o sobě cílí na běžné uživatele, ne na vývojáře. (source: https://www.sweethome3d.com/plug-in-developers-guide/)

### Klíčové třídy (balíček `com.eteks.sweethome3d.plugin`)

| Třída/Enum | Popis |
|---|---|
| `Plugin` | Nadtřída (super class) pluginu. |
| `PluginAction` | Akce zpřístupněná uživatelům aplikace přes plugin. |
| `PluginManager` | Správce pluginů Sweet Home 3D. |
| `HomePluginController` | MVC kontroler pro home view, který spravuje pluginy. |
| `PluginAction.Property` (enum) | Výčet vlastností, které akce může definovat. |

Plugin se skládá z jedné nebo více akcí (`PluginAction`), které se automaticky přidají do nástrojové lišty a/nebo menu, podle hodnot vlastností `TOOL_BAR` a `MENU`. (source: https://www.sweethome3d.com/javadoc/com/eteks/sweethome3d/plugin/package-summary.html)

Pro upward-kompatibilitu s budoucími verzemi Sweet Home 3D se doporučuje v pluginu používat pouze třídy z balíčků `com.eteks.sweethome3d.plugin`, `com.eteks.sweethome3d.model`, `com.eteks.sweethome3d.tools` a `com.eteks.sweethome3d.viewcontroller` — ostatní balíčky (`com.eteks.sweethome3d.swing`, `.j3d`, `.io`, `com.eteks.sweethome3d`) v javadoc nejsou zaručeně stabilní. (source: https://www.sweethome3d.com/plug-in-developers-guide/)

### Model vrstva (MVC)

Sweet Home 3D je postaven na architektuře MVC (Model View Controller). Centrální třídou v Model vrstvě je `HomeApplication`, přes kterou lze přistupovat k instancím `Home` a k `UserPreferences` (jednotky délky, katalog nábytku, katalog textur). Instance `Home` uchovává:
- seznam objektů `HomePieceOfFurniture` (implementují rozhraní `PieceOfFurniture`)
- kolekci objektů `Wall`
- seznam objektů `Room`
- kolekci objektů `DimensionLine`
- kolekci objektů `Label`

Model není thread-safe z výkonnostních důvodů — veškeré úpravy objektů modelu by měly probíhat v Event Dispatch Thread. Změny modelu se promítají do zobrazených komponent přes `PropertyChangeEvent`, `CollectionEvent` nebo `SelectionEvent`. (source: https://www.sweethome3d.com/plug-in-developers-guide/)

### Vytvoření a nasazení pluginu — postup dle příručky

1. Vytvořit podtřídu `com.eteks.sweethome3d.plugin.Plugin`, implementovat metodu `getActions()` vracející pole `PluginAction`.
2. Pro každou akci vytvořit podtřídu `PluginAction` s metodou `execute()` — zde se implementuje vlastní logika (příklad z příručky: výpočet objemu přesouvatelného nábytku ze `getWidth()*getDepth()*getHeight()` každého kusu).
3. V konstruktoru akce nastavit vlastnosti přes `putPropertyValue(Property.NAME, ...)`, `putPropertyValue(Property.MENU, ...)`, `setEnabled(true)`.
4. Vytvořit popisný soubor `ApplicationPlugin.properties` s klíči `name`, `class`, `description`, `version`, `license`, `provider`, `applicationMinimumVersion`, `javaMinimumVersion`.
5. Zabalit zkompilované třídy + `ApplicationPlugin.properties` do JAR souboru.
6. Nasadit: zkopírovat JAR do plug-ins složky uživatele. Od verze 1.6 lze plugin nainstalovat i dvojklikem na soubor s příponou `.sh3p` (přejmenovaný `.zip`), nebo příkazem `/path/to/SweetHome3D /path/to/plugin.sh3p`.

Umístění plug-ins složky:
- Windows Vista/7/8/10/11: `C:\Users\<user>\AppData\Roaming\eTeks\Sweet Home 3D\plugins`
- Windows XP a starší: `C:\Documents and Settings\<user>\Application Data\eTeks\Sweet Home 3D\plugins`
- macOS: `Library/Application Support/eTeks/Sweet Home 3D/plugins`
- Linux/Unix: `.eteks/sweethome3d/plugins`

(source: https://www.sweethome3d.com/plug-in-developers-guide/)

### Testování a spuštění

Plugin funguje s verzí Java Web Start, instalátory, nebo přímo spustitelným JAR (`SweetHome3D-7.5.jar`), který lze spustit příkazem `java -jar /path/to/SweetHome3D-7.5.jar`. (source: https://www.sweethome3d.com/plug-in-developers-guide/)

### Dokumentace a zdroje (dle stránky Documentation)

- Uživatelská příručka a FAQ jsou dostupné na webu projektu a v menu Help aplikace.
- API generované javadoc je dostupné online i ke stažení.
- Poslední část plug-in developer's guide popisuje architekturu tříd modelu Sweet Home 3D.
- Existuje francouzská kniha "Les cahiers du programmeur Swing" (Emmanuel Puybaret, Editions Eyrolles, prosinec 2006), jejímž studijním případem je Sweet Home 3D verze 0.10.

(source: https://www.sweethome3d.com/documentation/)

## Relevance pro pipeline agenta

Plugin API je Java-only (žádné nativní CLI/REST rozhraní zmíněné v těchto zdrojích) — pro skriptování z agenta by šlo o vytvoření Java pluginu, nikoli o přímé volání z Pythonu/CLI. Otázka pro Open questions: existuje kromě pluginu i jiný způsob automatizace (např. formát souboru .sh3d k přímé generaci)? Tento zdroj to nepopisuje.

## Odkazy

- Plug-in developer's guide: https://www.sweethome3d.com/plug-in-developers-guide/
- Dokumentace (přehled): https://www.sweethome3d.com/documentation/
- Javadoc balíčku plugin: https://www.sweethome3d.com/javadoc/com/eteks/sweethome3d/plugin/package-summary.html
