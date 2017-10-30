---
title       : Vektorite loomine, elementide valik
description : Kolmas teema - vektorid
--- type:NormalExercise lang:r xp:100 skills:1 key:ec64c03bcd
## Vektori moodustamine, tehted vektoriga

- Üksikuid arve või tekstiväärtusi saab kokku panna vektoriks funktsiooni `c()` (*combine*) abil. 
- Veel võimalusi vektorite moodustamiseks:
    * `1:5                 # arvujada 1, 2, 3, 4, 5`
    * `rep(1:3, times = 2) # vektorit elementidega 1, 2, 3 korrata 2 korda`
    * `seq(3, 9, by = 2)   # arvujada sammuga 2: 3, 5, 7, 9`
- Kui teha vektorobjektidega arvtusi, siis tehted tehakse läbi iga vektori elemendiga.

*** =instructions
- Tee läbi näited 1 kuni 3.
- **Ülesanne 1.** Teisenda temperatuurid celsiuse skaalalt fahrenheiti skaalale ($^\circ\hspace{-0.1em} F = ^\circ\hspace{-0.1em} C \times \frac{9}{5} + 32$). Omista tulemus muutujale `Fahrenheit` ja prindi see ekraanile.
- **Ülesanne 2.** Vektoris `lisa` on veel kaks õhutemperatuuri($^\circ\hspace{-0.1em} C$). Prindi see vektor ekraanile.
- **Ülesanne 3.** Kasutades funkstiooni `c()` moodusta vektor nimega `temp2`, mille esimesed 9 elementi  on temperatuurid vektorist `temp` ja järgmised 2 temperatuurid vektorist `lisa`. Väljasta tulemus ekraanile.


*** =hint
- Funktsiooni `c()` saab lisaks üksikutest väärtustest vektori tegemisele kasutada ka olemasolevate vektorite kombineerimiseks: `c(vektor1, vektor2)`.

*** =pre_exercise_code
```{r}
lisa <- c(-24.9, -16.1)
names(lisa) <- c("Mustvee", "Keila")


```

*** =sample_code
```{r}
# Näide 1: Moodustame 2 vektorit, millest ühes on kirjas temperatuurid (20.01.2010 kell 10), teises ilmajaamad, kus need on mõõdetud :
temp <- c(-6.2, -12.9, -13.0, -15.4, -16.1, -16.9, -17.0, -19.6, -19.9)
jaam <- c("Ruhnu", "Kihnu", "Pakri", "Tallinn", "Pärnu", "Kunda", "Kuusiku", "Võru", "Jõgeva")            

# Näide 2: Väljastame tulemused ekraanile
temp; jaam

# Näide 3: Paneme temperatuuridele jaamanimed juurde ja vaatame tulemust
names(temp) <- jaam
temp

# Ülesanne 1: Teisenda temperatuurid celsiuse skaalalt fahrenheiti skaalale (asenda alakriips vajaliku tehtega) ja prindi tulemus ekraanile
Fahrenheit <- ___________________ 
Fahrenheit 

# Ülesanne 2. Prindi ekraanile vektor nimega 'lisa'


# Ülesanne 3. Moodusta nõutud kujul uus vektor, selleks asenda alakriipsud vajalike objektidega. Prindi tulemus ekraanile.
temp2 <- c(_____, _____) 
temp2

```

*** =solution
```{r}
# Näide 1: Moodustame 2 vektorit, millest ühes on kirjas temperatuurid (20.01.2010 kell 10), teises jaamad, kus need on mõõdetud :
temp <- c(-6.2, -12.9, -13.0, -15.4, -16.1, -16.9, -17.0, -19.6, -19.9)
jaam <- c("Ruhnu", "Kihnu", "Pakri", "Tallinn", "Pärnu", "Kunda", "Kuusiku", "Võru", "Jõgeva")            # NB! Kui jutumärgid unustada, otsib R vastava nimega objekte!

# Näide 2: Väljastame tulemused ekraanile
temp; jaam

# Näide 3: Paneme temperatuuridele jaamanimed juurde ja vaatame tulemust
names(temp) <- jaam
temp

# Ülesanne 1: Teisenda temperatuurid celsiuse skaalalt fahrenheiti skaalale (asenda alakriipsud vajaliku tehteda) ja prindi tulemus ekraanile
Fahrenheit <- temp * 9/5 + 32
Fahrenheit 

# Ülesanne 2: Prindi ekraanile vektor nimega 'lisa'
lisa

# Ülesanne 3: Moodusta nõutud kujul uus vektor, selleks asenda alakriipsud vajalike objektidega. Prindi tulemus ekraanile.
temp2 <- c(temp, lisa) 
temp2
```

*** =sct
```{r}
test_object("Fahrenheit", undefined_msg = "Muutuja `Fahrenheit` on kaduma läinud!", incorrect_msg = "Kontrolli, kas omistad muutujale `Fahrenheit` õige tehte.")
test_output_contains("Fahrenheit", times = 1, incorrect_msg = "Prindi vektor `Fahrenheit` ekraanile!")


test_predefined_objects("lisa",undefined_msg = "Oled vektori `lisa` kustutanud! Alusta uuesti.", incorrect_msg = "Muutuja `lisa` väärtused on muudetud! Alusta uuesti.")
test_output_contains("lisa", incorrect_msg = "Vektor `lisa` pole välja prinditud!")


test_object("temp2", undefined_msg = "Puudub vektor `temp2`. Proovi uuesti!", incorrect_msg = "Vektori `temp2` väärtus ei vasta nõutule!")
test_output_contains("temp2", incorrect_msg = "Vektor `temp2` pole välja prinditud!")

success_msg("Super! Liigu järgmise ülesande juurde.")

```










--- type:NormalExercise lang:r xp:100 skills:1 key:de5673cfb7
## Funktsioonide rakendamine vektoritele

Kui anname funktsiooni argumendiks vektori, siis olenevalt funktsioonist võib tulemuseks olla teisendatud väärtustega vektor või mingi kokkuvõtlik summarne näitaja/näitajad.

Töölaual on temperatuurde vektor nimega `temp2`

*** =instructions
- Vaata millised väärtused  esinevad vektoris `temp2` st prindi väärtused ekraanile
- **Ülesanne 1.** Rakenda tempratuuride vektorile funktsiooni `exp()`. Kas tulemuses on sama palju elemente kui algses vektoris? Omista oma vastus (tekst "jah" või "ei") muutujale `vastus1`.
- **Ülesanne 2.** Rakenda tempratuuride vektorile funktsiooni `summary()`. Millisest temperatuurist on pooled temperatuuriväärtused madalamad ja pooled kõrgemad? Omista see väärtus muutujale`vastus2`. 
- **Ülesanne 3.** Rakenda tempratuuride vektorile funktsiooni `sd()`. Kas standardhälbe väärtus tuleks negatiivne, kui temperatuuride vektoris esineks nii positiivseid kui negatiiivseid väärtuseid? Omista oma vastus (tekst "jah" või "ei") muutujale `vastus3`. 




*** =hint
- Teises ülesandes peab muutujale `vastus2` omistama mediaani väärtuse.
- Standardhälve on mittenegatiivne suurus.

*** =pre_exercise_code
```{r}
temp2 <- c(-6.2, -12.9, -13.0, -15.4, -16.1, -16.9, -17.0, -19.6, -19.9, -24.9, -16.1)
jaam <- c("Ruhnu", "Kihnu", "Pakri", "Tallinn", "Pärnu", "Kunda", "Kuusiku", "Võru", "Jõgeva", "Mustvee", "Keila")            
names(temp2) <- jaam
```

*** =sample_code
```{r}
# prindi vektor
temp2

# Ülesanne 1: Rakenda funktsiooni exp() ja pane kirja vastus (asenda alakriips sobiva koodiga)
____(temp2)
vastus1 <- __________


# Ülesanne 2: Rakenda funktsiooni summary() ja pane kirja vastus (asenda alakriips sobiva koodiga)
____(temp2)
vastus2 <- __________



# Ülesanne 3: Rakenda funktsiooni sd() ja pane kirja vastus (asenda alakriips sobiva koodiga)
____(temp2)
vastus3 <- __________




```

*** =solution
```{r}
# prindi vektor
temp2

# Ülesanne 1: Rakenda funktsiooni exp() ja pane kirja vastus (asenda alakriips sobiva koodiga)
exp(temp2)
vastus1 <- "jah"


# Ülesanne 2: Rakenda funktsiooni summary() ja pane kirja vastus (asenda alakriips sobiva koodiga)
summary(temp2)
vastus2 <- -16.1



# Ülesanne 3: Rakenda funktsiooni sd() ja pane kirja vastus (asenda alakriips sobiva koodiga)
sd(temp2)
vastus3 <- "ei"


```

*** =sct
```{r}
# 1
test_function("exp", args = c("x"), index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Kasuta esimeses ülesandes  funktsiooni `exp()`!",
              args_not_specified_msg = "Kontrolli üle millise argumendi oled funktsioonile `exp()` andnud, see peaks olema temperatuuride vektor.",
              incorrect_msg = "Funktsiooni `exp()` tulemus on vale! Proovi uuesti.")
test_object("vastus1", undefined_msg = "Muutujat `vastus1` pole!", incorrect_msg = "Muutuja `vastus1` väärtus on vale! Kontrolli, kas kasutad vastuse kirjapanekuks jutumärke.")




# 2
test_function("summary", args = c("object"), index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Kasuta teises ülesandes  funktsiooni `summary()`!",
              args_not_specified_msg = "Kontrolli üle millise argumendi oled funktsioonile `summary()` andnud, see peaks olema temperatuuride vektor.",
              incorrect_msg = "Funktsiooni `summary()` tulemus on vale! Proovi uuesti.")
test_object("vastus2", undefined_msg = "Muutujat `vastus2` pole!", incorrect_msg = "Muutuja `vastus2` väärtus on vale!  ")




# 3
test_function("sd", args = c("x"), index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Kasuta viimases ülesandes  funktsiooni `sd()`!",
              args_not_specified_msg = "Kontrolli üle millise argumendi oled funktsioonile `sd()` andnud, see peaks olema temperatuuride vektor.",
              incorrect_msg = "Funktsiooni `sd()` tulemus on vale! Proovi uuesti.")
test_object("vastus3", undefined_msg = "Muutujat `vastus3` pole!", incorrect_msg = "Muutuja `vastus3` väärtus on vale! Kontrolli, kas kasutad vastuse kirjapanekuks jutumärke.")




success_msg("Väga tubli!")


```
--- type:NormalExercise lang:r xp:100 skills:1 key:2c0fd8e002
## Vektori alamosade selekteerimine

Väga sageli on tarvis vektorist kätte saada meile hetkel vajalikku alamosa. Vaatame paari võimalust vektorist elementide välja noppimiseks. 


*** =instructions
 - Tee  näited 1 kuni 3  ükshaaval läbi ja uuri tulemust.
 - **Ülesanne 1:** Vali temperatuurivektorist elemendid, mis on paarisarvulistel kohtadel (paarisarvulise vektori moodustamiseks kasuta funktsiooni `seq()`). Omista saadud alamvektor muutujale `vastus1`. Prindi tulemus ekraanile.
 - **Ülesanne 2:** Vali välja jaamad, kus temperatuur on olnud -17 või alla selle. Kasuta valiku tegemisel tõeväärtusvektorit ja kandilisi sulge `[]`. Omista saadud alamvektor muutujale `vastus2`.  Prindi tulemus ekraanile.



*** =hint
- Funktsioonis `seq()` peab määrama argumendid `from`, `to` ja `by`.
- Märgi $\leq$ moodustamiseks kombineeri `<` ja `=` märke:  `<=`.

*** =pre_exercise_code
```{r}
temp <- c(-6.2, -12.9, -13.0, -15.4, -16.1, -16.9, -17.0, -19.6, -19.9)
jaam <- c("Ruhnu", "Kihnu", "Pakri", "Tallinn", "Pärnu", "Kunda", "Kuusiku", "Võru", "Jõgeva")          
```

*** =sample_code
```{r}
# Objektid nimedega temp ja jaam on töölaual juba olemas
temp; jaam

# Näide 1. Elementide valimine indeksite kaudu
temp[ 1 ] # vektori esimene element
temp[ -1 ] # vektori kõik elemendid va esimene
temp[ c(1, 5, 9) ] # vektori esimene, viies ja üheksas element

# Näide 2. Tulemuseks tõeväärtustega vektorid 
temp < -15 # Kontrollime millised temperatuurid jäävad alla -15 kraadi 
jaam == "Tallinn"  # Millisel kohal vektoris on ilmajaama nimi Tallinn?

# Näide 3. Tingimustele vastavate elementide väljavalimine. Tõeväärtusvektori kasutamine
jaam[ temp < -15 ] # valime välja need  jaamad, kus temperatuur on alla -15
temp[jaam == "Tallinn"]  # valime välja Tallinnale vastava temperatuuri


# Ülesanne 1: Vali nõutud elemendid temperatuurivektorist, omista tulemus muutujale vastus1. Prindi tulemus ekraanile
vastus1 <- temp[_______]
vastus1


# Ülesanne 2: Vali välja tingimusele vastavad ilmajaamade nimed, omista tulemus muutujale vastus2. Prindi tulemus ekraanile
vastus2 <- ________
vastus2
```

*** =solution
```{r}
# Objektid nimedega temp ja jaam on töölaual juba olemas
temp; jaam

# Näide 1
temp[ 1 ] # vektori esimene element
temp[ -1 ] # vektori kõik elemendid va esimene
temp[ c(1, 5, 9) ] # vektori esimene, viies ja üheksas element

# Näide 2. Tulemuseks tõeväärtustega vektorid 
temp < -15 # Kontrollime millised temperatuurid jäävad alla -15 kraadi. 
jaam == "Tallinn"  # Mitmes jaam on Tallinn?

# Näide 3. Tingimustele vastavate elementide väljavalimine. Tõeväärtusvektori kasutamine
jaam[ temp < -15 ] # valime välja need  jaamad, kus temperatuur on alla -15
temp[jaam == "Tallinn"]  # valime välja Tallinnale vastava temperatuuri


# Ülesanne 1: Vali nõutud elemendid temperatuurivektorist, omista tulemus muutujale vastus1. Prindi tulemus ekraanile
vastus1 <- temp[seq(2, 9, 2)]
vastus1


# Ülesanne 2: Vali välja tingimusele vastavad ilmajaamade nimed, omista tulemus muutujale vastus2. Prindi tulemus ekraanile
vastus2 <- jaam[temp <= -17]
vastus2


```

*** =sct
```{r}
test_object("vastus1", undefined_msg = "Muutujat `vastus1` pole!", incorrect_msg = "Kontrolli, kas valid elemendid vektorist `temp` ja annad ette korrektsed indeksid?")
test_function("seq", args = c("from", "to", "by"), index = 1,
              eval = TRUE,
              eq_condition = "equivalent",
              not_called_msg = "Kasuta esimeses ülesandes indeksite määramiseks funktsiooni `seq()`!",
              args_not_specified_msg = "Kontrolli üle millised argumendid oled funktsioonile `seq()` andnud",
              incorrect_msg = "Funktsiooni `seq()` tulemus ei sobi! Proovi uuesti.")
test_output_contains("vastus1", incorrect_msg = "Vektor `vastus1` pole välja prinditud!")



test_object("vastus2", undefined_msg = "Muutujat `vastus2` pole!", incorrect_msg = "Kas moodustasid tõevektori kujul `temp <= -17`?")
test_output_contains("vastus2", incorrect_msg = "Vektor `vastus2` pole välja prinditud!")



success_msg("Tubli töö! Jätka samas vaimus!")
```










