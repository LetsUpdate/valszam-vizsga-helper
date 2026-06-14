# Valószínűségszámítás & Statisztika — Vizsgaösszefoglaló

> Feladattípusok fontossági sorrendben, felismerési tippekkel, képletekkel és buktatókkal.

---

## 1. Normális eloszlás ⭐⭐⭐

**Lényeg:** Szimmetrikus harang-görbe, m várható érték körül, σ szórással. A vizsgán a legtöbbször előforduló folytonos eloszlás.

**Mikor ismerem fel?**
„**normális eloszlású**", „**várható értéke m, szórása σ**", természetes mérési adatok (tömeg, magasság, mérési hiba).

**Képlet — standardizálás:**
```
X ~ N(m, σ²)  →  X* = (X - m) / σ  →  X* ~ N(0, 1)
```
Ezután Φ táblázatból olvasunk.

**Fontos azonosságok:**
```
P(X ≤ a)  = Φ((a - m) / σ)
P(X ≥ a)  = 1 - Φ((a - m) / σ)
P(a ≤ X ≤ b) = Φ((b-m)/σ) - Φ((a-m)/σ)
Φ(-x) = 1 - Φ(x)      ← SZIMMETRIA, vizsgán kritikus!
```

**Várható érték és szórásnégyzet:**
```
E(X) = m,   D²(X) = σ²
```

**Leggyakoribb buktatók:**
- Φ(-x) = 1 - Φ(x) szimmetria elfelejtése → negatív z-értéknél kötelező
- P(X ≥ a) = **1 −** Φ(...), nem csak Φ(...)
- Szórás (σ) ≠ szórásnégyzet (σ²) — a képletbe σ kerül, nem σ²
- Ha n db átlagáról kérdez: szórás = σ/√n (a minta átlagának szórása)

**Összefüggés más típusokkal:**
- Nagy mintánál Binomiális → Normális közelítés (ha n·p > 5 és n·(1-p) > 5)
- Exponenciális → nem szimmetrikus, ne keverd

**Hook:** „Normális = a természet kedvenc eloszlása — harang alakú, m körül szimmetrikus."

---

## 2. Hipotézisvizsgálat ⭐⭐⭐

**Lényeg:** Mintaadatból döntünk: igaz-e egy állítás a populáció paraméteréről?

**Mikor ismerem fel?**
„**döntsük el**", „**szignifikanciaszint α**", „**állítás a várható értékről / arányról**" → Hipotézisvizsgálat.

**Lépések:**
1. **H0 és H1 felírása** — H0 mindig tartalmaz `=`-t; H1 az egyenlőtlenséget
2. **Próbastatisztika kiválasztása:**
   - Ismert σ → **u-próba**: `u = (x̄ - μ₀) / (σ / √n)`
   - Ismeretlen σ, n < 30 → **t-próba**: `t = (x̄ - μ₀) / (s / √n)`
   - Ismeretlen σ, n ≥ 30 → u-próba is elfogadható
3. **Kritikus érték táblázatból** (u_α vagy t_{α, n-1})
4. **Döntés:** Ha |próbastatisztika| > kritikus érték → **H0 elvetése**

**Egy- vs kétoldali próba:**
- H1: μ ≠ μ₀ → kétoldali, α/2 mindkét oldalon
- H1: μ > μ₀ vagy μ < μ₀ → egyoldali, α egy oldalon

**Leggyakoribb buktatók:**
- H0-ba az `=` kerül, H1-be az `≠` / `>` / `<`
- Egyoldali vs kétoldali tévesztése → más kritikus értéket kell keresni
- s (tapasztalati szórás) és σ (elméleti szórás) összekeverése
- Kis n-nél (n < 30) ismeretlen σ esetén t-eloszlás, nem normális!

**Összefüggés más típusokkal:**
Konfidencia-intervallummal **duális kapcsolat**: ugyanaz az α, de más kérdés. Ha a próbastatisztika a kritikus tartományba esik ↔ μ₀ kívül esik a konfidencia-intervallumon.

**Hook:** „H0 az ártatlanság vélelme — addig nem vetjük el, amíg az adatok nem bizonyítják az ellenkezőjét."

---

## 3. Konfidencia-intervallum ⭐⭐⭐

**Lényeg:** Mintaadatból becsüljük meg, hol helyezkedik el az ismeretlen populációs paraméter adott megbízhatósággal.

**Mikor ismerem fel?**
„**X%-os megbízhatósággal**", „**intervallumbecslés**", „**adjunk konfidencia-intervallumot**" → KI.

**Képletek — várható értékre:**

| Eset | Képlet |
|------|--------|
| Ismert σ | x̄ ± u_{α/2} · σ/√n |
| Ismeretlen σ, n ≥ 30 | x̄ ± u_{α/2} · s/√n |
| Ismeretlen σ, n < 30 | x̄ ± t_{α/2, n-1} · s/√n |

**Megbízhatósági szint és α kapcsolata:**
```
Megbízhatóság = 1 - α
pl. 95%-os → α = 0,05 → u_{α/2} = u_{0,025} = 1,96
    99%-os → α = 0,01 → u_{α/2} = u_{0,005} = 2,576
```

**Leggyakoribb buktatók:**
- α/2 elfelejtése kétoldali KI-nél → rossz kritikus érték
- s vs σ összekeverése
- n < 30 esetén t-eloszlás szükséges, nem normális
- A KI nem azt jelenti, hogy 95% valószínűséggel tartalmazza μ-t — μ fix, a KI véletlenszerű

**Hook:** „KI = hálót vetünk a paraméterre; 95%-os KI → 100 ilyen hálóból 95 fogja meg."

---

## 4. Binomiális eloszlás ⭐⭐

**Lényeg:** n független kísérlet, mindegyiken p valószínűséggel „siker" — összesen hányszor lesz siker?

**Mikor ismerem fel?**
„**n független kísérlet**", „**visszatevéssel**", fix **p** és fix **n** → Binomiális.

**Képlet:**
```
X ~ B(n, p)
P(X = k) = C(n,k) · p^k · (1-p)^(n-k)

E(X) = n·p
D²(X) = n·p·(1-p)
```

**Leggyakoribb buktatók:**
- C(n,k) kiszámítása: n! / (k! · (n-k)!)
- P(X ≥ k) = 1 - P(X ≤ k-1) — kumulatív valószínűségnél komplemens!
- E(X) és D²(X) kötelező tudni
- Ha p nagyon kicsi és n nagy → Poisson közelítés (λ = n·p)

**Összefüggés más típusokkal:**
- Visszatevés nélkül + véges populáció → **Hipergeometriai**
- n·p < 5 és n nagy → **Poisson** közelítés
- n nagy, n·p > 5, n·(1-p) > 5 → **Normális** közelítés

**Hook:** „Binomiális = érmét dobálok n-szer, p eséllyel fejre — hányszor lesz fej?"

---

## 5. Poisson-eloszlás ⭐⭐

**Lényeg:** Ritkán bekövetkező esemény, ismert átlaggal, adott időintervallumon vagy területen.

**Mikor ismerem fel?**
„**átlagosan λ darab**" + „**időintervallumon**" / „**területen**" → Poisson.

**Képlet:**
```
X ~ Poisson(λ)
P(X = k) = (λ^k · e^(-λ)) / k!

E(X) = λ
D²(X) = λ
```

**Leggyakoribb buktatók:**
- **λ mindig az adott intervallumra vonatkozzon!** Ha óránkénti adat van, de percet kérdez → λ-t arányosan átváltani
- e^(-λ) nem hagyható el a képletből
- Várható érték = szórásnégyzet = λ (ezt megkérdezhetik)

**Összefüggés más típusokkal:**
- Binomiális közelítése ha n·p < 5 és n nagy (λ = n·p)
- Exponenciális: ha Poisson az eseményszámot adja, az Exponenciális az eseményközi időt

**Hook:** „Poisson = hány autó jön 10 perc alatt, ha ismerjük az átlagos érkezési rátát?"

---

## 6. Feltételes valószínűség és Bayes-tétel ⭐⭐

**Lényeg:** Hogyan változik egy esemény valószínűsége, ha már tudunk valamit?

**Mikor ismerem fel?**
„**feltéve hogy**", „**ha már bekövetkezett**", „**P(A|B)**" → feltételes valószínűség.
„**visszafelé feltételes**", „**mi annak valószínűsége, hogy ... adott ...**" + több lehetséges ok → **Bayes**.

**Képletek:**
```
Feltételes:   P(A|B) = P(A ∩ B) / P(B)

Teljes valószínűség:
P(B) = P(B|A₁)·P(A₁) + P(B|A₂)·P(A₂) + ... + P(B|Aₙ)·P(Aₙ)

Bayes-tétel:
P(Aᵢ|B) = P(B|Aᵢ)·P(Aᵢ) / P(B)
```

**Mikor Bayes?**
Ha van több **„ok"** (A₁, A₂, ...) és egy **„tünet"** (B), és azt kérdezik: melyik ok okozta B-t?
Pl.: „Pozitív a teszt — mi a valószínűsége, hogy valóban beteg?"

**Leggyakoribb buktatók:**
- P(A|B) ≠ P(B|A) — fordítva is van ilyen feladat!
- Teljes valószínűség tétele kell Bayes előtt (P(B) nevező kiszámítása)
- A₁, A₂, ... legyenek teljes eseményrendszer (diszjunktak, összegük 1)

**Hook:** „Bayes = detektív logika — ismert az eredmény, keressük a legvalószínűbb okot."

---

## 7. Geometriai eloszlás ⭐⭐

**Lényeg:** Addig ismételjük a kísérletet, amíg először sikerül — hányadik kísérletben?

**Mikor ismerem fel?**
„**addig ismételjük amíg**", „**hányadik kísérletben következik be először**" → Geometriai.

**Képlet:**
```
X ~ Geo(p)
P(X = k) = (1-p)^(k-1) · p     (k = 1, 2, 3, ...)

E(X) = 1/p
D²(X) = (1-p) / p²
```

**Leggyakoribb buktatók:**
- k a SIKERES kísérlet sorszáma (nem az előtte lévő sikerteleneké!)
- P(X > k) = (1-p)^k — ezt közvetlenül is lehet számolni
- E(X) = 1/p, nem p

**Összefüggés más típusokkal:**
- Speciális Binomiális: az első siker keresése
- **Memóriátlan**: P(X > m+n | X > m) = P(X > n) — akár az Exponenciálisnál

**Hook:** „Geometriai = dobálom a kockát amíg hatost nem dobok — hányadik dobásnál lesz meg?"

---

## 8. Hipergeometriai eloszlás ⭐⭐

**Lényeg:** Véges populációból **visszatevés nélkül** húzunk — hány „speciális" kerül a mintába?

**Mikor ismerem fel?**
„**visszatevés nélkül**", „**N elemből n-t húzunk**", „**M selejt/hibás/piros van**" → Hipergeometriai.

**Képlet:**
```
X ~ HGeo(N, M, n)
P(X = k) = C(M,k) · C(N-M, n-k) / C(N, n)

E(X) = n · M/N
D²(X) = n · (M/N) · (1 - M/N) · (N-n)/(N-1)
```
ahol: N = populáció, M = „speciális" elemek száma, n = húzott elemek száma, k = keresett darab.

**Leggyakoribb buktatók:**
- N, M, n, k összekeverése → mindig írd le mi mit jelöl!
- Ha n << N → Binomiális közelítés is elégséges (p = M/N)
- A nevező mindig C(N,n)

**Hook:** „Hipergeometriai = 100 golyóból 20 piros, 10-et húzok visszatevés nélkül — hány piros lesz?"

---

## 9. Exponenciális eloszlás ⭐⭐

**Lényeg:** Várakozási idő két Poisson-esemény között; élettartam modellezése.

**Mikor ismerem fel?**
„**átlagosan X ideig tart**", „**várakozási idő**", „**élettartam**", „**memóriátlan**" → Exponenciális.

**Képlet:**
```
X ~ Exp(λ)
f(x) = λ · e^(-λx),   x ≥ 0
F(x) = P(X ≤ x) = 1 - e^(-λx)
P(X > x) = e^(-λx)

E(X) = 1/λ
D²(X) = 1/λ²
```

**Memóriátlan tulajdonság:**
```
P(X > s+t | X > s) = P(X > t)
```
„Ha már s ideig várakoztam, ez nem csökkenti a maradék várakozást."

**Leggyakoribb buktatók:**
- λ az **intenzitás** (1/átlag), nem az átlag! Ha átlag = 5, akkor λ = 1/5
- P(X > a) = e^(-λa) — egyszerű, de sokszor elfelejtik a formulát
- Memóriátlan tulajdonság könnyen megkérdezik

**Hook:** „Exponenciális = Poisson esemény közbeni várakozási idő."

---

## 10. Klasszikus valószínűség ⭐

**Lényeg:** Egyforma valószínűségű elemi eseményeknél: kedvező / összes.

**Mikor ismerem fel?**
Véges, egyforma valószínűségű esetek; kártyahúzás, kockadobás, kombinatorikai feladatok.

**Képlet:**
```
P(A) = |A| / |Ω|   =   kedvező esetek száma / összes eset száma
```

**Kombinatorika-eszköztár:**
```
Permutáció (sorrend számít, visszatevés nélkül):  n!
Variáció (k-t választunk n-ből, sorrend számít):  n! / (n-k)!   vagy   nᵏ visszatevéssel
Kombináció (k-t választunk n-ből, sorrend NEM számít): C(n,k) = n! / (k! · (n-k)!)
```

**Leggyakoribb buktatók:**
- Sorrend számít-e? → Ha igen: variáció/permutáció. Ha nem: kombináció.
- Visszatevéssel vagy anélkül? → visszatevéssel: nᵏ; anélkül: n!/(n-k)!
- Komplementer esemény: P(Ā) = 1 - P(A) — sokszor könnyebb

**Hook:** „Klasszikus = kártyahúzás, kockadobás — számolj és osszál."

---

## 11. Egyenlőtlenségek: Markov és Csebisev ⭐

**Lényeg:** Valószínűségi korlátok — ha nem ismerjük az eloszlást, csak E(X) és D(X) adott.

**Mikor ismerem fel?**
„**becsüljük meg felülről**", „**adjunk korlátot**", az eloszlás ismeretlen → Egyenlőtlenség.

**Markov-egyenlőtlenség:**
```
Ha X ≥ 0:    P(X ≥ a) ≤ E(X) / a
```
Csak E(X) kell, X nemnegatív legyen.

**Csebisev-egyenlőtlenség:**
```
P(|X - E(X)| ≥ ε) ≤ D²(X) / ε²
```
E(X) és D²(X) is kell, de X lehet negatív is.

**Melyiket mikor?**

| | Markov | Csebisev |
|--|--------|----------|
| Kell | E(X), X ≥ 0 | E(X) + D²(X) |
| X lehet negatív? | Nem | Igen |
| Korlát formája | P(X ≥ a) | P(│X - m│ ≥ ε) |

**Leggyakoribb buktatók:**
- Markovnál X ≥ 0 feltétel kötelező
- Csebisevnél ε a várható értéktől való eltérés, nem a határérték maga
- Mindkét egyenlőtlenség **felső korlát** — a valódi valószínűség ennél kisebb (vagy egyenlő) lehet

**Hook:** „Ha nem tudod az eloszlást, de van E(X) → Markov. Ha D²(X) is van → Csebisev."

---

## 12. Egyenletes eloszlás ⭐

**Lényeg:** A valószínűségi változó egyenletesen oszlik el egy [a, b] intervallumon.

**Mikor ismerem fel?**
„**egyenletesen oszlik el [a, b]-n**", „**véletlenszerűen érkezik a és b között**", „**minimum a, maximum b**" → Egyenletes.

**Képlet:**
```
X ~ U(a, b)
f(x) = 1 / (b-a),   a ≤ x ≤ b
F(x) = (x-a) / (b-a)
P(c ≤ X ≤ d) = (d-c) / (b-a)   ← egyszerűen intervallum-arány!

E(X) = (a+b) / 2
D²(X) = (b-a)² / 12
```

**Leggyakoribb buktatók:**
- P(c ≤ X ≤ d) = (d−c)/(b−a) — nincs szükség integrálásra, csak arány
- E(X) a középpont, D²(X)-ben 12 van a nevezőben (nem 6, nem 4)

**Hook:** „Egyenletes = minden pont ugyanolyan eséllyel — terület/hossz arány."

---

## 13. Pontbecslés ⭐

**Lényeg:** Mintaadatokból becsüljük az ismeretlen populációs paramétereket.

**Mikor ismerem fel?**
„**adjunk becslést**", „**becsüljük a várható értéket / szórást**" → Pontbecslés.

**Legfontosabb becslők:**

```
Várható érték becslése:     x̄ = (1/n) · Σxᵢ          (mintaátlag)

Szórásnégyzet becslése:     s² = 1/(n-1) · Σ(xᵢ - x̄)²   (TORZÍTATLAN!)
                              s  = √s²                      (tapasztalati szórás)

Arány becslése:             p̂ = k/n                      (k = sikerek száma)
```

**Leggyakoribb buktatók:**
- Torzítatlan szórásnégyzetnél n-1 van a nevezőben, nem n!
- Ha σ ismeretlen és n kicsi → t-eloszlást kell használni KI-nél

**Hook:** „Pontbecslés = egy szám helyett adunk, KI = egy intervallumot."

---

## 14. Korreláció és lineáris regresszió ⭐

**Lényeg:** Két változó közötti lineáris kapcsolat erőssége (korreláció) és egyenese (regresszió).

**Mikor ismerem fel?**
„**kapcsolat két változó között**", „**regressziós egyenes**", „**korrelációs együttható**" → Korreláció/Regresszió.

**Korrelációs együttható:**
```
r = Sxy / (Sx · Sy)

ahol:
Sxy = Σ(xᵢ - x̄)(yᵢ - ȳ) / (n-1)   (kovariancia)
Sx, Sy = tapasztalati szórások

-1 ≤ r ≤ 1
r ≈ 1:  erős pozitív lineáris kapcsolat
r ≈ -1: erős negatív lineáris kapcsolat
r ≈ 0:  nincs (lineáris) kapcsolat
```

**Regressziós egyenes (y-t x-re):**
```
ŷ = b₀ + b₁·x

b₁ = Sxy / Sx²    (meredekség)
b₀ = ȳ - b₁·x̄    (tengelymetszet)
```

**Leggyakoribb buktatók:**
- r = 0 nem jelenti, hogy nincs kapcsolat — csak lineáris kapcsolat nincs!
- b₁ és b₀ felcserélése
- Regressziós egyenes csak az adott x tartományán érvényes (extrapoláció veszélyes)

**Hook:** „r = lineáris kapcsolat erőssége; regresszió = az egyenes maga."

---

## Gyors döntési fa

```
Van eloszlás megadva?
├── Normális → standardizálás + Φ tábla
├── Poisson  → λ átváltás + képlet
├── Binomiális → C(n,k)·p^k·(1-p)^(n-k)
├── Geometriai → (1-p)^(k-1)·p
├── Hipergeometriai → visszatevés nélkül, C(M,k)·C(N-M,n-k)/C(N,n)
├── Exponenciális → e^(-λx), memóriátlan
└── Egyenletes → intervallum-arány

Statisztika feladat?
├── "Adjunk becslést" → Pontbecslés (x̄, s²)
├── "Konfidencia-intervallum" → x̄ ± u/t · s/√n
├── "Döntsük el" → Hipotézisvizsgálat (H0, H1, próbastatisztika)
└── "Kapcsolat két változó" → Korreláció / Regresszió

Korlát, ismeretlen eloszlás?
├── X ≥ 0, csak E(X) → Markov
└── Van D²(X) is → Csebisev

Feltételes / "Visszafelé" kérdés?
├── P(A|B) → Feltételes valószínűség
└── Több ok, egy tünet → Bayes-tétel
```

---

*Készült vizsgafelkészítéshez — minden típusnál: felismerés → képlet → buktatók.*
