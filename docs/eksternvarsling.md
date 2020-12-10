# Eksternvarsling

#### `NB !! Betaversjon !! Snakk med Team DittNav før du bruker dette feltet.`

DittNAV kan varsle sluttbruker på SMS/epost om en ny melding på forsiden av DittNAV.

Ved å sette `eksternvarsling` til `true` vil beskjeden/oppgaven bli sendt til kafka-topic-en `dok-eksternnotifikasjon`. 
Team Dokumentløsninger eier denne topic-en og det er de som sender SMS/epost. 

For å kunne bruke `eksternvarsling` må alle produsenter ha et forhold til kafka-topic-en `aapen-dok-notifikasjon-status`. 
Team Dokumentløsninger skriver alle hendelser til denne topic-en og her må produsenten overvåke status til eventet som er sendt. 
Produsenten må selv vurdere om det er behov for å agere på hendelsen.
Les mer om statusene til Team Dokumentløsninger [her](https://confluence.adeo.no/display/BOA/For+Konsumenter).

Litt informasjon om eksternvarsling
* Vi varsler på både SMS og epost, men Team Dokumentløsninger henter kontaktinformasjonen til sluttbruker og dette avgjør hvilken kanal vi kan varsle i. Les mer om dette [her]()(?).
* Alle SMS og epost får en standard tekst. Se SMS-tekst her [beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_oppgave.txt) og epost-tekst her [beskjed](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_beskjed.txt) /[oppgave](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_oppgave.txt). 
* For oppgave-eventer sender Team Dokumentløsninger kun én renotifikasjon på nytt (SMS/epost), hvis done-event ikke er mottatt.
    * Det er 7 dager mellom notifikasjon og renotifikasjonen blir sendt. 
* Beskjed-event støtter ikke renotifikasjon.

