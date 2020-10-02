# Kodeeksempel

## Java
```
String topicnavn = "aapen-brukernotifikasjon-nyDone-v1-testing";
Nokkel nokkel = createNokkel();
Done done = createDone();
final ProducerRecord<Nokkel, Done> record = new ProducerRecord<>(topicnavn, nokkel, done);
producer.send(record);
```
Samme prinsipp som `Beskjed` og `Oppgave`. Se et eksempel på `Beskjed` [her](https://github.com/navikt/brukernotifikasjoner-demo-producer/blob/master/src/main/java/no/nav/brukernotifikasjon/BeskjedProducer.java).

## Kotlin
```
val topicnavn : String = "aapen-brukernotifikasjon-nyDone-v1-testing"
val key : Nokkel = createKeyForEvent(systembruker)
val event : Done = createDoneForIdent(innloggetBruker, dto)
val producerRecord = ProducerRecord(topicName, key, event)
kafkaProducer.send(producerRecord)
```
Se et komplett eksempel [her](https://github.com/navikt/dittnav-event-test-producer/blob/master/src/main/kotlin/no/nav/personbruker/dittnav/eventtestproducer/done/DoneProducer.kt).
