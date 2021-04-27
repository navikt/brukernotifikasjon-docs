# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)

## Statusoppdatering (Kafka value)
Beskrivelse av feltene til eventet `Statusoppdatering`.
Husk å validere alle eventene med `builderene` våre. Les mer om dette [her](../../builder.md).

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig. Bruk UTC som tidssone.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L51).

### grupperingsId
Feltet grupperingsId brukes for å kunne samle alle eventer som hører til en sak, søknad eller et dokument. Dette er typisk en saksId, søknadsId eller dokumentId, men dere velger selv hvilken verdi dere putter der. Men det er viktig at det er samme verdi for alle eventer som skal grupperes sammen. Typisk bruk for dette feltet vil være oppbygging av tidslinjer. Feltet har en begrensning på 100 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L52).

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll. Feltet har en begrensning på 200 tegn. Produsenten kan sende inn en tom String. Da vil ikke `link` være synlig for sluttbruker. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L53).

### sikkerhetsnivaa
Angir sikkerhetsnivået for informasjonen som eventet innholder.
DittNAV støtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### statusGlobal
Produsenten må velge én av våre fire globale statuser: SENDT, MOTTATT, UNDER_BEHANDLING eller FERDIG. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L55).

### statusIntern
StatusIntern kan være mer detaljert, f.eks Venter på dokumentasjon. Produsenten kan selv velge teksten i statusIntern. Feltet har en begrensning på 100 tegn. Dette feltet er ikke obligatorisk og kan være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L56).

### sakstema
Dette er sakstema til søknaden/saken. For eksempel fra kodeverket. Feltet har en begrensning på 50 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/statusoppdatering/Statusoppdatering.kt#L57).

#### Schemas
Du finner `Statusoppdatering-schemas` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/statusoppdatering.avsc).