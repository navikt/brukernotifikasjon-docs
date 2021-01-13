# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)

## Done (Kafka value)
Beskrivelse av feltene til eventet `done`.
Husk å valider alle event med `builder-n` vår. Les mer om dette [her](../builder.md).

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/done/Done.kt#L18).

### grupperingsId
Dette feltet er med for eventtypen `done` for å sikre at man får med alle eventer knyttet til en `grupperingsId`, og settet av eventer blir ikke komplett uten å ha med `done`-eventene. Dette er bla viktig for å kunne generere tidslinjer ut i fra eventer. Feltet har en begrensning på 100 tegn og kan ikke være null.

#### Schemas
Du finner `Done-schemas` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/done.avsc).