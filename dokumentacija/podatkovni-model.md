# KC Hipodrom Kamnica - začetni podatkovni model

## 1. Namen

Podatkovni model je začetni načrt podatkov, ki jih bo uporabljala aplikacija KC Hipodrom Kamnica. Temelji na [opisu projekta](./opis-projekta.md) in [uporabniških scenarijih](./uporabniski-scenariji.md).

Podatke bova shranjevali v **Supabase PostgreSQL**. Za zdaj so določene glavne entitete, njihovi podatki in povezave. Dokončne tabele, podatkovne tipe in omejitve bova pripravili ob izdelavi baze.

## 2. Glavne entitete

| Entiteta | Predvideni podatki | Namen |
|---|---|---|
| **Uporabniški profil** | ID uporabnika, ime, vloga, vidnost prisotnosti | Podatki o uporabniku, povezani s prijavo v Supabase Authentication. |
| **Konj** | ID, ime, fotografija, vrsta lastništva (član/klub), lastnik, prehrana, navodila za sprehajalko in izpust, posebna nega, opombe | Podatki o posameznem konju in njegovi oskrbi. |
| **Kompatibilnost konj** | ID obeh konj, podatek o kompatibilnosti | Informacija, ali sta konja primerna za skupen izpust. |
| **Objekt** | ID, ime, vrsta, kapaciteta, položaj na tlorisu | Podatki o manežah, sprehajalki, izpustih, boksih in drugih objektih. |
| **Dnevni načrt** | ID, uporabnik, datum, predvideni prihod in odhod | Napoved uporabnikovega obiska. |
| **Napoved uporabe objekta** | ID, dnevni načrt, objekt, začetek in konec uporabe, po potrebi konj | Posamezna uporaba objekta v okviru dnevnega načrta. |
| **Organizirani termin** | ID, vrsta (trening/jahalna šola), datum, začetek, konec, objekt, trener/inštruktor, ekskluzivnost, po potrebi število udeležencev | Skupen zapis za treninge in jahalno šolo. |
| **Prisotnost** | ID, uporabnik, dejanski prihod in odhod | Evidenca ročno označene prisotnosti na klubu. |
| **Opravilo** | ID, konj, vrsta, predvideni datum in čas, navodila, status, izvajalec in čas izvedbe, lastnikova opomba in čas opombe, kdo in kdaj je opravilo preklical | Posamezno opravilo za oskrbo konja. |
| **Zahteva za novo opravilo** | ID, konj, predlagatelj, vrsta, navodila, predvideni čas, status, odločitev vodje in čas odločitve | Predlog lastnika, ki postane opravilo šele po potrditvi vodje. |

Vsaka entiteta bo imela svoj identifikator (**ID**). Povezane podatke bova hranili prek identifikatorjev, ne s ponavljanjem istih podatkov v več tabelah.

## 3. Povezave med entitetami

- **Uporabnik – konji:** član ima lahko več svojih konj, konj pa je lahko tudi v lasti kluba.
- **Uporabnik – dnevni načrti – napovedi uporabe:** uporabnik lahko ustvari več dnevnih načrtov; posamezen načrt lahko vključuje več objektov in časov uporabe.
- **Objekt – napovedi in organizirani termini:** na isti objekt se lahko nanašajo različne napovedi in termini.
- **Trener/inštruktor – organizirani termini:** vsak termin ima odgovornega trenerja oziroma inštruktorja.
- **Uporabnik – prisotnosti:** uporabnik ima lahko več zapisov prihodov in odhodov.
- **Konj – opravila in zahteve:** posamezen konj ima lahko več opravil in zahtev za nova opravila.
- **Konj – konj:** povezava kompatibilnosti povezuje dva konja.

Napoved uporabe objekta lahko vsebuje tudi povezavo do konja, kadar je ta podatek potreben, na primer pri načrtovanem izpustu.

## 4. Osnovna pravila

### Dnevni načrti in zasedenost

Dnevni načrt je **napoved**, zapis prisotnosti pa podatek o dejanskem prihodu in odhodu. Zato bosta shranjena ločeno.

Napovedano zasedenost posameznega objekta bova izračunavali iz napovedi uporabe in organiziranih terminov, predvidoma v **30-minutnih intervalih**. Za zdaj ne načrtujeva dodatne tabele za že izračunano zasedenost.

Če je kapaciteta presežena, aplikacija uporabnika opozori, vendar mu ne prepreči oddaje napovedi. **Ekskluzivni organizirani termin** objekt rezervira za trening ali jahalno šolo; konfliktnega ekskluzivnega termina ni dovoljeno shraniti. Podatki o kompatibilnosti konj so namenjeni informativnim opozorilom, ne samodejnemu razporejanju.

### Konji in opravila

Član lahko spreminja podatke **svojih konj**, klubske konje pa ureja pooblaščena oseba. Konjar vidi navodila, potrebna za oskrbo.

Pri **še neizvedenem opravilu** svojega konja lahko lastnik neposredno doda ali spremeni opombo oziroma opravilo prekliče. Shrani se tudi čas opombe oziroma preklica. Že opravljenega opravila ni mogoče preklicati.

Za **novo opravilo** lastnik najprej odda zahtevo. Vodja jo potrdi ali zavrne. Šele po potrditvi se novo opravilo pojavi na konjarjevem seznamu. Ko konjar opravilo zaključi, se shranita izvajalec in čas izvedbe.

### Uporabniške pravice

Aplikacija bo prikazovala podatke glede na vlogo uporabnika. Trener/inštruktor ima tudi pravice člana. Vidnost prisotnosti drugih uporabnikov bo odvisna od njihove nastavitve zasebnosti.

Pravice za dostop in spreminjanje podatkov bova preverjali tudi v bazi s **Supabase Row Level Security (RLS)** in, kjer bo potrebno, z dodatnimi preverjanji posameznih sprememb.

## 5. Kaj morava še določiti?

Pred izdelavo dejanske baze morava potrditi:

- katere objekte bo vseboval tloris, njihove položaje in kapacitete;
- kako natančno se šteje zasedenost pri različnih vrstah objektov;
- dokončen način zapisa uporabniških vlog;
- pravila za popravljanje že zabeleženih izvedb opravil in ravnanje ob brisanju objekta, ki je že povezan z načrti ali termini.

To je **začetni podatkovni model**, zato še ne vsebuje SQL ukazov ali končne sheme baze. Med razvojem ga bova dopolnjevali glede na potrjena pravila in dejansko implementacijo.
