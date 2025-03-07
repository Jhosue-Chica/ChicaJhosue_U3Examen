# Sistema de Gestión de Reservas de Eventos

Sistema basado en microservicios para la gestión de eventos y reservas, desarrollado con Node.js, Express, PostgreSQL y Sequelize.

## Características

- Gestión completa de eventos: creación, consulta, actualización y eliminación.
- Sistema de reservas por usuario y evento.
- Validación de disponibilidad de tickets.
- Arquitectura limpia con separación de responsabilidades.
- API RESTful documentada con Swagger.
- Base de datos PostgreSQL con Sequelize ORM.

## Estructura del Proyecto

El proyecto sigue los principios de arquitectura limpia:

```
.
├── config/               # Configuraciones
├── controllers/          # Controladores
├── middlewares/          # Middlewares
├── migrations/           # Migraciones de Sequelize
├── models/               # Modelos
├── routes/               # Rutas
├── seeders/              # Datos de prueba
├── services/             # Servicios
├── .env                  # Variables de entorno
├── docker-compose.yml    # Configuración de Docker
├── index.js              # Punto de entrada
└── package.json          # Dependencias
```

## Requisitos Previos

- Node.js v14 o superior
- PostgreSQL v12 o superior
- Docker (opcional)

## Instalación

### Opción 1: Instalación Local

1. Clonar el repositorio:
```bash
git clone https://github.com/tu-usuario/event-booking-system.git
cd event-booking-system
```

2. Instalar dependencias:
```bash
npm install
```

3. Configurar variables de entorno:
```bash
cp .env.example .env
# Editar .env con los datos de conexión a la base de datos
```

4. Crear la base de datos en PostgreSQL:
```sql
CREATE DATABASE event_booking_db;
```

5. Ejecutar migraciones:
```bash
npm run migrate
```

6. Cargar datos de prueba (opcional):
```bash
npm run seed
```

7. Iniciar el servidor:
```bash
npm start
```

### Opción 2: Usando Docker

1. Clonar el repositorio:
```bash
git clone https://github.com/tu-usuario/event-booking-system.git
cd event-booking-system
```

2. Iniciar con Docker Compose:
```bash
docker-compose up
```

Este comando creará y configurará automáticamente la base de datos PostgreSQL, ejecutará las migraciones y cargará los datos de prueba.

## Uso de la API

### Documentación de la API

La documentación completa de la API está disponible en:

```
http://localhost:3000/api-docs
```

### Microservicio de Eventos (/api/events)

* **POST /api/events**: Crear un nuevo evento
* **GET /api/events**: Obtener lista de eventos
* **GET /api/events/:id**: Obtener evento por ID
* **PUT /api/events/:id**: Actualizar un evento
* **DELETE /api/events/:id**: Eliminar un evento
* **GET /api/events/:id/availability**: Verificar disponibilidad de tickets

### Microservicio de Reservas (/api/bookings)

* **POST /api/bookings**: Crear una nueva reserva
* **GET /api/bookings**: Obtener lista de reservas
* **GET /api/bookings/:id**: Obtener reserva por ID
* **GET /api/bookings/event/:eventId**: Obtener reservas de un evento específico
* **PUT /api/bookings/:id**: Actualizar una reserva
* **DELETE /api/bookings/:id**: Eliminar una reserva

## Ejemplos de Uso

### Crear un nuevo evento

```bash
curl -X POST http://localhost:3000/api/events \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Conferencia de Desarrollo Web",
    "description": "Una conferencia sobre las últimas tendencias en desarrollo web",
    "date": "2025-05-15T10:00:00Z",
    "capacity": 100
  }'
```

### Crear una reserva

```bash
curl -X POST http://localhost:3000/api/bookings \
  -H "Content-Type: application/json" \
  -d '{
    "event_id": "UUID_DEL_EVENTO",
    "user_email": "usuario@example.com",
    "num_tickets": 2
  }'
```

## Pruebas

Ejecutar pruebas unitarias:

```bash
npm test
```

## Autor

[Tu Nombre] - [Tu Email]

## Licencia

Este proyecto está licenciado bajo la Licencia ISC.
