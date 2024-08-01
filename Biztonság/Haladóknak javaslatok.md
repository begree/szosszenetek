Itt néhány további javaslatot gyűjtöttem össze, amelyekkel még jobban biztosíthatod magad. Ezek a tippek azonban nagyobb odafigyelést és alaposságot igényelnek. Csak akkor kövesd ezeket, ha teljesen biztos vagy benne, hogy évek múlva is emlékezni fogsz arra, miért és hogyan hajtottad végre őket, mert különben saját magadat is kizárhatod.

# Tartalom
- [[#Titkos kódokhoz és visszaállító kulcsok sózása]]
- [[#3-2-1-1 biztonsági mentési szabály]]
- [[#Rendszeresen ellenőrizni a biztonsági mentést]]
- [[#Ne használd a böngésző jelszókezelőjét]]

# Titkos kódokhoz és visszaállító kulcsok sózása

A sózás az, amikor egy jelszót biztonságosabbá teszünk azzal, hogy hozzáadunk egy extra, véletlenszerű szövegrészt, mielőtt elmentenénk. Olyan, mintha egy titkos összetevőt adnánk a recepthez, hogy csak mi tudjuk, mi is az igazi jelszó.

Te is hasonlóan eljárhatsz. Már egy minimális változtatás is sokat segíthet.

Amikor lementesz egy kulcsot a biztonsági mentésedhez, adj hozzá egy extra karaktert valahova. Például minden elmentett kulcshoz, titokhoz, visszaállítási kódhoz szúrj be véletlenszerűen egy oda illőnek tűnő betűt vagy számot a 3. karakter helyére (pl. ha a kód csak számokból áll, akkor legyen a 3. karakter is egy szám). Javaslom, hogy mindenhol egységesen ugyanazt a logikát kövesd, nem kell túlgondolni. Nem számít maga a szám/betű, sőt, lehetőleg ne mindig ugyanaz legyen, mert feltűnő lehet, ha mindenhol ugyanaz a karakter áll ugyanazon a helyen.

Ezzel a módszerrel, ha kiszivárognak a 2FA alkalmazásnál a kódgeneráláshoz a kódok (secret, seed), de van bennük valahol egy véletlenszerű karakter, akkor ha valaki nem tudja pontosan melyik karakter van rossz helyen, mit kell kitörölni vagy megváltoztatni, akkor nem lesz képes a kódjaid megtekintésére. Ehhez pusztán elég 1 ilyen karakter is, és máris szinte lehetetlenné teszed a dolgát. Viszont fontos, hogy tudd, hogy ezt tetted, mert ha elfelejted, akkor te magad sem leszel képes visszafejteni.

Ugyanez igaz lehet pl. a BitLocker visszaállítási kulcsához is, ha még ezt fel is írtad valahova, vagy pl. az emailjeid között ott csücsül, akkor sem lehet vele a titkosított pendrive-ot feloldani.

# 3-2-1-1 biztonsági mentési szabály

A kibővített 3-2-1-1 szabály a következőképpen néz ki:

1. Tarts legalább három (3) másolatot az adatokról!
2. Két (2) másolatot tárolj különböző adathordozókon!
3. Tárolj egy (1) másolatot külső helyszínen!
4. Hozz létre egy (1) megváltoztathatatlan vagy leválasztott másolatot!

Az én megoldásom:

- Egy BitLockerrel védett pendrive a lakásban.
- Egy BitLockerrel védett, írásvédhető SD kártya a pénztárcámban.
- Egy erősen védett és titkosított fájl a OneDrive és ProtonDrive felhőszolgáltatásokban.

Ehhez a módszerhez már egy 1 GB-os tárhely is bőségesen elegendő, mivel nagyon kevés adatot kell tárolni.

Fontos, hogy ezek a biztonsági mentések megfelelően védettek legyenek. Ha például elhagynám az SD kártyát, és az nem lenne megfelelően védett, bárki hozzáférhetne az érzékeny adatokhoz, amelyek a helyreállításhoz vagy belépéshez szükségesek.

A felhőbe történő mentésnél is érdemes valamilyen védett módot alkalmazni. Erre javaslom a ProtonDrive-ot, mivel ez a szolgáltatás a felhőben is titkosítva tárolja az adatokat, amelyeket csak a jelszóddal lehet feloldani. A ProtonDrive-ba is érdemes védett módon menteni az adatokat, például egy jelszóval védett ZIP fájlban. A 2 GB-os ingyenes korlát nem probléma, mivel az így mentett adatok nagyon kevés helyet foglalnak.

Azért nagyon fontos, hogy legyen offline biztonsági másolat is, mert ha pl. egy zsarolóvírus megtámadta a számítógéped, és mindent letitkosított rajta, és még a felhőbe lévő filet is sikerült neki, akkor is neked az offline elmentett adatok külön megvannak.

# Rendszeresen ellenőrizni a biztonsági mentést

Nagyon jó, ha több biztonsági másolatod van, viszont időnként (havonta-félévente) érdemes ellenőrizni, hogy ténylegesen hozzá is tudsz férni ezekhez a mentésekhez. A felhőben tárolt adatokat véletlenül törölheted, a pendrive meghibásodhat, vagy elfelejtheti az adatokat. Ha mondjuk először 3 év múlva lenne szükséged ezekre az adatokra, és nem tudsz belépni, mert elfelejtetted a jelszavad, vagy eltűnt az adat, az igen kellemetlen lenne.

Ha rendszeresen meggyőződsz róla, hogy még minden mentésed megvan, és hozzá tudsz férni, akkor az adatvesztés esélye minimálisra csökken.

Az én javaslatom, hogy ha tárolsz felhőben adatokat (természetesen jelszóval védve), rendszeresen nézd meg, hogy meg tudod-e őket még nyitni.

Az SD kártyák és pendrive-ok idővel "elfelejtik", mi volt rajtuk (ez legtöbb esetben egy évet vagy éveket jelent), ezért jobb rendszeresen "emlékeztetni" őket. Erre a legegyszerűbb módszer az, ha lemented, ami rajta van, majd visszamásolod, de még jobb ha az alább írt szinkronizálással oldod meg.

Fontos, hogy rendszeresen szinkronizáld a biztonsági mentéseid, tehát lehetőség szerint legyen mindegyik egyforma. Ha nem is teljesen naprakész, ne várj vele túl sokat.

Ha például csak az egyik pendrive-ra mentetted a legutolsó regisztrációdhoz az adatokat, de nem szinkronizáltad máshol is, akkor ha egy hét múlva kizárod magad, és nem találod pont azt a pendrive-ot, nem fogsz hozzáférni, és nem lesz meg máshol sem.

A javaslatom, hogy a felhőben egy jelszóval védett fájl legyen az elsődleges, ahová mentesz, és utána ezt a ZIP fájlt másold át a többi mentési helyre is.

# Ne használd a böngésző jelszókezelőjét

Bár kényelmes lehet, ha a Chrome, Safari stb. elmenti a jelszavaidat, ez az egyik legkevésbé biztonságos megoldás. Én a Proton Pass-t javaslom erre a célra.

Különösen fontos, hogy a böngésző és Google/Chrome vagy az Apple/Safari ne legyen az elsődleges jelszókezelőd. A támadók kiemelt célpontjai ezek a rendszerek, mert ha sikerül például a Gmail fiókodba belépniük, akkor nem csak egy fiókot, hanem mindent elérhetnek, ahol nincs egyéb biztonsági megoldás (pl. 2FA), egyszerűen egy jelszó visszaállító email segítségével. Ha a jelszavaid a Chrome-ban vannak elmentve, a támadó azonnal szinkronizálhatja ezeket is a saját rendszerébe.

Ezáltal megszerzik az email címedet és az összes ott tárolt regisztrációdat (hova, milyen felhasználóval, milyen jelszóval). Nem kell találgatniuk, hogy hol vagy még regisztrálva azzal az email címmel, mert minden információ rendelkezésre áll. Ellenben ha külön helyen tárolod a jelszavakat, akkor legalább ezeket az adatokat nem kínáltad tálcán.