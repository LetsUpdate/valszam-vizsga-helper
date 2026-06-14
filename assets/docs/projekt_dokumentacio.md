# Valszám Projekt — Dokumentáció

> **Cél:** Valószínűségszámítás és matematikai statisztika vizsgafelkészítés segédeszközei.
> **Forrásanyag:** Dr. Kárász Péter, BME — 2014-es kollokvium (`p142k1m.pdf`)

---

## Fájlok a projektben

```
Valszám/
├── valszam_feladatlap_megoldasok_nelkul.pdf   ← nyomtatható feladatlap (4 oldal)
├── valszam_feladatfelismero_v2.html            ← interaktív feladatfelismerő radar
└── docs/
    └── projekt_dokumentacio.md                 ← ez a fájl
```

---

## 1. Megoldás nélküli feladatlap PDF

**Fájl:** `valszam_feladatlap_megoldasok_nelkul.pdf`

Az eredeti vizsgafeladatlap (`p142k1m.pdf`) alapján generált, megoldásoktól megtisztított nyomtatható verzió. A feladatok szövege változatlan, minden feladat után üres válaszmező található, amelynek mérete arányos a feladat nehézségével.

### Szerkezet

Az eredeti kollokvium 3+10 feladatból áll:

**Számítási feladatok (1–3. feladat, mindegyik 3 részből):**
| Feladat | Típus | Pont |
|---------|-------|------|
| 1. | Exponenciális eloszlás | 2+3+4 |
| 2. | Binomiális / Poisson / Normális | 2+4+4 |
| 3. | Adott sűrűségfüggvény | 4+4+8 |

**Elméleti kérdések (4–13. feladat):**
10 db elméleti kérdés, egyenként 2–4 pont értékű.

### Technikai megvalósítás

**Generator script:** `gen_feladatlap.py` (ReportLab alapú Python szkript)

Kulcs paraméterek:
```python
M  = 2.0*cm          # margók
FS = 9.5             # betűméret
LH = FS * 1.38       # sorköz

doc = SimpleDocTemplate(out, pagesize=A4,
    leftMargin=M, rightMargin=M,
    topMargin=M, bottomMargin=M*0.6)   # 0.6 = kritikus érték!
```

**Fontok:** LiberationSans TTF (Helvetica nem támogatja az ő, ű karaktereket).

**Fontos tanulság — miért 0.6 a bottomMargin szorzó:**
A `KeepTogether` flowable eltávolítása után (ami oldalpazarlást okozott) az utolsó elméleti feladat válaszmezője éppen túlcsordult az 5. oldalra. A `M*0.6` (≈1.2 cm) bottomMargin elegendő helyet adott ahhoz, hogy minden tartalom elférjen 4 oldalon.

**Válaszmező méretek (cm-ben):**
- Számítási feladatok: 1a→2.0, 1b→3.2, 1c→3.8, 2a→2.5, 2b→3.2, 2c→3.8, 3a→1.8, 3b→3.5, 3c→7.5
- Elméleti kérdések: 2 pontos→2.5, 3 pontos→3.2, 4 pontos→3.5 (kivéve 10. kérdés: 2.2)

---

## 2. Feladatfelismerő radar

**Fájl:** `valszam_feladatfelismero_v2.html`

Interaktív HTML eszköz vizsgán / tanulás közben való gyors feladattípus-azonosításhoz. Két nézetben érhető el:

### Nézetek

**📡 Gyors radar tab:**
Kompakt kártyarács, kategóriánként csoportosítva. Minden kártyán:
- Kulcsszó chipek (mire keress a feladatszövegben)
- Legfontosabb buktató
- **Kattintásra popup** nyílik a teljes részletes leírással

**📖 Részletes tab:**
Kinyitható accordion kártyák. Minden típusnál 6 szekció:
1. Lényeg (egy mondatos összefoglaló)
2. Kulcsszavak (chipek)
3. Képletek (KaTeX renderelt matematika)
4. Paraméterek (szimbólum → leírás táblázat)
5. Buktatók (leggyakoribb hibák)
6. Összefüggés más típusokkal + Memória-hook

### Lefedett eloszlástípusok (13 db)

| Kategória | Típusok |
|-----------|---------|
| **Diszkrét** | Binomiális, Poisson, Geometriai, Hipergeometriai |
| **Folytonos** | Egyenletes, Exponenciális, Normális, Adott sűrűségfüggvény |
| **Statisztika** | Konfidencia-intervallum, Hipotézisvizsgálat (t/u-próba) |
| **Alapok** | Feltételes valószínűség / Bayes, Csebisev / Markov, CHT |

### Technikai részletek

- **Önálló HTML fájl** — nincs szerver, böngészőből nyitható
- **KaTeX** matematika renderelés (cdnjs CDN, v0.16.9)
- **CSS változók** + dark mode (`prefers-color-scheme: dark`)
- **Adatvezérelt** — minden tartalom egyetlen JS `T[]` tömbből generálódik
- Popup: CSS transition-nel animált, ESC-pel zárható

---

## 3. Legfontosabb vizsgacsapdák (összefoglaló)

Ezek kerültek elő a tutoring session során:

| Csapda | Részlet |
|--------|---------|
| **Poisson vs Exponenciális** | Poisson = HÁNY esemény adott idő alatt; Exponenciális = MENNYI IDŐ telik el két esemény KÖZÖTT. Egy folyamat két oldala. |
| **λ iránya** | Exponenciálisnál λ = 1/E(X). Ha az átlag 50 perc → λ = 1/50, NEM 50! |
| **Binomiális vs Hipergeometriai** | Visszatevéssel → Binomiális; visszatevés nélkül → Hipergeometriai |
| **Φ(−x) szimmetria** | Φ(−x) = 1 − Φ(x) — negatív z-értéknél kötelező alkalmazni |
| **CHT összeg vs átlag** | Sₙ szórása: σ√n; X̄ szórása: σ/√n — különböző, ne cseréld! |
| **H₀ tartalmazza az egyenlőséget** | H₀: μ ≥ μ₀; H₁: μ < μ₀ — soha ne fordítsd meg |
| **C meghatározása** | Adott sűrűségfüggvénynél az (a) rész MINDIG C = 1/∫f(x)dx |
| **t vs u próba** | Ismeretlen σ + n<30 → t-próba, f=n−1; ismert σ vagy n≥30 → u-próba |

---

## 4. Átállás GitHub Copilot-ra — kontextus amit add meg

Ha ezt a projektet GitHub Copilot-ban folytatod, az alábbi kontextust érdemes az első üzenetbe másolni:

```
## Projekt kontextus

Valószínűségszámítás vizsgafelkészítő projekt, BME.
Forrás: Dr. Kárász Péter 2014-es kollokvium (p142k1m.pdf).

### Fájlok
- valszam_feladatlap_megoldasok_nelkul.pdf — megoldás nélküli 4 oldalas nyomtatható feladatlap
- valszam_feladatfelismero_v2.html — interaktív feladatfelismerő, 13 eloszlástípus,
  KaTeX képletek, popup modal, CSS dark mode, adatvezérelt (T[] tömb a JS-ben)

### Aktív tutoring feladatlap feladatai
1. feladat: Exponenciális eloszlás (λ = 1/E(X) kritikus!)
2. feladat: [folytatandó]
3. feladat: Adott sűrűségfüggvény

### Pedagógiai irány
Szókratikus módszer: kérdésekkel vezesse a hallgatót a felismerésre, 
ne adja meg rögtön a választ. Először a típusfelismerés, aztán a képlet,
aztán a számítás lépéseiben segít.
```

### Ami Copilot-ban nem lesz meg (ami Claude-ban volt):
- A valszam-tutor skill (SKILL.md alapú Szókratikus tutoring logika)
- A `gen_feladatlap.py` szkript közvetlen futtatása
- Automatikus PDF generálás és ellenőrzés

---

## 5. Folytatandó feladatok

- [ ] Tutoring session folytatása: 1b, 1c, 2a–2c, 3a–3c feladatok megoldása
- [ ] A feladatfelismerő radar esetleges bővítése (pl. Negatív binomiális, χ² próba)
- [ ] A radar mobilnézet finomhangolása

---

*Generálva: 2026-06-14 | Claude Sonnet 4.6 (Cowork mode)*
