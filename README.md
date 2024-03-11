# Actualización de Mensajes en Discord con Webhooks

Para empezar crea un nuevo proyecto en PyCharm y abre un archivo Python.

## Instalación de la librería discord-webhook:
Abre la terminal o consola.
Ejecuta el siguiente comando para instalar la librería:

```
pip install discord-webhook
```

## Creación de un Webhook en Discord:
En tu servidor de Discord, haz clic en la rueda de configuración y selecciona “Interacciones”.

Si no tienes un webhook, crea uno y copia el enlace proporcionado.

```
##Código Python:
Copia el siguiente código en tu archivo Python:

#importamos las librerias necesarias
from discord_webhook import DiscordWebhook, DiscordEmbed
import json
import requests

#Creamos el webhook y el embed, sustituyendo el enlace al webhook por el que hayamos creado en Discord
webhook = DiscordWebhook(url="enlace al webhook")

#Creamos el embed
embed = DiscordEmbed(
	# titulo, descripcion y color del embed
	title="Taco Love",
	description="Tu taquito ya está!",
	color="03b2f8")

#Añadimos la imagen del taco al mensaje
embed.set_image(url="https://cdn.dribbble.com/users/545781/screenshots/3157610/happy-taco.jpg")
#Añadimos el embed al webhook
webhook.add_embed(embed)
#Ejecutamos el webhook, enviando el mensaje a Discord
webhook.execute()

def lambda_handler(event, context):
	# TODO implement
	return {
    	'statusCode': 200,
    	'body': json.dumps('Hello from Discord Lambda!')
	}
```

## Crea un webhook 

Lo puedes crear en Discord accediendo a un canal de audio en la tuerca, dirigiendote a Integraciones y agregando nuevo Webhook, ahi podras copiar el link que necesitaras pegar en:

```
#Creamos el webhook y el embed, sustituyendo el enlace al webhook por el que hayamos creado en Discord
webhook = DiscordWebhook(url="enlace al webhook")
```

## Configuración en AWS Lambda:
Crea una función en AWS Lambda (asegúrate de que sea en Python).
Añade una capa que incluya la librería discord-webhook.
Copia y pega el código en la función.
Ejecución:
Lanza la función en AWS Lambda.
Verifica que no haya errores en los registros.
El mensaje debería aparecer en el canal de Discord especificado por el webhook.

## Configuración de AWS Lambda para Ejecutar el Script
Inicia sesión en la Consola de Administración de AWS

Busca y selecciona “Lambda” en la barra de búsqueda o encuentra el servicio en la lista de servicios.

Haz clic en el botón “Crear función”.

Selecciona “Python 3.12” o una versión posterior.

Crea un nuevo rol o selecciona uno existente que tenga permisos para acceder a los recursos de AWS necesarios (como S3, DynamoDB, etc.).

Puedes escribir directamente el código en el editor de la consola.

Después de crear la función, ve a la pestaña “Pruebas”.
Crea un evento de prueba (por ejemplo, “test”) y guárdalo.

Necesitas agregar dependencias adicionales (como la librería discord-webhook), puedes adjuntar la carpeta del discord comprimida.
Guarda los cambios y ejecuta tu función para verificar que se ejecute correctamente.