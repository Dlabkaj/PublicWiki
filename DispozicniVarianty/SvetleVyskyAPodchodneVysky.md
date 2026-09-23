# Světlé a podchodné výšky

Jediné rozměry, které vyhláška u obytných místností skutečně ukládá. Text je z e-Sbírky (úplné znění
účinné od 1. 7. 2026), doplněný technickým standardem ČKAIT.

## § 38 vyhl. č. 146/2024 Sb. — doslova

**Odst. 1.** „Světlá výška obytné místnosti nebo pobytové místnosti stavby pro bydlení musí být
minimálně **2,5 m**. Světlá výška může být snížena až na **2,2 m**, nejvýše nad polovinou podlahové
plochy obytné místnosti. V podkroví musí být světlá výška obytné místnosti minimálně **2,2 m**.
V obytné místnosti se šikmým stropem musí být nejmenší světlá výška dosažena minimálně nad polovinou
podlahové plochy prostoru, u prostorů se šikmými stropy **se do plochy obytné místnosti nezapočítává
plocha se světlou výškou menší než 1,2 m**."

**Odst. 3.** Podjezdná výška v garáži minimálně **2,2 m**; v místech přechodu mezi rampami s různým
podélným sklonem nebo nad rampami se sklonem více než 8 % minimálně **2,3 m**.

Dvě věci, které se z toho čtou špatně:

> **Snížení na 2,2 m není volba tvaru stropu, ale plošná podmínka.** Nad **polovinou** podlahové
> plochy místnosti musí zůstat plná výška. Podkroví se řeší stejnou logikou: do plochy místnosti se
> nezapočítá pás, kde je pod 1,2 m — takže místnost s plytkou střechou může „ztratit" tolik plochy,
> že přestane být obytným prostorem podle § 2 písm. b) (8 m²).

> **Světlá výška se měří k nášlapné vrstvě, ne k nosnému stropu.** Podle
> [TS 01 ČKAIT](https://profesis.ckait.cz/dokumenty-ckait/ts-01/) (verze 3, účinná od 1. 7. 2026,
> bod 2.1) je to svislá vzdálenost mezi **horním lícem nášlapné vrstvy podlahy** a rovinou spodního
> líce stropu nebo zavěšeného podhledu v jednom podlaží; u trámových stropů po spodní líc podhledu
> mezi trámy, u klenby do spodního líce vrcholu, u šikmého stropu k **nejvyššímu** bodu zešikmení.
> Skladba podlahy a podhled tedy jdou proti limitu — v hmotě z B2 je to výška konstrukční, ne světlá.

## Přehled hodnot podle TS 01

TS 01 srovnává čtyři režimy vedle sebe (ČSN 73 4301, Pražské a Brněnské stavební předpisy,
vyhl. 146/2024 Sb.). Pro RD mimo Prahu a Brno platí posledně jmenovaná:

| | vyhl. 146/2024 Sb. | Praha / Brno |
|---|---|---|
| obytná / pobytová místnost RD a domu pro rodinnou rekreaci | **2 500 mm** (§ 38 odst. 1) | 2 500 mm |
| totéž v podkroví | **2 200 mm** (§ 38 odst. 1) | 2 300 mm |
| obytná / pobytová místnost bytového domu | 2 500 mm | **2 600 mm** |
| podchodná výška hlavních schodišť a chodeb RD | nestanoveno vyhláškou | 2 100 mm |
| hygienické prostory podle ČSN 73 4301 (2026) | — | **2 200 mm** (dříve 2 300 mm) |

> **V Praze a Brně jsou požadavky vyšší.** Studie pro pozemek v těchto městech se řídí jejich
> předpisy, ne vyhláškou — a dispozice v podkroví se tím mění, protože 2 300 mm proti 2 200 mm je
> u malého sklonu střechy rozdíl v šířce použitelného pásu místnosti.

**Odchylka v historii normy:** hranice nezapočítávané plochy u šikmého stropu je podle vyhlášek
(268/2009 i 146/2024) **1,2 m**, ale podle ČSN 73 4301 platné do 30. 6. 2026 byla **1 300 mm**
(TS 01, poznámka 3). Rozhoduje vyhláška.

## Spor, který má význam pro čtení nové normy

Nová ČSN 73 4301 (2026) uvádí ostatní výšky jako **podchodné, nejméně 2 100 mm** (čl. 6.2.3 domovní
komunikace, 8.5.1 vstupní prostor bytu, 8.6.1 další prostory bytu) a v bodě 3.24 ji definuje jako
svislou vzdálenost mezi povrchem podlahy a spodním lícem stropu, podhledu nebo prvku zasahujícího do
průchozí plochy. ČKAIT namítá, že **takto definovaná „podchodná výška" je definicí světlé výšky** —
srov. § 2 písm. j) vyhl. č. 460/2021 Sb. a bod 2.1 TS 01.

Pro studii z toho plyne praktický důsledek: **v textu vždy napsat, která výška se myslí a podle
kterého dokumentu**, protože stejné slovo v nové normě a v TS 01 znamená dvě různé věci.

## Co z toho kontroluje nástroj

`tools/dispozice/dispozice.py` ověří světlou výšku podlaží proti 2,5 m (resp. 2,2 m v podkroví) a
u místnosti se šikmým stropem podíl plochy nad nejmenší výškou. Co **nezkontroluje**: skladbu podlahy
a podhled — model nese konstrukční výšku podlaží, takže tenká skladba je předpoklad, ne fakt. Viz
[Index](Index.md).

## Related pages

- [Plochy a nejmenší rozměry místností](PlochyAMinimalniRozmery.md)
- [Schodiště](Schodiste.md)
- [Okna a denní osvětlení](OknaADenniOsvetleni.md)
