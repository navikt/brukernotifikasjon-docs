Alle brukernotifikasjoner består av en key og en value som legges på kafka-topicene. Alle eventtypene bruker [Nokkel]() som key, 
mens hver eventtype har sin egen value. Se egene underkapitler for dette.

## Hva gjør et event unikt?


## Kafka key (Nokkel)
Feltene i Nokkel er som en kompositt-nøkkel for å unikt identifisere eventet.

### systembruker
Navn på systembruker som har produsert eventet.

### eventId
Den unike identifikatoren per event, og den må være unik innen for hver `systembruker` (produsent). Det er denne `eventID`-en som benyttes for å deaktivere eventer som er utført. Dette gjøres ved å sende et event av typen done, med referanse til det eventet som ikke skal vises på DittNAV lengre.
