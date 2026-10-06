# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G104 – G104-stene |
| **Product brief** | `Project brief` (commit `affa0e7`). `Project brief.pdf` (commit `9117a3e`) har samme innhold. |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

**Det som er bra:**

1. Briefen følger malens struktur, og kjerneflyten «Upload > Generate > Study» er enkel og tydelig. Den er et godt utgangspunkt for stories.
2. Det er bra at dere vil vise referanser til sider eller avsnitt i kildematerialet. Det gjør det mulig for studenten å sjekke om KI-ens sammendrag og quizsvar stemmer, og det løser et reelt problem med generelle KI-verktøy.

**De viktigste endringene:**

1. Suksesskriteriene kan ikke testes i emnet. «70 %+ av brukerne», «60 %+ bruker flashcards» og «70 %+ rapporterer» krever mange ekte brukere over tid. Legg til funksjonelle kriterier, for eksempel «en student kan laste opp en PDF på 10 sider og få et sammendrag med sidehenvisninger» og «en quiz på 10 spørsmål kan besvares i appen, og studenten ser riktig svar etterpå».
2. Gjør briefen til deres egen. Den ligger svært nær forslag 1 på forslagslista. Beskriv én konkret primærbruker i stedet for «students of all kinds», for eksempel en logistikkstudent som skal repetere forelesningsnotater før eksamen, og hva som er deres valg og vri på ideen.
3. Planlegg språkmodell og kjørbarhet. Appen er helt avhengig av et KI-API. Beskriv hvilken modell dere vil bruke, hva det koster, og hvordan sensor kan kjøre appen uten deres nøkkel, for eksempel med en mock-modus og et ferdig eksempeldokument.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Enkel**

**Sammenlignbart med:** 1) AI Study Buddy (enkel). Briefen beskriver i praksis dette forslaget.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Lav | Få regler utover valg av språk og detaljnivå. |
| Datamodell – antall entiteter og relasjoner mellom dem | Lav | Dokument, sammendrag, flashcards, quizspørsmål og nøkkelbegreper. Mer hvis materiale skal lagres per bruker og emne. |
| Brukere, roller og innlogging | Lav | Ikke beskrevet. Avklar om materialet skal lagres, i så fall trengs enkel innlogging. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Middels | Fire typer KI-generert innhold fra samme kilde, med sidehenvisninger. Krever gode prompts, strukturert output og håndtering av feil. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | Språkmodell-API, som ikke er valgt ennå. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Lav | Ikke relevant. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Middels | PDF-lesing med sidehenvisninger er krevende å gjøre pålitelig, særlig for lysbilder. |
| Sikkerhet og personvern | Lav | Studentenes eget materiale. Avklar om det lagres, og om det sendes til en ekstern KI-tjeneste. |

**Hva vanskelighetsgraden betyr for dere:**

- _Enkel:_ Et enkelt prosjekt gir stor sjanse for å bli ferdig. Vanskelighetsgraden inngår likevel i vurderingen, så for å nå helt opp må dere vise mer i gjennomføringen. Det betyr særlig et gjennomarbeidet design, grundig testing, en tydelig dokumentert prosess og en README som virker.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | OK | Én kjerneflyt med fire innholdstyper er overkommelig for én person. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Det er uklart om materiale og resultater lagres, om studenten kan ta quizen i appen, og hvordan flashcards brukes. Dette må avklares for at PRD-en ikke skal få hull. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En enkel webapp med PDF-lesing og et KI-API er godt egnet for Claude Code. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | Risiko | Dere kan selv vurdere om et sammendrag er rimelig, men det er vanskelig å sjekke at quizsvar og sidehenvisninger alltid stemmer. Bruk et eget, kort testdokument der dere kjenner innholdet. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | Opplasting, validering, antall spørsmål og visning er testbart. Kvaliteten på KI-innholdet krever manuelle testplaner og et fast testdokument. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Uten KI-nøkkel virker ingenting i dag. Planlegg mock-modus med forhåndsgenerert innhold for et eksempeldokument. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Ikke omtalt. Velg en modell med gratisnivå eller lav kostnad, og begrens dokumentstørrelsen. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart som beskrevet.**

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Legg til én utvidelse som gir mer å vise, for eksempel en interaktiv quizmodus der studenten svarer og får poeng, eller lagring av materiale per emne slik at studenten kan komme tilbake.
2. Start med tekst og enkle PDF-er, og la lysbilder med mye grafikk ligge utenfor v1. Det gjør sidehenvisningene mer pålitelige.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Klart hva AI Study Buddy gjør. Briefen er på engelsk, noe som er greit. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | Juster | Problemet er generelt. Siste setning sier at studentene bruker mindre tid på å jobbe med materialet, som er det motsatte av poenget. Rett den, og gi et konkret eksempel. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | Juster | Flyten er tydelig, men beskriv hva studenten gjør med resultatet: blar i flashcards, tar quizen i appen, eller laster ned? |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig om at fordelen er enkelhet og utførelse. Sidehenvisninger er en god differensiator. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Endre | «Students of all kinds» er ingen tydelig målgruppe. Velg én primærbruker og beskriv situasjonen hennes. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Bruksandeler kan ikke måles i emnet. Legg til funksjonelle kriterier som kan bli testtilfeller. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Juster | God inn/ut-liste, men lagring, innlogging og om quizen kan tas i appen er verken inne eller ute. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Kort og nøktern. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Briefen ligger både som tekstfil uten filendelse og som PDF. Gjør den til én markdown-fil (for eksempel `docs/product-brief.md`), slik at endringer kan følges i historikken. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Juster | Realistisk, men enkelt. Én utvidelse gir mer å vise. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Ingen testbare kriterier ennå. Lag funksjonelle kriterier og et fast testdokument. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | Juster | Uten tydelig bruker blir designet generelt. Skisser opplasting, resultatvisning og flashcard-/quizvisning. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Ingen teknologi er nevnt, noe som er greit i en brief, men velg en enkel stakk i arkitekturen. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg mock-modus og eksempeldokument, slik at sensor kan kjøre appen uten nøkkel. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Flytt briefen til en dokumentasjonsmappe, fjern duplikatet, og planlegg `.env.example` og en mappe for testdokumenter. |

## 3. Neste steg for gruppen

1. Skriv om suksesskriteriene til funksjonelle, testbare kriterier, og beskriv én konkret primærbruker.
2. Avklar lagring, innlogging og hvordan quiz og flashcards brukes i appen, og velg språkmodell med en plan for mock-modus.
3. Samle briefen i én markdown-fil i en dokumentasjonsmappe, og gå videre til PRD med BMAD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
