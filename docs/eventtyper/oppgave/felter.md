# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)

### Oppgave (Kafka value)
Beskrivelse av feltene til eventet `Oppgave`.

#### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

#### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L46).

#### grupperingsId
Feltet grupperingsId brukes for å kunne samle alle eventer som hører til en sak, søknad eller et dokument. Dette er typisk en saksId, søknadsId eller dokumentId, men dere velger selv hvilken verdi dere putter der. Men det er viktig at det er samme verdi for alle eventer som skal gruppers samme. Typisk bruk for dette feltet vil være oppbygging av tidslinjer. Feltet har en begrensning på 100 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L47).

#### tekst
Dette er teksten som faktisk vises i eventet. Det er ikke noen støtte for å formatere teksten som settes i dette feltet. Feltet har en begrensning på 500 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L48).

#### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll. Feltet har en begrensning på 200 tegn, og kan ikke være null eller inneholde en tom streng. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L49).

#### sikkerhetsnivaa
Angir sikkerhetsnivået for informasjonen som eventet innholder.
DittNAV søtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

#### Schemas
Du finner `Oppgave-schemas` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/oppgave.avsc).
