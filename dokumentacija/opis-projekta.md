# KC Hipodrom Kamnica – opis projekta

## 1. Namen aplikacije

**KC Hipodrom Kamnica** je načrtovani Android prototip mobilne aplikacije za člane in osebje konkretnega konjeniškega kluba Hipodrom Kamnica. V digitalni obliki rešuje vse probleme, ki jih imajo člani kluba, zaposleni in vodstvo.

## 2. Problem

Člani brez skupnega pregleda težje ocenijo, kdaj bodo posamezni objekti obremenjeni in kdaj potekajo organizirane dejavnosti. Osebje potrebuje dostop do pomembnih navodil za posamezne konje in pregleden seznam dnevnih opravil. Aplikacija združi te informacije v enostavnem mobilnem vmesniku.

## 3. Ciljni uporabniki

- **Član:** načrtuje obisk, spremlja zasedenost, označuje prisotnost in upravlja podatke svojih konj.
- **Trener/inštruktor:** poleg osnovnih članskih funkcij ureja svoje organizirane termine treningov in jahalne šole.
- **Konjar:** pregleduje informacije, potrebne za oskrbo konj, ter označuje opravljena dnevna opravila.
- **Vodja/lastnik:** upravlja klubske konje, objekte, kapacitete, organizirane termine in opravila.

Dostop je odvisen od uporabniške vloge in se preverja tudi v podatkovni bazi.

## 4. Glavne funkcionalnosti

### 4.1 Interaktivni tloris in napovedana zasedenost

Osrednji del aplikacije je poenostavljen, prepoznaven tloris dejanskega kluba. Na njem bodo označeni glavni objekti, na primer maneže, sprehajalka, izpusti in boksi. Uporabnik izbere objekt in dan ter pregleda napovedano zasedenost po časovnih intervalih, predvidoma po 30 minut. Podatki izhajajo iz dnevnih napovedi članov in organiziranih terminov. Presežena kapaciteta sproži opozorilo, ne pa prepovedi napovedi obiska. Napovedana zasedenost ni dokaz dejanske prisotnosti.

### 4.2 Dnevni načrt obiska

Ob prvem odprtju aplikacije v dnevu se članu ponudi možnost načrtovanja obiska. Navede lahko predviden prihod, odhod, objekte in čas njihove uporabe. Vprašanje lahko preskoči; svoj načrt lahko pozneje ustvari, spremeni ali izbriše. Napoved uporabe ni rezervacija objekta.

### 4.3 Konji in profili

Profil konja vsebuje ime, fotografijo, lastnika (član ali klub), podatke o prehrani, navodila za sprehajalko in izpust, kompatibilnost z drugimi konji, posebno nego in opombe. Član ureja le podatke svojih konj, pooblaščena oseba pa klubske konje. Konjar ima vpogled v informacije, potrebne za oskrbo. (Podatek o kompatibilnosti z drugimi konji je informativen; aplikacija ne razporeja konj samodejno - lahko npr. opozori uporabnika ki želi napovedat izpust svojega konja, da bo v tistem času v izpustu konj, ki z njegovim ni kompatibilen)

### 4.4 Treningi in jahalna šola

Organizirane dejavnosti uporabljajo skupen model termina: vrsta, datum, začetek in konec, objekt, odgovorni trener/inštruktor, oznaka ekskluzivnosti in po potrebi število udeležencev. Ekskluzivni termin blokira objekt in se prikaže kot rezerviran za trening oziroma jahalno šolo. Neekskluzivni termin prispeva k napovedani zasedenosti.

### 4.5 Evidenca prisotnosti

Uporabnik ročno označi »Sem na klubu« in ob odhodu »Zapustil sem klub«. Sistem shrani čas prihoda in odhoda ter med aktivno prisotnostjo prikaže oznako »Active«. Uporabnik nadzoruje, ali je njegova prisotnost vidna drugim. Evidenca prisotnosti je ločena od napovedi obiska.

### 4.6 Konjarjeva dnevna opravila

Konjar vidi podrobna opravila za posamezne konje: vrsto opravila, konja, predvideni čas, navodila in status. Pri izvedbi označi opravilo kot opravljeno; zabeležita se izvajalec in čas. Ob opravilu so na voljo relevantne posebne zahteve/informacije iz profila konja. Vodja ustvarja in ureja klubska opravila, kompleksno načrtovanje izmen pa ni predvideno.

Lastnik konja lahko pri še neizvedenih opravilih, povezanih z njegovim konjem, neposredno doda opombo (npr. »danes naj dobi samo pol merice hrane«, zabeleži se tudi datum in čas opombe) ali prekliče opravilo (npr. »danes konj ne gre na izpust«). Če želi novo opravilo (npr. dodatno nego poškodbe), pošlje zahtevo, ki jo mora potrditi vodja. Šele potrjeno novo opravilo se pojavi na konjarjevem seznamu za izvedbo. Že opravljenega opravila ni mogoče preklicati. 

## 5. Tehnološki okvir

- **React Native, Expo in TypeScript:** razvoj Android aplikacije.
- **Supabase PostgreSQL:** podatkovna baza.
- **Supabase Authentication:** prijava in uporabniški računi.
- **Supabase API in Row Level Security (RLS):** komunikacija s podatki in uveljavljanje pravic.
- **GitHub in GitHub Actions:** sodelovanje, nadzor različic, testi in priprava Android APK.
- **Figma Make:** samo vizualna zasnova in interaktivni mockupi.


## 6. Nadgradnje, ki sledijo, če bo čas

- Samodejno zaznavanje prisotnosti z GPS.
- AI pomočnik za načrtovanje obiska.
- Klepet med člani.
- Predlogi za prestavljanje treningov s potrjevanjem.
- Prijave na jahalno šolo.
- Dodeljevanje klubskih konj jahačem.
- Novice in dogodki.
- Potisna obvestila.
- Naprednejša avtomatizacija ponavljajočih se opravil.
- Spletna različica aplikacije.

Te funkcionalnosti niso del načrtovanega MVP.
