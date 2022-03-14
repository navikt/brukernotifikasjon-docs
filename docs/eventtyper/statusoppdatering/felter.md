# Feltbeskrivelser

## NokkelInput (Kafka key)
Se [NokkelInput](../fellesinfo.md)

## StatusoppdateringInput (Kafka value)
Beskrivelse av feltene til eventet `Statusoppdatering`.
Husk å validere alle eventene med `builderene` våre. Les mer om dette [her](../../builder.md).

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.
Må være epoch milliseconds, og UTC som tidssone.

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. 
En lenke må være en komplett URL, inkludert `https` protokoll. Feltet har en begrensning på 200 tegn.
Produsenten kan sende inn en tom String. Da vil ikke `link` være synlig for sluttbruker.

### sakstema
Dette er sakstema til søknaden/saken. For eksempel fra kodeverket.
Feltet har en begrensning på 50 tegn og kan ikke være null.

### statusGlobal
Produsenten må velge én av våre fire globale statuser: SENDT, MOTTATT, UNDER_BEHANDLING eller FERDIG.

### sikkerhetsnivaa (valgfri)
Angir sikkerhetsnivået for informasjonen som eventet innholder. Kan inneholde verdien `3` eller `4`, default verdi er `4`.
DittNAV støtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut".
Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet.
For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### statusIntern (valgfri)
StatusIntern kan være mer detaljert, f.eks Venter på dokumentasjon. Produsenten kan selv velge teksten i statusIntern. 
Feltet har en begrensning på 100 tegn.

## Schemas
[Statusoppdatering-schemas](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/statusoppdateringInput.avsc) på Github.
