# DPH u stavby pro bydlení — a proč o ní rozhoduje dispozice

Devět procentních bodů na celé stavbě závisí na jednom čísle: **podlahové ploše rodinného domu**.
Texty jsou z e-Sbírky (zák. č. 235/2004 Sb. a vyhl. č. 163/2025 Sb. účinná od 1. 7. 2025), takže se
u nich druhý zdroj neuvádí.

## Řetězec, který to rozhoduje

1. **§ 47 odst. 1**: sazby jsou „a) základní sazba daně ve výši **21 %**, nebo b) snížená sazba daně
   ve výši **12 %**".
2. **§ 48a odst. 1 písm. b)**: „Stavbou pro sociální bydlení se pro účely daně z přidané hodnoty
   rozumí … **stavba rodinného domu, jejíž podlahová plocha nepřesahuje 350 m²**."
3. **§ 49 odst. 1**: „**Snížená sazba daně se uplatní při poskytnutí stavebních nebo montážních
   prací spojených s výstavbou stavby, která je stavbou pro sociální bydlení.**" Odst. 3 totéž pro
   dodání takové stavby, odst. 4 pro práce na dokončené stavbě pro bydlení.
4. **§ 48a odst. 6**: „Způsob výpočtu podlahové plochy pro účely daně z přidané hodnoty stanoví
   Ministerstvo financí vyhláškou." → to je **vyhl. č. 163/2025 Sb.**

A ještě jedna definice, která se plete: **§ 48 odst. 3** — stavbou rodinného domu se pro účely DPH
rozumí stavba **zapsaná v registru územní identifikace se způsobem využití rodinný dům**, nebo
stavba, u níž lze důvodně předpokládat, že tak zapsána bude. Není to tedy definice ze stavebního
zákona, ale z RÚIAN.

> **Pozor na záměnu s obytným prostorem.** Hranice **120 m²** z § 48a odst. 5 platí pro *obytný
> prostor pro sociální bydlení* (byt), ne pro rodinný dům. U RD je hranice 350 m².

## Jak se těch 350 m² počítá (vyhl. č. 163/2025 Sb.)

- **§ 2 odst. 1:** podlahová plocha stavby = **součet podlahových ploch jednotlivých místností
  a prostorů uvnitř obvodové konstrukce** stavby, která ji oddělje od vnějšího prostředí.
- **§ 1:** *místnost* je prostorově uzavřená část stavby vymezená podlahou, stropem nebo konstrukcí
  střechy a **pevnými stěnami**; *prostor* je totéž, ale chybí mu alespoň jedna celá pevná stěna;
  *půda* je přístupná místnost nebo prostor vymezené konstrukcí střechy, **které nejsou určeny
  k účelovému využití**.
- **§ 2 odst. 3 — co se NEzapočítává:** a) půda, b) lodžie, c) **schodiště, výtahová šachta** nebo
  jiný prostor k obdobnému využití, d) prostory výhradně určené jako technologické zázemí
  prostorů podle písm. c).
- **§ 3 odst. 1:** plocha místnosti se měří **vnitřním lícem pevných stěn**; v místnosti se šikmou
  stěnou, šikmým stropem nebo šikmou konstrukcí střechy se plocha vymezí v úrovni **1,2 m nad
  podlahou**.
- **§ 3 odst. 2:** připočte se i plocha **galerie**, dosahuje-li její světlá výška alespoň **2,3 m**.
- **§ 3 odst. 3:** v m² na dvě desetinná místa; rozměry v metrech na dvě desetinná místa.
- **§ 4:** u *prostoru* se místo chybějící stěny plocha vymezí pravoúhlým průmětem obvodu vodorovné
  konstrukce.

> **Tři důsledky pro fázi B4 a B6, které se dají využít.** (1) **Schodiště se nepočítá** — dvoupodlažní
> dům tím pádem „ztratí" plochu schodišťového prostoru v každém podlaží. (2) **Podkroví se měří
> v 1,2 m nad podlahou**, takže šikminy plochu snižují — stejná hranice 1,2 m jako u obytné
> místnosti v § 38 odst. 1 stavební vyhlášky, ale k úplně jinému účelu. (3) **Garáž uvnitř domu se
> počítá** — v seznamu výjimek není. Dům, který by bez garáže byl pod 350 m², s ní může být nad.

## Co z toho dělá nástroj

`tools/cena/cena.py` sečte čisté plochy místností z modelu, vyloučí ty, jejichž **název** odpovídá
půdě, lodžii, schodišti nebo šachtě, a podle výsledku nasadí 12 % nebo 21 %. Dvě upřímná omezení:

- vylučování je **podle názvu**, ne podle typu — model nemá pole „schodišťový prostor", takže
  chodba, ve které schodiště stojí, se započítá celá;
- model měří obrysy v osách stěn, vyhláška vnitřním lícem a u šikmin v 1,2 m — proto nástroj hlásí
  varování, jakmile je výsledek do **10 %** pod hranicí 350 m². Na téhle straně hranice stojí 9
  procentních bodů, takže tam studie nesmí říct „vejdeme se"; to potvrzuje daňový poradce.

## Vedlejší efekt, na který se zapomíná

U **dodávky na klíč** se snížená sazba uplatní na celé plnění včetně materiálu, protože jde o jedno
plnění — stavební práce. Kupuje-li si stavebník materiál sám, platí u něj **21 %**, a snížená sazba
mu zbude jen na fakturách za práci. Část teoretické úspory ze svépomoci tím padne zpět státu; kolik
přesně, závisí na podílu materiálu, který má jediný dohledaný zdroj (viz
[Svépomoc](Svepomoc.md), [SvepomocKorekce](../NakladyStavby/CenoveUkazatele/SvepomocKorekce.md)).
*(needs second source — mechanismus je doložen, konkrétní podíl materiálu ne.)*

## Related pages

- [Postup odhadu](PostupOdhadu.md)
- [Cenové ukazatele](CenoveUkazatele.md)
- [Obestavěný prostor](ObestavenyProstor.md)
- [Plochy a nejmenší rozměry místností (B4)](../DispozicniVarianty/PlochyAMinimalniRozmery.md)
