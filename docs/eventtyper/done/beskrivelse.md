# Beskrivelse

`Done` sendes når oppgaven er utført. Hvis vi bruker samme eksempel som over ville du sendt et `done-event` når sluttbrukeren har lastet opp vedlegget.

`Done-event` må ha samme Nokkel, fødselsnummer og grupperingsid som Oppgaven/Beskjeden den skal deaktivere. 

DittNAV sender `done-event` på `beskjed-event`, siden brukeren selv kan klikke bort disse eventene når beskjeden er mottatt.

Deaktiverte eventer vil fortsatt være tilgjengelig fra historikk-visningen på DittNAV.

![Images](https://github.com/navikt/brukernotifikasjon-docs/blob/master/docs/assets/Historikk_dittnav.png?raw=true)
