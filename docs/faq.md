# FAQ

## Kan eventer reaktiveres?
Nei, eventer kan ikke reaktiveres. Hvis det først har blitt sendt minst ett done-event for en brukernotifikasjon så vil 
eventet blir satt som inaktivt.

### Hvordan oppnå samme effekt
Send et done-event for eventer man vil dekativere. Send deretter en ny brukernotifikasjon.

## Hva er `grupperingsid`?
Feltet brukes til vise at eventer naturlig hører sammen, for eksempel at de tilhører samme sak, søknad, etc. Hvis flere eventer fra 
samme produsent, tilhørende samme bruker, har samme grupperingsid vil de kunne grupperes sammen.
Dette kan for eksempel visualiseres ved hjelp av en [tidslinje](./tidslinjer.md). 

## Kan vi sende et nytt event for å kvittere ut det opprinnelige eventet?
Nei. Dersom oppgaven eller beskjeden i et event skal markeres som utført, lest,
ikke lenger relevant o.l., skal det sendes et [done-event](./eventtyper/done/beskrivelse.md).

## Hvis vi sender to eventer med samme nøkkel, vil nyeste event overskrive det opprinnelige?
Nei, siden vi allerede har et event med samme nøkkel vil det siste eventet ikke bli skrevet til vår event-cache, og dermed heller ikke vist på Ditt NAV.
Noe av grunnen til det er at vi ønsker å kunne bygge opp tidslinjer basert på alt som har skjedd innenfor den samme grupperingsId-en. 

## Hvordan kan vi se om eventene vi produserer blir mottatt?
Man kan se antall prosesserte eventer pr. produsent i et [Grafana-board](https://grafana.adeo.no/d/jXntDVWGk/brukernotifikasjoner-per-produsent?var-env=prod&var-cluster=prod-sbs&var-cluster_fss=prod-fss&var-namespace=default).
Se ellers flere detaljer under ["Metrics"](./metrics.md)

## Må eventid-en være unik?
Ja. Event-id-en som settes må være unik pr. systembruker og eventtype. Se flere detaljer under [Eventtyper](./eventtyper/fellesinfo.md)

## Kan det sendes varsel på SMS og/eller e-post til bruker?
Det er foreløpig ikke støtte for dette, men funksjonaliteten er på vei. Det vil da bli introdusert et nytt felt, som kan brukes for å bestemme hvorvidt det skal sendes
varsel til bruker. Ta kontakt med #team-personbruker for nærmere informasjon om dette.

## Hvorfor kan vi ikke skrive mer tekst i eventene?
Tanken er at eventene gi bruker beskjed om at noe har skjedd/noe må gjøres, men at handlingen hovedsakelig skal skje i de respektive innsynsløsninger og domener. Visning
av større mengder domenespesifikk tekst i Ditt NAV er ikke hensiktsmessig, og bryter med tanken om at Ditt NAV skal være en felles inngangsport til de ulike tjenestene.

## Hvem eier dataene som ligger lagret i eventene?
Kafka-topicene eies av #team-personbruker, men den enkelte produsent har selv ansvar for innholdet i det enkelte event. 
For å få skrivetilgang må man som produsent bekrefte at man har forstått hva dette ansvaret innebærer. Se med under [Komme i gang](./komme_i_gang.md)

## Kan vi bruke aktørid istedenfor fødselsnummer for å identifisere brukeren?
Nei, vi støtter kun fødselsnummer som identifikator for en bruker.
