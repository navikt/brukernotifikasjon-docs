
Brukeren kan ikke selv klikke bort et `oppgave-event`. Så her må du som produsent sende et [done-event]( https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/done.avsc) på en egen [done-topic]( https://github.com/navikt/brukernotifikasjon-topic-iac/blob/master/dev/aapen-brukernotifikasjon-done-v1.json), og dette done-eventet må ha samme Nokkel som oppgaven den skal markere som done. Altså `done-eventet` må ha samme `event-id` og `systembruker` som `oppgave-eventet` sitt `event-id` og `systembruker`. `Done-eventet` må også ha samme `fødselsnummer` som `oppgave-eventet`. Vi ser for oss at `event-id` kan være en random UUID som unikt kobler beskjed/oppgaven til done-eventet.

Oppgave: Denne brukes når du vil ha utført en konkret oppgave. For eksempel, «vi mangler et vedlegg. Send inn her <...>.»

