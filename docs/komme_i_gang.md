# Komme i gang

1. Last ned schemas.
1. Skrive en produsent.
1. Bruke DittNAV-docker-compose-oppsett for å teste lokalt.
1. Bestill tilgang i `dev`, det gjøres [her](https://github.com/navikt/brukernotifikasjon-topic-iac).
1. Publiser et event i `dev` og verifiser at det fungerer:
    1. Verifiser at eventene som produseres dukker opp i [grafanaboardet 'Brukernotifikasjoner per produsent'](https://grafana.adeo.no/d/jXntDVWGk/brukernotifikasjoner-per-produsent?orgId=1&refresh=5m&var-env=dev&var-cluster=dev-sbs&var-cluster_fss=dev-fss&var-namespace=q1), og velg `<appens systembruker i FSS>` i nedtrekkslisten for `producer`.
        1. For at dette skal fungere så må man bruke `<appens systembruker i FSS>` i feltet `systembruker` i kafka-key-en `Nokkel`. 
            1. Hvis dette ikke fungerer kontakt [Team Personbruker på Slack](https://nav-it.slack.com/archives/C9CJ794PP).
    1. Logg inn på [DittNAV i `dev`](https://www.dev.nav.no/person/dittnav) og verifiser at eventet dukker opp på forsiden.          

 
[Schema registry url](https://confluence.adeo.no/pages/viewpage.action?pageId=239339073)
