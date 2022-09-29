# Kafka topics

| Miljø  | Topic-navn  |
|---|---|
| dev | [aapen-brukernotifikasjon-done-v1](https://github.com/navikt/brukernotifikasjon-public-topic-iac/blob/main/dev-gcp/aapen-brukernotifikasjon-done.yaml) |
| prod | [aapen-brukernotifikasjon-done-v1](https://github.com/navikt/brukernotifikasjon-public-topic-iac/blob/main/prod-gcp/aapen-brukernotifikasjon-done.yaml) |

Når en skal spesifisere topic-navn i sin app må man også ha med navn på namespace foran topic.
For de ovennevnte topicsene gjelder "min-side". Eksempel:
```
min-side.aapen-brukernotifikasjon-done-v1
```

## Tilgang
Tilgang til topic-ene kan bestilles ved å opprette en pull-request mot [dette repo-et](https://github.com/navikt/brukernotifikasjon-public-topic-iac).
