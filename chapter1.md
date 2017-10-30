---
title       : R kui kalkulaator
description : Esimene teema - kalkulaator, omistamine
--- type:NormalExercise lang:r xp:0 skills:1 key:7483cd3c09
## Sissejuhatus

Kirjuta kõigi ülesannete lahendused paremal aknapoolel olevasse *script.R* lehele, vastava ülesande sõnastuse alla. Siinses näites on esimese ülesande lahendus juba kirja pandud.

Ühe vastuse väljaarvutamiseks või testimiseks pane *script.R* lehel hiirekursor vastava rea peale ja vajuta klahvikombinatsiooni `Ctrl+Enter`, 
sellega saadetakse vastav rida allpool olevale R-i konsoolile täitmiseks. Konsooli käsurida võid ka kasutada: kirjuta käsk ning vajuta täitmiseks `Enter`-klahvi. Proovi siin ülesandes need võimalused läbi.

Lahenduse vihjete saamiseks vajuta nuppu `Take Hint`, aga sellega kaotad võimalikke punkte! Kui oled lahti teinud vihjed, siis võid edasi avada ka kogu lahenduse koodi, kuid nii toimides lähevad ülesande punktid nulli.

Oma vastuse esitamiseks vajuta `Submit Answer`-nuppu, siis saadetakse ülesanded kontrollimiseks. Vajuta seda nuppu siis kui oled kirja pannud **kõik** selle lehekülje ülesannete vastused.


*** =instructions
**Prooviülesanne (0 punkti):**

1. Liida arvud 3 ja 4.
2. Omista väärtus 7 muutujale `x`.


*** =hint
- Liitmiseks kasuta märki `+` või funktsiooni `sum`
- Omistamiseks kasuta kombinatsiooni `<-`

*** =pre_exercise_code
```{r}
# pole midagi
```

*** =sample_code
```{r}
# Liida
3 + 4


# Omista
```



*** =solution
```{r}
# Liida
3 + 4

# Omista
x <- 7

```

*** =sct
```{r}
# esimene
test_output_contains("3 + 4", times = 1, incorrect_msg = "Oled esimeses ülesandes õige vastuse valeks parandanud. Alusta uuesti!")
test_student_typed("3",  not_typed_msg = "Kontrolli, kas esimese ülesande tehe on kujul `3 + 4`!")
test_student_typed("4",  not_typed_msg = "Kontrolli, kas esimese ülesande tehe on kujul `3 + 4`!")
 

# teine
test_object("x",  undefined_msg = "Vali muutuja nimeks `x`.",  incorrect_msg = "Omistasid muutujale  `x` vale väärtuse. Proovi uuesti!")
success_msg("Tubli! Asu nüüd päris ülesandeid lahendama!")

```


<!--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------->

--- type:NormalExercise lang:r xp:100 skills:1 key:65ef1386ac
## Arvutamine

Esmalt mõned arvutusülesanded. 

Meeldetuletuseks tehtemärgid:

- Liitmine: `+`
- Lahutamine: `-`
- Korrutamine: `*`
- Jagamine: `/`
- Astendamine: `^` või `**`
- Jääk jagamisel: `%%`

ja paar funktsiooni:

- Siinus: `sin()`
- Naturaallogaritm: `log()`
- Ruutjuur: `sqrt()`
- Eksponentfunkstioon `exp()`

**NB!** R teeb vahet suurtel ja väikestel tähtedel. Seega näiteks `sin()` ja `Sin()` viitavad erinevatele funktsioonidele.


*** =instructions
**Leia vastused järgmistele tehetele:**

1. $25 - 1:4  + 5:9$

1. $ (\sqrt{3} + 4) : 5 $

1. $ (245 - 3^6)^2 $

1. $ \frac{\ln{3} + 4}{55}$


*** =hint
- Pööra tähelepanu tehete järjekorrale.
- Ruutjuure leidmiseks kasuta funktsiooni `sqrt()` ja naturaallogaritmi leidmiseks funktsiooni `log()`.

*** =pre_exercise_code
```{r}
Sin <- function(x) print("Vahele jäid! Siinuse leidmiseks kasuta ikka funktsiooni sin()")

```

*** =sample_code
```{r}
# Ülesanne 1


# Ülesanne 2


# Ülesanne 3


# Ülesanne 4


```

*** =solution
```{r}
# Ülesanne 1
25 - 1/4  + 5/9

# Ülesanne 2
(sqrt(3) + 4) / 5

# Ülesanne 3
(245 - 3^6)^2 

# Ülesanne 4
(log(3) + 4) / 55


```

*** =sct
```{r}
# Ül 2
#test_function_result(name = "sqrt",
#                     index = 2,
#                     eq_condition = "equivalent",
#                     not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `sqrt`",
#                     error_msg = "Esimeses ülesandes on midagi valesti!",
#                     incorrect_msg = "Oled esimeses funktsioonile `sqrt` andnud vale väärtusega argumendi")

#check_operator(state, name, index = 1, append = TRUE, not_called_msg = NULL)

#test_function(name = "sqrt",
#                     index = 1,
#                     eq_condition = "equivalent",
#                     not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `sqrt`",
#                     args_not_specified_msg = "Funktsioonile `sqrt` pole antud argumendi väärtust.",
#                     incorrect_msg = "Oled esimeses funktsioonile `sqrt` andnud vale väärtusega argumendi")
#test_output_contains(expr = "(sqrt(3) + 4) / 5",
#                    times = 1,
#                    incorrect_msg = "Midagi läks valesti! Kontrolli esimese ülesande vastust.")
 
 
#Ü1 1
test_output_contains(expr = "25 - 1/4  + 5/9 ",
                    times = 1,
                    incorrect_msg = "Midagi on esimeses ülesandes valesti! Kontrolli tehete järjekorda ja tehtemärke.")
 
# Ül 2
test_output_contains(expr = "(sqrt(3) + 4) / 5",
                    times = 1,
                    incorrect_msg = "Midagi on teises ülesandes valesti! Kontrolli tehete järjekorda. Ruutjuure leidmiseks kasuta: `sqrt(3)`.")
# ÜL 3
test_output_contains(expr = "(245 - 3^6)^2 ",
                     times = 1,
                     incorrect_msg = "Midagi on komandas ülesandes valesti! Kontrolli tehete järjekorda. Astendamiseks kasuta märki `^` või `**`.")
 
# Ül 4
test_output_contains(expr = "(log(3) + 4) / 55",
                     times = 1,
                     incorrect_msg = "Midagi on viimases ülesandes valesti! Kontrolli tehete järjekorda. Naturaallogaritmi leidmiseks kasuta `log(3)`.")
 
success_msg("Hästi! Mine edasi järgmise ülesande juurde.")


```

<!--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------->








