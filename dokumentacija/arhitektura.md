# KC Hipodrom Kamnica - začetna arhitektura

## 1. Osnovna zasnova

Aplikacijo razvijava kot **Android prototip** z uporabo React Native, Expo in TypeScript. Za prijavo uporabnikov in shranjevanje podatkov bova uporabili Supabase. Lastnega strežnika ne bova postavljali.

Predviden potek delovanja:

```text
Uporabnik (Android aplikacija)
          ↓
Uporabniški vmesnik (zasloni in komponente)
          ↓
Logika aplikacije (preverjanje vnosov, pravila in izračuni)
          ↓
Dostop do podatkov (Supabase API)
          ↓
Supabase
├── Authentication – prijava uporabnikov
└── PostgreSQL – podatkovna baza z RLS za preverjanje pravic
```

Tako bova ločili prikaz podatkov, pravila delovanja in komunikacijo z bazo. To bo olajšalo pregledovanje kode in poznejše spremembe.

## 2. Izbrane tehnologije

| Tehnologija | Namen |
|---|---|
| **React Native in Expo** | Razvoj in preizkušanje Android aplikacije. |
| **TypeScript** | Preglednejša koda in preverjanje podatkovnih tipov. |
| **Supabase PostgreSQL** | Shranjevanje podatkov o uporabnikih, konjih, objektih, obiskih, terminih in opravilih. |
| **Supabase Authentication** | Prijava uporabnikov. |
| **Supabase API in RLS** | Dostop do podatkov ter preverjanje pravic glede na uporabnika in njegovo vlogo. |
| **GitHub in GitHub Actions** | Sodelovanje, sledenje spremembam in samodejno preverjanje kode. |
| **Figma Make** | Vizualna zasnova in interaktivni mockupi zaslonov. |

Te tehnologije sva izbrali, ker omogočajo razvoj brez lastnega strežnika in uporabo večinoma brezplačnih orodij. Figma je namenjena zasnovi videza; dejansko mobilno aplikacijo bova izdelali v React Native.

## 3. Organizacija aplikacije

Kodo nameravava razdeliti na tri preproste dele:

- **Uporabniški vmesnik:** zasloni, obrazci in ponovno uporabne komponente. Tu uporabnik vidi podatke in vnaša spremembe.
- **Logika aplikacije:** preverjanje vnosov, obdelava časovnih intervalov, izračun napovedane zasedenosti in priprava opozoril.
- **Dostop do podatkov:** funkcije, ki prek Supabase pridobijo ali shranijo podatke.

Primer predvidene strukture:

```text
src/
  components/   skupne komponente vmesnika
  screens/      zasloni aplikacije
  logic/        pravila in izračuni
  data/         dostop do Supabase
  types/        skupni TypeScript tipi
```

**To je načrt, ne že ustvarjena struktura map.** Dodajali jih bova postopoma, ko jih bova potrebovali.

## 4. Pomembna pravila pri razvoju

**Tloris in zasedenost.** Izračun napovedane zasedenosti bo na enem mestu in bo temeljil na dnevnih načrtih ter organiziranih terminih. Ekskluzivni termini bodo objekt označili kot rezerviran, ob preseženi kapaciteti pa se bo prikazalo opozorilo. Napoved obiska ne pomeni rezervacije, dejanska prisotnost pa se vodi ločeno.

**Treningi in jahalna šola.** Obe dejavnosti bosta uporabljali skupen model organiziranih terminov. Pri dodajanju in spreminjanju terminov bo treba preverjati tudi konflikte ekskluzivne uporabe objektov.

**Konji in opravila.** Podatki o konjih in opravila bodo povezani. Lastnik konja bo lahko dodal opombo ali preklical še neizvedeno opravilo. Za novo opravilo bo poslal zahtevo, ki jo mora potrditi vodja, preden se pojavi na konjarjevem seznamu. Kompatibilnost konj bo služila informativnim opozorilom, ne samodejnemu razporejanju.

**Vloge in pravice.** Po prijavi bo aplikacija prikazala funkcionalnosti glede na uporabnikovo vlogo. Pravice ne bodo preverjene samo s skrivanjem gumbov, ampak tudi v Supabase z Row Level Security (RLS). Pri prisotnosti bo treba upoštevati uporabnikovo nastavitev vidnosti.

## 5. Preverjanje delovanja in nadaljnji razvoj

Ob vnosih bova preverjali obvezne podatke in smiselnost časovnih intervalov. Pri pridobivanju podatkov bova predvideli prikaz nalaganja, razumljiva sporočila ob napakah in možnost ponovnega poskusa, če povezava ne deluje.

Začetni projekt **Expo + TypeScript** je že pripravljen. Na GitHubu je vzpostavljen začetni **GitHub Actions** za preverjanje TypeScript in ESLint. Povezava s Supabase in glavne funkcionalnosti aplikacije še niso implementirane.

V naslednjih fazah bova dodajali zaslone, povezavo z bazo, pravila dostopa in avtomatizirane teste. Posebej bova preizkusili izračun zasedenosti in pravila opravil. Pred končno oddajo načrtujeva tudi gradnjo in preizkus Android APK.

Dokument opisuje **začetno arhitekturo**. Podatkovne entitete in povezave so predstavljene v [podatkovni-model.md](./podatkovni-model.md), glavne funkcionalnosti v [opis-projekta.md](./opis-projekta.md), uporabniške vloge in pravice pa v [uporabniski-scenariji.md](./uporabniski-scenariji.md).