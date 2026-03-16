# Fintech Micro-Ecosystem

### Microservices Architecture with Java & Spring Boot

Proyecto backend basado en **arquitectura de microservicios** inspirado en plataformas fintech modernas como Revolut.

El objetivo es construir un **ecosistema backend desacoplado** capaz de gestionar:

* autenticación de usuarios
* balances de wallets
* transferencias entre usuarios
* consulta de precios de criptomonedas mediante APIs externas

Este proyecto está pensado como **entrenamiento previo a prácticas en una consultora**, aplicando prácticas de ingeniería reales utilizadas en entornos fintech.

---

# Project Goals

El proyecto busca demostrar competencias en:

* **Arquitectura de microservicios**
* **Autenticación segura con JWT**
* **Diseño de APIs REST**
* **Integración con APIs externas**
* **Contenerización con Docker**
* **Buenas prácticas de ingeniería backend**
* **Testing e integración continua**

El sistema simula una **infraestructura fintech simplificada**.

---

# Architecture Overview

Sistema compuesto por varios servicios independientes que se comunican mediante HTTP APIs.

```
                +------------------+
                |    Frontend      |
                |  (React/Next.js) |
                +--------+---------+
                         |
                         v
                +------------------+
                |   Auth Service   |
                | Spring Security  |
                |       JWT        |
                +--------+---------+
                         |
                         v
         +---------------+---------------+
         |                               |
         v                               v
+------------------+           +------------------+
|  Wallet Service  |           | Crypto Proxy     |
| User balances    |           | CoinGecko API    |
| Database storage |           | Price caching    |
+--------+---------+           +---------+--------+
         |
         v
+------------------+
| Transactions     |
| Transfer logic   |
+------------------+
```

Principios utilizados:

* **Service isolation**
* **Single responsibility**
* **Stateless authentication**
* **External API abstraction**

---

# Microservices

## Auth Service

Servicio responsable de **gestionar autenticación e identidad de usuarios**.

### Features

* Registro de usuario
* Login
* Generación de tokens JWT
* Configuración de seguridad con Spring Security
* Autenticación stateless

### Tech Stack

* Java
* Spring Boot
* Spring Security
* JWT

### Example Endpoints

```
POST /auth/register
POST /auth/login
```

---

## Wallet Service

Gestiona los **balances de usuario y operaciones de wallet**.

### Features

* Entidad Wallet
* Persistencia de balances
* Simulación de depósitos
* Consulta de balances
* Validación JWT para acceso seguro

### Wallet Schema Example

```
Wallet
------
id
userId
balance
currency
createdAt
```

### Example Endpoints

```
GET /wallet/balance
POST /wallet/deposit
```

---

## Transactions Service

Simula **transferencias de dinero entre usuarios**.

### Features

* Transferencias entre wallets
* Validación de balance
* Historial de transacciones
* Operaciones atómicas

### Example Endpoints

```
POST /transactions/transfer
GET /transactions/history
```

### Transaction Schema Example

```
Transaction
-----------
id
senderId
receiverId
amount
timestamp
status
```

---

## Crypto Proxy Service

Servicio encargado de consumir precios de criptomonedas desde APIs externas como:

* CoinGecko

### Purpose

* Evitar llamadas directas desde frontend
* Abstraer APIs externas
* Añadir capa de caché
* Controlar rate limiting

### Example Endpoint

```
GET /crypto/prices
```

### Example Response

```
{
  "bitcoin": 65000,
  "ethereum": 3200
}
```

---

# Tech Stack

## Backend

* Java
* Spring Boot
* Spring Security
* JWT
* REST APIs
* OpenAPI / Swagger

## Frontend (opcional)

* React
* Next.js
* TailwindCSS

## Infrastructure

* Docker
* Docker Compose

## Testing

* JUnit
* Mockito
* Integration Tests

---

# Database Options (Recommended Order)

Dependiendo del tipo de arquitectura, estas bases de datos serían adecuadas:

### 1️⃣ PostgreSQL (Recomendado)

La opción más utilizada en fintech modernas.

Ventajas:

* Alta consistencia
* Transacciones ACID
* Excelente soporte para sistemas financieros
* Muy buen rendimiento con Spring Boot

Ideal para:

* wallets
* transacciones
* usuarios

---

### 2️⃣ MariaDB / MySQL

Muy estable y ampliamente utilizada.

Ventajas:

* Fácil de usar
* Muy buena integración con Java
* Buena documentación

Es una buena opción si ya se utiliza en el entorno académico.

---

### 3️⃣ MongoDB

Base de datos NoSQL orientada a documentos.

Ventajas:

* Flexible
* Ideal para datos no estructurados
* Escalabilidad horizontal

Uso recomendado en este proyecto:

* almacenar caché de precios crypto
* logs o datos analíticos

---

# Development Roadmap

## Sprint 1 — Auth Service

Objetivo: implementar autenticación.

Tasks:

* Configurar Spring Security
* Implementar JWT
* Crear endpoints register/login
* Crear tests básicos

---

## Sprint 2 — Wallet Service

Objetivo: persistencia de wallets.

Tasks:

* Crear entidad Wallet
* Implementar endpoints de balance
* Seguridad con JWT
* Validar ownership del usuario

---

## Sprint 3 — Crypto Service

Objetivo: integración con API externa.

Tasks:

* Cliente para CoinGecko
* Implementar caching
* Endpoint de precios
* Simulación de compra de crypto

---

## Sprint 4 — Transactions Service

Objetivo: transferencias entre usuarios.

Tasks:

* Transferencias
* Validación de balances
* Historial de transacciones
* Operaciones atómicas

---

## Sprint 5 — DevOps & Quality

Objetivo: entorno más cercano a producción.

Tasks:

* Dockerizar servicios
* docker-compose
* Tests de integración
* Documentación OpenAPI
* Logging estructurado

---

# Running the Project

Clonar repositorio:

```
git clone https://github.com/yourusername/fintech-micro-ecosystem.git
cd fintech-micro-ecosystem
```

Ejecutar con Docker:

```
docker-compose up --build
```

Servicios que se levantarán:

* Auth Service
* Wallet Service
* Transactions Service
* Crypto Proxy
* Database

---

# API Documentation

Swagger disponible en:

```
http://localhost:8080/swagger-ui.html
```

---

# Suggested Repository Structure

Un enfoque profesional sería:

```
fintech-micro-ecosystem
│
├── auth-service
│   ├── src
│   └── Dockerfile
│
├── wallet-service
│   ├── src
│   └── Dockerfile
│
├── transaction-service
│   ├── src
│   └── Dockerfile
│
├── crypto-proxy-service
│   ├── src
│   └── Dockerfile
│
├── docker-compose.yml
├── README.md
└── docs
```

---

# Learning Outcomes

Este proyecto demuestra:

* arquitectura de microservicios
* diseño de APIs seguras
* integración con APIs externas
* separación de responsabilidades
* infraestructura dockerizada

Son exactamente las habilidades utilizadas en **backend fintech modernos**.

---

# Future Improvements

Posibles extensiones avanzadas:

* API Gateway (Spring Cloud Gateway)
* Service discovery
* Event-driven architecture con Kafka
* Deployment en Kubernetes
* Rate limiting
* Monitoring con Prometheus y Grafana
* CI/CD pipeline

---

# License

MIT License

---
