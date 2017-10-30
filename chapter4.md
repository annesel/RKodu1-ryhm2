---
title       : Väärtuste tüübid
description : Neljas teema - väärtuste tüübid, tõeväärtused
--- type:NormalExercise lang:r xp:100 skills:1 key:5e89d5ccd7
## Väärtuste tüübid. Puuduvad väärtused
R-is on põhilised väärtuste tüübid, mida kasutame:

* `int` / `integer` -- täisarvud
* `numeric` -- reaalarvud
* `char` / `character` -- sõned (tähemärgid ja muud tekstilised sümbolid, sisestamisel kasutada jutumärke)
* `logical` -- tõeväärtused (ainult kaks väärtust: `TRUE` või `FALSE`)

Erisümbolid

* `NA` -- puuduv väärtus
* `NaN` -- määramatus
* `Inf`, `-Inf` -- lõpmatus


Tüübi kontroll, teisendamine

* Objekti väärtuse tüübi kontrolliks saab kasutada funktsioone kujul `is.<tüüp>`, näiteks `is.character(muutuja)`, `is.nan(muutuja)`.
* Tüübi teisenduseks aga funktsioone `as.<tüüp>`, näiteks `as.integer(muutuja)`.



*** =instructions

- Vaata üle millised vektorid etteantud koodi alguses moodustatakse.
- **Ülesanne 1**: Kontrolli, kas vektor `muutuja1` on tõeväärtusvektor. Täienda etteantud koodi, pannes kirja kontrolliks sobiva funktsiooni nime.
- **Ülesanne 2**: Rakenda funktsiooni `is.nan()` teisele moodustatud vektroile `muutuja2`. Pane tähele, et funktsiooni tulemus on ka vektor.
- **Ülesanne 3**: Asenda vektoris `muutuja3` esimene element tühikuga, kasutades funktsiooni `is.na()` abi. Prindi muudetud vektor ekraanile.

*** =hint
- Esimeses ülesandes kasuta funktsiooni `is.logical()`.
- Selleks, et esimene element määrata tühikuks, peab elemendi `is.na(muutuja3)[1]` väärtuseks omistama `TRUE`.


*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Moodustame mõned vektorid ja vaatame tulemust.
muutuja1 <- c("TRUE", "true",  "Tru", "FALSE", "F", "false", NA)
muutuja2 <- c(1:3, NA, 0, Inf - Inf)
muutuja3 <- 1:6
muutuja1; muutuja2; muutuja3



# Ülesanne 1: Kontrolli kas vektor muutuja1 on tõeväärtusvektor (asenda alakriipis sobivalt, et moodustuks õige funktsiooni nimi).
is.______(muutuja1)

# Ülesanne 2: Rakenda funktsiooni is.nan() vektorile muutuja2.


# Ülesanne 3: Asenda vektori muutuja3 esimene element puuduva väärtusega, selleks asenda järgmises käsus alakriipis sobiva tõeväärtusega. Prindi tulemus ekraanile.
is.na(muutuja3)[1] <- _________
muutuja3


```

*** =solution
```{r}
# Moodustame mõned vektorid ja vaatame tulemust.
muutuja1 <- c("TRUE", "true",  "Tru", "FALSE", "F", "false", NA)
muutuja2 <- c(1:3, NA, 0, Inf - Inf)
muutuja3 <- 1:6
muutuja1; muutuja2; muutuja3


# Ülesanne 1: Kontrolli kas objekt muutuja1 on loogilist tüüpi(asenda alakriipis sobiva sõnega, et moodustuks õige funktsiooni nimi).
is.logical(muutuja1)


# Ülesanne 2: Rakenda funktsiooni is.nan() objektile muutuja2.
is.nan(muutuja2)

# Ülesanne 3: Asenda objekti muutuja3 esimene element puuduva väärtusega, selleks asenda alakriipis sobiva tõeväärtusega. Prindi tulemus ekraanile.
is.na(muutuja3)[1] <- TRUE
muutuja3
```

*** =sct
```{r}
test_predefined_objects("muutuja1",undefined_msg = "Oled vektori `muutuja1` kustutanud! Alusta uuesti.", incorrect_msg = "Muutuja `muutuja1` väärtused on muudetud! Alusta uuesti")
test_predefined_objects("muutuja2",undefined_msg = "Oled vektori `muutuja2` kustutanud! Alusta uuesti.", incorrect_msg = "Muutuja `muutuja2` väärtused on muudetud! Alusta uuesti")


test_function("is.logical",  args = "x", index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Esimeses ülesandes kasuta funktsiooni `is.logical()`",
              args_not_specified_msg = NULL,
              incorrect_msg = "Esimeses ülesandes on funktsioonile `is-logical()` ette antud vale argumendiväärtus. Alusta uuesti.")



test_function("is.nan",  args = "x", index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Teises ülesandes kasuta funktsiooni `is.nan()`",
              args_not_specified_msg = NULL,
              incorrect_msg = "Teises ülesandes on funtsioonile `is.nan()` ette antud vale argumendiväärtus. Alusta uuesti.")




test_function("is.na",  args = "x", index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Viimases ülesandes kasuta funktsiooni `is.na()`",
              args_not_specified_msg = NULL,
              incorrect_msg = "Viimases ülesandes on funtsioonile ette antud vale argumendiväärtus. Alusta uuesti.")
test_object("muutuja3", undefined_msg = "Objekti `muutuja3` pole!", incorrect_msg = "Kas tegid omistamise kujul `is.na(muutuja3)[1] <- TRUE`?")

test_output_contains("muutuja3", incorrect_msg = "Vektor `muutuja3` pole välja prinditud!")


success_msg("Tubli töö!")
```



--- type:NormalExercise lang:r xp:100 skills:1 key:efa4b167fa
## Veel tõeväärtustest 1

Tõeväärtuseid on kaks: `TRUE` ja `FALSE`. R saab aru ka lühenditest `T` ja `F`.


Tõeväärtused on tulemuseks kui teeme võrdlusi:

* võrdumine `==`
* mittevõrdumine `!=`
* väiksem kui `<`
* väiksem või võrdne `<=`
* suurem kui `>`
* suurem või võrdne `>=`


Loogilisi tehteid on kolm

* korrutamine (`&`)
* liitmine (`|`) 
* eitus (`!`). 



*** =instructions
- Tee läbi näited 1 kuni 3.
- **Ülesanne 1.**  Väärtusta tõeväärtusvektor, mille elementide väärtus on `TRUE`, kui `x` väärtused on suuremad kui 30 (`FALSE` vastasel juhul). Omista tulemus muutujale `x4` ja prindi see ekraanile.
- **Ülesanne 2.** Moodusta tõeväärtusvektor, mille elementide väärtus on `TRUE`, kui  `x` väärtused on  väiksemad kui 40  (`FALSE` vastasel juhul). Omista tulemus muutujale `x5` ja prindi see ekraanile.
- **Ülesanne 3.** Moodusta tõeväärtusvektor `x6`, mille elementide väärtus on `TRUE`, kui  `x` väärtused on vahemikus 30 kuni 40  (`FALSE` vastasel juhul), kasutades vektoreid  `x4` ja  `x5` ning sobivat loogilist tehet (`|`, `&`, `!`). Prindi `x6` ekraanile.



*** =hint
- Sobiv tehe on korrutamine (`&`).


*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# antud on vektor x
x <- c(34, 23, 45, 67, 10, 21, 37)

#Näide 1: Väärtustame tõeväärtusvektori, mille elementide väärtus on `TRUE`, kui x väärtused on suuremad kui 50. Prindime ekraanile
x1 <- x > 50
x1

#Näide 2: Väärtustame tõeväärtusvektori, mille elementide väärtus on `TRUE`, kui  x väärtused on  väiksemad kui 20. Prindime ekraanile
x2 <- x < 20
x2

#Näide 3: Moodustame tõeväärtusvektori, mis näitab, millised x väärtused on alla 20 või üle 50. Prindime ekraanile
x3 <- x1 | x2 # loogiline tehe 'või'
x3


#Ülesanne 1: Väärtusta tõeväärtusvektor x4. Prindi x4 ekraanile
x4 <- _________________
x4


#Ülesanne 2: Moodusta tõeväärtusvektor vektor x5. Prindi  ekraanile
x5 <- _________________
x5


#Ülesanne 3: Moodusta tõeväärtusvektor x6 kasutades vektoreid x4 ja x5 ning sobivat loogilist tehet. Prindi tulemus ekraanile
x6 <- ________ __ __________
x6


 


```

*** =solution
```{r}
# antud on vektor x
x <- c(34, 23, 45, 67, 10, 21, 37)

#Näide 1: Väärtustame tõeväärtusvektori, mille elementide väärtus on `TRUE`, kui x` väärtused on suuremad kui 50. Prindime ekraanile
x1 <- x > 50
x1

#Näide 2: Väärtustame tõeväärtusvektori, mille elementide väärtus on `TRUE`, kui  x väärtused on  väiksemad kui 20. Prindime ekraanile
x2 <- x < 20
x2

#Näide 3: Moodustame tõeväärtusvektori, mis näitab, millised x väärtused on alla 20 või üle 50. Prindime ekraanile
x3 <- x1 | x2 # loogiline tehe 'või'
x3


#Ülesanne 1: Väärtusta tõeväärtusvektor x4. Prindi x4 ekraanile
x4 <- x > 30
x4


#Ülesanne 2: Moodusta tõeväärtusvektor vektor x5. Prindi  ekraanile
x5 <- x < 40
x5


#Ülesanne 3: Moodusta tõeväärtusvektor x6 kasutades vektoreid x4 ja x5 ning sobivat loogilist tehet. Prindi tulemus ekraanile
x6 <- x4 & x5
x6
```

*** =sct
```{r}
test_predefined_objects("x", undefined_msg = "Oled vektori `x` kustutanud! Alusta uuesti.", incorrect_msg = "Muutuja `x` väärtused on muudetud! Alusta uuesti")

test_object("x4", undefined_msg = "Objekti `x4` pole!", incorrect_msg = "Kas tegid võrdluse kujul `x > 30` ?")
test_output_contains("x4", incorrect_msg = "Vektor `x4` pole välja prinditud!")
test_student_typed(c("x>30", "30<x"), not_typed_msg = "Kasuta võrdluste tegemisel märke `>` ja `<`.")


test_object("x5", undefined_msg = "Objekti `x5` pole!", incorrect_msg = "Kas tegid võrdluse kujul `x < 40` ?")
test_output_contains("x4", incorrect_msg = "Vektor `x4` pole välja prinditud!")
test_student_typed(c("x<40", "40>x"), not_typed_msg = "Kasuta võrdluste tegemisel märke `>` ja `<`.")


test_object("x6", undefined_msg = "Objekti `x6` pole!", incorrect_msg = "Kas tegid tehte kujul  `x4 & x5` ?")
test_output_contains("x6", incorrect_msg = "Vektor `x6` pole välja prinditud!")
test_student_typed(c("x4 & x5", "!(!x4 | !x5)"), not_typed_msg = "Kas tegid tehte kujul  `x4 & x5` ?")


success_msg("Tubli! Järgmine ülesanne on viimane.")

```



--- type:NormalExercise lang:r xp:100 skills:1 key:720b8a9769
## Veel tõeväärtustest 2

Tõeväärtuseid on kaks: `TRUE` ja `FALSE`. R saab aru ka lühenditest `T` ja `F`.


Tõeväärtused on tulemuseks kui teeme võrdlusi:

* võrdumine `==`
* mittevõrdumine `!=`
* väiksem kui `<`
* väiksem või võrdne `<=`
* suurem kui `>`
* suurem või võrdne `>=`


Loogilisi tehteid on kolm

* korrutamine (`&`)
* liitmine (`|`) 
* eitus (`!`). 



*** =instructions
- Tee läbi näide.
- **Ülesanne**  Leia tõevektor, mis näitaks millised vektori `y` väärtused vastavad sõnele "tere" või "tsau".  
Omista vektor muutujale `viimane`, prindi see ekraanile. Vektori `y` väärtustest saad ülevaate sagedustabeli `table(y)` abil.

*** =hint
- Vastuse kirjapanekuks on siin mitu võimalust. 

    - Tere **või** tsau
    - (**Ei** ole hei)  **ja** (**ei** ole hommikust)
    -  **Ei** ole (hei **või** hommikust)

*** =pre_exercise_code
```{r}
kordused <- c(45, 20, 68, 9)
y <- sample(rep(c("tere", "hei", "tsau", "hommikust"), times = kordused), size = sum(kordused))
```

*** =sample_code
```{r}
# Näide: vaatame tähestiku algust, moodustame kolme moodi tõevektori, mille väärtus on TRUE, kui täht on a või b ning on FALSE vastasel korral
abc <- letters[1:3]
abc
abc == "a" | abc == "b" # täht on 'a' või täht on 'b'
abc != "c"  # täht ei ole 'c'
!(abc == "c")  # eitame väidet, et täht on 'c'


# Ülesandes on uurimise all tekstiväärtustega vektor y, vaata selle väärtuste sagedustabelit
table(y)


# Ülesanne: Leia tõevektor, mis näitaks millised vektori y väärtused vastavad sõnele "tere" või "tsau".  Omista vektor muutujale viimane, prindi see ekraanile.

 
```

*** =solution
```{r}
# Näide: vaatame tähestiku algust, moodustame kolme moodi tõevektori, mille väärtus on TRUE, kui täht on 'a' või 'b' ning on FALSE vastasel korral
abc <- letters[1:3]
abc
abc == "a" | abc == "b" # täht on 'a' või täht on 'b'
abc != "c"  # täht ei ole 'c'
!(abc == "c")  # eitame väidet, et täht on 'c'


# Ülesandes on uurimise all vektor y, vaata selle väärtuste sagedustabelit
table(y)


# Ülesanne: Leia tõevektor, mis näitaks millised vektori 'y' väärtused vastavad sõnele "tere" või "tsau".  Omista vektor muutujale viimane, prindi see ekraanile.
viimane <- y == "tere" | y == "tsau"
viimane

```

*** =sct
```{r}
test_predefined_objects("y",undefined_msg = "Oled vektori `y` kustutanud! Alusta uuesti.", incorrect_msg = "Muutuja `y` väärtused on muudetud! Alusta uuesti")

test_object("viimane", undefined_msg = "Objekti `viimane` pole!", incorrect_msg = "Muutuja `viimane` väärus on vale. Proovi uuesti. Kontrolli  ka tekstiväärtuste kirjapanek üle, ega 'hei' asemel pole näiteks 'hie'?")
test_output_contains("viimane", incorrect_msg = "Vektor `viimane` pole välja prinditud!")
#test_student_typed(c("y == "tere" | y == "tsau"", "!(y == "hommikust" | y == "hei")", "y != "hommikust" & y != "hei"") )


success_msg("Tubli! Viimane ülesanne on tehtud. Premeeri end millegi heaga.")
```





