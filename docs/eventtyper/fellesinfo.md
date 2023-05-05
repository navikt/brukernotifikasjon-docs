# Hei!
Vi har laga ny dokumentasjonside som ser bedre ut og oppdateres oftere, hurra!
Der finner du info om både varsler(tidligere brukernotifikasjoner) og alt det andre innholdet som ditt team kan få inn på min-side.

https://tms-dokumentasjon.intern.nav.no/


Se vår [guide](../guide_varslingstype.md) for valg av brukernotifikasjon.

Alle brukernotifikasjoner består av en `key` og en `value` som legges på kafka-topicene. Alle eventtypene bruker [NokkelInput]() som key, 
mens hver eventtype har sin egen value. Se egene underkapitler for dette ([Beskjed](./beskjed/beskrivelse.md), [Oppgave](./oppgave/beskrivelse.md) og [Done](./done/beskrivelse.md).

Husk å bruk `builderene` våre for å validere alle eventer. Les mer om dette [her](../builder.md).

## Kafka key (NokkelInput)
Feltene i NokkelInput er som en kompositt-nøkkel for å unikt identifisere eventet.
Alle feltene nedenfor må være med for at eventet skal bli validert.

### eventId
Den unike identifikatoren per event, må enten være en UUID eller en ULID.
Det er denne `eventID`-en som benyttes for å deaktivere eventer som er utført. 
Dette gjøres ved å sende et event av typen done, med referanse til det eventet som ikke skal vises på DittNAV lengre.
Feltet kan ikke være null.

### grupperidsId - deprecated
Feltet vil etter hvert fjernes.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører. Feltet har en begrensning på 11 tegn og kan ikke være null.

### namespace
Namespacet til appen som har produsert eventet. Feltet har en begrensning på 63 tegn og kan ikke være null.

### appnavn
Navnet på appen som har produsert eventet. Feltet har en begrensning på 100 tegn og kan ikke være null.

#### Schemas
[Nokkel-schemas](https://github.com/navikt/brukernotifikasjon-schemas/blob/main/src/main/avro/nokkelInput.avsc) på Github.
