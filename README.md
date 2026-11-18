# KC Hipodrom Kamnica

Projekt pri predmetu **Razvoj vseprisotnih informacijskih rešitev (RVIR)** v študijskem letu **2026/2027**.

## Članici ekipe:
- Ana Cvetko
- Živa Šumak

## Opis projekta

KC Hipodrom Kamnica je načrtovani prototip Android aplikacije za člane in osebje konjeniškega kluba Hipodrom Kamnica. Članom bo omogočal načrtovanje obiskov in pregled napovedane zasedenosti objektov, osebju pa pregled podatkov o konjih in dnevnih opravil.

Osrednja funkcionalnost bo **interaktivni tloris kluba**, na katerem bo mogoče preveriti napovedano zasedenost posameznih objektov. Podrobnejši opis funkcionalnosti je v [opisu projekta](./dokumentacija/opis-projekta.md), uporabniške vloge in pravice pa v [uporabniških scenarijih](./dokumentacija/uporabniski-scenariji.md).

## Tehnologije

- **React Native, Expo in TypeScript** – razvoj Android aplikacije.
- **Supabase** – podatkovna baza PostgreSQL, prijava uporabnikov in dostop do podatkov z upoštevanjem pravic (RLS).
- **Git, GitHub in GitHub Actions** – sodelovanje pri razvoju, nadzor različic in samodejno preverjanje kode.
- **Figma Make** – priprava vizualne zasnove in interaktivnih mockupov.

## Lokalni zagon

Za zagon projekta sta potrebna **Node.js** in **npm**.

Projekt prenesemo in namestimo odvisnosti:

```bash
git clone https://github.com/zivasumak/kc-hipodrom-kamnica.git
cd kc-hipodrom-kamnica
npm install
```

Razvojni strežnik zaženemo z ukazom:

```bash
npx expo start
```

Za preizkušanje na Android telefonu uporabimo aplikacijo **Expo Go** in skeniramo QR-kodo, ki se prikaže v terminalu. Telefon in računalnik morata biti povezana v isto omrežje.

Za preverjanje projekta v brskalniku lahko uporabimo:

```bash
npx expo start --web
```

Aplikacija je namenjena Androidu, spletni prikaz pa uporabljamo samo za razvojno preverjanje.

## Dokumentacija

Projektna dokumentacija je v mapi [`dokumentacija`](./dokumentacija/). V njej so zbrani [opis projekta](./dokumentacija/opis-projekta.md), [uporabniški scenariji](./dokumentacija/uporabniski-scenariji.md), [začetni podatkovni model](./dokumentacija/podatkovni-model.md), [začetna arhitektura](./dokumentacija/arhitektura.md) in [razvojni načrt](./dokumentacija/nacrt-razvoja.md).


## Trenutno stanje

Vzpostavljen je začetni Expo projekt s TypeScriptom. Preverjen je zagon v brskalniku in nastavljeno samodejno preverjanje TypeScript ter ESLint kode z GitHub Actions. Glavne funkcionalnosti in povezava s Supabase še niso implementirane.
