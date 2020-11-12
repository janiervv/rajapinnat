# Event-rajapinta

Tässä dokumentoidaan kaikki Event- eli tapahtuma-luokkaan kohdistuvat API-kutsut.



**Näytä tapahtumat**
----
* **URL**

    api/events

* **Metodi:**
  
  `GET`
  
* **URL-parametrit**

   **Pakolliset:**
 
   Ei ole

* **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 

        {
        "_embedded": {
            "events": [
                {
                    "event_name": Event name,
                    "starts_at": "2020.10.01.12.00.00",
                    "ends_at": "2020.10.01.18.00.00",
                    "capacity": 1000,
                    "_links": {
                        "self": {
                            "href": "http://localhost:8080/api/events/9"
                        },
                        "event": {
                            "href": "http://localhost:8080/api/events/9"
                        },
                        "priceCat": {
                            "href": "http://localhost:8080/api/events/9/priceCat"
                        },
                        "organizer": {
                            "href": "http://localhost:8080/api/events/9/organizer"
                        },
                        "location": {
                            "href": "http://localhost:8080/api/events/9/location"
                        }
                    }
                }
            ]
        },
        "_links": {
            "self": {
                "href": "http://localhost:8080/api/events"
            },
            "profile": {
                "href": "http://localhost:8080/api/profile/events"
            }
        }
    }


* **Virheellinen vastaus:**

* **Status:** 404 Not Found <br />
    **Sisältö:** 
        {
            "timestamp": "2020-09-29T18:003:23.758+00:00",
            "status": 404,
            "error": "Not Found",
            "message": "No message available",
            "path": "/api/events/"
        }

* **Sample Call:**

  Postman: GET http://localhost:8080/api/events/





**Näytä yksittäinen tapahtuma**
----
* **URL**

    api/events/{id}

* **Metodi:**
  
  `GET`
  
* **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

* **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 

        {
            "event_name": Event name,
            "starts_at": "2020.10.01.12.00.00",
            "ends_at": "2020.10.01.18.00.00",
            "capacity": 1000,
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "event": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "priceCat": {
                    "href": "http://localhost:8080/api/events/1/priceCat"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/events/1/organizer"
                },
                "location": {
                    "href": "http://localhost:8080/api/events/1/location"
                }
            }
        }

* **Virheellinen vastaus:**

  * **Status:** 404 Not Found <br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: GET http://localhost:8080/api/events/8




**Lisää tapahtuma**
----
Lisää uuden tapahtuman tietokantaan. 

* **URL**

  /api/events/

* **Metodi:**
  
  `POST`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   Ei ole

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

        {
            "event_name":"Event name",
            "starts_at":"2020.10.01.12.00.00", 
            "ends_at":"2020.10.01.18.00.00", 
            "capacity":"1000", 
            "organizer_id":"/api/organizer/{id}", 
            "location_id":"/api/location/{id}"", 
            "price_cat_id":"/api/priceCat/{id}""
        }

* **Onnistunut vastaus:**
  
  * **Status:** 201 Created <br />
    **Sisältö:** 

        {
            "event_name": Event name,
            "starts_at": "2020.10.01.12.00.00",
            "ends_at": "2020.10.01.18.00.00",
            "capacity": 1000,
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "event": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "priceCat": {
                    "href": "http://localhost:8080/api/events/1/priceCat"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/events/1/organizer"
                },
                "location": {
                    "href": "http://localhost:8080/api/events/1/location"
                }
            }
        }
 
* **Virheellinen vastaus:**

  * **Status:** <br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: POST http://localhost:8080/api/events/

* **Muistiinpanoja:**



**Poista tapahtuma**
----
Poistaa tapahtuman. 

* **URL**

  /api/events/{id}

* **Metodi:**
  
  `DELETE`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 204 No Content <br />
    **Sisältö:** ``
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found<br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: DELETE http://localhost:8080/api/events/7

* **Muistiinpanoja:**
  
  -




**Muuta tapahtumaa**
----
Muuttaa tapahtumaa tietokannassa. 

* **URL**

  /api/events/{id}

* **Metodi:**
  
  `PUT`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

        {
            "event_name":"Event name",
            "starts_at":"2020.10.01.12.00.00", 
            "ends_at":"2020.10.01.18.00.00", 
            "capacity":"1000", 
            "organizer_id":"/api/organizer/{id}", 
            "location_id":"/api/location/{id}"", 
            "price_cat_id":"/api/priceCat/{id}""
        }

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 

        {
            "event_name": Event name,
            "starts_at": "2020.10.01.12.00.00",
            "ends_at": "2020.10.01.18.00.00",
            "capacity": 1000,
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "event": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "priceCat": {
                    "href": "http://localhost:8080/api/events/1/priceCat"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/events/1/organizer"
                },
                "location": {
                    "href": "http://localhost:8080/api/events/1/location"
                }
            }
        }
 
* **Virheellinen vastaus:**

  * **Status:** <br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: PUT http://localhost:8080/api/events/{id}

* **Muistiinpanoja:**




**Muuta tapahtuman yksittäistä tietoa**
----
Muuttaa tapahtuman tietoa tietokannassa. 

* **URL**

  /api/events/{id}

* **Metodi:**
  
  `PATCH`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

Alla olevat kutsut toimivat dataparametrinä. 

        {"event_name":"Event name"}

        {"starts_at":"2020.10.01.12.00.00"}

        {"ends_at":"2020.10.01.18.00.00"}

        {"capacity":"1000"}

        {"organizer_id":"/api/organizer/{id}"}

        {"location_id":"/api/location/{id}""}

        { "price_cat_id":"/api/priceCat/{id}""}

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 

        {
            "event_name": Event name,
            "starts_at": "2020.10.01.12.00.00",
            "ends_at": "2020.10.01.18.00.00",
            "capacity": 1000,
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "event": {
                    "href": "http://localhost:8080/api/events/1"
                },
                "priceCat": {
                    "href": "http://localhost:8080/api/events/1/priceCat"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/events/1/organizer"
                },
                "location": {
                    "href": "http://localhost:8080/api/events/1/location"
                }
            }
        }
 
* **Virheellinen vastaus:**

  * **Status:** <br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: PUT http://localhost:8080/api/events/{id}

* **Muistiinpanoja:**




## Muut GET-pyynnöt




**Tapahtuman 1 organizer:** 

    /api/events/1/organizer

Vastaus:

        `{
            "organizer_name": "Organizer Name",
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/organizers/2"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/organizers/2"
                },
                "events": {
                    "href": "http://localhost:8080/api/organizers/2/events"
                }
            }
        }´


**Tapahtuman 1 paikka:** 

    /api/events/1/location

Vastaus:

        {
            "organizer_name": "Organizer Name",
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/organizers/2"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/organizers/2"
                },
                "events": {
                    "href": "http://localhost:8080/api/organizers/2/events"
                }
            }
        }



**Tapahtuman 1 hintaluokka:** 

    /api/events/1/priceCat

Vastaus



### /api/events/1/priceCat

        {
            "location": "Price Category",
            "_links": {
                "self": {
                    "href": "http://localhost:8080/api/priceCat/1"
                },
                "organizer": {
                    "href": "http://localhost:8080/api/priceCat/1"
                },
                "events": {
                    "href": "http://localhost:8080/api/priceCat/1/events"
                }
            }
        }

