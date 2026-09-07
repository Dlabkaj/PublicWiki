# Legislativa a normy ČR

Právní rámec, ve kterém vzniká architektonická studie rodinného domu.

Ověřeno: 2026-07-27

## Podstránky

| Stránka | Obsah |
|---|---|
| [[PozadavkyNaVystavbu]] | Vyhl. č. 146/2024 Sb. + novela 97/2026 Sb. — odstupy, osvětlení, proslunění, stínění, rozměry, výšky, schodiště |
| [[NormyCSN]] | Kdy je ČSN závazná; ČSN 73 4301 nové vydání 6/2026; seznam norem pro RD |
| [[MestskePredpisy]] | Praha, Brno, Ostrava mají vlastní pravidla — celostátní vyhláška tam platí podpůrně |

## Hierarchie předpisů

```
zákon č. 283/2021 Sb. (stavební zákon)        ve znění k 1. 1. 2026 (nov. 330/2025 Sb.)
  └─ vyhl. č. 146/2024 Sb. o požadavcích na výstavbu   ve znění nov. 97/2026 Sb. od 1. 7. 2026
  └─ vyhl. č. 131/2024 Sb. o dokumentaci staveb        (typy PD — studie mezi nimi NENÍ)
  └─ nařízení Prahy 12/2024 / Brna 14/2024 / Ostravy   (přednost před 146/2024 tam, kde platí)
       └─ ČSN                                          závazné jen přes výlučný odkaz, viz NormyCSN
  └─ územní plán obce / regulační plán                 (konkrétní pozemek — dohledat vždy)
```

## Tři věci, které musí agent vědět nazpaměť

1. **Proslunění se u rodinných domů nevyžaduje** (od 1. 7. 2024). Prokazuje se denní osvětlení. Většina online rad i starších podkladů tvrdí opak. Viz [[PozadavkyNaVystavbu]].
2. **Zůstal jediný číselný odstup: 2 m od hranice pozemku.** Pravidlo „7 m mezi domy" bylo zrušeno. Vzájemný odstup se dnes řeší přes stínění (úhel 45°).
3. **ČSN nejsou samy o sobě závazné.** Než agent řekne „norma to zakazuje", ověří, jestli na ni vyhláška odkazuje výlučně (příloha č. 14) nebo indikativně (§ 94).

## Právní postavení samotné studie

Studie není zákonem vyžadovaná, není projektová dokumentace, na povolení nestačí, a PD pro RD musí zpracovat autorizovaná osoba. Ověřeno a sepsáno v sekci *Právní postavení studie (ČR)* ve skillu agenta AIArchitect (`.claude/skills/architectural-study/SKILL.md` v repozitáři agenta) — zde se to záměrně neduplikuje, aby to nedivergovalo. Právní rozbor viz [[../ZivnostOdpovednostCR/Index]].

Otevřená právní otázka (živnost, odpovědnost za chybu ve studii) je v [[../ZivnostOdpovednostCR/Index]].

## Co tady zatím chybí

- **Požární bezpečnost RD** — odstupové vzdálenosti požárně nebezpečného prostoru, ČSN 73 0833. Vůbec nezpracováno, přitom může omezit osazení domu na pozemku.
- **Energetika** — ČSN 73 0540, PENB, nZEB požadavky.
- **Povolovací proces** — jednotné povolení, lhůty, kdo je stavební úřad. Studie do procesu nevstupuje, ale klient se ptát bude.
- **Ochranná pásma sítí a komunikací** — samostatné předpisy (zák. 458/2000 Sb., 13/1997 Sb.).
