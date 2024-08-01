# Mi az a kétfaktoros hitelesítés
A kétfaktoros hitelesítés (two-factor authentication, 2FA) a multifaktoros hitelesítés egyik formája.

Több fajtája is létezik, de most csak egyre fogok részletesebben kitérni, amely az aktuális idő alapján generált kódot használ.

Alapesetben, amikor regisztrálsz egy helyre, legtöbbször van egy felhasználóneved és jelszavad. Azonban, ha valaki ezeket ismeri, be tud lépni, használhatja a nevedben a fiókodat, rosszabb esetben el is lophatja azt. Ha a fiókodban elmentett kártyaadatok is vannak, az illető akár vásárolhat is a nevedben.

A kétfaktoros hitelesítés megnehezíti a dolgot azzal, hogy még ha a felhasználóneved és jelszavad illetéktelen kezekbe is kerül, szükség van egy kódra is. Ha az illető nem tudja ezt a kódot, nem fog tudni belépni a fiókodba.

Erre a legelterjedtebb megoldás az, amikor egy körülbelül félpercenként változó, 6 jegyű kódot kell megadni. Mivel a kód folyamatosan változik, egy korábbi kód kiszivárgása sem jelent kockázatot.

Az idő és a kód hossza változhat, lehet rövidebb, hosszabb, de a lényege ez.
# Hogyan működik

Legtöbbször, amikor aktiválni szeretnéd ezt a szolgáltatást, egy QR kódot kell leolvasni, amely tartalmazza a legfontosabb adatokat a 2FA alkalmazás számára.

Ebben jellemzően az alábbi adatok szerepelnek:

- Titkos kód (angolul: secret vagy seed)
- Periódus (például fél perc, ilyen gyakran változik majd a kód)
- HASH algoritmus (legtöbbször SHA-1, de ezzel neked nem kell foglalkoznod)

Ami még benne lehet, de nem kötelező, és csak kényelmi szerepet tölt be:

- Felhasználói név
- Alkalmazás neve
- Az alkalmazás ikonja
- és még akár ennél is több

Amikor beolvasol egy ilyen QR kódot, vagy megnyitod/beírod a megfelelő adatokat, akkor a titkos kód segítségével az oldal és a telefonod pontosan tudni fogja, hogy mikor milyen kódot kell generálni. Ez már teljesen offline működik, és nincs szükség internetkapcsolatra a kód generálásához.

# Példa
## QR kód

![[qrcode_example.png]]
## Kézi beállításhoz az adatok

![[seed_period_number_example.png]]

## Link
otpauth://totp/remelemeznemfoglaltmeg@proton.me?secret=IH7GRYZ2IO5ZZU2KV457U2XN6UTSSIDO&issuer=Proton&algorithm=SHA1&digits=6&period=30

## Részletesen (a link alapján)
- Titkos kód: IH7GRYZ2IO5ZZU2KV457U2XN6UTSSIDO
- Periódus: 30
- HASH algoritmus: SHA1
- Szolgáltatás neve: Proton
- Felhasználó neve: remelemeznemfoglaltmeg@proton.me

# Biztonsági mentés
Nagyon fontos, hogy amikor ezt beállítod, a QR kódot, linket vagy a fent bemutatott adatokat mentsd el valamilyen módon. Ha van egy tartalék telefonod, érdemes lehet oda is beállítani párhuzamosan.

Létfontosságú, hogy legyen róla biztonsági mentésed, mert ha például ellopják a telefonodat, és nem volt róla biztonsági másolatod, akkor többé te sem fogsz tudni belépni az alkalmazásba, még ha tudod is a felhasználóneved és jelszavad.

Azonban ha a QR kódot vagy a link szövegét lemented biztonságos helyre (például egy pendrive-ra), később egy új készüléken ismét be tudod állítani, így ismét hozzáférhetsz az alkalmazáshoz.

# Visszaállítási kódok
A legtöbb esetben az oldal amikor bekapcsoltad a kétfaktoros azonosítást akkor mutat pár backup kódot, amivel ha elfelejtetted a QR kódot/linket/stb. lementeni, akkor még engedi feloldani.

Legtöbbször ezeket a kódokat csak egyszer, közvetlenül a 2FA bekapcsolása után mutatja meg. Ezeket is érdemes lementeni. Viszont továbbra is erősen javaslom, hogy készíts backupot már a legelején.

Viszont mivel ez függ az oldaltól, így nincs garancia rá, hogy kapsz ilyet. Ne alapozz a szolgáltató jóindulatára.

## Példa:

![[2fa_backup_recovery_codes.png]]

# Telefonos kód

Egy másik elterjedt módszer az SMS-ben küldött kód használata. Bár jobb megoldás, mint a semmi, mégsem ajánlott. Ennek fő oka, hogy a telefon ellopásával vagy úgynevezett SIM-swap támadással a támadó megszerezheti a SIM kártyát, és így az SMS-ben küldött kódot is, amely lehetővé teszi számára a hozzáférést. Ezért ahol csak lehet, érdemes az Authenticator alkalmazást használni, és a telefonos opciót csak végső esetben engedélyezni. Ugyanakkor még a felhasználónév-jelszó-SMS kód kombináció is biztonságosabb, mintha csak a felhasználónév és jelszó lenne.

# SIM-csere (SIM-swap) támadás

A SIM-swap egy olyan támadási módszer, amelynek során a támadó megszerzi az áldozat telefonszámát, általában úgy, hogy a mobilszolgáltatónál eléri a SIM-kártya cseréjét. A támadó gyakran az áldozat személyes adatait használja fel, hogy a szolgáltatónál úgy tegyen, mintha ő lenne az igazi előfizető. Ha a szolgáltató elfogadja a kérelmet, a támadó új SIM-kártyát kap az áldozat telefonszámával, és így minden hívás, SMS és kétfaktoros hitelesítési kód az ő telefonjára érkezik meg.

Ezzel a módszerrel a támadó hozzáférhet az áldozat online fiókjaihoz, beleértve a banki, e-mail és közösségi média fiókokat is, amelyek SMS-ben küldött kódokat használnak a biztonsági ellenőrzéshez.

Mivel új SIM-kártyát kap a támadó a telefonszámoddal, azonnal leszakadsz a hálózatról, és még telefonálni sem tudsz, ha érzékeled, hogy baj van. Másrészt, mivel a támadó új SIM-kártyát kapott, ismerni fogja a hozzá tartozó PIN-PUK kódokat is.

Ezért különösen fontos, hogy például az e-mail címed vagy egyéb szolgáltatás helyreállításához ne a telefonszámodat használd, ha lehetséges. Gondolj bele, hogy egy ilyen támadás során, ha elegendő pusztán egy SMS-ben kapott kód vagy link megnyitása, a támadó akár ezzel is megszerezheti a fiókodhoz való hozzáférést. Szerencsére a nagyobb szolgáltatók jobban védettek ez ellen, de ennek ellenére érdemes elővigyázatosnak lenni, és más helyreállítási módszereket választani, ha van rá lehetőség.

[Cikk a módszerről](https://telex.hu/techtud/2024/07/15/hekker-hekkeles-telefonszam-lopas-sim-kartya)

# Javaslatok a 2FA használatához

A példák miatt lehet említek konkrét alkalmazásokat, de nem az a fontos, hanem az elv. Ha más alkalmazást használsz, és nem fogadod meg a lenti javaslatokat, akkor ugyanúgy ki leszel téve a veszélynek, amiről írok.
## Külön alkalmazás használata

Használj külön alkalmazást erre a célra. Bár a Proton Pass képes 2FA-ra, ha ez az alkalmazás kompromittálódik, akkor nagy gondban lennél. A támadó láthatná, hogy milyen oldalra milyen névvel és jelszóval vagy regisztrálva. Ha még a 2FA is itt tárolódik, akkor szinte biztos, hogy a legtöbbe be is fog tudni lépni. Ha viszont egy külön alkalmazást használsz (pl. Authy), akkor még a jelszavaid ismeretében sem fog tudni belépni, mivel a 2FA kódokhoz nem fér hozzá.

Ezért is fontos továbbá, hogy a jelszókezelőben ne legyen elmentve semmilyen információ a 2FA alkalmazásról. Amikor telefonon beüzemeled az alkalmazást, állíts be egy erős jelszót, amit sehol máshol nem mentesz le, és a jövőben már elég csak ujjlenyomattal feloldani. Így még ha a támadó hozzáférne is a jelszókezelődhöz, nem fogja tudni, melyik hitelesítőt használod, és mivel a jelszó nincs elmentve, még ha tudná is, akkor sem lenne képes belépni.
## A felhasználói neved ne írd ki a 2FA alkalmazásba sem

Több olyan 2FA alkalmazás is van, ami kényelmi okokból megmutatja, melyik felhasználói névhez tartozik az aktuális kód, amit legtöbbször a QR kódban tárolt adatból tud. Javaslom, hogy ezeket az adatokat ne jelenítsd meg. Ha az alkalmazás betölti neked a nevet, töröld ki utólag.

Ha egy adott oldalra csak egy regisztrációd van, egyértelmű, hogy az a kód hozzá tartozik. Ha több regisztrációd is van, akkor is javaslom, hogy másképp nevezd át a bejegyzéseket. Így, ha valaki valahogyan meg tudja nyitni a 2FA alkalmazásod és látja a kódokat, nem fogja feltétlenül tudni, melyik kód melyik felhasználói névhez tartozik.