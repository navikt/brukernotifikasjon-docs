Det følgende er kun eksempler på hvordan brukernotifikasjoner kan tas i bruk, og verdiene i feltene må tilpasses til hver enkelt applikasjon.


#### Minimal kafka-producer som publiserer brukernotifikasjoner på kafka
[Dette](https://github.com/navikt/brukernotifikasjoner-demo-producer) er et mini-prosjekt som viser hvordan man kan lage en minimal kafka-producer for å publisere brukernotifikasjoner som vil vises på forsiden av DittNAV. I det du produserer et event til en kafka-topic så vil kafka “notere” seg hvilken versjon av skjemaet som den konkrete meldingen ble produsert med.

URL-en til Kafkas schema-register må spesifiseres, dette gjøres i din kafka-producer-config f.eks. slik:

```
put(KafkaAvroDeserializerConfig.SCHEMA_REGISTRY_URL_CONFIG, env.schemaRegistryUrl)
```


riktig [URL finnes her](https://confluence.adeo.no/pages/viewpage.action?pageId=239339073).
Deretter kan eventer sendes ved å f.eks. kalle:
```
producer.send(ProducerRecord(topicNavn, nokkel, oppgaveEvent))
```
, se [her](https://github.com/navikt/brukernotifikasjoner-demo-producer) for mer info. 

#### DittNAV-event-test-producer
[Denne]( https://github.com/navikt/dittnav-event-test-producer) kan også brukes som inspirasjon for å koble seg på kafka. Vi bruker denne appen til å legge test eventer på kafka. For å kjøre vår test-app må du sette opp hele [riggen vår](https://github.com/navikt/dittnav-docker-compose) med docker-compose.
Hvis du ikke er godt kjent med docker-compose anbefaler jeg deg heller å se på [denne appen](https://github.com/navikt/brukernotifikasjoner-demo-producer), men bruk gjerne dittnav-event-test-producer som inspirasjon.  


# Testing lokalt
