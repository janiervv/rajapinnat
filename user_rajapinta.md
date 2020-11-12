# User
Tässä dokumentoidaan kaikki User- eli käyttäjä-luokkaan kohdistuvat API-kutsut.

**Näytä käyttäjät**
----
Palauttaa JSON-tyyppisen listan käyttäjistä.

* **URL**

  /api/users/

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
        "users": [
            {
                "password": null,
                "firstname": "Essi",
                "lastname": "Esimerkki",
                "username": "kayttaja1"
                "role": "ADMIN",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/users/{id}"
                    },
                    "user": {
                        "href": "http://localhost:8080/api/users/{id}"
                    },
                    "ordrs": {
                        "href": "http://localhost:8080/api/users/{id}/ordrs"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/users/"
        },
        "profile": {
            "href": "http://localhost:8080/api/profile/users"
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
      "path": "/api/users/"  
    }
```
  
**Sample Call:**

  Postman: `GET` http://localhost:8080/api/users/

* **Muistiinpanoja:**
  
  -


**Näytä yksittäinen käyttäjä**
----
Näyttää yksittäisen käyttäjän tiedot listasta.

* **URL**

  /api/users/{id}

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
    "password": null,
    "firstname": "Essi",
    "lastname": "Esimerkki",
    "username": "kayttaja1"
    "role": "ADMIN",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/users/{id}"
        },
        "user": {
            "href": "http://localhost:8080/api/users/{id}"
        },
        "ordrs": {
            "href": "http://localhost:8080/api/users/{id}/ordrs"
      }
    }
  }
```
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:** 

* **Sample Call:**

  Postman: `GET` http://localhost:8080/api/users/75

* **Muistiinpanoja:**
  
  -

**Lisää Käyttäjä**
----
Lisää uuden käyttäjän.

* **URL**

/api/users

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
    "password": "salainen",
    "firstname": "Esko",
    "lastname": "Esimerkki",
    "username": "kayttaja1",
    "role": "user"
  }
```
  * **Onnistunut vastaus:**
    * **Status:** 200 OK tai 201 Created
    * **Sisältö:**
```
    {
      "password": "salainen",
      "firstname": "Esko",
      "lastname": "Esimerkki",
      "username": "kayttaja1",
      "role": "user",
      "_links": {
          "self": {
              "href": "http://localhost:8080/api/users/{id}"
          },
          "user": {
              "href": "http://localhost:8080/api/users/{id}"
          },
          "ordrs": {
              "href": "http://localhost:8080/api/users/{id}/ordrs"
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
            "entity": "User",
            "property": "firstname",
            "invalidValue": "k",
            "message": "Etunimen täytyy olla vähintään 2 kirjainta"
        },
        {
            "entity": "User",
            "property": "role",
            "invalidValue": "",
            "message": "Käyttäjä rooli ei voi olla tyhjä"
        },
        {
            "entity": "User",
            "property": "lastname",
            "invalidValue": "kkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkkk",
            "message": "Sukunimi voi olla maksimissaan 30 kirjainta"
        }
    ]
}
```
* **Sample Call:**

Postman `POST` http://localhost:8080/api/users

* **Muistiinpanoja:**

  - 400 Bad request syntyy virheellisillä tai puuttuvilla data  parametreillä.


**Muuta olemassa olevaa käyttäjää**
----
Muokkaa jo luotua käyttäjää.

* **URL**

/api/users/{id}

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
    "password": "salainen",
    "firstname": "Erkki",
    "lastname": "Esimerkki",
    "username": "kayttaja1",
    "role": "user"
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
    "username": "kayttaja1",
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
    -

* **Sample Call:**

Postman `PATCH` http://localhost:8080/api/users/5

* **Muistiinpanoja:**

  - Väärä URL parametri aiheuttaa 404 Not Found errorin



**Poista käyttäjä**
----
Poistaa käyttäjän. 

* **URL**

  /api/users/{id}

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

  Postman: `DELETE` http://localhost:8080/api/users/5

* **Muistiinpanoja:**