# Brukernotifikasjoner

## Hva er DittNAV sitt nye konsept?

Nå kan alle i NAV sende meldinger på brukernotifikasjons-topic-en vår. Vi leser fra kafka topic-en og viser meldingen (brukernotifikasjonen) på forsiden av DittNAV.

Vi har tre typer brukernotifikasjoner:

* Beskjed: Dette er en typisk melding til sluttbrukeren. For eksempel, «vi har mottatt søknaden din».
* Oppgave: Denne brukes når du vil ha utført en konkret oppgave. For eksempel, «vi mangler et vedlegg. Send inn her <...>.»
* Done: Dette sendes når oppgaven er utført. Hvis vi bruker samme eksempel som over ville du sendt et done-event når sluttbrukeren har lastet opp vedlegget.

Du kan se en oversikt over konseptet [her](https://navikt.github.io/dittnav-brukernotifikasjoner-intro/).
