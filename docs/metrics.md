# Metrics
DittNAV teamet har laget et par granfa-dashbards som kan brukes for å verifisere at alt fungerer som det skal.

## Prosessering
Viser info om den løpende prosesseringen av eventer:

* Prosesseringstid
* Antall eventer motatt.
* Antall felende eventer.

## Topic vs cache
Metrics som oppdateres hvert femte minutt for å verifisere at alt unikt innhold på topic-ene har havnet i DittNAVs-event-cache.

[Dashboardet finnes her.](https://grafana.adeo.no/d/6ore-PuZz/dittnav-kafka?orgId=1&refresh=1m&var-cluster=prod-sbs&var-namespace=All&var-event_type=All&var-producer=All)

### Totaloversikt
Alle eventer sett under ett:

* Info om eventuell diff, mellom hva som finnes av eventer på kafka-topic-ene og hva som finnes i cache-en. 
* Visualisert per eventtype.

[Dashboardet finnes her.](https://grafana.adeo.no/d/ZpeXY3mGz/dittnav-brukernotifikasjoner?orgId=1&refresh=5m)

### Oversikt per team
Alle evneter gruppert per systembruker/produsent:

* Info om eventuell diff, mellom hva som finnes av eventer på kafka-topic-ene og hva som finnes i cache-en. 
* Visualisert per eventtype.

[Dashboardet finnes her.](https://grafana.adeo.no/d/jXntDVWGk/brukernotifikasjoner-per-produsent?orgId=1&refresh=5m&var-env=prod&var-cluster=prod-sbs&var-cluster_fss=prod-fss&var-namespace=default&var-producer=syfo-sykmeldingsvarsel)
