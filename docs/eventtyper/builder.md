# Builder

Alle produsenter skal bruke `Builder-n` til å validere event. 

Her kan dere new-e opp objekter og validere felt.
Hvis felt ikke tilfredstiller `Builder-en` kaster den en `FieldValidationException`. Her får dere informasjon om hvilket felt som feilet og hva som skjedde.

Se valideringsregler [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/java/no/nav/brukernotifikasjon/schemas/builders/util/ValidationUtil.java)

### Validering
* [Nokkel](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/NokkelBuilder.java#L16)
* [Beskjed](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/BeskjedBuilder.java#L54)
* [Oppgave](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/OppgaveBuilder.java#L48)
* [Done](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/DoneBuilder.java#L29)
* [Statusoppdatering](https://github.com/navikt/brukernotifikasjon-schemas/blob/cc113a4258430b8f9f13b8f92b05e47abce40048/src/main/java/no/nav/brukernotifikasjon/schemas/builders/StatusoppdateringBuilder.java#L61)

## Kode eksempel 
```
BeskjedBuilder builder = getBuilderWithValues(); //opprett ny BeskjedBuilder()
Beskjed beskjed = builder.build(); //Valider alle felt med build()

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