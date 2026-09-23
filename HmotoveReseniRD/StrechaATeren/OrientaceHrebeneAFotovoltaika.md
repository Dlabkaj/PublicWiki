# Orientace a sklon střechy vzhledem k fotovoltaice

Hlavní zdroj: (source: https://acetex.cz/clanky-energeticka-optimalizace/sklon-a-orientace-strechy-pro-idealni-fungovani-fotovoltaicke-elektrarny,
**09.09.2021** — datum ověřeno v raw textu; Acetex s.r.o. je dodavatel FVE, tedy komerční zdroj).
Všechna čísla níže byla v REVIEW zkontrolována doslovně proti zdroji — souhlasí. Otázka není, zda
je zdroj citován věrně (je), ale zda ta čísla platí; k tomu viz CONFLICT níže.

## Orientace je důležitější než sklon

- Použitelná je prakticky jakákoli orientace kromě **severní** — na severně orientovanou střechu
  se instalace FVE kvůli nízké efektivitě nedělá a zdroj ji nedoporučuje.
- **Východ** — panely vyrábí nejefektivněji ráno.
- **Západ** — maximalizuje večerní výrobu.
- **Jih** — nejvíc energie během dne, nejdelší časový úsek výroby → **ideální volba**.

⚠️ **CONFLICT: o kolik je jih lepší než východ/západ — o 20 %, nebo o 5–10 %?**
- Acetex, doslovně: "Orientace na jih, ve srovnání s orientací na východ či západ, je o cca **20 %
  efektivnější**."
  (source: https://acetex.cz/clanky-energeticka-optimalizace/sklon-a-orientace-strechy-pro-idealni-fungovani-fotovoltaicke-elektrarny)
- Viessmann CZ: při sklonu **30–35°** neklesne roční výnos plně východně nebo západně orientovaných
  panelů o více než **5–10 %**; při malém sklonu (10–20°) je ztráta v průměru kolem 5 %.
  (source: https://www.viessmann.cz/cs/rady-a-tipy/info-a-tipy-k-nakupu/orientace-fotovoltaickych-panelu.html)

Rozdíl je dvoj- až čtyřnásobný a **nelze ho z těchto zdrojů rozhodnout**: ani jeden neuvádí, k jaké
lokalitě, sklonu, azimutu ("přesně na východ" vs. jihovýchod) a k jakému referenčnímu sklonu jižní
varianty se to počítá, a přesně na těchto parametrech ztráta závisí (Viessmann svoje číslo váže na
sklon 30–35°, Acetex svoje na nic). Třetí, slabší údaje z vyhledávání se pohybují okolo 15 %, takže
reálné rozpětí je asi **5–20 %**.

**Pro fázi B2:** nepoužívat jedno procento. Orientaci řešit tak, že jih je nejlepší a východ/západ
je zhoršení řádu jednotek až ~20 %, a konkrétní ztrátu si nechat spočítat kalkulačkou pro danou
lokalitu, sklon a azimut (PVGIS nebo nabídka dodavatele) — ne převzít z článku.

## Doporučené sklony pro FVE panely

- Sedlová střecha: nejlépe osvědčený sklon **35°–45°** pro panely. *(needs second source)*
- Šikmá střecha obecně: instalace možná v rozsahu **15°–50°**, ale mimo optimum je výtěžnost nižší
  (lze kompenzovat větším počtem panelů). *(needs second source)*
- Plochá (vodorovná) střecha: panely na nosné konstrukci s nastavitelným sklonem, obvykle
  **10°–35°**. *(needs second source)*

Poznámka k tomu pásmu: Viessmann CZ uvádí pro jižní orientaci jako příznivý rozsah **20–50°** a jako
prakticky optimální pro ČR se jinde opakuje **30–35°**, zatímco Acetex píše 35–45°. Rozsahy se
překrývají a měří trochu jiné věci ("osvědčené pro instalaci" vs. "maximální roční výnos"), takže to
nevedeme jako rozpor — ale **35° je jediná hodnota, kterou potvrzují oba zdroje**, a je to zároveň
hodnota uvnitř běžného sklonu sedlové střechy. Pro B2 je to bezpečná volba.

## Zatížení střechy

- Šikmá střecha s panely: přídavné zatížení cca **20 kg/m²**. *(needs second source)*
- Plochá střecha se zátěžovými bloky: cca **35–40 kg/m²**. *(needs second source)*
- Nutnost dostatečně dimenzovaného krovu a krytiny umožňující kotvení konstrukce vruty do krokví.

## Když je střecha orientovaná na sever

Alternativy dle zdroje: panely na přidružené stavby (garáž, technický/zahradní domek), nebo přímo
na pozemek (pozemní FVE).

## Co fotovoltaika dělá se skladbou šikmé střechy (druhý zdroj)

(source: https://www.nasestrecha.cz/clanky/jak-pouziti-fotovoltaiky-ovlivnuje-skladbu-sikme-strechy/,
**21. 10. 2024**, autor **Jan Rypl, manažer aplikací JUTA a.s.** — výrobce podstřešních membrán,
tedy opět komerční zdroj, navíc se zájmem na prodeji konkrétní fólie; autor i datum ověřeny v raw
textu.) Tento zdroj byl pro task stažen, ale do wiki nebyl dosud vůbec zpracován — doplněno
v REVIEW.

Podstatné pro rozhodování o hmotě a sklonu střechy (netýká se běžných panelů nad krytinou, ale
**fotovoltaiky zabudované do krytiny** nebo krytiny s FV účinností):

- FV krytiny a panely **nejsou vysoce paropropustné** a bývají mezi sebou hermeticky utěsněné, takže
  větrání střechy se musí řešit jako u nízkoparopropustných krytin (např. plechových) — podle
  tabulky B.2, přílohy B normy **ČSN 73 1901-2 Navrhování střech, část 2: Střechy se skládanou
  krytinou**.
- Zabudované FV prvky často **neumožní vytvořit dostatečný profil pro odvětrání u hřebene**, pod
  jejich plochou roste teplota (nejvíc při vypnutí FV) a to zatěžuje podstřešní membránu; přes
  průhledná místa navíc na membránu trvale působí UV.
- Požadavek na vyšší **třídu těsnosti DHV 2** vzniká podle toho, o kolik stupňů je sklon střechy
  menší než bezpečný sklon zvolené krytiny, a kolik "zvýšených požadavků" na skladbu působí (dle
  *Pravidel pro navrhování a provádění střech* Cechu klempířů, pokrývačů a tesařů ČR, na která
  odkazuje i ČSN 73 1901-2, str. 11, bod 5.3.3).
- Důsledek pro volbu sklonu: **jít se sklonem pod bezpečný sklon krytiny se prodražuje ve skladbě**,
  ne jen v krytině. Příklady ze zdroje: taška s bezpečným sklonem 30° na střeše se sklonem 28°
  → DHV 2; taška s bezpečným sklonem 22° na pultovém vikýři se sklonem 16° → DHV 2;
  vláknocementová šablona (bezpečný sklon 40° nad 400 m n. m.) na střeše 36° → DHV 2.

Tyto příklady zároveň **nezávisle potvrzují dvě hodnoty** z tabulky bezpečných sklonů na stránce
[[TvarASklonStrechy]] (pálená/betonová taška 30°, drážková ražená se spojitou drážkou 22°) a — což je
důležitější — odkazují na **aktuální** znění normy ČSN 73 1901-2, ne na verzi z roku 2007.

## Vztah k volbě tvaru/orientace hřebene ve fázi B2

Z tohoto zdroje plyne prakticky použitelné kritérium: pokud má být na střeše FVE, **hřeben by měl
být orientován tak, aby jedna z hlavních rovin směřovala na jih** (u sedlové/valbové střechy) nebo
je vhodná pultová střecha s jedinou plochou orientovanou na jih (viz též
[[TvarASklonStrechy]] — pultová střecha je dle BMI/Bramac "obzvláště vhodná pro instalaci
solárních systémů"). Sklon okolo **35°** leží současně v pásmu doporučeném pro FVE (35–45° dle
Acetexu, 20–50° dle Viessmannu) a v běžném pásmu sedlové střechy (25–45° dle BMI/Bramac), takže
volba sklonu pro FVE a pro klasickou sedlovou střechu se nevylučuje.

Toto je **úsudek z kombinace zdrojů, ne citace** — žádný zdroj tu větu neříká; netagujeme ji jako
nedoloženou, ale ani ji necitujeme jako fakt. Pozor, že u pultové střechy jde pásmo dle BMI/Bramac
jen 5–20°, což je pod optimem pro FVE — u pultovky se tedy jih platí nižší výtěžností na stupeň
sklonu, nebo nosnou konstrukcí panelů.

## Open questions

- **Blokující:** ztráta výnosu při orientaci východ/západ místo jihu — 20 % (Acetex) vs. 5–10 %
  (Viessmann, při sklonu 30–35°). Potřeba výpočet pro konkrétní lokalitu/sklon/azimut (PVGIS nebo
  nabídka dodavatele), ne další článek.
- Vliv vikýřů na plochu využitelnou pro FVE — ani v jednom ze dvou zdrojů neřešeno (zdroj JUTA
  zmiňuje pultový vikýř jen jako příklad lomení sklonu a DHV 2).
- Konkrétní výnos v kWh/kWp/rok pro ČR podle orientace a sklonu — žádný z dosavadních zdrojů
  neuvádí absolutní čísla.
- Přídavné zatížení střechy od FVE (20 kg/m² šikmá, 35–40 kg/m² plochá) má jen jeden zdroj —
  pro statiku krovu ověřit u dodavatele konkrétní konstrukce.

<!-- nerd:links -->
## See also

- [[TvarASklonStrechy]]
<!-- /nerd:links -->
