# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)


## Beskjed (Kafka value)
Beskrivelse av feltene til eventet `Beskjed`.

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/beskjed/Beskjed.kt#L51).

### grupperingsId
Feltet grupperingsId brukes for å kunne samle alle eventer som hører til en sak, søknad eller et dokument. Dette er typisk en saksId, søknadsId eller dokumentId, men dere velger selv hvilken verdi dere putter der. Men det er viktig at det er samme verdi for alle eventer som skal grupperes sammen. Typisk bruk for dette feltet vil være oppbygging av tidslinjer. Feltet har en begrensning på 100 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/beskjed/Beskjed.kt#L52).

### tekst
Dette er teksten som faktisk vises i eventet. Det er ikke noen støtte for å formatere teksten som settes i dette feltet. Feltet har en begrensning på 300 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/beskjed/Beskjed.kt#L53).

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll. Feltet har en begrensning på 200 tegn. Produsenten kan sende inn en tom String. Da vil ikke `link` være synlig for sluttbruker. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/beskjed/Beskjed.kt#L54).

### sikkerhetsnivaa
Angir sikkerhetsnivået for informasjonen som eventet innholder.
DittNAV støtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### synligFremTil
Et tidspunkt på når eventet ikke skal være synlig mer, f.eks beskjeden skal kun være synlig 7 dager. SynligFramTil = null -> synlig for alltid, med mindre brukeren selv krysser den ut fra forsiden av DittNAV.

#### Schemas
Du finner `Beskjed-schemas` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/beskjed.avsc).