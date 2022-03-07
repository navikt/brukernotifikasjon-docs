# Beskrivelse

`Done-event` sendes når brukernotifikasjonen skal fjernes fra brukernotifikasjonslisten på DittNAV,
for eksempel når oppgaven er utført, eller beskjeden er lest.

`Done-event` må ha samme eventId og fødselsnummer som Oppgaven/Beskjeden den skal deaktivere. 

Hvis brukeren trykker på arkivér-knappen på en beskjed vil DittNAV selv sende et `done-event` for beskjeden.
Hvis synligFremTil-tidspunktet har passert vil det også automatisk sendes et `done-event`.

Deaktiverte eventer vil fortsatt være tilgjengelig fra historikk-visningen på DittNAV.

![Images](https://github.com/navikt/brukernotifikasjon-docs/blob/master/docs/assets/Historikk_dittnav.png?raw=true)
