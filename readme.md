# Primer Parcial 2023 Arquitectura Orientada a Servicios

## Descripción 

Servicio de API REST del primer parcial de la asignatura Arquitectura orientada a servicios (SOA), desarrollado con Node.js , Express y Postgresql.

Esta API permite obtener y almacenar información de productos varios, siempre y cuando el usuario este autenticado, registrando en una base de datos de posgrest. La API cuenta con las siguientes funciones: 

- Autorización median Basic Auth
- Paginación 
- Validación de parametros de entrada
- Manejador de errores


## Instalación

### Clonar el repositorio:
```
    git clone https://github.com/bluemaster23/clase.git
    cd clase
```

### Instalación Manual

```
    npm install
```

## Tabla de contenido

- [Caracteristicas](#Caracteristicas)
- [Comandos](#Comandos)
- [Variables de Entorno](#Variables-de-Entorno)
- [Estructura del Proyecto](#Estructura-del-Proyecto)
- [API Endpoints](#API-Endpoints)


## Característica
- Node js
- NPM

## Comandos
Run Local:
```
    npm run dev
```
Run Producción:
```
    npm run start
```

## Variables de Entorno
```
###> CONFIG SERVER <####
PORT=3100
URL_SERVER=http:\\127.0.0.1:3100\
###> CONFIG SERVER <####

###> DB_CONNECTION ### 
DB_URL_PG=postgres://postgres:1234@localhost:5432/prueba
###< CONFIGURE SERVER ###

###> SECRET_KEY ###
SECRET_KEY=passwordBasico203-*210ss3
###< SECRET_KEY ###
```

## Estructura del Proyecto

```
src\
 |--config\         # Variables de entorno y configuración 
 |--controllers\    # Controladores 
 |--img\            # Imagenes públicas
 |--middlewares\    # Middleware Personalizados
 |--models\         # Postgrest models (data layer) 
 |--routes\         # Rutas del sistema
 |--services\       # Servicios de conexión BD y Token 
 |--validator\      # Esquemas de validación
 |--index.js        # Express app
```


## API Endpoints

<code>GET /auth</code> 
- **query:** 
    - **username**:  requerido
    - **password**:  requerido

<code>GET /api/producto</code> 
- Request
    - **query**
        - **page**
        - **limit**
- Response
    - **success:** boolean   
    - **msg :** string
    - **count:** number
    - **page :** number
    - **all :** number
    - **data :** array
 
<code>GET /api/producto/:id</code> 
- Request
    - **params:**
        - **id**:  requerido
- Response
    - **success :** boolean
    - **msg :** string
    - **data :** json
    
<code>POST /api/producto</code>
- Request
    - **body:**
        - **nombre** :  requerido
        - **detalle**
        - **valor** :  requerido
        - **img**
- Response
    - **success :** boolean
    - **data :** json
    - **msg :** string 

<code>PUT /api/producto</code>
- Request
    - **body**
        - **id** :  requerido
        - **nombre**
        - **detalle**
        - **valor**
        - **img**
- Response
    - **success :** boolean
    - **data :** json
    - **msg :** string 
    
<code>DELETE /api/producto/:id</code> 
- Request
    - **params:**
        - **id** : requerido 
    - **success :** boolean
- Response
    - **data :** array
    - **msg :** string 