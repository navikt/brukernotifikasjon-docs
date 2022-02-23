# Feltbeskrivelser

## Nokkel (Kafka key)
Se [Nokkel](../fellesinfo.md)

## Oppgave (Kafka value)
Beskrivelse av feltene til eventet `Oppgave`.
Husk å validere alle eventene med `builderene` våre. Les mer om dette [her](../../builder.md).

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig. Bruk UTC som tidssone.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L46).

### grupperingsId
Feltet grupperingsId brukes for å kunne samle alle eventer som hører til en sak, søknad eller et dokument. Dette er typisk en saksId, søknadsId eller dokumentId, men dere velger selv hvilken verdi dere putter der. Men det er viktig at det er samme verdi for alle eventer som skal gruppers samme. Typisk bruk for dette feltet vil være oppbygging av tidslinjer. Feltet har en begrensning på 100 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L47).

### tekst
Dette er teksten som faktisk vises i eventet. Det er ikke noen støtte for å formatere teksten som settes i dette feltet. Feltet har en begrensning på 500 tegn og kan ikke være null. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L48).

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll. Feltet har en begrensning på 200 tegn, og kan ikke være null eller inneholde en tom streng. Validering skjer [her](https://github.com/navikt/dittnav-event-aggregator/blob/ee610abdf1040199ba65ede76eda1c33b42acffa/src/main/kotlin/no/nav/personbruker/dittnav/eventaggregator/oppgave/Oppgave.kt#L49).

### sikkerhetsnivaa
Angir sikkerhetsnivået for informasjonen som eventet innholder.
DittNAV søtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### synligFremTil
Et tidspunkt på når eventet ikke skal være synlig mer, f.eks oppgaven skal kun være synlig 7 dager. Bruk UTC som tidssone.

### eksternVarsling 
Default-verdien til dette feltet er `false`, men hvis det blir satt til `true` vil oppgave-eventet bli varslet på SMS eller e-post. Les mer om eksternvarsling [her](../../eksternvarsling.md).

### prefererteKanaler
Angir ønskede varslingskanaler for ekstern varsling. Gyldige verdier finnes [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/domain/PreferertKanal.java). Feltet kan inneholde flere prefererte kanaler, men er valgfritt.
Dersom det ikke settes velges EPOST som default preferert kanal. Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### smsVarslingstekst
Tekst som skal overstyre SMS [standard tekst](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/sms_oppgave.txt) for ekstern varsling. Teksten kan ikke være lengre enn 160 tegn. Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### epostVarslingstekst
Tekst som skal overstyre epost [standard tekst](https://github.com/navikt/dittnav-varselbestiller/blob/master/src/main/resources/texts/epost_oppgave.txt) for ekstern varsling. Kun innhold av `<body>`([e-post mal](https://github.com/navikt/dittnav-varselbestiller/blob/6d4790261c4dd8bcde293da3b87b30a2d605f3c5/src/main/resources/texts/epost_mal.txt)) skal overstyres. Tekst kan innholde HTML tagger som er gyldig i `<body>` tag og den kan ikke være lengre enn 4,000 tegn. Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### epostVarslingsttittel
Tekst som skal overstyre epost standard tittel ("Du har fått en oppgave fra NAV") for ekstern varsling. Tekst kan ikke være lengre enn 40 tegn. Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

## Schemas
[Oppgave-schemas](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/legacy/oppgaveLegacy.avsc) på Github.
