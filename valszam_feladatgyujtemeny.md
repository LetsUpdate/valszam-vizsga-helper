# VALSZÁM VIZSGAFELKÉSZÍTÉS
## Feladatgyűjtemény és Gyakorló Feladatsor
_Mérnökinformatikus II. | Val.szám. és mat. stat. | 2014–2023 vizsgák alapján_

---

## VIZSGASTRATÉGIA — 20/40 pont kell az átmenéshez

Témák fontossági sorrendben:

1. **Hipotézisvizsgálat (t-próba)** → 8p, 100%-os előfordulás, mindig ugyanaz az algoritmus
2. **Poisson eloszlás** → 3–4p, 90%+ előfordulás (2020+ minden vizsgán)
3. **Binomiális eloszlás** → 3–4p, 90%+ előfordulás
4. **Normális eloszlás + CHT** → 4–6p, 90%+ előfordulás
5. **Adott sűrűségfüggvény (a) rész** → 4p, 2022+ minden vizsgán önálló F2

**1–4 témával: ~20–24p garantált | +5. téma: ~25–28p (biztos tartalék)**

---

## 1. Hipotézisvizsgálat (t-próba)

Minden vizsgán jelen van — mindig az utolsó feladat, mindig 8 pont. Az algoritmus sosem változik.

### Az algoritmus

```
LÉPÉS 1 — Hipotézisek felírása:
   H0: mu = mu0        (nullhipotézis)
   H1: mu != mu0       (kétoldali)  |  mu > mu0  vagy  mu < mu0  (egyoldali)

LÉPÉS 2 — Mintastatisztikák:
   x_atlag  =  Sxi / n
   s2       =  [ Sxi2  -  (Sxi)^2 / n ]  /  (n - 1)
   s        =  sqrt(s2)

LÉPÉS 3 — Tesztstatisztika:
   t  =  (x_atlag - mu0) / (s / sqrt(n))

LÉPÉS 4 — Kritikus érték táblázatból:
   df = n - 1,   alfa = 0.05  -->  t(0.025; n-1)  [kétoldalinál]

LÉPÉS 5 — Döntés:
   |t| > t_krit  -->  H0 ELUTASÍTVA  (szignifikáns eltérés)
   |t| <= t_krit -->  H0 nem utasítható el
```

### Valódi vizsgafeladatok

**▶ 2023. jún. 27.** _(8 pont)_

Azt állítják, hogy Shaquille O'Neal egy-egy meccsen töltött játékidejének várható értéke eléri a három játéknegyednyi időt (3×12 = 36 perc). Ellenőrzésre 150 meccs adatát választják ki:
- Sxi = 5 205    és    Sxi2 = 185 286

Döntse a minta alapján! (5%-os szignifikanciaszinten)

---

**▶ 2023. jún. 9.** _(8 pont)_

Azt állítják, hogy Shaquille O'Neal egy meccsen átlagosan legalább 27 pontot szerez. 100 meccs adatai: Sxi = 2 680, Sxi2 = 73 240. Döntse el 5%-os szignifikanciaszinten, hogy az állítás elfogadható-e!

---

**▶ 2023. jún. 15.** _(8 pont)_

Azt állítják, hogy a futballista egy mérkőzésen átlagosan legalább 8 km-t fut. 60 mérkőzés adatai: Sxi = 470, Sxi2 = 3 760. Döntse el 5%-os szignifikanciaszinten!

---

**▶ 2022_1.** _(8 pont)_

n = 80, Sxi = 1 640, Sxi2 = 34 500. H0: mu = 20 — döntse el 5%-os szignifikanciaszinten!

---

**▶ 2014. máj. 22.** _(8 pont)_

Adott minta alapján tesztelje, hogy a várható érték egyenlő-e mu0-val. x_atlag és s a mintából számítható. Döntse el alfa = 0.05 szinten!

### Gyakorló feladatok

**1. feladat**
Egy gyár azt állítja, hogy termékeinek átlagos élettartama 500 óra. 36 terméket tesztelnek: Sxi = 17 820, Sxi2 = 8 990 000. Döntse el 5%-os szignifikanciaszinten, hogy az állítás elfogadható-e! (H1: mu != 500)

**2. feladat**
Egy tanár szerint az osztályátlag legalább 70 pont a dolgozaton. 25 fős mintából: x_atlag = 67.4, s = 8.2. Döntse el 5%-os szignifikanciaszinten! (H1: mu < 70, egyoldali)

**3. feladat**
Egy étteremben az átlagos várakozási idő állítólag legfeljebb 15 perc. 40 látogató méréséből: Sxi = 632, Sxi2 = 10 450. Döntse el 5%-os szignifikanciaszinten! (H1: mu > 15, egyoldali)

**4. feladat**
n = 100, Sxi = 3 150, Sxi2 = 102 800. H0: mu = 30. Végezze el a kétoldali t-próbát alfa = 0.05 szinten, és értelmezze az eredményt!

---

## 2. Poisson eloszlás

2020 óta szinte minden vizsgán szerepel F1 egyik részeként (3–4 pont). Egyetlen képlet — csak be kell helyettesíteni.

### Képlet

```
X ~ Poisson(lambda)    — lambda az átlagos előfordulás (meccs/nap/perc stb.)

P(X = k)  =  e^(-lambda) * lambda^k / k!

P(X >= k)  =  1 - P(X <= k-1)  =  1 - sum[i=0..k-1] P(X=i)
P(X <= k)  =  sum[i=0..k] P(X=i)

E(X) = lambda     D2(X) = lambda     D(X) = sqrt(lambda)

Hasznos: e^(-1) ~ 0.3679,  e^(-2) ~ 0.1353,  e^(-3) ~ 0.0498,  e^(-5) ~ 0.0067
```

### Valódi vizsgafeladatok

**▶ 2023. jún. 27.** _(4 pont)_

Shaquille O'Neal egy meccsen átlagosan 10.9 lepattanót szerez. Mennyi a valószínűsége, hogy egy meccsen pontosan 15-öt sikerül, ha a sikerei Poisson-eloszlásúak? [lambda = 10.9, k = 15]

---

**▶ 2023. jún. 9.** _(4 pont)_

Egy csokoládégyárban átlagosan lambda = 2 hibás termék keletkezik percenként. Mennyi a valószínűsége, hogy egy adott percben pontosan 4 hibás termék van?

---

**▶ 2023. jún. 15.** _(4 pont)_

Egy telefonközpontba átlagosan 6 hívás érkezik percenként. Mennyi a valószínűsége, hogy egy percben legalább 8 hívás érkezik?

---

**▶ 2022_1.** _(4 pont)_

Egy szervizhez átlagosan 3 autó érkezik naponta (Poisson).
- (a) P(X = 5) = ?
- (b) P(X >= 2) = ?

### Gyakorló feladatok

**1. feladat**
Egy szerviz naponta átlagosan lambda = 4 autót javít. Mennyi a valószínűsége, hogy egy nap pontosan 6 autót javítanak?

**2. feladat**
Egy weboldalt percenként átlagosan 3 felhasználó látogat meg.
- (a) P(X = 0) = ?
- (b) P(X <= 2) = ?
- (c) P(X >= 5) = ?

**3. feladat**
lambda = 2. Számítsa ki P(X=0), P(X=1), P(X=2), P(X=3) értékeket! Ellenőrzés: összegük legyen közel 1.

**4. feladat**
lambda = 5. Mennyi a valószínűsége, hogy X > 3?
[Hint: P(X > 3) = 1 - P(X=0) - P(X=1) - P(X=2) - P(X=3)]

---

## 3. Binomiális eloszlás

Szinte minden vizsgán megjelenik — általában 3–6 pont értékű részfeladatban, néhol önálló nagy feladat (12p).

### Képlet

```
X ~ B(n, p)    — n független kísérlet, p a siker valószínűsége

P(X = k)  =  C(n,k) * p^k * (1-p)^(n-k)

C(n, k)  =  n! / (k! * (n-k)!)    — binomiális együttható

P(X >= k)  =  1 - P(X <= k-1)

E(X) = n*p     D2(X) = n*p*(1-p)     D(X) = sqrt(n*p*(1-p))

Nagy n esetén: X ~ N(np,  np(1-p))   [CLT közelítés]
```

### Valódi vizsgafeladatok

**▶ 2023. jún. 27. (a)** _(4 pont)_

Shaquille O'Neal büntetődobások nélkül 58.2%-os találati arányú. Mennyi a valószínűsége, hogy 10 kosárra dobásból legalább 8-cal pontot szerez?
[X ~ B(10, 0.582), P(X >= 8) = ?]

---

**▶ 2023. jún. 27. (b)** _(4 pont)_

O'Neal 19 szezonjából 10-ben volt a legmagasabb a találati aránya a ligában. Ha találomra megnézünk 5 szezont, mennyi a valószínűsége, hogy közöttük pontosan 3 olyan van, amelyben a liga legjobb eredményét érte el?
[X ~ B(5, 10/19), P(X = 3) = ?]

---

**▶ 2023. jún. 15.** _(4 pont)_

Egy kosárlabda-játékos 3 pontosokból 35%-os sikerességű. 10 kísérletből mennyi a valószínűsége, hogy legalább 4-et eltalál?
[X ~ B(10, 0.35), P(X >= 4) = ?]

---

**▶ 2022_5. (panzió feladatsor)** _(12 pont)_

Egy esemény bekövetkezési valószínűsége p = 0.4. 12 kísérletből:
- (a) P(X = 4) = ?
- (b) P(X <= 3) = ?
- (c) E(X) és D(X) = ?

[X ~ B(12, 0.4)]

### Gyakorló feladatok

**1. feladat**
Egy érmét 10-szer dobják fel (p = 0.5).
- (a) P(X = 6) = ?
- (b) P(X >= 7) = ?
- (c) E(X) és D(X) = ?

**2. feladat**
Egy teszt 20 igaz-hamis kérdésből áll — valaki találomra tölti ki. Mennyi a valószínűsége, hogy legalább 14-et helyesen válaszol meg?
[X ~ B(20, 0.5), P(X >= 14) = ?]

**3. feladat**
Termékek 15%-a hibás. 12 terméket vizsgálnak meg.
- (a) P(X = 0) = ?
- (b) P(X <= 2) = ?
- (c) Várhatóan hány hibás?

**4. feladat**
n = 8, p = 0.3. Számítsa ki P(X=0), P(X=1), ..., P(X=8) értékeket! Ellenőrzés: összegük = 1.

---

## 4. Normális eloszlás és CHT

Szinte minden vizsgán szerepel. A Centrális Határeloszlás Tétel (CHT): nagy mintánál az összeg/átlag normálisan oszlik el.

### Képlet

```
X ~ N(mu, sigma2)    — várható érték mu, szórásnégyzet sigma2

Standardizálás:  Z = (X - mu) / sigma,    Z ~ N(0, 1)

P(X <= x)  =  Phi( (x - mu) / sigma )          [Phi-táblázatból]
P(X > x)   =  1 - Phi( (x - mu) / sigma )
P(a < X < b) =  Phi( (b-mu)/sigma ) - Phi( (a-mu)/sigma )

Hasznos: Phi(1.96) ~ 0.975,  Phi(1.645) ~ 0.95,  Phi(2.576) ~ 0.995

── CHT (n >= 30) ────────────────────────────────────────────────
Sn = X1+...+Xn  ~  N(n*mu,  n*sigma2)
X_atlag = Sn/n  ~  N(mu,  sigma2/n)

Standardizálás CHT-vel:
   Z  =  (Sn - n*mu) / (sigma*sqrt(n))     [összegre]
   Z  =  (X_atlag - mu) / (sigma/sqrt(n))  [átlagra]
```

### Valódi vizsgafeladatok

**▶ 2023. jún. 27. (d)** _(4 pont)_

A szezonvégi, egy meccsen átlagosan szerzett pont normális eloszlású, várható értéke 23.7 és szórása 5. Mennyi a valószínűsége, hogy egy szezonban 29-nél magasabb az átlag?
[X ~ N(23.7, 25), P(X > 29) = 1 - Phi( (29-23.7)/5 ) = ?]

---

**▶ 2023. jún. 27. — CHT (c rész)** _(4 pont)_

50 koktél elkészítéséhez összesen mennyi vodka fogy el?
[Sn ~ N(50*E(X), 50*D2(X)) --> standardizálás, Phi-táblázat]

---

**▶ 2020. jún. 11.** _(4 pont)_

Adott normális eloszlású változó. Mennyi a valószínűsége, hogy értéke egy adott intervallumba esik? Standardizáljon és olvassa le a Phi-táblázatból!

---

**▶ 2022_1. — CHT** _(4 pont)_

Gép alkatrészeket gyárt, tömegük X ~ N(mu, sigma2). 50 alkatrész összesített tömege meghalad-e egy határértéket?
[CHT: S50 ~ N(50*mu, 50*sigma2)]

### Gyakorló feladatok

**1. feladat**
X ~ N(50, 100) (mu=50, sigma=10). Számítsa ki:
- (a) P(X > 60)
- (b) P(40 < X < 55)
- (c) P(X < 45)

**2. feladat**
Alkatrész hossza X ~ N(20, 4) mm.
- (a) P(18 < X < 22) = ?
- (b) P(X > 24) = ?

**3. feladat**
CHT: 64 db mérés, X ~ N(5, 16). Mennyi a valószínűsége, hogy a minta átlaga 4.5 és 5.5 közé esik?
[X_atlag ~ N(5, 16/64) = N(5, 0.25), sigma_atlag = 0.5]

**4. feladat**
CHT: n=100, X ~ N(10, 9). Mennyi P(S100 > 1050)?
[S100 ~ N(1000, 900), Z = (1050-1000)/30]

---

## 5. Adott sűrűségfüggvény (Cx^n típus)

2022 óta szinte minden vizsgán F2-ként jelenik meg önálló feladatként (8–16 pont). Az (a) rész mindig egyszerű integrálás — ingyen 4 pont!

### Módszer — lépésről lépésre

```
Adott: f(x) = C*x^n  (vagy más egyszerű alak),  x in [a, b],  egyébként 0

LÉPÉS 1 — C meghatározása (normálási feltétel):
   integral[a..b] f(x) dx = 1   -->  ebből C = ...

LÉPÉS 2 — Valószínűség:
   P(X > t)  =  integral[t..b] f(x) dx
   P(X < t)  =  integral[a..t] f(x) dx

LÉPÉS 3 — Várható érték:
   E(X) = integral[a..b] x * f(x) dx

LÉPÉS 4 — Második momentum:
   E(X2) = integral[a..b] x^2 * f(x) dx

LÉPÉS 5 — Szórásnégyzet és szórás:
   D2(X) = E(X2) - [E(X)]^2
   D(X)  = sqrt(D2(X))

LÉPÉS 6 — CHT az összegre (n darab változó esetén):
   Sn ~ N(n*E(X),  n*D2(X))   -->  standardizálás, Phi-tábla
```

### Valódi vizsgafeladatok

**▶ 2023. jún. 27. — f(x) = x/2 - 1, x in [2, 4]** _(12 pont)_

- (a) Mennyi a valószínűsége, hogy legalább 3 cl vodka kerül a koktélba?
  P(X >= 3) = integral[3..4] (x/2-1) dx
- (b) Számítsa ki E(X) és D(X) értékeket!
- (c) Becsülje meg annak valószínűségét, hogy 50 koktélhoz több mint [X] cl fogy!
  [CHT: S50 ~ N(50*E(X), 50*D2(X))]

---

**▶ 2023. jún. 9. — f(x) = C*x^3, x in [0, 2]** _(8 pont)_

- (a) Határozza meg C értékét!
  integral[0..2] C*x^3 dx = C*[x^4/4]_0^2 = C*4 = 1  -->  C = 1/4
- (b) E(X) = integral[0..2] x * (x^3/4) dx = integral[0..2] x^4/4 dx = ?
  D2(X) = E(X2) - [E(X)]^2 = ?
- (c) P(X > 1.5) = integral[1.5..2] (x^3/4) dx = ?

---

**▶ 2023. jún. 15. — f(x) = C*x^2, x in [0, 3]** _(11 pont)_

- (a) C = ?  [integral[0..3] C*x^2 dx = C*9 = 1 --> C = 1/9]
- (b) E(X) = ?    D(X) = ?
- (c) P(X > 2) = integral[2..3] x^2/9 dx = ?

### Gyakorló feladatok

**1. feladat**
f(x) = C*x^2, x in [0, 3].
- (a) C = ?
- (b) E(X) = ?    D(X) = ?
- (c) P(X > 2) = ?

[Megoldás: C = 1/9, E(X) = 9/4 = 2.25]

**2. feladat**
f(x) = C*x, x in [1, 3].
- (a) C = ?
- (b) E(X) = ?    D(X) = ?
- (c) P(X < 2) = ?

**3. feladat**
f(x) = 3*x^2, x in [0, 1] (C már adott).
- (a) Ellenőrizze, hogy valóban sűrűségfüggvény-e!
- (b) E(X) = ?    D2(X) = ?
- (c) P(0.5 < X < 1) = ?

**4. feladat**
f(x) = x/2 - 1, x in [2, 4] (mint a 2023. jún. 27. vizsgán).
- (a) Ellenőrizze: integral f(x) dx = 1?
- (b) E(X) = integral[2..4] x*(x/2-1) dx = ?
- (c) E(X2) = ?    D2(X) = ?    D(X) = ?

---

_Valszám Vizsgafelkészítés | Mérnökinformatikus II. | 2014–2023 vizsgák alapján_
