## Kafka key
Se [Nokkel](../fellesinfo.md)


## Kafka value

### tidspunkt
Et tidspunkt som noe skjedde, f.eks. da saksbehandlingen av en søknad var ferdig.

### fodselsnummer
Fødselsnummeret til brukeren som eventet tilhører.

### grupperingsId
Feltet grupperingsId brukes for å kunne samle alle eventer som hører til en sak, søknad eller et dokument. Dette er typisk en saksId, søknadsId eller dokumentId, men dere velger selv hvilken verdi dere putter der. Men det er viktig at det er samme verdi for alle eventer som skal grupperes sammen. Typisk bruk for dette feltet vil være oppbygging av tidslinjer.

### tekst
Dette er teksten faktisk vises i eventet. Det er ikke noen støtte for å formatere teksten som settes i dette feltet.

### link
Dette er lenken som blir aktivert i det en bruker trykker på selve eventet. En lenke må være en komplett URL, inkludert `https` protokoll.

### sikkerhetsnivaa
Angir sikkerhetsnivået for informasjonen som eventet innholder.
DittNAV støtter at en bruker er innlogget på nivå 3, hvis denne brukeren har eventer med nivå 4 så vil disse eventene bli "grået ut". Brukeren ser bare hvilken type event dette er, men ikke noe av innholdet. For å se innholdet må brukeren steppe opp til et høyere innloggingsnivå.

### synligFremTil
Et tidspunkt på når eventet ikke skal være synlig mer, f.eks beskjeden skal kun være synlig 7 dager. SynligFramTil = null -> synlig for alltid, med mindre brukeren selv krysser den ut fra forsiden av DittNAV.
