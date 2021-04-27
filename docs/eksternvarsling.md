# Ekstern varsling

Det er mulig å sende ekstern varsling på e-post og/eller SMS til sluttbruker om ny beskjed eller oppgave på forsiden av Ditt NAV.

Skjemaene for Beskjed og Oppgave inneholder et felt som brukes for å indikere dette, `eksternVarsling`. Feltet er ikke påkrevet, og har default-verdien `false`. Settes dette til `true` vil det bestilles varsling.
Rent praktisk foregår dette ved at DittNAV da oppretter et Kafka-event på en topic tilhørende Team Dokumentløsninger. Det er Team Dokument som står for selve varselutsendingen, gjennom tjenesten doknotifikasjon.

For å ta dette i bruk må alle produsenter ha et forhold til Kafka-topic-en `aapen-dok-notifikasjon-status`. Team Dokumentløsninger skriver alle hendelser i forbindelse med en varselbestilling til denne topic-en, og her må produsenten overvåke status til eventet som er sendt. 
Produsenten må selv vurdere om det er behov for å agere på hendelsen. Les mer om mulige statuser [her](https://confluence.adeo.no/display/BOA/For+Konsumenter). Tilgang til topic kan fås ved å kontakte Team Dokumentløsninger på #team-dokumentløsninger.

Generell informasjon:

* Det bestilles varsel til både SMS og epost. Team Dokumentløsninger henter kontaktinformasjonen til sluttbruker og det er dette som til slutt avgjør hvilken kanal det kan varsles i. Les mer om dette [her](https://confluence.adeo.no/display/BOA/For+Konsumenter).
* All SMS og e-post får en standard tekst. Se SMS-tekst her [beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_oppgave.txt) og epost-tekst her [beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_oppgave.txt). 
* For oppgave-eventer sender Team Dokumentløsninger kun én re-notifikasjon på nytt (SMS/epost)
    - Det er 7 dager mellom notifikasjon og re-notifikasjonen blir sendt.
    - Re-notifikasjon avbestilles hvis vi mottar Done-event for oppgaven.
* Beskjed-event støtter ikke re-notifikasjon.
