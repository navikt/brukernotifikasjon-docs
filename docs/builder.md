# Builder

Alle produsenter oppfordres sterkt til å bruke `builderene` til å opprette eventer. Grunnen til dette er at 
builderene vil validere alle feltene, før et event opprettes. Dette er de samme valideringsreglene som brukes av 
DittNAV ved innlesing fra kafka, før eventene vises til sluttbruker. Ved å bruke builderene minimeres sjansene for at
eventene blir avvist av DittNAV pga valideringsfeil. 

Hvis det forsøkes å bygge et event med ugyldige feltverdier, så vil builderen kaste en `FieldValidationException` ved kallet 
til `*.build()`. Denne exception-en vil gi informasjon om om hvilket felt som feilet og hva som skjedde.

Se valideringsregler [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/util/ValidationUtil.java)

### Buildere
* [Nokkel](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/NokkelInputBuilder.java)
* [Beskjed](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedInputBuilder.java)
* [Oppgave](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/OppgaveInputBuilder.java)
* [Done](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/DoneInputBuilder.java)
* [Statusoppdatering](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/java/no/nav/brukernotifikasjon/schemas/builders/StatusoppdateringInputBuilder.java)

## Kodeeksempel 
```
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
