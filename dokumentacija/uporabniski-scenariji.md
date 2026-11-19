# Uporabniške vloge, pravice in scenariji

## 1. Uporabniške vloge

### 1.1 Član

- **Vidi:** tloris in napovedano zasedenost, organizirane termine, svoje načrte obiskov, svoje konje in podatke, ki so mu dovoljeni za ogled; lastno evidenco prisotnosti ter prisotnost drugih samo, kadar je ta vidna po njihovih nastavitvah.
- **Ustvarja:** svoje dnevne načrte obiskov in zapise lastne prisotnosti; lahko poda zahtevo za novo opravilo pri svojem konju; novo opravilo začne veljati šele po potrditvi vodje.
- **Spreminja:** svoje načrte, podatke konj v svojem lastništvu in nastavitev vidnosti lastne prisotnosti; zaključi svojo aktivno prisotnost. Pri še neizvedenih opravilih svojega konja lahko neposredno doda ali spremeni opombo in neposredno prekliče opravilo; novo opravilo lahko le predlaga vodji v potrditev.
- **Ne sme spreminjati:** tujih načrtov in konj, klubskih konj, objektov, kapacitet, organiziranih terminov drugih uporabnikov in konjarjevih opravil za tuje konje oziroma dokončnih evidenc izvedbe.
- **Najpomembneje:** načrtovanje obiska, pregled zasedenosti in upravljanje lastnih konj.

### 1.2 Trener/inštruktor

- **Vidi:** vse, kar vidi član, ter svoje organizirane termine treningov in jahalne šole.
- **Ustvarja:** lastne organizirane termine z datumom, časom, objektom, vrsto, ekskluzivnostjo in predvidenim številom udeležencev, če je potrebno.
- **Spreminja:** lastne termine in vse, kar lahko spreminja član.
- **Ne sme spreminjati:** terminov drugih trenerjev, klubskih objektov in kapacitet, klubskih konj ter konjarjevih opravil, razen če mu je posebej dodeljena dodatna vloga/pooblastilo (ni del osnovnega MVP).
- **Najpomembneje:** pregled in urejanje lastnih treningov ter terminov jahalne šole, skupaj z napovedano zasedenostjo.

### 1.3 Konjar

- **Vidi:** današnja in druga relevantna opravila, opombe in preklice lastnikov ter potrjene nove naloge, potrebne podatke o konjih (prehrana, sprehajalka, izpust, posebna nega, opozorila in opombe za oskrbo) ter podatke o izvedbi opravil. Obseg drugih pogledov je odvisen od končne odločitve o navigaciji.
- **Ustvarja:** zapis izvedbe opravila (kdo in kdaj ga je opravil) ob spremembi statusa.
- **Spreminja:** status relevantnega opravila v »opravljeno«; po potrebi popravi svoj zapis po pravilih, ki jih še določimo.
- **Ne sme spreminjati:** navodil in lastništva konj, razporeda oziroma vsebine opravil, klubskih objektov, kapacitet ali terminov.
- **Najpomembneje:** jasen dnevni seznam opravil in hiter dostop do navodil za posameznega konja.

### 1.4 Vodja/lastnik

- **Vidi:** objekte, kapacitete, organizirane termine, klubske konje, opravila in napovedano zasedenost ter podatke, potrebne za upravljanje kluba. Zasebnost prisotnosti članov se upošteva tudi pri vodji, razen če se izrecno določi drugače.
- **Ustvarja:** klubske konje, objekte, organizirane termine in konjarjeva opravila.
- **Spreminja:** klubske konje, objekte in kapacitete, organizirane termine ter opise, navodila in statuse opravil; potrjuje ali zavrača zahteve lastnikov za nova opravila.
- **Ne sme spreminjati:** osebnih načrtov članov ali njihovih zasebnih konj brez posebej opredeljenega pooblastila; ne sme obiti dogovorjenih pravil zasebnosti.
- **Najpomembneje:** upravljanje klubskih podatkov, pregled zasedenosti in nadzor nad opravili.

**Opomba o vlogah:** Trener/inštruktor podeduje pravice člana. Druge kombinacije vlog niso potrjene. Za MVP se lahko uporabi ena primarna vloga na uporabnika, če se ekipa tako dogovori; model naj ne predpostavlja več vlog brez potrebe.

## 4. Ključni uporabniški scenariji

### UC-01: Prijava uporabnika
- **Uporabnik:** vse štiri vloge.
- **Namen:** varen dostop do funkcionalnosti, primernih njegovi vlogi.
- **Osnovni potek:** uporabnik odpre aplikacijo, vnese prijavne podatke; Supabase Authentication preveri prijavo; aplikacija pridobi njegov profil in vlogo ter odpre ustrezen začetni pogled.
- **Rezultat:** uporabnik je prijavljen in vidi dovoljena dejanja.
- **Izjema:** napačni podatki ali prekinjena povezava sprožijo razumljivo sporočilo; brez veljavne seje ni dostopa do zaščitenih podatkov.

### UC-02: Pregled tlorisa in zasedenosti
- **Uporabnik:** predvsem član, trener in vodja;
- **Namen:** preveriti napovedano uporabo objektov na izbrani dan
- **Osnovni potek:** uporabnik odpre tloris, izbere datum in objekt; aplikacija pokaže ime, vrsto, kapaciteto in napovedano zasedenost po 30-minutnih intervalih ter morebitne organizirane termine. Če načrtuje svojega konja dati na izpust ali pašnik, lahko prejme informativno opozorilo o nekompatibilnosti z drugim konjem, ki ima za isti objekt in čas vpisano napoved.
- **Rezultat:** uporabnik vidi pričakovano gnečo in opozorila ob preseženi kapaciteti ali ekskluzivnem terminu.
- **Opomba:** podatek je napoved, ne dokaz dejanske prisotnosti.

### UC-03: Vnos dnevnega načrta
- **Uporabnik:** član ali trener/inštruktor kot član.
- **Namen:** napovedati obisk in uporabo objektov.
- **Osnovni potek:** ob prvem odprtju aplikacije v dnevu se prikaže neobvezno vprašanje o obisku; uporabnik izbere datum oziroma današnji obisk, čas prihoda/odhoda, objekte in časovne razpone uporabe in potrdi vnos.
- **Rezultat:** shranjen je njegov načrt, ki prispeva k napovedani zasedenosti.
- **Izjema:** uporabnik lahko vprašanje preskoči; ob predvideni gneči vidi opozorilo, vendar lahko načrt vseeno shrani. Ob izbiri izpusta in konja se lahko prikaže tudi opozorilo o napovedani sočasni uporabi z nekompatibilnim konjem; opozorilo ne izvaja samodejnega razporejanja.

### UC-04: Sprememba ali izbris načrta
- **Uporabnik:** član ali trener/inštruktor kot član.
- **Namen:** uskladiti napoved z novimi namerami.
- **Osnovni potek:** uporabnik odpre svoj načrt, spremeni čase, objekte ali konja oziroma izbere izbris; aplikacija potrdi spremembo in ponovno izračuna napovedano zasedenost.
- **Rezultat:** v bazi ostane posodobljen načrt ali se načrt izbriše; tuji načrti ostanejo nedotaknjeni.

### UC-05: Pregled konjevega profila
- **Uporabnik:** lastnik konja, konjar za oskrbo, vodja za klubskega konja.
- **Namen:** pridobiti informacije o konju glede na pooblastila.
- **Osnovni potek:** uporabnik odpre seznam konj, do katerih ima dostop, izbere konja in vidi dovoljene podatke: ime, fotografijo, lastništvo, prehrano, navodila za sprehajalko/izpust, kompatibilnost, posebno nego in opombe.
- **Rezultat:** prikazane so informacije, potrebne za izbrano opravilo oziroma skrb za konja.
- **Opomba:** konjar vidi potrebna navodila, ne pa nujno vseh osebnih podatkov lastnika.

### UC-06: Urejanje lastnega konja
- **Uporabnik:** član ali trener/inštruktor, ki je lastnik konja.
- **Namen:** vzdrževati pravilne podatke o svojem konju.
- **Osnovni potek:** uporabnik odpre profil svojega konja, izbere urejanje, popravi dovoljene podatke in shrani; sistem preveri lastništvo.
- **Rezultat:** profil je posodobljen in konjar pri oskrbi vidi aktualna navodila.
- **Dodatno:** lastnik lahko pri opravilu svojega konja dopiše dnevno opombo (npr. spremenjena količina hrane), neposredno prekliče še neizvedeno opravilo (npr. izpust) ali pošlje zahtevo za novo opravilo (npr. dodatno nego), ki jo potrdi ali zavrne vodja. To je ločeno od trajnega urejanja profila konja.
- **Izjema:** sprememba tujega ali klubskega konja je zavrnjena tudi na ravni RLS.

### UC-07: Upravljanje treninga ali jahalne šole
- **Uporabnik:** trener/inštruktor za svoje termine; vodja/lastnik za klubsko upravljanje.
- **Namen:** evidentirati organizirano uporabo objekta.
- **Osnovni potek:** uporabnik ustvari ali uredi termin; vnese vrsto (trening/jahalna šola), datum, začetek, konec, objekt, odgovornega trenerja, ekskluzivnost in po potrebi število udeležencev; aplikacija preveri konflikt ekskluzivnih terminov in shrani veljaven termin.
- **Rezultat:** termin je viden v pregledu objekta; ekskluziven termin označi objekt kot rezerviran za trening oziroma jahalno šolo, neekskluziven pa prispeva k napovedani zasedenosti.
- **Izjema:** konflikt ekskluzivnih terminov prepreči shranjevanje spornega organiziranega termina. Prijave udeležencev niso del MVP.

### UC-08: Označevanje prisotnosti
- **Uporabnik:** član ali trener/inštruktor kot član.
- **Namen:** ročno evidentirati prihod in odhod.
- **Osnovni potek:** ob prihodu uporabnik pritisne »Sem na klubu«; shrani se čas prihoda in pokaže oznaka »Active«; ob odhodu pritisne »Zapustil sem klub«, s čimer se shrani čas odhoda; ločeno lahko nastavi vidnost prisotnosti drugim.
- **Rezultat:** nastane zapis prisotnosti, drugi ga vidijo samo skladno z nastavitvijo zasebnosti.
- **Opomba:** GPS in samodejno zaznavanje nista del MVP; prisotnost ne nadomešča dnevne napovedi uporabe objektov.

### UC-09: Pregled in izvedba konjarjevih opravil
- **Uporabnik:** konjar; vodja za pregled in upravljanje.
- **Namen:** zanesljivo opraviti dnevno oskrbo posameznih konj.
- **Osnovni potek:** konjar odpre seznam opravil, izbere opravilo, pregleda konja, vrsto, predvideni čas, navodila, posebne zahteve in morebitne lastnikove opombe in preklice; vidi le potrjena nova opravila, ne pa nepotrjenih zahtev kot nalog za izvedbo; preveri veljavni status opravila in po izvedbi označi opravilo kot opravljeno.
- **Rezultat:** zabeleženi so status, izvajalec in čas izvedbe; vodja vidi napredek. Lastnikov preklic učinkuje neposredno; zahteva za novo opravilo se konjarju prikaže kot opravilo za izvedbo šele po potrditvi vodje.
- **Izjema:** konjar ne more samovoljno spreminjati vsebine navodil ali zahtev lastnika; konjar ne sme označiti preklicanega opravila kot opravljenega; potrjevanje je potrebno samo za nova opravila.

### Dopolnitev UC-09: Zahteva za novo opravilo
- **Uporabnik:** lastnik konja (član ali trener/inštruktor) in vodja/lastnik.
- **Namen:** omogočiti lastniku, da predlaga dodatno oskrbo, brez samostojnega razporejanja novih opravil konjarju.
- **Osnovni potek:** lastnik pri svojem konju vnese zahtevo z vrsto opravila, navodili in predvidenim časom; zahteva dobi status »čaka na potrditev«. Vodja jo pregleda in potrdi ali zavrne. Ob potrditvi nastane veljavno opravilo za konjarja.
- **Rezultat:** potrjena zahteva postane opravilo; zavrnjena zahteva ne postane opravilo. Lastnik vidi status zahteve.
- **Varnost:** lastnik ne sme neposredno nastaviti statusa »potrjeno« ali ustvariti aktivnega konjarjevega opravila; to pravilo se uveljavi tudi v bazi.

### UC-10: Upravljanje objektov in klubskih podatkov
- **Uporabnik:** vodja/lastnik.
- **Namen:** ohranjati pravilne podatke, ki jih uporabljajo tloris, napovedi in oskrba konj.
- **Osnovni potek:** vodja odpre upravljavski pogled; doda ali uredi objekt (ime, vrsta, kapaciteta, položaj), klubski profil konja ali dnevno opravilo; shrani spremembo.
- **Rezultat:** dovoljene spremembe so zapisane v bazo in prikazane v ustreznih pogledih.
- **Izjema:** sistem preveri obvezna polja in pravice; brisanje objekta s povezanimi načrti/termini zahteva posebej dogovorjeno pravilo (npr. onemogočanje namesto fizičnega izbrisa).
