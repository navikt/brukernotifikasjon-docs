# Kodeeksempel

## Java
```
String topicnavn = "aapen-brukernotifikasjon-nyOppgave-v1-testing";
Nokkel nokkel = createNokkel();
Oppgave oppgave = createOppgave();
final ProducerRecord<Nokkel, Oppgave> record = new ProducerRecord<>(topicnavn, nokkel, oppgave);
producer.send(record);
```
Se et komplett eksempel [her](https://github.com/navikt/brukernotifikasjoner-demo-producer/blob/master/src/main/java/no/nav/brukernotifikasjon/OppgaveProducer.java).

## Kotlin
```
val topicnavn : String = "aapen-brukernotifikasjon-nyOppgave-v1-testing"
val key : Nokkel = createKeyForEvent(systembruker)
val event : Oppgave = createOppgaveForIdent(innloggetBruker, dto)
val producerRecord = ProducerRecord(topicName, key, event)
kafkaProducer.send(producerRecord)
```
Se et komplett eksempel [her](https://github.com/navikt/dittnav-event-test-producer/blob/master/src/main/kotlin/no/nav/personbruker/dittnav/eventtestproducer/oppgave/OppgaveProducer.kt).
