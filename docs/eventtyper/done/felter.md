# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)

## Done (Kafka value)
Beskrivelse av feltene til eventet `done`.

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/done/Done.kt#L18).

### eventId
`EventId`-en til eventet som nå ikke skal være aktivt lengre. Eventet med den eventId-en vil ikke dukke opp på forsiden av DittNAV lengre, men vil fortsatt være tilgjengelig i historikken over eventer på DittNAV. Feltet har en begrensning på 50 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/done/Done.kt#L17).

### grupperingsId
Dette feltet er med for eventtypen `done` for å sikre at man får med alle eventer knyttet til en `grupperingsId`, og settet av eventer blir ikke komplett uten å ha med `done`-eventene. Dette er bla viktig for å kunne generere tidslinjer ut i fra eventer. Feltet har en begrensning på 100 tegn og kan ikke være null.
