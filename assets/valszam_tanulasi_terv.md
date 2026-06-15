# Valszám tanulási terv — egyszerű, felépíthető rendszer

> Az **Óbudai Egyetem NIK** valószínűségszámítás vizsgához. A vizsga lényege nem a
> levezetés, hanem a **felismerés + recept alkalmazása** — ezért a tanulás is erre épül.
> Interaktív változat: a [feladatfelismerő tool](../valszam_feladatfelismero_v2.html) **🎓 Tanulási út** füle.

---

## A rendszer egy mondatban

Nem 14 különálló dolgot tanulsz, hanem **3 családot → azon belül rétegenként a fontosság
szerint**, és minden típust ugyanazzal a 4-elemű kártyával raksz a fejedbe.

---

## 1. szint — A térkép (1 ülés, mielőtt bármit magolnál)

Előbb a váz, hogy legyen hova akasztani a részleteket:

- **Diszkrét** („hányszor? / hány db? / hányadik?", megszámolható)
  → Binomiális, Poisson, Geometriai, Hipergeometriai
- **Folytonos** („mennyi? / mennyi idő?", mérhető)
  → Normális, Exponenciális, Egyenletes, Adott sűrűségfüggvény f(x)
- **Statisztika** („mintából következtetünk")
  → Hipotézisvizsgálat, Konfidencia-intervallum, Pontbecslés
- **Valószínűségi alapok** (átszövik az egészet)
  → Klasszikus valószínűség, Bayes, Markov/Csebisev, CHT

👉 Eszköz: a **🧭 Felismerő** fül — ez maga a térkép.

## 2. szint — Felismerő szótár (a kulcsszó dönt)

A feladat szövegében szinte mindig van egy **árulkodó szókapcsolat**. Ezt kösd a
típushoz — a képlet már másodlagos. Ez a vizsga legfontosabb készsége.

| Ha ezt látod a szövegben… | …ez a típus |
|---|---|
| „visszatevés**sel**", fix n és p | **Binomiális** |
| „visszatevés **nélkül**", N elemből | **Hipergeometriai** |
| „**hányadik**ra jön az első siker" | **Geometriai** |
| „átlagosan λ db adott idő alatt" | **Poisson** |
| „mennyi **idő** két esemény közt", élettartam | **Exponenciális** |
| haranggörbe, „várható értéke m, szórása σ" | **Normális** |
| „adott f(x), C = ?" | **Sűrűségfüggvény f(x)** |
| „[a, b]-n egyenletesen", minden pont egyforma | **Egyenletes** |
| „döntse el / szignifikanciaszinten / azt állítják" | **Hipotézisvizsgálat** |
| „X%-os megbízhatósággal", intervallumbecslés | **Konfidencia-intervallum** |
| „feltéve hogy", visszafelé / megfordított kérdés | **Feltételes / Bayes** |
| „n darab összege / átlaga", nagy n (≥30) | **CHT** |
| „felső korlát", az eloszlás ismeretlen | **Csebisev / Markov** |

> A tool **🎓 Tanulási út** füljén ez a szótár kattintható: a típusra koppintva
> rögtön nyílik a részletes kártyája.

## 3. szint — A 3 leggyakoribb csapda (egy mondatban)

- **Poisson = darab, Exponenciális = idő.** Ugyanaz a folyamat két oldala; λ = 1/E(X)!
- **Összegnél σ√n, átlagnál σ/√n.** CHT: Sₙ-nél szorzol, X̄-nál osztasz — ne cseréld fel.
- **Negatív z-nél: 1 mínusz.** Φ(−x) = 1 − Φ(x) — a Φ-tábla csak pozitív értékeket ad.

## 4. szint — Rétegek fontosság szerint (ne mindent egyszerre!)

Az átmenőhöz (20/40) a mag sokszor elég:

| Réteg | Típusok | Cél |
|------|---------|-----|
| **🔴 Mag** ⭐⭐⭐ | Normális, Hipotézisvizsgálat, CHT, Binomiális, Poisson, Adott f(x) | Ezt **vasból**. Önmagában közel viszi az átmenőt. |
| **🟠 Gyakori** ⭐⭐ | Exponenciális, Konfidencia-intervallum, Bayes | Ezekkel van meg biztosan a 20+. |
| **🟡 Ráadás** ⭐ | Geometriai, Hipergeometriai, Egyenletes, Markov/Csebisev | Csak ha a mag már stabil. |

## 5. szint — Minden típusra ugyanaz a 4 kártya (FKKB)

Mindig pontosan ezt a négyet jegyzed meg egy típusról — semmi többet először:

1. **F — Felismerés:** 2-3 kulcsszó, amitől beugrik (pl. „visszatevéssel" → Binomiális)
2. **K — Képlet:** az 1 fő képlet
3. **K — Kata (recept):** a lépések sorrendje
4. **B — Bukta:** az 1 tipikus csapda (pl. Φ(−x) = 1 − Φ(x))

👉 A **📖 Részletes** fülön minden típusnál pont ez a 4 dolog ott van.

## 6. szint — A tanulási hurok (minden ülés ugyanígy, ~30-40 perc)

1. **Bemelegítés (2 perc):** végigkattintod a Felismerő fát, *hangosan* megnevezed a típust.
2. **1 új típus mélyen:** elolvasod az FKKB kártyát + **kézzel** megoldod a mintapéldáját.
3. **Aktív felidézés:** **🎯 Kvíz** a *már tanult* típusokra (nem olvasol — felidézel!).
4. **Hibajavítás:** amit elrontasz, azt 1 mondatban felírod magadnak.

## Ütemterv (példa, 2 hét)

| Napok | Mit |
|------|-----|
| 1–3. | A ⭐⭐⭐ **mag** (Normális, Hipotézisvizsgálat, CHT, Binomiális, Poisson, Adott f(x)) |
| 4–7. | A ⭐⭐ **gyakori** típusok |
| 8–10. | A ⭐ **ráadás** típusok |
| 11–14. | Vegyes **Kvíz** + régi vizsgák, gyenge pontok pótlása |

---

## Haladáskövető checklist

Pipáld ki, amit már **vasból tudsz** (felismerés + képlet + recept + bukta).
Interaktív, mentett változata a tool **🎓 Tanulási út** füle alján van.

**🔴 Mag — ezt vasból (önmagában közel viszi az átmenőt):**

- [ ] Binomiális eloszlás ⭐⭐⭐
- [ ] Poisson eloszlás ⭐⭐⭐
- [ ] Normális eloszlás ⭐⭐⭐
- [ ] Adott sűrűségfüggvény f(x) ⭐⭐⭐
- [ ] Hipotézisvizsgálat (t / u-próba) ⭐⭐⭐
- [ ] Centrális határeloszlás tétel (CHT) ⭐⭐⭐

**🟠 Gyakori — erre építs (ezekkel van meg biztosan a 20+):**

- [ ] Exponenciális eloszlás ⭐⭐
- [ ] Konfidencia-intervallum ⭐⭐
- [ ] Feltételes valószínűség / Bayes ⭐⭐

**🟡 Ráadás — ha a mag stabil (a biztos pont megszerzése után):**

- [ ] Geometriai eloszlás ⭐
- [ ] Hipergeometriai eloszlás ⭐
- [ ] Egyenletes eloszlás [a, b] ⭐
- [ ] Csebisev / Markov egyenlőtlenség ⭐

---

_A kulcs: **felismerés-először, aktív felidézés, rétegenként** — nem lineáris átolvasás._
