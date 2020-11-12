# Location
Tässä dokumentoidaan kaikki Location eli tapahtumapaikka luokkaan kohdistuvat API-kutsut.

**Näytä tapahtumapaikat**
----
Palauttaa JSON-tyyppisen listan tapahtumapaikoista.

* **URL**

  /api/locations/

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
        "locations": [
            {
                "locationname": "Nosturi",
                "locationaddress": "Telakkakatu 8",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/locations/1"
                    },
                    "location": {
                        "href": "http://localhost:8080/api/locations/1"
                    },
                    "events": {
                        "href": "http://localhost:8080/api/locations/1/events"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/locations"
        },
        "profile": {
            "href": "http://localhost:8080/api/profile/locations"
        }
    }
}
```
* **Virheellinen vastaus:**
    Virheellinen url palauttaa 404 errorin
      
  * **Status:** 404 Not Found   
    **Sisältö:**
```
    {  
      "timestamp": "2020-09-28T09:36:06.458+00:00",  
      "status": 404,  
      "error": "Not Found",  
      "message": "No message available",  
      "path": "/api/locationss/"  
    }
```
  
**Sample Call:**

  Postman: `GET` http://localhost:8080/api/locations/

* **Muistiinpanoja:**
  
  -


**Näytä yksittäinen tapahtumapaikka**
----
Näyttää yksittäisen tapahtumapaikan tiedot listasta.

* **URL**

  /api/locations/{id}

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
    "locationname": "Nosturi",
    "locationaddress": "Telakkakatu 8",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/locations/1"
        },
        "location": {
            "href": "http://localhost:8080/api/locations/1"
        },
        "events": {
            "href": "http://localhost:8080/api/locations/1/events"
        }
    }
}
```
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:** 

* **Sample Call:**

  Postman: `GET` http://localhost:8080/api/locations/123

* **Muistiinpanoja:**
  
  -

**Lisää tapahtumapaikka**
----
Lisää uuden tapahtumapaikan.

* **URL**

/api/locations/

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
    "locationname": "Nosturi",
    "locationaddress": "Telakkakatu 8"
}
```
  * **Onnistunut vastaus:**
    * **Status:** 201 Created
    * **Sisältö:**
```
   {
    "locationname": "Nosturi",
    "locationaddress": "Telakkakatu 8",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/locations/2"
        },
        "location": {
            "href": "http://localhost:8080/api/locations/2"
        },
        "events": {
            "href": "http://localhost:8080/api/locations/2/events"
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
            "entity": "Location",
            "property": "locationaddress",
            "invalidValue": "T",
            "message": "size must be between 2 and 255"
        }
    ]
}
```
* **Sample Call:**

Postman `POST` http://localhost:8080/api/locations

* **Muistiinpanoja:**

  - 400 Bad request syntyy virheellisillä data parametreillä.


**Muuta olemassa olevaa tapahtumapaikkaa**
----
Muokkaa jo luotua tapahtumapaikkaa

* **URL**

/api/locationss/{id}

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
  "locationaddress": "Satamakatu 19"
  }
```
  * **Onnistunut vastaus:**
    * **Status:** 200 OK
    * **Sisältö:**
```
    {
    "locationname": "Nosturi",
    "locationaddress": "Satamakatu 19",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/locations/2"
        },
        "location": {
            "href": "http://localhost:8080/api/locations/2"
        },
        "events": {
            "href": "http://localhost:8080/api/locations/2/events"
        }
    }
}
```
  * **Virheellinen vastaus:**
    * **Status:** 404 Not Found
    * **Sisältö:**
    -

* **Sample Call:**

Postman `PATCH` http://localhost:8080/api/locations/2

* **Muistiinpanoja:**

  - Väärä URL parametri aiheuttaa 404 Not Found errorin



**Poista tapahtumapaikan**
----
Poistaa tapahtumapaikan. 

* **URL**

  /api/locationss/{id}

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

  Postman: `DELETE` http://localhost:8080/api/locations/2

* **Muistiinpanoja:**
  -