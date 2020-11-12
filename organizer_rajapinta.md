# Organizer
Tässä dokumentoidaan kaikki Organizer- eli tapahtuman järjestäjä-luokkaan kohdistuvat API-kutsut.

**Näytä Tapahtuman järjestäjät**
----
Palauttaa JSON-tyyppisen listan tapahtuman järjestäjistä

* **URL**

  /api/organizers/

* **Metodi:**
  
  `GET`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   Ei ole

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK  
    **Sisältö:**  
```
   {
    "_embedded": {
        "organizers": [
            {
                "organizer_name": "Keikka kekkonen Oy",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/organizers/12"
                    },
                    "organizer": {
                        "href": "http://localhost:8080/api/organizers/12"
                    },
                    "events": {
                        "href": "http://localhost:8080/api/organizers/12/events"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/organizers"
        },
        "profile": {
            "href": "http://localhost:8080/api/profile/organizers"
        }
    }
}
```
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:**
```
    {  
      "timestamp": "2020-09-28T09:36:06.458+00:00",  
      "status": 404,  
      "error": "Not Found",  
      "message": "No message available",  
      "path": "/api/organizerss/"  
    }
```
  
**Sample Call:**

  Postman: `GET` http://localhost:8080/api/organizers/

* **Muistiinpanoja:**
  
  -


**Näytä yksittäinen tapahtuman järjestäjä**
----
Näyttää yksittäisen tapahtuman järjestäjän tiedot listasta.

* **URL**

  /api/organizers/{id}

* **Metodi:**
  
  `GET`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK   
    **Sisältö:**
```
 {
    "organizer_name": "Keikka kekkonen Oy",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/organizers/12"
        },
        "organizer": {
            "href": "http://localhost:8080/api/organizers/12"
        },
        "events": {
            "href": "http://localhost:8080/api/organizers/12/events"
        }
    }
}
```
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:** 

* **Sample Call:**

  Postman: `GET` http://localhost:8080/api/organizers/75

* **Muistiinpanoja:**
  
  -

**Lisää tapahtuman järjestäjä**
----
Lisää uuden tapahtumajärjestäjän.

* **URL**

/api/organizers/

* **Metodi**

`POST`

* **URL-parametrit**

  **Pakolliset:**

    Ei ole

  **Valinnaiset**
  
  Ei ole

  * **Dataparametrit**
```
  {
    "organizer_name": "Keikka kekkonen Oy"
  }
```
  * **Onnistunut vastaus:**
    * **Status:** 201 Created
    * **Sisältö:**
```
   {
    "organizer_name": "Keikka kekkonen Oy",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/organizers/19"
        },
        "organizer": {
            "href": "http://localhost:8080/api/organizers/19"
        },
        "events": {
            "href": "http://localhost:8080/api/organizers/19/events"
        }
    }
}
```
  * **Virheellinen vastaus:**
    * **Status:** 400 Bad request
    * **Sisältö:**
```
{
    "errors": [
        {
            "entity": "Organizer",
            "property": "organizer_name",
            "invalidValue": "s",
            "message": "Liian lyhyt"
        }
    ]
}
```
* **Sample Call:**

Postman `POST` http://localhost:8080/api/organizers

* **Muistiinpanoja:**

  - 400 Bad request syntyy virheellisillä data parametreillä.


**Muuta olemassa olevaa tapahtuman järjestäjää**
----
Muokkaa jo luotua tapahtuman järjestäjää

* **URL**

/api/organizers/{id}

* **Metodi**

`PATCH`

* **URL-parametrit**

  **Pakolliset:**

  id=[integer]

  **Valinnaiset**
  
  Ei ole

  * **Dataparametrit**
```
  {
    "organizer_name": "Keikka Salmi Oy"
  }
```
  * **Onnistunut vastaus:**
    * **Status:** 200 OK
    * **Sisältö:**
```
    {
    "organizer_name": "Keikka Salmi Oy",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/organizers/12"
        },
        "organizer": {
            "href": "http://localhost:8080/api/organizers/12"
        },
        "events": {
            "href": "http://localhost:8080/api/organizers/12/events"
        }
      }
    }
```
  * **Virheellinen vastaus:**
    * **Status:** 404 Not Found
    * **Sisältö:**
    -

* **Sample Call:**

Postman `PATCH` http://localhost:8080/api/organizers/590

* **Muistiinpanoja:**

  - Väärä URL parametri aiheuttaa 404 Not Found errorin



**Poista tapahtuman järjestäjä**
----
Poistaa tapahtuman järjestäjän. 

* **URL**

  /api/organizers/{id}

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
  
  * **Status:** 204 No Content   
    **Sisältö:** 
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found  
    **Sisältö:** 

* **Sample Call:**

  Postman: `DELETE` http://localhost:8080/api/organizers/12

* **Muistiinpanoja:**
  -