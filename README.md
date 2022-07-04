#Tarifa Fedex Test

   Prueba: funcion que consulta Web Service de Fedex para cotizar tarifas.



##Pre-Requisitos.

   Python 3.5 o superior



##Instalar dependencias

   pip install requests

   pip install xmltodict




##Instalar

   pip install tarifafedextest==0.3



##Ejemplo uso

###Importamos la clase CotizarTarifa

   from cotizatarifa import CotizaTarifa

   import json



###Creamos el nuevo objeto de la clase CotizarTarifa

   ct = CotizaTarifa()



###Creamos objeto json con las credenciales del cliente

   credentials = json.dumps(

    {

        "Key":"bkjIgUhxdghtLw9L",

        "Password":"6p8oOccHmDwuJZCyJs44wQ0Iw",

        "AccountNumber":"510087720",

        "MeterNumber":"119238439",

        "LanguageCode":"es",

        "LocaleCode":"mx"

    }

   )



###Creamos objeto json con la informacion de paquete a enviar

   quote_params = json.dumps({

    "address_from": {

        "zip": "64000",

        "country": "MX"

    },

    "address_to": {

        "zip": "64000",

        "country": "MX"

    },

    "parcel": {

        "length": 25.0,

        "width": 28.0,

        "height": 46.0,

        "distance_unit": "cm",

        "weight": 6.5,

        "mass_unit": "kg"

    }    

   })



###Ejecutamos la funcion get, para obtener la cotizacion

   ct.get(credentials,quote_params)



###Ejemplo de respuesta

   [

   {

      "price":"14.71",

      "currency":"USD",

      "service_level":{

         "name":"Priority Overnight",

         "token":"PRIORITY_OVERNIGHT"

      }

   },

   {

      "price":"11.34",

      "currency":"USD",

      "service_level":{

         "name":"Fedex Express Saver",

         "token":"FEDEX_EXPRESS_SAVER"

      }

   },

   {

      "price":"12.1",

      "currency":"USD",

      "service_level":{

         "name":"Standard Overnight",

         "token":"STANDARD_OVERNIGHT"

      }

   }

   ]
