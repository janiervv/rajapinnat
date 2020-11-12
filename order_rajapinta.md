# Ordr

Tässä dokumentoidaan kaikki Ordr- eli tilaus-luokkaan kohdistuvat API-kutsut.

**Näytä tilaukset**
----
Palauttaa JSON-tyyppisen listan käyttäjistä.

* **URL**

  /api/ordrs/

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
  
  * **Status:** 200 OK <br />
    **Sisältö:** 
            `{
            "_embedded": {
                "ordrs": [
                    {
                        "sold": "2020-10-01T00:00:00.000+00:00",
                        "_links": {
                            "self": {
                                "href": "http://localhost:8080/api/ordrs/6"
                            },
                            "ordr": {
                                "href": "http://localhost:8080/api/ordrs/6"
                            },
                            "user": {
                                "href": "http://localhost:8080/api/ordrs/6/user"
                            },
                            "tickets": {
                                "href": "http://localhost:8080/api/ordrs/6/tickets"
                            }
                        }
                    },
                    {
                        "sold": null,
                        "_links": {
                            "self": {
                                "href": "http://localhost:8080/api/ordrs/7"
                            },
                            "ordr": {
                                "href": "http://localhost:8080/api/ordrs/7"
                            },
                            "user": {
                                "href": "http://localhost:8080/api/ordrs/7/user"
                            },
                            "tickets": {
                                "href": "http://localhost:8080/api/ordrs/7/tickets"
                            }
                        }
                    }
                ]
                },
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/ordrs"
                    },
                    "profile": {
                        "href": "http://localhost:8080/api/profile/ordrs"
                    }
                }
            }`
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found <br />
    **Sisältö:** 
            `{
                "timestamp": "2020-09-27T10:04:00.758+00:00",
                "status": 404,
                "error": "Not Found",
                "message": "No message available",
                "path": "/api/orders/"
            }`

* **Sample Call:**

  Postman: GET http://localhost:8080/api/ordrs/

* **Muistiinpanoja:**
  
  -


**Näytä yksittäinen tilaus**
----
Näyttää yksittäisen tilauksen listasta.

* **URL**

  /api/ordrs/{id}

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
  
  * **Status:** 200 OK <br />
    **Sisältö:** 
            `{
                "sold": "2020-10-01T00:00:00.000+00:00",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/ordrs/6"
                    },
                    "ordr": {
                        "href": "http://localhost:8080/api/ordrs/6"
                    },
                    "user": {
                        "href": "http://localhost:8080/api/ordrs/6/user"
                    },
                    "tickets": {
                        "href": "http://localhost:8080/api/ordrs/6/tickets"
                    }
                }
            }`
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found <br />
    **Sisältö:** ``

* **Sample Call:**

  Postman: GET http://localhost:8080/api/ordrs/6

* **Muistiinpanoja:**
  
  -


**Lisää tilaus**
----
Lisää uuden tilauksen listaan. 

* **URL**

  /api/ordrs/

* **Metodi:**
  
  `POST`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   Ei ole

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

  **Pakolliset**
       `{
        "user": "http://localhost:8080/api/users/{id}"
       }`

  **Valinnaiset
       `{
        "sold": Date-tyyppinen data
       }`
   
   **Esimerkkikutsu:
   
       {
        "sold":"2020-10-10",
        "user": "http://localhost:8080/api/users/3" 
        }

* **Onnistunut vastaus:**
  
  * **Status:** 201 Created <br />
    **Sisältö:** 
    `{
    "sold": null,
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/ordrs/8"
        },
        "ordr": {
            "href": "http://localhost:8080/api/ordrs/8"
        },
        "user": {
            "href": "http://localhost:8080/api/ordrs/8/user"
        },
        "tickets": {
            "href": "http://localhost:8080/api/ordrs/8/tickets"
        }
    }
}`
 
* **Virheellinen vastaus:**

  * **Status:** 400 Bad Request <br />
    **Sisältö:** 
    `"errors": [
        {
            "entity": "Ordr",
            "property": "user",
            "invalidValue": null,
            "message": "must not be null"
        }
    ]
}`

* **Sample Call:**

  Postman: POST http://localhost:8080/api/ordrs/

* **Muistiinpanoja:**
  
  - Tilauksen POST-viestiin on sisällytettävä käyttäjän tiedot


**Poista tilaus**
----
Poistaa tilauksen listalta. 

* **URL**

  /api/ordrs/{id}

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

  Postman: DELETE http://localhost:8080/api/ordrs/1

* **Muistiinpanoja:**
  
  -

**Muuta koko tilaus**
----
Muuttaa yksittäisen tilauksen tietoja. 

* **URL**

  /api/ordrs/{id}

* **Metodi:**
  
  `PUT`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   `{
    "sold": Date-tyyppinen data
    "user": "http://localhost:8080/api/users/{id}",
   }`

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 
`{
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/ordrs/{id}"
        },
        "ordr": {
            "href": "http://localhost:8080/api/ordrs/{id}"
        },
        "user": {
            "href": "http://localhost:8080/api/ordrs/{id}/user"
        },
        "tickets": {
            "href": "http://localhost:8080/api/ordrs/{id}/tickets"
        }
    }
}`
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found<br />
    **Sisältö:** 
`{
    "timestamp": "2020-09-27T10:42:34.801+00:00",
    "status": 404,
    "error": "Not Found",
    "message": "No message available",
    "path": "/api/ordrs/"
}`
  * **Status:** 400 Bad Request<br />
    **Sisältö:** 
`{
    "errors": [
        {
            "entity": "Ordr",
            "property": "user",
            "invalidValue": null,
            "message": "must not be null"
        }
    ]
}`

* **Sample Call:**

  Postman: PUT http://localhost:8080/api/ordrs/1

* **Muistiinpanoja:**
  
  - Tilauksen muokkaus PUT-metodilla ilman kaikkien attribuuttien lisäämistä on mahdollista ja se antaa 200 OK -statusviestin

**Muuta tilauksen yksittäistä parametria**
----
Muuttaa yksittäisen tilauksen valittuja kenttiä. 

* **URL**

  /api/ordrs/{id}

* **Metodi:**
  
  `PATCH`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[integer]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   `{
    "user": "http://localhost:8080/api/users/{id}"
   }`
   TAI
   `{
    "sold": Date-tyyppinen data
   }`

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK <br />
    **Sisältö:** 
`{
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/ordrs/{id}"
        },
        "ordr": {
            "href": "http://localhost:8080/api/ordrs/{id}"
        },
        "user": {
            "href": "http://localhost:8080/api/ordrs/{id}/user"
        },
        "tickets": {
            "href": "http://localhost:8080/api/ordrs/{id}/tickets"
        }
    }
}`
 
* **Virheellinen vastaus:**

  * **Status:** 400 Bad Request<br />
    **Sisältö:** 
   `{
    "errors": [
        {
            "entity": "Ordr",
            "property": "user",
            "invalidValue": null,
            "message": "must not be null"
        }
    ]
}`

* **Sample Call:**

  Postman: PATCH http://localhost:8080/api/ordrs/1

* **Muistiinpanoja:**
  
  - Tilauksen parametrin muuttaminen PATCH-metodilla olematonta parametria käyttäen antaa 200 OK -statusvastauksen, mutta kyseisen parametrin tiedot eivät tallennu, vaan API-kutsu kyseiseen endpointiin aiheuttaa 404-virheviestin
