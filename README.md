# brukernotifikasjon-docs
Teknisk dokumentasjon av Team personbruker sin løsning for brukernotifikasjoner

### For å kjøre lokalt:
```
$ pip install mkdocs-material
$ mkdocs serve
```
Siden skal nå vises her: http://127.0.0.1:8000

### Automatisk deploy
Dette repoet skal deploy-e automatisk til [denne](https://navikt.github.io/brukernotifikasjon-docs/) siden ved push til main.

### Manuell deploy
For å deploy-e manuelt:
```
$ mkdocs build
$ mkdocs gh-deploy
```

