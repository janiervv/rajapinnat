# Ticket
Tässä dokumentoidaan kaikki Ticket- eli lippu-luokkaan kohdistuvat API-kutsut.

**Näytä liput**

Palauttaa JSON-tyyppisen listan lipuista.


* **URL**

  /api/tickets/

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
        "tickets": [
            {
                "unitprice": 20.0,
                "usedat": null,
                "ticket_id": "bce53022-3dd1-4b8a-8b9e-c41daff22a63",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/api/tickets/bce53022-3dd1-4b8a-8b9e-c41daff22a63"
                    },
                    "ticket": {
                        "href": "http://localhost:8080/api/tickets/bce53022-3dd1-4b8a-8b9e-c41daff22a63"
                    },
                    "pricecat": {
                        "href": "http://localhost:8080/api/tickets/bce53022-3dd1-4b8a-8b9e-c41daff22a63/pricecat"
                    },
                    "ordr": {
                        "href": "http://localhost:8080/api/tickets/bce53022-3dd1-4b8a-8b9e-c41daff22a63/ordr"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/tickets"
        },
        "profile": {
            "href": "http://localhost:8080/api/profile/tickets"
        },
        "search": {
            "href": "http://localhost:8080/api/tickets/search"
        }
    }
}
```
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:**
```
    {  
      "timestamp": "2020-10-07T09:36:06.458+00:00",  
      "status": 404,  
      "error": "Not Found",  
      "message": "No message available",  
      "path": "/api/tickets/"  
    }
```
  
**Sample Call:**

  Postman: `GET` http://localhost:8080/api/tickets/

* **Muistiinpanoja:**
  
  -


**Näytä yksittäinen lipun**

Näyttää yksittäisen lipun tiedot listasta.


* **URL**

  /api/tickets/uuid/{id}

* **Metodi:**
  
  `GET`
  
*  **URL-parametrit**

   **Pakolliset:**
 
   id=[UUID]

   **Valinnaiset:**
 
   Ei ole

* **Dataparametrit**

   Ei ole

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK   
    **Sisältö:**
```
{
   "ticketid":"4bd85c30-f052-4f44-afe1-6de75866c1e1",
   "usedat":"2020-11-07T21:44:13.484638",
   "unitprice":15.0,
   "pricecat":{
      "price_cat_id":9,
      "price_cat_name":"Eläkeläinen",
      "price":15,
      "event":{
         "id":4,
         "event_name":"Tapsan tanssit",
         "starts_at":"2020-12-26T12:00:00.000+00:00",
         "ends_at":"2020-12-26T18:00:00.000+00:00",
         "capacity":1000,
         "organizer":{
            "organizer_id":2,
            "organizer_name":"Keikka kekkonen Oy"
         },
         "location":{
            "location_id":2,
            "locationname":"Nosturi",
            "locationaddress":"Telakkakatu 8"
         }
      }
   },
   "ordr":{
      "ordr_id":2,
      "user":{
         "user_id":3,
         "password":"salainen",
         "firstname":"Matti",
         "lastname":"Meikäläinen",
         "role":"ADMIN"
      },
      "sold":"2020-10-10T00:00:00.000+00:00"
   }
}
```
 
* **Virheellinen vastaus:**

  * **Status:** 404 Not Found   
    **Sisältö:** 

* **Sample Call:**

  Postman: `GET` http://localhost:8080/api/tickets/{id}

* **Muistiinpanoja:**
  
  -



**Luo Lipun**
----
Luo uuden lipun.

* **URL**

/api/tickets/

* **Metodi**

`POST`

  * **Dataparametrit**
```
{
{
    "unitprice": 10,
    "ordr": "http://localhost:8080/api/ordrs/6",
    "pricecat": "http://localhost:8080/api/priceCats/5"
}
}
```
  * **Onnistunut vastaus:**
    * **Status:** 200 OK tai 201 Created
    * **Sisältö:**
```
{
    "unitprice": 10.0,
    "usedat": null,
    "ticket_id": "2e869898-f2f1-48bb-ba19-348909486c85",
    "_links": {
        "self": {
            "href": "http://localhost:8080/api/tickets/2e869898-f2f1-48bb-ba19-348909486c85"
        },
        "ticket": {
            "href": "http://localhost:8080/api/tickets/2e869898-f2f1-48bb-ba19-348909486c85"
        },
        "pricecat": {
            "href": "http://localhost:8080/api/tickets/2e869898-f2f1-48bb-ba19-348909486c85/pricecat"
        },
        "ordr": {
            "href": "http://localhost:8080/api/tickets/2e869898-f2f1-48bb-ba19-348909486c85/ordr"
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
        "message": "Unexpected character ('}' (code 125)): was expecting double-quote to start field name\n at [Source: (org.apache.catalina.connector.CoyoteInputStream); line: 5, column: 2]"
    },
    "message": "JSON parse error: Unexpected character ('}' (code 125)): was expecting double-quote to start field name; nested exception is com.fasterxml.jackson.core.JsonParseException: Unexpected character ('}' (code 125)): was expecting double-quote to start field name\n at [Source: (org.apache.catalina.connector.CoyoteInputStream); line: 5, column: 2]"
}
```



* **Lipun merkkaaminen käytetyksi:**

Postman `PATCH` http://localhost:8080/api/tickets/useticket/{id}

* **Onnistunut vastaus:**
  
  * **Status:** 200 OK   
    **Sisältö:**

{
   "ticketid":"65aaefc0-c4cc-4124-9026-e931258ea3ac",
   "usedat":"2020-11-07T21:54:54.213755",
   "unitprice":50.0,
   "pricecat":{
      "price_cat_id":9,
      "price_cat_name":"Eläkeläinen",
      "price":15,
      "event":{
         "id":4,
         "event_name":"Tapsan tanssit",
         "starts_at":"2020-12-26T12:00:00.000+00:00",
         "ends_at":"2020-12-26T18:00:00.000+00:00",
         "capacity":1000,
         "organizer":{
            "organizer_id":2,
            "organizer_name":"Keikka kekkonen Oy"
         },
         "location":{
            "location_id":2,
            "locationname":"Nosturi",
            "locationaddress":"Telakkakatu 8"
         }
      }
   },
   "ordr":{
      "ordr_id":2,
      "user":{
         "user_id":3,
         "password":"salainen",
         "firstname":"Matti",
         "lastname":"Meikäläinen",
         "role":"ADMIN"
      },
      "sold":"2020-10-10T00:00:00.000+00:00"
   }
}
```


