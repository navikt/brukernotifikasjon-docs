# Feltbeskrivelser

## NokkelInput (Kafka key)
Se [NokkelInput](../fellesinfo.md)

## DoneInput (Kafka value)
Beskrivelse av feltene til eventet `done`.
Husk å validere alle eventene med `builderene` våre. Les mer om dette [her](../../builder.md).

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig. Bruk UTC som tidssone.

## Schemas
[DoneInput-schemas](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/doneInput.avsc) på Github.
