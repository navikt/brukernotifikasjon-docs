# FAQ

## Kan varsler reaktiveres?
Nei. Hvis det først har blitt sendt minst ett done-event for varsel er det permanent satt til inaktivert.

### Hvordan oppnå samme effekt
Send et done-event for varselet du vil deaktivere. Send deretter ett nytt varsel.

## Kan vi sende et nytt varsel for å kvittere ut det opprinnelige varselet?
Nei. Dersom oppgaven eller beskjeden i ett varsel skal markeres som utført, lest,
ikke lenger relevant o.l., skal det sendes et [done-event](./eventtyper/done/beskrivelse.md).

## Vi har sendt ett varsel med feil lenke/tekst. Hva gjør vi?
Dere kan selv sende [done-event](./eventtyper/done/beskrivelse.md). Da vil beskjeden/oppgaven bli deaktivert og dere kan sende ett nytt varsel med rett info. Varselet vil være synlig på historikksiden så det kan være lurt å skrive for eksempel "Beklager, det var feil lenke i den forrige beskjeden", så sluttbruker ikke blir forvirret med to like beskjeder/oppgaver på historikksiden.

## Hvis vi sender to varsler med samme nøkkel, vil nyeste varsel overskrive det opprinnelige?
Nei. Siden vi allerede har ett varsel med samme nøkkel vil det siste varselet ikke bli forkastet, og dermed heller ikke vist på min side.

## Hvordan kan vi se om varslene vi produserer blir mottatt?
Man kan se antall prosesserte varsel pr. produsent i et [Grafana-board](https://grafana.nais.io/d/lh20Pgv7z/brukernotifikasjonbestiller-bnb).

## Må eventid-en være unik?
Ja. Event-id-en som settes må være unik pr. systembruker og eventtype. Se flere detaljer under [Eventtyper](./eventtyper/fellesinfo.md)

## Hvorfor kan vi ikke skrive mer tekst i varslene?
Varsler gir bruker beskjed om at noe har skjedd/noe må gjøres, men at handlingen hovedsakelig skal skje i de respektive innsynsløsninger og domener. Visning av større mengder domenespesifikk tekst på min side er ikke hensiktsmessig, og bryter med tanken om at min side skal være en felles inngangsport til de ulike tjenestene.

## Hvem eier dataene som ligger lagret i varslene?
Kafka-topicene eies av #team-personbruker, men den enkelte produsent har selv ansvar for innholdet i det enkelte varslene. 
For å få skrivetilgang må produsent bekrefte at hen har forstått hva dette ansvaret innebærer. 

## Kan vi bruke aktørid istedenfor fødselsnummer for å identifisere brukeren?
Nei, vi støtter kun fødselsnummer som identifikator for en bruker.

## Hva er retention-tiden på brukernotfikasjon-topicene?
Topicene produsentene skriver til har én uke retention, men vi har et eget sett med intern-topics med uendelig retention.

## Kan det sendes varsel på SMS og/eller e-post til bruker samtidig som det opprettes varsel på min side?
Ja. Se mer informasjon om dette under [Ekstern varsling](./eksternvarsling.md)

## Kan vi sette vår egen tekst i varsel på SMS og e-post?
Som standard settes en pre-definert tekst som ikke avslører noen sensitiv informasjon om hva brukerens varsel gjelder. Det er imidlertid mulig å sette sin egen tekst dersom man ønsker det,både for SMS og e-post.

Teksten bør være kort og konsis, med så mye informasjon om området som juridisk mulig. Eksempel-tekst/anbefalt tekst: "Hei! Du har fått <brev, melding> om <område>. Logg inn på nav.no for å lese..."

## Kan vi sende lenker i varsel på SMS og e-post?
Det er ikke anbefalt å sende lenker på SMS og e-post, men det er ingen teknisk begrensning som hindrer det. Det anbefales generelt at man henviser brukeren til "Logg inn på nav.no" fremfor å lenke direkte.

## Kan man sende SMS eller e-post i dev-miljø?
Ja. Se mer informasjon om dette under [Ekstern varsling](./eksternvarsling.md)
