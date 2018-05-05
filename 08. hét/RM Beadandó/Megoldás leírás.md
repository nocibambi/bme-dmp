A megtalált legnagyobb AUC érték 0.614, ami k=210 esetben jön ki.

Főbb lépések:
1. Kiugró értékekhez egy korábbi subprocesst használtam fel, mivel a rapidminer beépített processzeihez képest ez tűnt a leghasználhatóbbnak.
2. Kategória változókból próbáltam bináris változókat csinálni, de nem segítették a teljesítményt, ezért inkább kiszűrtem őket.
3. Normalizálást a rapidminer beépített processzével végeztem el.
4. Az optimalizáláshoz az Optimize Parameters (Grid) operátort használtam. Egy ideig 1-1000 intervallumban vizsgáltam, de 210-nél csak alacsonyabb optimum-értékek jöttek ki, ezért 300-nál maximalizáltam az iterációk számát.
