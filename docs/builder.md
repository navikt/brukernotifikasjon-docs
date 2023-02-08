# Builder

Builderene validerer alle felteer, før et event opprettes og bruker samme valideringsregler som brukes av 
min side ved innlesing fra kafka, før varslet vises til sluttbruker. Ved å bruke builderene minimeres sjansene for at
eventene blir avvist av min side pga valideringsfeil. 

Se valideringsregler [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/util/ValidationUtil.java)

### Buildere
* [Nokkel](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/NokkelInputBuilder.java)
* [Beskjed](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedInputBuilder.java)
* [Oppgave](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/OppgaveInputBuilder.java)
* [Done](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/DoneInputBuilder.java)

## Kodeeksempel 
```java
BeskjedInputBuilder builder = getBuilderWithValues();
Beskjed beskjed = builder.build(); // Alle felter valideres, før eventet eventuelt blir opprettet

private BeskjedInputBuilder getBuilderWithValues() {
    return new BeskjedInputBuilder()
            .withSikkerhetsnivaa(sikkerhetsnivaa)
            .withLink(link)
            .withTekst(tekst)
            .withTidspunkt(tidspunkt)
            .withSynligFremTil(synligFremTil)
            .withEksternVarsling(eksternVarsling)
            .withPrefererteKanaler(prefererteKanaler);
}
```
