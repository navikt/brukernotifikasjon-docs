# Feilsøking

1. Verifiser at alt gikk bra med prosesseringen av eventet:
    1. Sjekk i [Grafana](metrics.md)
    2. Sjekk [loggene](https://logs.adeo.no/goto/1ebde483398205cd39b21e08c882fce1) for dittnav-brukernotifikasjonbestiller, som er appen som leser inn eventene fra Kafka.
2. Konsumer topic-en `aapen-brukernotifikasjon-feilrespons.yaml` (tilgang gis via IAC-repoet som beskrevet under [Komme i gang](./komme_i_gang.md)). Hvis eventet av ulike grunner ble avvist vil årsaken finnes her. Se [Avro-skjema](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/avro/feilrespons.avsc) 
for topic-en. 
