# espocrm
Centrar Logo en Login

Problema
El logo de la empresa no aparece centrado en la página de login de EspoCRM con el tema Espo.

Solución
Se implementó CSS personalizado usando el sistema de archivos de EspoCRM.

Archivos necesarios

1. CSS personalizado:
client/custom/css/custom.css
css/* Centrar y agrandar el logo en la página de login */
#login .logo-container {
    text-align: center;
    margin: 0 auto;
    width: 100%;
    height: auto; /* Permite que crezca */
}
#login .logo-container img.logo {
    display: block;
    margin: 0 auto;
    max-width: 250px; /* Aumenta el ancho máximo */
    height: auto;
    width: auto;
}
/* Ajustes para dispositivos móviles */
@media (max-width: 768px) {
    #login .logo-container {
        text-align: center;
    }
    #login .logo-container img.logo {
        max-width: 200px; /* Más pequeño en móviles */
    }
}

2. Configuración para cargar el CSS:
custom/Espo/Custom/Resources/metadata/app/client.json
json{
    "cssList": [
        "__APPEND__",
        "client/custom/css/custom.css"
    ],
    "favicon": "client/custom/img/favicon.ico",
    "favicon196": "client/custom/img/favicon-196.png"
}
Pasos de implementación

Crear directorio CSS personalizado:

mkdir -p client/custom/css/

# Crear archivo CSS:

nano client/custom/css/custom.css

# Crear directorio de configuración:

bashmkdir -p custom/Espo/Custom/Resources/metadata/app/

# Crear archivo de configuración:

nano custom/Espo/Custom/Resources/metadata/app/client.json

# Establecer permisos correctos:

bashchown -R usuario:usuario client/custom/
chown -R usuario:usuario custom/Espo/

# Limpiar caché:

Desde admin: Administración → Limpiar Caché
Desde SSH: rm -rf data/cache/*

# Verificación
Para verificar que la configuración está activa:

# Ver archivos CSS personalizados
ls -la client/custom/css/

# Ver configuración JSON
cat custom/Espo/Custom/Resources/metadata/app/client.json
Notas

El logo se centra usando selectores específicos #login .logo-container
Se incluye responsive design para móviles
El tamaño máximo es 250px en desktop, 200px en móviles
