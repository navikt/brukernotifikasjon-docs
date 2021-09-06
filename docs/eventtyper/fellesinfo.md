Se vår [guide](../guide_varslingstype.md) for valg av brukernotifikasjon.

Alle brukernotifikasjoner består av en `key` og en `value` som legges på kafka-topicene. Alle eventtypene bruker [Nokkel]() som key, 
mens hver eventtype har sin egen value. Se egene underkapitler for dette ([Beskjed](./beskjed/beskrivelse.md), [Oppgave](./oppgave/beskrivelse.md), [Done](./done/beskrivelse.md) og [Statusoppdatering](./statusoppdatering/beskrivelse.md)).

Husk å bruk `builderene` våre for å validere alle eventer. Les mer om dette [her](../builder.md).

## Hva gjør et event unikt?


## Kafka key (Nokkel)
Feltene i Nokkel er som en kompositt-nøkkel for å unikt identifisere eventet.

### systembruker
Navn på systembruker som har produsert eventet. Feltet har en begrensning på 100 tegn og kan ikke være null. 

### eventId
Den unike identifikatoren per event, og den må være unik for hver `systembruker` (produsent). Det er denne `eventID`-en som benyttes for å deaktivere eventer som er utført. Dette gjøres ved å sende et event av typen done, med referanse til det eventet som ikke skal vises på DittNAV lengre. Feltet har en begrensning på 50 tegn og kan ikke være null. 

#### Schemas
Du finner `Nokkel-schemas` [her](https://github.com/navikt/brukernotifikasjon-schemas/blob/master/src/main/avro/nokkel.avsc).
