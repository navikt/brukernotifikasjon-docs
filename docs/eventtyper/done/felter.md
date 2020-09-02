## Kafka key
Se [Nokkel](../fellesinfo.md)

## Done
Beskrivelse av feltene til eventet `done`.

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører.

### eventId
`EventId`-en til eventet som nå ikke skal være aktivt lengre. Eventet med den eventId-en vil ikke dukke opp på forsiden av DittNAV lengre, men vil fortsatt være tilgjengelig i historikken over eventer på DittNAV.

### grupperingsId
Dette feltet er med for eventtypen `done` for å sikre at man får med alle eventer knyttet til en `grupperingsId`, og settet av eventer blir ikke komplett uten å ha med `done`-eventene. Dette er bla viktig for å kunne generere tidslinjer ut i fra eventer.
