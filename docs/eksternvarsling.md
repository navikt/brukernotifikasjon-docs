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
[beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_oppgave.txt).
* `epostVarslingstekst` skal overstyre epost-teksten. Hvis dette feltet ikke er satt, skal bruker få en epost med standard tekst:
[beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_oppgave.txt). 
Kun innhold av `<body>`([e-post mal](https://github.com/navikt/dittnav-varselbestiller/blob/6d4790261c4dd8bcde293da3b87b30a2d605f3c5/src/main/resources/texts/epost_mal.txt)) skal overstyres.
* `epostVarslingstittel` skal overstyre epost-tittel. Hvis dette feltet ikke er satt, skal bruker få en epost med standard tittel, "Beskjed fra NAV" for `beskjed` og "Du har fått en oppgave fra NAV" for `oppgave`.

For å ta dette i bruk må alle produsenter ha et forhold til Kafka-topic-en `aapen-dok-notifikasjon-status`. 
Team Dokumentløsninger skriver alle hendelser i forbindelse med en varselbestilling til denne topic-en, og her må produsenten overvåke status til eventet som er sendt. 
Produsenten må selv vurdere om det er behov for å agere på hendelsen. Les mer om mulige statuser [her](https://confluence.adeo.no/display/BOA/For+Konsumenter). 
Tilgang til topic kan fås ved å kontakte Team Dokumentløsninger på #team-dokumentløsninger.

#### Generell informasjon:

* Det kan bestilles eksternt varsel på både SMS og epost. Team Dokumentløsninger henter kontaktinformasjonen til sluttbruker og det er dette som til slutt avgjør hvilken kanal det kan varsles i. 
Les mer om dette [her](https://confluence.adeo.no/display/BOA/For+Konsumenter).
* For oppgave-eventer sender Team Dokumentløsninger kun én re-notifikasjon (SMS/epost)
    - Det er 7 dager mellom notifikasjon og re-notifikasjonen blir sendt.
    - Re-notifikasjon avbestilles hvis vi mottar Done-event for oppgaven.
* Beskjed-event støtter ikke re-notifikasjon.
* Når varselbestillingen oversendes Team Dokumentløsninger opprettes en bestillingsID. Denne ID-en har følgende format: `<eventtype>-<appnavn>-<eventID>`. 
`<eventtype>` er enten B for Beskjed eller O for Oppgave. BestillingsID-en vil bl.a. finnes igjen i eventene som skrives til status-topic-en nevnt tidligere.

![Images](https://github.com/navikt/brukernotifikasjon-docs/blob/master/docs/assets/Eksternvarsling.png?raw=true)
