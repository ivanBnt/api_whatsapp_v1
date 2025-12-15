<h1 align="center"> whatsapp-api-nodejs-baileys Multi Dispositivo</h1>


Una implementación de Baileys como un servicio API RESTful simple con soporte para múltiples dispositivos

# paquetes utilizados

-   [Baileys](https://github.com/WhiskeySockets/Baileys)
-   [Express](https://github.com/expressjs/express)

# Instalación

1. Descargue o clone este repositorio.
2. Ingrese al directorio del proyecto.
3. Ejecute `npm install` para instalar las dependencias.
4. Copie `.env.example` a `.env` y configure las variables de entorno.

# Docker Compose

1. Siga el procedimiento de [Instalación](#installation).
2. Actualice `.env` y configure

```
MONGODB_ENABLED=true
MONGODB_URL=mongodb://mongodb:27017/whatsapp_api
```

3. Establezca su `TOKEN=` en una cadena aleatoria.
4. Ejecute

```
docker-compose up -d
```

# Configuración

Editar variables de entorno en `.env`

```a
Importante: debe configurar TOKEN= en una cadena aleatoria para proteger la ruta.
```

```env
# ==================================
# CONFIGURACIÓN DE SEGURIDAD
# ==================================
TOKEN=RANDOM_STRING_HERE
```

# Uso

1. `DESARROLLO:` Ejecutar `npm run dev`
2. `PRODUCCIÓN:` Ejecutar `npm start`

## Generar una instancia básica utilizando una clave aleatoria.

Para generar una clave de instancia
Utilizando la ruta:

```bash
curl --location --request GET 'localhost:3000/instance/init' \
--data-raw ''
```

Response:

```json
{
    "error": false,
    "message": "Initializing successfull",
    "key": "d7e2abff-3ac8-44a9-a738-1b28e0fca8a5"
}
```

## WEBHOOK_ALLOWED_EVENTS

Puede configurar qué eventos desea enviar al webhook configurando la variable de entorno `WEBHOOK_ALLOWED_EVENTS`

Establezca una lista separada por comas de eventos sobre los que desea recibir notificaciones.

El valor predeterminado es `all`, que reenviará todos los eventos.

Valores permitidos:

- `connection` - recibe todos los eventos de conexión
- `connection:open` - recibe eventos de conexión abierta
- `connection:close` - recibe eventos de conexión cerrada
- `presense` - recibe eventos de presencia
- `messages` - recibe todos los eventos de mensajes
- `call` - recibe todos los eventos relacionados con llamadas
- `call:terminate` - recibe eventos de finalización de llamadas
- `call:offer` - recibe eventos de finalización de llamadas
- `groups` - recibe todos los eventos relacionados con grupos
- `group_participants` - recibe todos los eventos relacionados con participantes de grupos

También puede utilizar el ejemplo de formato de evento Baileys: `messages.upsert`

## Generar instancia personalizada con clave personalizada y webhook personalizado.

Para generar una instancia personalizada
Utilizando la ruta:

```bash
curl --location --request GET 'localhost:3000/instance/init?key=CUSTOM_INSTANCE_KEY_HERE&webhook=true&webhookUrl=https://webhook.site/d7114704-97f6-4562-9a47-dcf66b07266d' \
--data-raw ''
```

Response:

```json
{
    "error": false,
    "message": "Initializing successfull",
    "key": "CUSTOM_INSTANCE_KEY_HERE"
}
```

# Uso de la clave

Guarde el valor de la clave de la respuesta. Luego, use este valor para llamar a todas las rutas.

## Documentación de Postman


## QR Code

Visit [http://localhost:3000/instance/qr?key=INSTANCE_KEY_HERE](http://localhost:3000/instance/qr?key=INSTANCE_KEY_HERE) para ver el código QR y escanearlo con tu dispositivo. Si tardas demasiado en escanear el código QR, tendrás que actualizar la página.

## Send Message

```sh
# /message/text?key=INSTANCE_KEY_HERE&id=PHONE-NUMBER-WITH-COUNTRY-CODE&message=MESSAGE

curl --location --request POST 'localhost:3000/message/text?key=INSTANCE_KEY_HERE' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'id=919999999999' \
--data-urlencode 'message=Hello World'
```

# Nota

No puedo garantizarlo ni puedo responsabilizarme si te bloquean o te prohíben usar este software. WhatsApp no ​​permite que los bots utilicen métodos no oficiales en su plataforma, por lo que no debería considerarse totalmente seguro.
# Legal

- Este código no está afiliado, autorizado, mantenido, patrocinado ni respaldado de ninguna manera por WA (WhatsApp) ni por ninguna de sus filiales o subsidiarias.
- El sitio web oficial de WhatsApp se puede encontrar en https://whatsapp.com. "WhatsApp", así como los nombres, marcas, emblemas e imágenes relacionados son marcas registradas de sus respectivos propietarios.
- Este es un software independiente y no oficial. Úselo bajo su propio riesgo.
- No envíe spam a las personas con esto.
