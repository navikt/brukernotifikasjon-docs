# Feltbeskrivelser

## NokkelInput (Kafka key)
Se [NokkelInput](../fellesinfo.md)

## OppgaveInput (Kafka value)
Beskrivelse av feltene til eventet `Oppgave`.
Husk å validere alle eventene med `builderene` våre. Les mer om dette [her](../../builder.md).

### tidspunkt - deprecated
Feltet vises ikke til bruker, og feltet vil derfor etter hvert forsvinne. Tidspunktet som vises til bruker er tidspunktet da eventet ble behandlet første gang.

### tekst
Dette er teksten som faktisk vises i eventet. Det er ikke noen støtte for å formatere teksten som settes i dette feltet. 
Feltet har en begrensning på 500 tegn og kan ikke være null.

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll.
Feltet har en begrensning på 200 tegn, og kan ikke være null eller inneholde en tom streng. 

### sikkerhetsnivaa (valgfri)
Angir sikkerhetsnivået for informasjonen som eventet innholder. Kan inneholde verdien `3` eller `4`, default verdi er `4`.
DittNAV støtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". 
Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. 
For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### synligFremTil (valgfri)
Et tidspunkt på når eventet ikke skal være synlig mer, f.eks oppgaven skal kun være synlig 7 dager. Bruk UTC som tidssone.

### eksternVarsling (valgfri)
Default-verdien til dette feltet er `false`, men hvis det blir satt til `true` vil oppgave-eventet bli varslet på SMS eller e-post. 
Les mer om eksternvarsling [her](../../eksternvarsling.md).

### prefererteKanaler (valgfri)
Angir ønskede varslingskanaler for ekstern varsling. 
Gyldige verdier finnes [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/domain/PreferertKanal.java). 
Feltet kan inneholde flere prefererte kanaler, men er valgfritt. Dersom det ikke settes velges EPOST som default preferert kanal. 
Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### smsVarslingstekst (valgfri)
Tekst som skal overstyre SMS [standard tekst](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/sms_oppgave.txt) for ekstern varsling.
Teksten kan ikke være lengre enn 160 tegn. Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### epostVarslingstekst (valgfri)
Tekst som skal overstyre epost ([standard tekst](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/epost_oppgave.txt)) for ekstern varsling. 
Kun innhold av `<body>`([e-post mal](https://github.com/navikt/dittnav-varselbestiller/blob/main/src/main/resources/texts/epost_mal.txt)) skal overstyres. 
Teksten kan innholde HTML tagger som er gyldig i `<body>` tag og den kan ikke være lengre enn 4,000 tegn. 
Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

### epostVarslingsttittel (valgfri)
Tekst som skal overstyre epostens standardtittel ("Du har fått en oppgave fra NAV") for ekstern varsling. Teksten kan ikke være lengre enn 40 tegn. 
Det er ikke tillatt å sette feltet dersom `eksternVarsling` er `false`.

## Schemas
[Oppgave-schemas](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/avro/oppgaveInput.avsc) på Github.
