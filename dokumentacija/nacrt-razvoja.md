# KC Hipodrom Kamnica - začetni načrt razvoja

## 1. Cilj in način dela

Cilj projekta je izdelati delujoč **Android prototip aplikacije KC Hipodrom Kamnica**. Razvijava ga dve študentki. Delo si bova razdelili na manjše naloge in se najprej posvetili osnovnim funkcionalnostim. Podrobnejši opis aplikacije je v [opis-projekta.md](./opis-projekta.md), scenariji in pravice pa v [uporabniski-scenariji.md](./uporabniski-scenariji.md).

Za razvoj bova uporabljali React Native, Expo in TypeScript, za podatke in prijavo uporabnikov pa Supabase. Napredek bova spremljali na GitHubu. Dodatne funkcionalnosti bova obravnavali šele, če bo po dokončanju osnovnega prototipa ostalo dovolj časa.

## 2. Glavni mejniki

| Mejnik | Rok | Načrtovani rezultat |
|---|---|---|
| Načrtovanje in prototipna dokumentacija | **20. 11. 2026 ob 08:00** | Opis projekta, uporabniški scenariji in diagram, mockupi, začetni podatkovni model in arhitektura, README, razvojni načrt, začetni Issues in delujoč osnovni GitHub Actions. |
| Delujoči prototip | **18. 12. 2026 ob 08:00** | Delujoča navigacija in pomemben del funkcionalnosti, začetna povezava s Supabase, prvi avtomatizirani testi ter avtomatizirana gradnja aplikacije. |
| Končna oddaja | **15. 1. 2027 ob 08:00** | Dokončan in preizkušen Android prototip, APK, delujoča GitHub Actions preverjanja in gradnja ter posodobljena dokumentacija in predstavitev. |

## 3. Razdelitev dela za prvi mejnik

Za prvi teden sva si delo razdelili na vsebinski oziroma vizualni del in tehnične priprave. Na GitHubu imava za te naloge odprte oziroma zaključene Issues.

| Odgovorni član | Naloge (GitHub Issues) |
|---|---|
| **Ana Cvetko** | **#3** – opis projekta; **#4** – uporabniški scenariji in diagram primerov uporabe; **#5** – Figma mockupi in načrt navigacije. |
| **Živa Šumak** | **#1** – repozitorij in dostopi; **#2** – začetni Expo projekt; **#6** – začetni podatkovni model; **#7** – arhitektura in tehnologije; **#8** – README in razvojni načrt; **#9** – začetni GitHub Actions. |

Pred oddajo bova preverili, ali sta [opis projekta](./opis-projekta.md) in [uporabniški scenariji](./uporabniski-scenariji.md) skupaj s Figma mockupi usklajena z [začetnim podatkovnim modelom](./podatkovni-model.md) in [arhitekturo](./arhitektura.md). Vsaka bo svoje dokumente dodala v repozitorij s svojimi commiti.

## 4. Načrt nadaljnjega razvoja

**Po prvem mejniku do 18. 12. 2026:** pripravili bova Supabase bazo in prijavo, osnovno navigacijo ter začeli povezovati zaslone z dejanskimi podatki. Prednost bo imel interaktivni tloris s pregledom napovedane zasedenosti. Postopoma bova dodajali druge dogovorjene funkcionalnosti ter začetne teste in avtomatizirano gradnjo.

**Od 19. 12. 2026 do končne oddaje:** dokončali in preverili bova preostale funkcionalnosti, uredili pravice dostopa in napake, preizkusili aplikacijo na Androidu ter pripravili APK. Dopolnili bova dokumentacijo, navodila za zagon, zaslonske slike in predstavitev.

Nove GitHub Issues za implementacijo bova določali sproti, ko bo jasno, katere manjše naloge je treba opraviti in kako si jih bova razdelili.

## 5. Organizacija dela na GitHubu

- **Issues:** vsaka pomembnejša naloga ima opis, odgovornega člana, prioriteto in pričakovani rezultat.
- **Project tabla:** napredek spremljava v stolpcih *Todo*, *In Progress* in *Done*; status spreminjava glede na dejansko stanje.
- **Razvojne veje:** vsaka pripravlja spremembe na svoji veji oziroma na veji za posamezno nalogo, ne neposredno na `main`.
- **Commits in Pull Requests:** uporabljava ločeni Git identiteti, razumljiva sporočila commitov in Pull Requeste za pregled ter združevanje sprememb v `main`.
- **GitHub Actions:** za zdaj preverja TypeScript in ESLint; pozneje bova dodali avtomatizirane teste in izdelavo APK.

Ob pomembnejših spremembah obsega ali razdelitve dela bova posodobili Issues in po potrebi tudi ta načrt.

## 6. Trenutno stanje

Vzpostavljeni so GitHub repozitorij, začetni Expo projekt, Project tabla in devet začetnih Issues. Osnovni GitHub Actions za preverjanje kode je že uspešno izveden. Dokumentacijo za prvi mejnik še usklajujeva in pripravljava za objavo; preveriti morava tudi, ali so vsi potrebni dostopi urejeni.

Ta dokument je **začetni načrt**. Med razvojem ga bova dopolnjevali glede na dejanski napredek in navodila predmeta.
