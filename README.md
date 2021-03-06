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
18.11 | 1h | Sääasema - kosteuden ja lämmön mittaaminenTehtävä
Yht | 14h |
  
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
### Web-käyttöliittymän rakentaminen LED:n hallintaa varten  
![Ledi kontrolli web liittymällä kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Ledi%20kontrolli%20web%20liittym%C3%A4ll%C3%A4%20kuva.jpg)  
Ledi syttyy ja sammuu kuvassa olevien nappien mukaan. Kuvat ovat samat kuin edellisessä kohdassa.  

````
<html>
  <head>
    <meta charset="UTF-8" />
  </head>
  <body>
    <<center>
      <br />
      <br />
      <br />
      <form action= "https://api.particle.io/v1/devices/devoceid/led?access_token=accestoken" method="post">
      LED:n kontrollointi web-käyttöliittymällä
      <br />
      <br />
      <input name="arg" type="radio" value="on" />
      Sytytä LED. 
      <br />
      <input name="arg" type="radio" value="off"/>
      Sammuta LED. 
      <br />
      <br />
    <input type="submit" value="valmis" />
      </form>
    </center>
  </body>
  </html>
````  
### Valoisuuden mittaaminen photosensorilla  
![Valosensori rakennus](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Valosensori%20rakennus.jpg)  
![Valosensori kuva](https://github.com/MikaLiikanen/koodiharjoitus/blob/master/Valosensori%20kuva.jpg)  
Sensori mittaa vallon määrää. Peittää sensorin lukema on pienenpi.  

````
int led = D6; 

int photosensor = A0; 
//valitaan sensori ja ledi
int analogvalue; 

int ledToggle(String command); 

void setup() {
    
    Serial.begin();

    pinMode(led, OUTPUT); 
    digitalWrite(led, HIGH);

    Particle.variable("analogvalue", &analogvalue, INT);

    Particle.function("led",ledToggle);

}

void loop() {

    analogvalue = analogRead(photosensor);

    Serial.printlnf("%d", analogvalue);

    delay(100);
}


int ledToggle(String command) {

    if (command=="on") {
        digitalWrite(led,HIGH);
        return 1;
    }
    else if (command=="off") {
        digitalWrite(led,LOW);
        return 0;
    }
    else {
        return -1;
    }
}
````  


