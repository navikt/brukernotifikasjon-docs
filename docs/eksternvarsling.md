# Ekstern varsling

Det er mulig å sende ekstern varsling på enten epost eller SMS, eller begge deler, til sluttbruker om ny beskjed eller oppgave på forsiden av Ditt NAV.

Skjemaene for Beskjed og Oppgave inneholder et felt som brukes for å indikere dette, `eksternVarsling`. 
Feltet er ikke påkrevet, og har default-verdien `false`. Settes dette til `true` vil det bestilles varsling.
Rent praktisk foregår dette ved at DittNAV da oppretter et Kafka-event på en topic tilhørende Team Dokumentløsninger. 
Det er dette teamet som står for selve varselutsendingen, gjennom tjenesten doknotifikasjon.

Beskjed og Oppgave inneholder i tillegg feltet `prefererteKanaler`. I dette feltet kan det settes hvilke kanaler som er prefererte varslingskanaler til brukeren. 
Feltet er ikke påkrevet. Hvis det ikke settes vil epost være preferert varslingskanal.

All SMS og e-post får en standard tekst. Dette er mulig å overstyre for både SMS og e-post, dette gjøres gjennom disse to feltene, disse feltene er ikke påkrevet:

* `smsVarslingstekst` skal overstyre SMS-teksten. Hvis dette feltet ikke er satt, skal bruker få en SMS med standard tekst:
[beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/sms_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/sms_oppgave.txt).
* `epostVarslingstekst` skal overstyre epost-teksten. Hvis dette feltet ikke er satt, skal bruker få en epost med standard tekst:
[beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/epost_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/epost_oppgave.txt). 
Kun innhold av `<body>`([e-post mal](https://github.com/navikt/dittnav-varselbestiller/blob/6d4790261c4dd8bcde293da3b87b30a2d605f3c5/src/main/resources/texts/epost_mal.txt)) skal overstyres.
* `epostVarslingstittel` skal overstyre epost-tittel. Hvis dette feltet ikke er satt, skal bruker få en epost med standard tittel, "Beskjed fra NAV" for `beskjed` og "Du har fått en oppgave fra NAV" for `oppgave`.

For å ta dette i bruk må alle produsenter ha et forhold til Kafka-topic-en `aapen-dok-notifikasjon-status`. 
Team Dokumentløsninger skriver alle hendelser i forbindelse med en varselbestilling til denne topic-en, og her må produsenten overvåke status til eventet som er sendt. 
Produsenten må selv vurdere om det er behov for å agere på hendelsen. Les mer om mulige statuser [her](https://confluence.adeo.no/display/BOA/For+Konsumenter). 
Tilgang til topic kan fås ved å kontakte Team Dokumentløsninger på #team-dokumentløsninger.

#### Generell informasjon

* Det kan bestilles eksternt varsel på både SMS og epost. Team Dokumentløsninger henter kontaktinformasjonen til sluttbruker og det er dette som til slutt avgjør hvilken kanal det kan varsles i. 
Les mer om dette [her](https://confluence.adeo.no/display/BOA/For+Konsumenter).
* For oppgave-eventer sender Team Dokumentløsninger kun én re-notifikasjon (SMS/epost)
    - Det er 7 dager mellom notifikasjon og re-notifikasjonen blir sendt.
    - Re-notifikasjon avbestilles hvis vi mottar Done-event for oppgaven.
* Beskjed-event støtter ikke re-notifikasjon.
* Når varselbestillingen oversendes Team Dokumentløsninger vil den originale brukernotifikasjonens eventID brukes som bestillingsID. 
* BestillingsID-en kan brukes til å finne igjen tilhørende oppdateringer når en lytter på `aapen-dok-notifikasjon-status`.

![Images](https://github.com/navikt/brukernotifikasjon-docs/blob/main/docs/assets/Eksternvarsling.png?raw=true)

#### Ekstern varsling i dev-miljø

Funksjonaliteten for faktisk å sende epost og/eller SMS fra dev-miljø er som standard inaktiv. Det er imidlertidig mulig å aktivere denne muligheten, men det krever noen forberedelser. Sending av eksternt varsel
gjøres via Altinn, og man må derfor benytte en testbruker som også eksisterer i Altinns testmiljø. Det er noen få slike testbrukere listet opp i [dokumentasjonen](https://confluence.adeo.no/display/BOA/QDIST011+-+DistribuerForsendelseTilDPI-2.+Testing) til Team Dokumentløsninger.
Før man sender bør man sjekke hvilken kontaktinformasjon som er registrert på testbrukeren i Dolly, og om nødvendig endre dette til en adresse/nummer man selv har kontroll på. 
I tillegg må man gi beskjed til Team Dokumentløsninger, f.eks. i #team_dokumentløsninger på Slack, om at man ønsker midlertidig å aktivere integrasjonen mot Altinn. 
