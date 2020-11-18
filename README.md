# Sääasema 2020
  
## Vaatimusmäärittely
  
### Sovelluksen tarkoitus
  
* Mitataan ympäristön lämpötila- ja ilmankosteustietoja.  
* Saatuja tietoja voidaan tarkastella tekstinä ja grafiikkana web sovelluksella.  

### Käyttäjät  
Web sovellus on tarkoitettu julkiseen käyttöön.  

### Käyttöliittymä  
Käyttöliittymä koostuu kahdesta näkymästä:  
1. Tekstimuotoisen datan selaamiseen tarkoitettu näkymä.
2. Grafiikkamuotoisen datan selaamiseen tarkoitettu näkymä.  
    
### Jatkokehitysideoita  
Säätietojen selaaminen valitulla aikavälillä.  

## Arkkitehtuurikuvaus  

### Luokkakaavio  

### Sekvenssikaavio  

## Työaikakirjanpito  
Päivä | Aika | Tehtävät
------|------|--------
21.10 | 3h | Ledin kytkentä
30.10 | 4h | Ledinvilkuttaminen
04.11 | 3h | Web-käyttöliittymän rakentaminen LED:n hallintaa varten
18.11 | 3h | Valoisuuden mittaaminen photosensorilla
Yht | 13h |
  
## Työvaiheet    
### Ledin kytkentä  
![Ledinvilkuttaminen asennus kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Ledinvilkuttaminen%20asennus%20kuva.jpg)  
![Ledinvilkuttaminen kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Ledinvilkuttaminen%20kuva.jpg)  
Ledi menee päälle kun photoni liitetään virtalähteeseen  

### Ledinvilkuttaminen  
![WebkäyttöliittymänrakentaminenLedinhallintaavarten asennus kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Webk%C3%A4ytt%C3%B6liittym%C3%A4nrakentaminenLedinhallintaavarten%20asennus%20kuva.jpg)  
![WebkäyttöliittymänrakentaminenLedinhallintaavarten kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Webk%C3%A4ytt%C3%B6liittym%C3%A4nrakentaminenLedinhallintaavarten%20kuva.jpg)  
Ledit vilkkuvat kun photoni liitetään virtalähteeseen

````
int led1 = D6; 
int led2 = D7; 
// valitan oikeat ledit
void setup() {

  pinMode(led1, OUTPUT);

  pinMode(led2, OUTPUT);

}

void loop() {

  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);

  delay(1000);
// määritellään ledin päälle ja pois meno aika
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);

  delay(1000);

}
````  
Käynnistä projekti paikallisesti porttiin 3000  

````
npm start
````


