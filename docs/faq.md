# FAQ

## Kan eventer reaktiveres?
Nei, eventer kan ikke reaktiveres. Hvis det først har blitt sendt minst ett done-event for en brukernotifikasjon så vil 
eventet bli satt inaktivt.

### Hvordan oppnå samme effekt
Send et done-event for eventer man vil deaktivere. Send deretter en ny brukernotifikasjon.

## Hva er `grupperingsid`?
Feltet brukes til å vise at eventer naturlig hører sammen, for eksempel at de tilhører samme sak, søknad, etc. Hvis flere eventer fra 
samme produsent, tilhørende samme bruker, har samme grupperingsid vil de kunne grupperes sammen.

## Kan vi sende et nytt event for å kvittere ut det opprinnelige eventet?
Nei. Dersom oppgaven eller beskjeden i et event skal markeres som utført, lest,
ikke lenger relevant o.l., skal det sendes et [done-event](./eventtyper/done/beskrivelse.md).

##Vi har sendt event med feil lenke/tekst. Hva gjør vi?
Dere kan selv sende [done-event](./eventtyper/done/beskrivelse.md). Da vil beskjeden/oppgaven bli deaktivert og dere kan sende ett nytt event med rett info. 
Eventet vil være synlig på historikksiden så det kan være lurt å skrive for eksempel "Beklager, det var feil lenke i den forrige beskjeden", så sluttbruker ikke blir forvirret med to like beskjeder/oppgaver på historikksiden.

## Hvis vi sender to eventer med samme nøkkel, vil nyeste event overskrive det opprinnelige?
Nei, siden vi allerede har et event med samme nøkkel vil det siste eventet ikke bli skrevet til vår event-cache, og dermed heller ikke vist på Ditt NAV.

## Hvordan kan vi se om eventene vi produserer blir mottatt?
Man kan se antall prosesserte eventer pr. produsent i et [Grafana-board](https://grafana.nais.io/d/lh20Pgv7z/brukernotifikasjonbestiller-bnb).
Se ellers flere detaljer under ["Metrics"](./metrics.md)

## Må eventid-en være unik?
Ja. Event-id-en som settes må være unik pr. systembruker og eventtype. Se flere detaljer under [Eventtyper](./eventtyper/fellesinfo.md)

## Hvorfor kan vi ikke skrive mer tekst i eventene?
Tanken er at eventene gir bruker beskjed om at noe har skjedd/noe må gjøres, men at handlingen hovedsakelig skal skje i de respektive innsynsløsninger og domener. Visning
av større mengder domenespesifikk tekst i Ditt NAV er ikke hensiktsmessig, og bryter med tanken om at Ditt NAV skal være en felles inngangsport til de ulike tjenestene.

## Hvem eier dataene som ligger lagret i eventene?
Kafka-topicene eies av #team-personbruker, men den enkelte produsent har selv ansvar for innholdet i det enkelte event. 
For å få skrivetilgang må man som produsent bekrefte at man har forstått hva dette ansvaret innebærer. Se mer under [Komme i gang](./komme_i_gang.md)

## Kan vi bruke aktørid istedenfor fødselsnummer for å identifisere brukeren?
Nei, vi støtter kun fødselsnummer som identifikator for en bruker.

## Hva er retention-tiden på brukernotfikasjon-topicene?
Topicene produsentene skriver til har én uke retention, men vi har et eget sett med intern-topics med uendelig retention.

## Kan det sendes varsel på SMS og/eller e-post til bruker samtidig som det opprettes Brukernotifikasjon på Ditt NAV?
Ja. Se mer informasjon om dette under [Ekstern varsling](./eksternvarsling.md)

## Kan vi sette vår egen tekst i varsel på SMS og e-post?
Som standard settes en pre-definert tekst, som ikke avslører noen sensitiv informasjon om hva brukerens varsel gjelder. Det er imidlertid mulig å sette sin egen tekst dersom man ønsker det,
både for SMS og e-post for beskjeder og oppgaver. Se mer informasjon under feltbeskrivelsene for den enkelte eventtypen.

Teksten bør være kort og konsis, med så mye informasjon om området som juridisk mulig. Eksempel-tekst/anbefalt tekst: "Hei! Du har fått <brev, melding> om <område>. Logg inn på nav.no for å lese..."

## Kan vi sende lenker i varsel på SMS og e-post?
Det er ikke anbefalt å sende lenker på SMS og e-post, men det er ingen teknisk begrensning som hindrer det. Det anbefales generelt at man henviser brukeren til "Logg inn på nav.no" fremfor å lenke direkte.

## Kan man sende SMS eller e-post i dev-miljø?
Ja. Se mer informasjon om dette under [Ekstern varsling](./eksternvarsling.md)
