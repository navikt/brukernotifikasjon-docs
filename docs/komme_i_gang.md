# Komme i gang

1. Velg rett eventtype. Les gjennom eventtypene [her](./eventtyper/fellesinfo.md).
2. Se på [dette](./eksempler.md) eksemplet. [Her](https://github.com/navikt/brukernotifikasjon-schemas/tree/master/src/main/avro) finner du våre schemas. Biblioteket finner du [her](https://jitpack.io/#navikt/brukernotifikasjon-schemas).
3. Se også på kodeeksemplet til valgt event-type. For eksempel [Beskjed](./eventtyper/beskjed/kodeeksempel.md).
4. Bestill tilgang til `dev-topic` [her](https://github.com/navikt/brukernotifikasjon-topic-iac).
5. Publiser et event i `dev` og verifiser at det fungerer:
    - Verifiser at eventene som produseres dukker opp i [grafanaboardet 'Brukernotifikasjoner per produsent'](https://grafana.adeo.no/d/jXntDVWGk/brukernotifikasjoner-per-produsent?orgId=1&refresh=5m&var-env=dev&var-cluster=dev-sbs&var-cluster_fss=dev-fss&var-namespace=q1). 
    Velg din `systembruker`-mapping i nedtrekkslisten `producer`. 
    Se mapping av systembruker [her](https://github.com/navikt/brukernotifikasjon-topic-iac/blob/master/dev/systembrukermapping-dev.sql). Feilsøking se [her](./feilsoking.md).
    - Logg inn på [DittNAV i `dev`](https://www.dev.nav.no/person/dittnav) og verifiser at eventet dukker opp på forsiden.          
6. Produser noen eventer og verifiser at det fungerer som det skal i dev.
7. Kontakt Team Personbruker på Slack #brukernotifikasjoner så vi kan gå gjennom feltverdiene, slik at vi er sikre på at vi bruker de på samme måte.
8. Bestill tilgang til `prod-topic-en` [her](https://github.com/navikt/brukernotifikasjon-topic-iac). 