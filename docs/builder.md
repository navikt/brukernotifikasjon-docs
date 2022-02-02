# Builder

Alle produsenter oppfordres sterkt til å bruke `builderene` til å opprette eventer. Grunnen til dette er at 
builderene vil validere alle feltene, før et event opprettes. Dette er de samme valideringsreglene som brukes av 
DittNAV ved innlesing fra kafka, før eventene vises til sluttbruker. Ved å bruke builderene minimeres sjansene for at
eventene blir avvist av DittNAV pga valideringsfeil. 

Hvis det forsøkes å bygge et event med ugyldige feltverdier, så vil builderen kasse en `FieldValidationException` ved kallet 
til `*.build()`. Denne exception-en vil gi informasjon om om hvilket felt som feilet og hva som skjedde.

Se valideringsregler [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/util/ValidationUtil.java)

### Validering
* [Nokkel](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/NokkelBuilder.java#L21)
* [Beskjed](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/BeskjedBuilder.java#L91)
* [Oppgave](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/OppgaveBuilder.java#L91)
* [Done](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/DoneBuilder.java#L30)
* [Statusoppdatering](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/StatusoppdateringBuilder.java#L63)

## Kodeeksempel 
```
BeskjedBuilder builder = getBuilderWithValues();
Beskjed beskjed = builder.build(); // Alle felter valideres, for eventet eventuelt blir opprettet

private BeskjedBuilder getBuilderWithValues() {
    return new BeskjedBuilder()
            .withFodselsnummer(fodselsnr)
            .withGrupperingsId(grupperingsId)
            .withSikkerhetsnivaa(sikkerhetsnivaa)
            .withLink(link)
            .withTekst(tekst)
            .withTidspunkt(tidspunkt)
            .withSynligFremTil(synligFremTil);
}
```

Se `BeskjedBuilder()` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/BeskjedBuilder.java) og `build()` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/legacy/BeskjedBuilder.java#L90).
