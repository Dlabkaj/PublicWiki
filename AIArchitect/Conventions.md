# Konvence — wiki pro agenta AIArchitect

Pravidla pro psaní a údržbu stránek, které agent AIArchitect čte a zapisuje. Přečti dřív, než do wiki cokoliv zapíšeš.

Ověřeno: 2026-08-30

## K čemu wiki je

Wiki drží **ověřená externí fakta** — legislativu, normy, ceny, nástroje. Nedrží postup práce (to je `SKILL.md` v repozitáři agenta) ani data konkrétního klienta (to je `userInput/` a `output/`).

Test: *Platilo by to i pro úplně jiného klienta?* Ano → wiki. Ne → `output/`.

Druhý test, protože jde o **veřejný** repozitář: *Smí to vidět kdokoliv?* Ne → soukromá wiki, ne sem. Čísla parcel, výpisy z LV, jména vlastníků do veřejné wiki nepatří nikdy.

## Struktura

```
<koren wiki>/
  Index.md            seznam všech témat — aktualizuj při každém přidání/odebrání stránky
  AIArchitect/        věci specifické pro agenta (tato složka)
    Index.md          mapa téma → fáze skillu, stav rešerší, otevřené body
    Conventions.md    tento soubor
    Log.md            chronologický záznam rešerší, nejnovější nahoře
  <Tema>/
    Index.md          přehledová stránka tématu + tabulka podstránek
    <Podtema>.md      jedna podstránka na koncept, který přesáhne ~300 znaků
```

Tématické složky se **nezanořují pod `AIArchitect/`** — fakta o legislativě nebo cenách používají i jiné projekty.

## Formát stránky

- Nadpis H1 = název stránky. Pod ním jednořádkový popis, k čemu stránka je.
- **Řádek `Ověřeno: RRRR-MM-DD`** hned pod popisem. Bez data je stránka podezřelá.
- Sekce H2 podle konceptů, ne podle zdrojů.
- Odkazy uvnitř složky `[[Podtema]]`, mezi složkami `[[../Tema/Podtema]]`.
- Na konci sekce **Zdroje** — číslovaný seznam URL.

## Citace a ověřování

- **Každý konkrétní údaj má zdroj.** Číslo, paragraf, datum, cena → odkaz do sekce Zdroje.
- **Právní ustanovení**: vždy název předpisu + číslo Sb. + paragraf a odstavec. `§ 11 odst. 2 vyhl. č. 146/2024 Sb.` Ne „podle vyhlášky o výstavbě".
- **Značka `*(neověřeno)*`** u údaje z jediného zdroje, nebo tam, kde se zdroje rozcházejí.
- **Značka `*(1 zdroj)*`** u údaje, který sedí, ale nemá druhé potvrzení.
- **Rozpor mezi zdroji se nepřepisuje** — zapiš obě verze i se zdroji a označ `⚠️ ROZPOR`.
- Sekundární zdroj (blog, článek) je vstup, ne důkaz. U paragrafů se dohledává primární text předpisu.

## Aktuálnost

Legislativa a ceny se mění. Proto:

- U každého předpisu uveď **znění ke dni** a poslední novelu, o které víš.
- Stránka starší než ~6 měsíců se před použitím pro klienta **znovu ověří**, ne opíše.
- Zrušené předpisy se nemažou — přesunou se do sekce *Historie* s datem zrušení. Klient může mít starší dokumentaci.

## Údržba

Po každém zápisu do wiki:

1. Aktualizuj `Index.md` v kořeni wiki (nová stránka nebo změněný popis).
2. Přidej záznam do [[Log]] — datum, téma, co přibylo, kolik zdrojů.
