
**Alla kuvattu sanallisesti jokainen tietoelementti ja sen attribuutit.**

### Location
Location taulu pitää sisällään tapahtumien järjestystpaikan. Location    taulu on yhteydessä Event tauluun, yhdellä tapahtumalla voi olla yksi   lokaatio. Yksi lokaatio voi kuitenkin olla useammassa eri tapahtumassa.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
location_id | auto int PK | Tapahtuma paikan id, pääavain
location_name | varchar(50) | Tapahtumapaikan nimi
address | varchar(100) | Tapahtumapaikan osoite

### User
User on käyttäjä taulu, taulu pitää sisällään käyttäjän tiedot ja roolin  järjestelmässä.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
user_id | auto int PK | Käyttäjän id, pääavain
password | varchar(8-20) | Käyttäjän salasana 
firstname | varchar(30) | Käyttäjän etunimi
lastname | varchar(30) | Käyttäjän sukunimi
username | varchar(30) | Käyttäjänimi
role | int | Käyttäjän rooli järjestelmässä


### Order
Ordr-taulu sisältää tilaukset. Tilaus kuuluu aina vain yhdelle käyttäjälle (user).

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
ordr_id | auto int PK | Tilauksen id, pääavain
user_id | int FK | Tilauksen luonut käyttäjä, viittaus User-tauluun
date |date | Päivämäärä, milloin tilaus on tehty

### _Event_
Event-taulu sisältää tapahtumat. Tapahtumalla voi olla vain yksi lokaatio ja järjestäjä.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
event_it | auto int PK | Tilin id
event_name | varchar(30) |  Tapahtuman nimi
location_id | int FK | Tapahtuman sijainti, viittaus locations-tauluun
starts_at | timestamp | Tapahtuman alkamisajakohta
ends_at | timestamp | Tapahtuman päättymisajankohta
capacity | int | Tapahtuman suurin mahdollinen osallistujamäärä
organizer_id | int FK | Tapahtuman järjestäjä, viittaus organizer-tauluun

### Organizer
Organizer-taulu sisältää tapahtumanjärjestäjät. Yhdellä tapahtumanjärjestäjällä voi olla monta tapahtumaa.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
organizer_id | auto int PK | Tapahtumanjärjestäjän ID, Primary key
organizer_name | varchar(30) | Tapahtumanjärjestäjän nimi

### Price Category
Price category-taulu sisältää hintakategoriat. Hintakategorialla voi olla yksi tapahtuma ja yksi tilausrivi.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
price_cat_id | auto int PK | Hintakategorian ID, Primary key
price_cat_name | varchar(30) | Hintakategorian nimi
price | int | Hintakategorian hinta
event_id | int | Tapahtuman ID, viittaus Event-tauluun

### Ticket
Ticket-taulu sisältää tiedon siitä, onko lippu käytetty. Yhdellä lipulla voi olla yksi tilausrivi.

Kenttä | Tyyppi | Kuvaus
------ | ------ | ------
ticket_id | auto int PK | Lipun id, pääavain
ordr_id | int FK | Tilausrivin tilaus, viittaus Order-tauluun
usedat | datetime | Kertoo, onko lippu käytetty ja milloin. Luodaan nullina, ja kun lippu käytetään niin tälle luodaan arvo.
unit_price | int | Tuotteen yksikköhinta
price_cat_id | int FK | Tuotteen hintakategoria, viittaus Price_cat-tauluun


