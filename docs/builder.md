# Builder

Alle produsenter oppfordres sterkt til å bruke `builderene` til å opprette eventer. Grunnen til dette er at 
builderene vil validere alle feltene, før et event opprettes. Dette er de samme valideringsreglene som brukes av 
DittNAV ved innlesing fra kafka, før eventene vises til sluttbruker. Ved å bruke builderene minimeres sjansene for at
eventene blir avvist av DittNAV pga valideringsfeil. 

Hvis det forsøkes å bygge et event med ugyldige feltverdier, så vil builderen kasse en `FieldValidationException` ved kallet 
til `*.build()`. Denne exception-en vil gi informasjon om om hvilket felt som feilet og hva som skjedde.

Se valideringsregler [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/util/ValidationUtil.java)

### Validering
* [Nokkel](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/NokkelBuilder.java#L16)
* [Beskjed](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedBuilder.java#L54)
* [Oppgave](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/OppgaveBuilder.java#L48)
* [Done](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/DoneBuilder.java#L29)
* [Statusoppdatering](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/StatusoppdateringBuilder.java#L61)

## Kode eksempel 
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

Se `BeskjedBuilder()` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedBuilder.java#L9) og `build()` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedBuilder.java#L54).