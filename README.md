# English GitHub README

# sPg Star Citizen Mining Comparator

A searchable and version-aware Star Citizen mining equipment comparator for mining heads, active modules, passive modules and mining gadgets.

The tool automatically retrieves current LIVE equipment data from the Star Citizen Wiki API. It also includes a UEX-powered shopping list that finds the simplest purchasing solution by minimizing the number of separate locations the player must visit.

The entire application is contained in a single HTML file. No installation, server or database is required.

## Main features

* Searchable mining head, module and gadget database.
* Separate filters for mining heads, active modules, passive modules and gadgets.
* Filtering by size and gameplay modifiers.
* Sortable comparison table.
* Direct comparison of up to four selected items.
* Compact display of mining power, extraction power, resistance, instability, charge rate, green zone, inert material and other available modifiers.
* Direct links to the corresponding Star Citizen Wiki item pages.
* Automatic detection of the current default LIVE game version.
* Automatic loading of new mining equipment added to the Wiki API.
* Embedded fallback data when the remote API is temporarily unavailable.
* Manual PTU preview entries for equipment that does not yet exist in the LIVE API.
* Automatic replacement of PTU preview data when the item becomes available in the LIVE API.
* Integrated UEX shopping cart.
* Quantity controls for every selected item.
* Minimum-stop shopping calculation.
* Location-grouped shopping results with item prices and total cost.
* Responsive dark Star Citizen-inspired interface.

## Automatic data updates

When the application opens, it requests the current default game version from the Star Citizen Wiki API.

The application then loads:

* The complete mining laser catalogue.
* The complete mining modifier catalogue.
* Additional items classified as mining equipment.
* Detailed item specifications for all detected mining equipment.

The Star Citizen Wiki API supports version-scoped game data. When the version parameter is omitted, the API uses its current default game version. List endpoints support filtering and pagination, allowing the application to discover newly added mining equipment without requiring a manually updated item list. ([GitHub][1])

New equipment is included automatically when:

1. It appears in one of the monitored mining categories or classifications.
2. It contains a supported mining specification in the API response.
3. The API structure remains compatible with the fields used by the application.

A manual code update may still be required if the API provider fundamentally changes endpoint names, response structures or mining specification field names.

## PTU equipment

Items that are known from PTU information but are not yet available in the LIVE Wiki API can be stored as local preview entries.

These entries are clearly marked as PTU or preliminary data.

When the same item later appears in the LIVE API, the application automatically prefers the complete LIVE API record and removes the duplicate local PTU presentation.

PTU statistics can change before release and should not be treated as final.

## UEX shopping list

Every item has a shopping-cart button.

Clicking the button once adds the item to the cart. Clicking it again removes the item. Items currently present in the cart receive a visible selected state.

Inside the shopping window, the user can:

* Increase or decrease quantities.
* Remove individual items.
* Clear the complete shopping list.
* Start the UEX location search.
* View the shopping list and search result side by side.

The shopping algorithm prioritizes only one main objective:

**Buy the complete list while visiting the fewest separate locations possible.**

Stores located within the same station, city, outpost or point of interest are grouped into one stop whenever the available UEX location information allows it.

Price does not create an additional stop. It is only used as a secondary tie-breaker when an item is available at multiple already-selected, equally convenient locations.

The result includes:

* Number of required stops.
* Star system and location.
* Shop or terminal name.
* Items to purchase at each stop.
* Required quantities.
* Unit prices.
* Location subtotals.
* Total estimated cost.

## Data sources and attribution

### Star Citizen Wiki API

Used for:

* Current default game version.
* Item names and UUIDs.
* Manufacturers.
* Mining equipment categories.
* Mining head specifications.
* Mining module and gadget modifiers.
* Item detail links.
* Detection of newly added mining equipment.

Links:

* [Star Citizen Wiki API documentation](https://docs.star-citizen.wiki/)
* [Star Citizen Wiki API GitHub repository](https://github.com/StarCitizenWiki/API)
* [Star Citizen Wiki API base address](https://api.star-citizen.wiki/api)

The Star Citizen Wiki API is community-maintained and provides version-scoped game data sourced from game files, the RSI website and community contributions. Its public documentation describes the current default-version endpoint, filtering, pagination and game-item endpoints. ([GitHub][1])

### UEX API

Used for:

* Item purchase prices.
* Item UUID matching.
* Terminal identification.
* Shop and terminal names.
* Star system, station, city, outpost and POI information.
* LIVE availability information.
* Minimum-stop shopping calculations.

Links:

* [UEX items_prices_all documentation](https://uexcorp.space/api/documentation/id/get_items_prices_all/?set_lang=en_US)
* [UEX terminals documentation](https://uexcorp.space/api/documentation/id/get_terminals?is_kiosk=0&set_lang=en_US)
* [UEX website](https://uexcorp.space/)
* [UEX API base address](https://api.uexcorp.uk/2.0)

The `items_prices_all` resource provides item UUIDs, terminal IDs, item names and current purchase prices. The `terminals` resource supplies the location hierarchy and LIVE availability information used to group shops into stops. UEX states that its data is community-maintained and may not always match the current LIVE servers exactly. ([uexcorp.space][2])

## Local caching

UEX responses are temporarily stored in the browser’s local storage.

The current application uses a six-hour local cache to avoid repeatedly downloading the complete item-price and terminal datasets during the same session period.

The user can refresh the page or clear browser storage when a completely fresh local dataset is required.

## Running the application

1. Download the HTML file.
2. Open it in a modern web browser.
3. Allow the page to access the public Wiki and UEX API endpoints.
4. Wait for the LIVE API status indicator to finish loading.

No installation or build process is required.

A normal web host or GitHub Pages is recommended because some browsers may restrict remote API requests when an HTML file is opened directly through a local `file://` address.

## Limitations

* Wiki and UEX information is maintained by third parties.
* API data can temporarily lag behind the LIVE game version.
* PTU values are preliminary and can change.
* Shop inventories and prices may differ from the actual game servers.
* A complete redesign of either external API may require a code update.
* The application does not calculate exact flight time or navigation distance.
* The shopping algorithm minimizes separate locations, not travel duration.
* Module stacking and final combined loadout values are not calculated because these mechanics can be version-dependent.

## Disclaimer

This is an unofficial, community-made fan tool.

It is not affiliated with, endorsed by or sponsored by Cloud Imperium Games, Roberts Space Industries, the Star Citizen Wiki project or UEX.

Star Citizen, Roberts Space Industries and Cloud Imperium are trademarks or registered trademarks of their respective owners.

Third-party game data remains subject to the terms and licensing conditions of its original providers.

---

# Magyar GitHub README

# sPg Star Citizen Mining Összehasonlító

Kereshető és verziókövető Star Citizen segédoldal mining headek, aktív modulok, passzív modulok és mining gadgetek összehasonlítására.

Az oldal az aktuális LIVE adatokat automatikusan lekéri a Star Citizen Wiki API-ból. A beépített UEX bevásárlólista pedig megkeresi azt a beszerzési megoldást, amelynél a lehető legkevesebb külön helyen kell megállni.

A teljes alkalmazás egyetlen HTML-fájlban található. Nem igényel telepítést, külön szervert vagy adatbázist.

## Fő funkciók

* Kereshető mining head, modul és gadget adatbázis.
* Külön kategóriaszűrés mining headekre, aktív modulokra, passzív modulokra és gadgetekre.
* Szűrés méret és különböző mining módosítók alapján.
* Rendezhető összehasonlító táblázat.
* Legfeljebb négy kijelölt elem közvetlen összehasonlítása.
* Mining power, extraction power, resistance, instability, charge rate, green zone, inert material és más módosítók kompakt megjelenítése.
* Közvetlen hivatkozás az adott Star Citizen Wiki-adatlapra.
* Az aktuális alapértelmezett LIVE játékverzió automatikus felismerése.
* A Wiki API-ba később bekerülő új mining eszközök automatikus betöltése.
* Beágyazott tartalék adatok hálózati vagy API-hiba esetére.
* Kézzel megadott PTU-előzetesek a LIVE API-ban még nem szereplő eszközökhöz.
* A kézi PTU-adat automatikus lecserélése, amikor az elem bekerül a LIVE API-ba.
* Beépített UEX bevásárlókosár.
* Darabszám állítása minden kiválasztott eszköznél.
* Legkevesebb megállóra optimalizált beszerzési keresés.
* Helyszínenként csoportosított találatok árakkal és végösszeggel.
* Reszponzív, sötét Star Citizen-hangulatú felület.

## Automatikus adatfrissítés

Az oldal megnyitásakor lekéri a Star Citizen Wiki API aktuális alapértelmezett játékverzióját.

Ezután betölti:

* A teljes mining laser katalógust.
* A teljes mining modifier katalógust.
* A mining kategóriába vagy classification alá sorolt további elemeket.
* Az észlelt mining eszközök részletes adatlapját.

A Wiki API játékverzióhoz kötött adatokat szolgáltat. Ha nincs külön verzió megadva, az aktuális alapértelmezett verziót használja. A listázó végpontok támogatják a szűrést és a lapozást, ezért az oldal nem kizárólag egy előre kézzel összeállított névlistából dolgozik. ([GitHub][1])

Egy új eszköz automatikusan bekerülhet, ha:

1. Megjelenik valamelyik figyelt mining kategóriában vagy besorolásban.
2. Az API válaszában megtalálható a támogatott mining specifikáció.
3. Az API mezőinek felépítése kompatibilis marad az oldal feldolgozási rendszerével.

Kódmódosítás akkor válhat szükségessé, ha az API szolgáltatója teljesen átnevezi a végpontokat, vagy alapjaiban megváltoztatja a válaszok és mining mezők szerkezetét.

## PTU-eszközök

A PTU-információkból már ismert, de a LIVE Wiki API-ban még nem szereplő eszközök helyi előzetes adatként jelenhetnek meg.

Ezek külön PTU vagy előzetes jelölést kapnak.

Amikor ugyanaz az eszköz később bekerül a LIVE API-ba, az oldal automatikusan a teljes LIVE API-adatlapot részesíti előnyben, így nem jelenik meg mellette külön, duplikált PTU-sor.

A PTU-értékek megjelenés előtt bármikor változhatnak.

## UEX bevásárlólista

Minden eszköz mellett található egy kosárgomb.

Egy kattintással az eszköz bekerül a kosárba. A következő kattintással teljesen kikerül belőle. A kosárban lévő elemek külön vizuális jelölést kapnak.

A külön kosárablakban lehet:

* Növelni vagy csökkenteni a darabszámot.
* Egyenként törölni az eszközöket.
* Törölni a teljes listát.
* Elindítani a UEX-keresést.
* Egymás mellett látni a kosarat és a találatot.

A keresés egyetlen elsődleges célt követ:

**A teljes bevásárlólista a lehető legkevesebb külön hely meglátogatásával legyen beszerezhető.**

Az azonos állomáson, városban, outposton vagy POI-n található üzleteket az oldal egy megállónak kezeli, amennyiben ezt a UEX helyadatai lehetővé teszik.

Az ár miatt a program nem ad hozzá újabb megállót. Az ár csak másodlagos döntési szempont, amikor ugyanaz az eszköz több, már kiválasztott és teljesen egyenértékű helyen is megvásárolható.

A találat tartalmazza:

* A szükséges megállók számát.
* A csillagrendszert és a helyszínt.
* Az üzlet vagy terminál nevét.
* A helyszínen megvásárolandó eszközöket.
* A szükséges darabszámokat.
* A darabárakat.
* A helyszínenkénti részösszeget.
* A teljes becsült vételárat.

## Felhasznált adatforrások

### Star Citizen Wiki API

Felhasználási területek:

* Aktuális alapértelmezett játékverzió.
* Elemnevek és UUID-k.
* Gyártók.
* Mining kategóriák és besorolások.
* Mining head specifikációk.
* Modul- és gadgetmódosítók.
* Wiki-adatlapokra mutató hivatkozások.
* Új mining eszközök automatikus felismerése.

Hivatkozások:

* [Star Citizen Wiki API dokumentáció](https://docs.star-citizen.wiki/)
* [Star Citizen Wiki API GitHub repository](https://github.com/StarCitizenWiki/API)
* [Star Citizen Wiki API alapcím](https://api.star-citizen.wiki/api)

A Star Citizen Wiki API közösségi karbantartású szolgáltatás. A dokumentáció szerint játékfájlokból, az RSI weboldaláról és közösségi forrásokból származó, verziókezelt adatokat biztosít. ([GitHub][1])

### UEX API

Felhasználási területek:

* Eszközök vételára.
* UUID-alapú párosítás.
* Terminálazonosítás.
* Üzlet- és terminálnevek.
* Csillagrendszer, állomás, város, outpost és POI adatok.
* LIVE elérhetőségi állapotok.
* A legkevesebb megállós bevásárlólista kiszámítása.

Hivatkozások:

* [UEX items_prices_all dokumentáció](https://uexcorp.space/api/documentation/id/get_items_prices_all/?set_lang=en_US)
* [UEX terminals dokumentáció](https://uexcorp.space/api/documentation/id/get_terminals?is_kiosk=0&set_lang=en_US)
* [UEX weboldal](https://uexcorp.space/)
* [UEX API alapcím](https://api.uexcorp.uk/2.0)

Az `items_prices_all` végpont tartalmazza többek között az item UUID-jét, a terminálazonosítót, az elem nevét és a legutóbbi vételárat. A `terminals` végpont biztosítja a helyszínek hierarchiáját és az elérhetőségi adatokat. A UEX közösségi adatbázis, ezért a megjelenített információ esetenként eltérhet a tényleges LIVE szerver állapotától. ([uexcorp.space][2])

## Helyi gyorsítótár

A UEX válaszokat az oldal ideiglenesen eltárolja a böngésző helyi tárhelyében.

A jelenlegi változat hatórás helyi gyorsítótárat használ. Ez megakadályozza, hogy minden kosárkeresésnél újra le kelljen tölteni a teljes ár- és termináladatbázist.

## Használat

1. Töltsd le a HTML-fájlt.
2. Nyisd meg egy modern böngészőben.
3. Engedélyezd a nyilvános Wiki és UEX API-k elérését.
4. Várd meg, amíg a felső API-állapotsor befejezi a LIVE adatok betöltését.

Nincs szükség telepítésre vagy fordítási folyamatra.

GitHub Pages vagy más normál webes tárhely használata ajánlott, mert egyes böngészők korlátozhatják a távoli API-k elérését, amikor a HTML közvetlenül helyi `file://` címről fut.

## Korlátok

* A Wiki és a UEX külső, közösségi adatforrás.
* Az API-adatok időnként lemaradhatnak a LIVE játék aktuális állapotától.
* A PTU-adatok előzetesek.
* Az üzletkészlet vagy az ár eltérhet a játékban látott értéktől.
* Az API-k teljes szerkezeti átalakítása kódmódosítást igényelhet.
* Az oldal nem számol pontos repülési időt vagy útvonalhosszt.
* A bevásárlólista a külön helyszínek számát csökkenti, nem az utazási időt.
* A program nem adja össze a modulok teljes loadout-hatását, mert a stacking működése játékverziónként változhat.

## Jogi nyilatkozat

Ez egy nem hivatalos, közösségi rajongói segédeszköz.

A projektet nem támogatja, nem szponzorálja, és nincs hivatalos kapcsolatban a Cloud Imperium Gamesszel, a Roberts Space Industriesszal, a Star Citizen Wiki projekttel vagy a UEX-szel.

A Star Citizen, a Roberts Space Industries és a Cloud Imperium az adott jogtulajdonosok védjegyei vagy bejegyzett védjegyei.

A külső adatforrásokból származó információkra azok eredeti szolgáltatóinak felhasználási és licencfeltételei vonatkoznak.
