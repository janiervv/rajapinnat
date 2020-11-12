# PriceCat
Tässä dokumentoidaan kaikki PriceCat- eli hintakategoria-luokkaan kohdistuvat API-kutsut.

**Näytä hintakategoriat**
----
Palauttaa JSON-tyyppisen listan hintakategorioista.

* **URL**

  /api/pricecats/

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
  "_embedded" : {
    "priceCats" : [ {
      "price_cat_name" : "eläkeläinen",
      "price" : 15,
      "_links" : {
        "self" : {
          "href" : "http://localhost:8080/api/priceCats/2"
        },
        "priceCat" : {
          "href" : "http://localhost:8080/api/priceCats/2"
        },
        "event" : {
          "href" : "http://localhost:8080/api/priceCats/2/event"
        },
        "tickets" : {
          "href" : "http://localhost:8080/api/priceCats/2/tickets"
        }
      }
    ]
  },
  "_links" : {
    "self" : {
      "href" : "http://localhost:8080/api/priceCats"
    },
    "profile" : {
      "href" : "http://localhost:8080/api/profile/priceCats"
    }
  }
}
```
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:**
```
    {  
      "timestamp": "2020-10-07T10:36:06.458+00:00",  
      "status": 404,  
      "error": "Not Found",  
      "message": "No message available",  
      "path": "/api/priceCats/"  
    }
```
  
**Sample Call:**
  Postman: `GET` http://localhost:8080/api/priceCats/
  
  * **Muistiinpanoja:**
  
  -


**Näytä yksittäinen hintakategoria**
----
Näyttää yksittäisen hintakategorian tiedot listasta.

* **URL**

  /api/priceCats/{id}
  
  
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
    "price_cat_name": "eläkeläinen",
    "price": 15,
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/priceCats/{id}"
        },
        "priceCat": {
            "href": "http://localhost:8080/api/priceCats/{id}"
        },
        "event": {
            "href": "http://localhost:8080/api/priceCats/{id}/event"
        },
        "tickets": {
            "href": "http://localhost:8080/api/priceCats/{id}/tickets"
        }
    }
}
```
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:** 

* **Sample Call:**

  Postman: `GET` http://localhost:8080/api/priceCats/2

* **Muistiinpanoja:**
  
  -
**Lisää Hintakategoria**
----
Lisää uuden hintakategorian.

* **URL**

/api/priceCat/{id}

* **Metodi**

`PUT`

* **URL-parametrit**

  **Pakolliset:**

  id=[integer]

  **Valinnaiset**
  
  Ei ole

  * **Dataparametrit**
```
{
    "price_cat_name": "kokeilukatsomo",
    "price": "43",
    "event": "http://localhost:8080/api/events/1"
      
}
```

  * **Onnistunut vastaus:**
    * **Status:** 201 Created
    * **Sisältö:**
```
{
    "price_cat_name": "kokeilukatsomo",
    "price": 43,
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/priceCats/{id}"
        },
        "priceCat": {
            "href": "http://localhost:8080/api/priceCats/{id}"
        },
        "event": {
            "href": "http://localhost:8080/api/priceCats/{id}/event"
        },
        "tickets": {
            "href": "http://localhost:8080/api/priceCats/{id}/tickets"
        }
    }
}
```
  * **Virheellinen vastaus:**
    * **Status:** 400 Bad request
    * **Sisältö:**
```
{
    "cause": {
        "cause": null,
        "message": "No content to map due to end-of-input\n at [Source: (org.apache.catalina.connector.CoyoteInputStream); line: 1, column: 0]"
    },
    "message": "JSON parse error: No content to map due to end-of-input; nested exception is com.fasterxml.jackson.databind.exc.MismatchedInputException: No content to map due to end-of-input\n at [Source: (org.apache.catalina.connector.CoyoteInputStream); line: 1, column: 0]"
}
```

  * **Kun hintakategoria on tyhjänä:**
    * **Status:** 400 Bad request
    * **Sisältö:**
```
{
    "errors": [
        {
            "entity": "PriceCat",
            "property": "price_cat_name",
            "invalidValue": "",
            "message": "Hintakategorian nimi ei voi olla tyhjä"
        }
    ]
}

```

* **Sample Call:**

Postman `PUT` http://localhost:8080/api/priceCats/{id}

* **Muistiinpanoja:**

  - 400 Bad request syntyy virheellisillä tai puuttuvilla data  parametreillä.


**Muuta olemassa olevaa hintakategoriaa**
----
Muokkaa jo luotua hintakategoriaa.

* **URL**

/api/priceCats/{id}

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
    "price_cat_name": "kokeilukatsomo",
    "price": "43",
    "event": "http://localhost:8080/api/events/1"   
}
```
  * **Onnistunut vastaus:**
    * **Status:** 200 OK
    * **Sisältö:**
```
    {
    "password": "salainen",
    "firstname": "Erkki",
    "lastname": "Esimerkki",
    "role": "user",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/users/5"
        },
        "user": {
            "href": "http://localhost:8080/api/users/5"
        },
        "ordrs": {
            "href": "http://localhost:8080/api/users/5/ordrs"
        }
    }
}
```
  * **Virheellinen vastaus:**
    * **Status:** 404 Not Found
    * **Sisältö:**
 ```
    {
    "timestamp": "2020-10-07T17:46:51.047+00:00",
    "status": 404,
    "error": "Not Found",
    "message": "No message available",
    "path": "/api/priceCats/"
  }
 ```
* **Sample Call:**


Postman `PATCH` http://localhost:8080/api/priceCats/{id}


* **Muistiinpanoja:**


**Poista hintakategoria**
----
Poistaa hintakategorian. 

* **URL**

  /api/priceCat/{id}

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

  Postman: `DELETE` http://localhost:8080/api/priceCats/{id}

* **Muistiinpanoja:**
