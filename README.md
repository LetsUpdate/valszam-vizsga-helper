# ValszamVizsgaHelper 📡

**Interaktív valószínűségszámítás vizsga feladatfelismerő és segédlet** az **Óbudai Egyetem Neumann János Informatikai Kar (OE NIK)** hallgatóinak.

> Valószínűségszámítás és matematikai statisztika kollokvium / vizsga felkészülés — mérnökinformatikus szak.

🔗 **Élő verzió:** https://letsupdate.github.io/valszam-vizsga-helper/

---

## Mi ez?

A **ValszamVizsgaHelper** egy önálló, egyetlen HTML-fájlból álló tanulósegéd, ami abban segít,
hogy egy vizsgafeladatról **azonnal felismerd, milyen eloszlás vagy próba tartozik hozzá**,
és emlékeztet a tipikus buktatókra. Nincs build, nincs telepítés — csak nyisd meg a böngészőben.

## Funkciók

- 📡 **Gyors radar** — kereshető kártyarács az összes eloszlás- és próbatípussal.
- 🧭 **Felismerő** — döntési fa, ami kérdésről kérdésre elvezet a helyes típushoz.
- 🔀 **Mikor melyik?** — könnyen összekeverhető párok szembeállítása (pl. Poisson vs. Exponenciális).
- 🎯 **Kvíz** — gyakorló kérdések magyarázattal.
- 📐 **Táblázat** — Φ, u, t és e⁻ᵏ kritikus értékek referenciatáblái.
- 📖 **Részletes** — minden típus képletekkel, kulcsszavakkal és kidolgozott mintapéldával.

## Témakörök

Diszkrét és folytonos eloszlások (binomiális, hipergeometriai, Poisson, geometriai,
egyenletes, exponenciális, normális), a centrális határeloszlás-tétel, valamint
hipotézisvizsgálat (u-próba, t-próba) — a leggyakoribb vizsgatípusok fontossági sorrendben.

## Használat

Nyisd meg a [`valszam_feladatfelismero_v2.html`](valszam_feladatfelismero_v2.html)
fájlt bármelyik modern böngészőben. A matematikai képleteket a [KaTeX](https://katex.org/)
rendereli (CDN-ről). Nincs szükség internetkapcsolat nélküli telepítésre, csak a KaTeX CDN-hez.

## A repó tartalma

| Fájl | Szerep |
|------|--------|
| `valszam_feladatfelismero_v2.html` | Az interaktív feladatfelismerő (a fő eszköz). |
| `index.html` | Átirányító a feladatfelismerőre (GitHub Pages kezdőlap). |
| `assets/valszam_osszefoglalo.md` | Vizsga-összefoglaló: 13 eloszlás/próba típus, fontossági sorrendben. |
| `assets/valszam_feladatgyujtemeny.md` | Feladatgyűjtemény valós vizsgapéldákkal. |
| `assets/docs/projekt_dokumentacio.md` | Projektdokumentáció. |

## Jogi megjegyzés

Nem hivatalos, hallgatói felkészülést segítő anyag. Nem áll kapcsolatban az
Óbudai Egyetemmel. A tartalom pontosságáért nem vállalunk felelősséget — vizsga előtt
mindig ellenőrizd a hivatalos jegyzetekkel.

---

_Made for OE NIK valszám survivors. 🎓_
