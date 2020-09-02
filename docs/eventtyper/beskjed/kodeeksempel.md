# Kodeeksempel

## Java
```
String topicnavn = "aapen-brukernotifikasjon-nyBeskjed-v1-testing";
Nokkel nokkel = createNokkel();
Beskjed beskjed = createBeskjed();
final ProducerRecord<Nokkel, Beskjed> record = new ProducerRecord<>(topicnavn, nokkel, beskjed);
producer.send(record);
```
Se et komplett eksempel [her](https://github.com/navikt/brukernotifikasjoner-demo-producer/blob/master/src/main/java/no/nav/brukernotifikasjon/BeskjedProducer.java).

## Kotlin
```
val topicnavn : String = "aapen-brukernotifikasjon-nyBeskjed-v1-testing"
val key : Nokkel = createKeyForEvent(systembruker)
val event : Beskjed = createBeskjedForIdent(innloggetBruker, dto)
val producerRecord = ProducerRecord(topicName, key, event)
kafkaProducer.send(producerRecord)
```
Se et komplett eksempel [her](https://github.com/navikt/dittnav-event-test-producer/blob/master/src/main/kotlin/no/nav/personbruker/dittnav/eventtestproducer/beskjed/BeskjedProducer.kt).
