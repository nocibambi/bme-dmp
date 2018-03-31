4. gyakorlat - 2017-03-27

A feladat megoldásának határideje (eddig várjuk az e-maileket): 2018-04-13
Folytasd az órán elkezdett feladat megoldását.

1. Hozz létre egy olyan subprocesst, amelyben optimalizálod a k-NN algoritmusnál használt k értékét. A visszamérés során, az AUC értékére optimaalizálj.
2.  Az alábbi adatelőkészítési lépéseket tedd meg a modell tanítása előtt:
    1. kiugró értékek keresése és
    2. kategóriaváltozók kezelése
    3. normalizálás
4. Két megoldási lehetőség áll előtted az optimalizálásra:
    1. A klaszterezésnél használt Loop operátor használatával mérd ki, hogy melyik k érték esetében a legnagyobb az AUC értéke.
    2. Az Optimize Parameters (Grid) operátor használatba vétele.

Küldd át a processzed és pár soros leírást arról, hogy mit-miért-milyen eredménnyel csináltál a következő címre.

# Elemzés leírása
## 0. KNN kezdeti lefuttatása
### k=5
accuracy: 73.85%
AUC: 0.522 (positive class: 1)
Túlnyomorészt False Negatívakat produkál.

### k=10
accuracy: 77.32%
AUC: 0.513 (positive class: 1)
Túlnyomorészt False Negatívakat produkál.

## 1. Kiugró értékek keresése
A legtöbb beápített Outlier process nagyon hosszú ideig tartott lefutni.
### 1. Densities (DB-Outlier)
Ez gyorsabban lefutott, de különböző paraméter-kombinációkra minden sort outlierként kezel.



2. Class Outlier Factors (COF)
3. Local Outlier Factors (LOF)
4. Distances


[] Visualization:
[] Interquartilis
[] Mean +- 3 standard deviation


## 2. Kategória változók kezelése
Az alábbi kategória változókkal akarunk foglalkozni:
Dummyzással
