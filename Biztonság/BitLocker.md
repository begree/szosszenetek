# Mi a Bitlocker

A BitLocker a Windows által kínált meghajtótitkosítási megoldás. A beállítás során meg kell adni egy erős jelszót. Ezután, amikor legközelebb csatlakoztatod a meghajtót a géphez, ezt a jelszót kell megadni ahhoz, hogy hozzáférj az ott tárolt adatokhoz. Jelszó hiányában nem lehet hozzáférni az adatokhoz.

A meghajtót a jelszó ismerete nélkül is le lehet formázni, ekkor azonban a BitLocker által védett adatok is törlődnek, és nem lehet hozzáférni hozzájuk. Ha például elveszíted a fontos adataidat tartalmazó pendrive-ot az utcán, és valaki megtalálja, nem fogja tudni, mi van rajta. Maximum leformázhatja, és így minden adatot letöröl róla.

Fontos, hogy a BitLockert alapvetően a Windows ismeri alapértelmezés szerint, és abból is legalább a Pro verzióra van szükség. Azért csak erre térek ki, mert a legtöbb olvasó számára ez a legegyszerűbb kéznél lévő eszköz, amit egyből tud használni.

Egyéb rendszeren is amúgy lehetőség van ilyen meghajtó olvasására, pl. BitLocker reader for Mac vagy Linuxon a Dislocker alkalmazások segítségével.

# BitLocker bekapcsolása

Két egyszerű módszerrel lehet bekapcsolni a BitLockert:

1. Kattints jobb gombbal a csatlakoztatott meghajtóra, majd válaszd a BitLocker bekapcsolása lehetőséget.
2. Nyisd meg a BitLocker alkalmazást, válaszd ki a megfelelő meghajtó betűjelét, és kattints a BitLocker bekapcsolása szövegre.

Ezután megjelenik egy ablak, ahol meg kell adnod a jelszót. Ha több meghajtót használsz, például több biztonsági mentéshez, használhatsz ugyanazt a jelszót mindegyikhez. Fontos, hogy ez a jelszó ne legyen más helyen használatban. Még jobb lenne, ha mindegyikhez egyedi jelszót használnál, de ne bonyolítsd túl. A lényeg, hogy ha véletlenül elveszíted a meghajtót, ne lehessen könnyen hozzáférni az adatokhoz.

Ezután mentsd el a visszaállítási kulcsot egy fájlba (később ki is nyomtathatod, ha szeretnéd). Azért javaslom ezt a megoldást, mert lehet, hogy pont a Mircosoft fiókból zártad ki magad, és ha a Microsoft fiókban való tárolást választottad, akkor nem fogsz hozzáférni. Ellenben így igen.

Itt két fontos dolog lesz: egy Identifier és egy Recovery Key.
```
Például:
Identifier:458B81C8-3D0C-4501-96B3-6F7CA295FDB7
Recovery Key: 434940-695607-241681-691933-554037-360239-063140-688985
```

Ezeket jegyezd tedd el biztonságos helyre. Fontos, hogy ezek viszont minden esetben egyediek lesznek, tehát ha van 2 titkosított pendriveod, akkor ezek az adatok el fognak térni. Ennek akkor van jelentősége, ha a jelszót elfelejtetted, és szeretnél hozzáférni az adataidhoz. Akkor fel fogja ajánlani a lehetőséget, hogy add meg a visszaállításhoz szükséges kulcsot (Recovery Key). Mutatni fogja az Identifier sor elejét, ebből tudod majd, hogy mire lesz szükséged.

# Helyreállítási kulcs kezelése

A BitLocker által adott helyreállítási kulcsok tárolása kiemelten fontos. Javaslom, hogy ezeket a kulcsokat "védtelenül" tárold, de 3-4 különböző helyen:

- Egy példányt a Gmail fiókodban
- Egy példányt a Proton Mail fiókodban
- Egy példányt a telefonodon
- Akár ki is nyomtathatod, és egy könyvbe beleteheted

Ne írd ki nagy betűkkel, hogy ez pontosan micsoda; a lényeg, hogy te tudd. Ennek csak akkor van értelme, ha fizikailag hozzáférsz a BitLocker által védett meghajtóhoz. Ha el is lopják a telefonodat, és megtalálják rajta ezt a fájlt, önmagában nem tudnak vele mit kezdeni, csak ha a pendrive is náluk van.

Javaslom, hogy egy egyszerű szöveges fájlba (txt) írd bele ezeket a kulcsokat, majd nevezd át a fájlt, például aranyoskiscica.jpg-re. Így avatatlan szemek csak egy képfájlt látnak, amit nem tudnak megnyitni, de te tudod, hogy csak a kiterjesztést kell visszaírnod txt-re.

A cél nem az, hogy teljesen lehetetlen legyen feltörni a védelmet, hanem hogy te gyorsan hozzáférj a kulcshoz, ha szükséged van rá. Az alkalmi tolvajok ne tudjanak könnyedén hozzáférni az adataidhoz. Ne bonyolítsd túl a dolgot, mert ha 2-3 év múlva szükséged lesz a kulcsra, és elfelejted, hogyan tároltad, akkor te sem fogsz hozzáférni.