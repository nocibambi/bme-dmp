# BME DMP Beadandó
A feladat megoldásának határideje (eddig várjuk az e-maileket): 2018-03-02 12.00

## Nominális változók kezelése
1. A logisztikus regresszió nem képes a nominális változók kezelésére, ezért az első lépésben ezeket a változókat kiszűrtük
2. Használjuk a kiszűrés helyett a Nominal to Numerical operátort, amely segítségével dummy kódolhatjuk a nominális változóinkat.
    1. Kössük be az operátort mind a tanuló, mind a teszt adathalmaz elé ugyanolyan paraméterezéssel.
    1. Futtassuk le a processzt.
    1. A processz nagy valószínűséggel hibát dob, mi a probléma oka?
3. Javítsuk ki a processzt: A Nominal to Numerical operátor kimeneti portjai között van egy, amelyen az adatelőkészítési modellt tudjuk exportálni. Ezt felhasználva hozzunk létre egy adatelőkészítési modellt az egész adathalmazon, majd azt alkalmazzuk külön a tanuló és teszt halmazra.
    1. Mindkét adathalmazból válogassuk ki a nominális változókat. Vigyázat: szűrjük ki a customer_id és target változókat, mert ezeken nem akarunk dummy kódolást csinálni.
    1. Az Append operátor  segítségével kapcsoljuk össze a két adathalmazt.
    1. Ezen az adathalmazon alkalmazzuk a Nominal to Numerical operátort. A legalsó porton található az adatelőkészítési modell.
    1. Ezt a modellt egy-egy Apply Model operátor segítségével alkalmazzuk a tanító és teszthalmazon.
    1. Majd futassuk a regressziónk és nézzük meg az eredményét.
    1. Minden operátor csak egy másik operátorba köthető bele, az adatok sokszorozására a ﻿Multiply operátort használjátok.


normaliye preprocessing model
maximal F-measure
1. 72.41%
2. 72.22%
3. 72.41%
4. 72.24%
