# Fintech Micro-Ecosystem

### Microservices Architecture with Java & Spring Boot ☕

Backend system inspirado en arquitecturas fintech modernas, diseñado como un **ecosistema de microservicios desacoplados**.

El sistema permite gestionar:

- Autenticación de usuarios
- Wallets y balances
- Transferencias entre usuarios
- Consulta de precios de criptomonedas mediante APIs externas

---

## 🚀 Why This Project?

Este proyecto no es solo funcional, sino **intencionalmente diseñado para demostrar criterio de ingeniería backend**, incluyendo:

- Diseño de sistemas distribuidos
- Seguridad stateless con JWT
- Separación de responsabilidades
- Integración con servicios externos
- Preparación para entornos productivos (Docker, testing, etc.)

---

## 🧠 Architecture Overview

Arquitectura basada en microservicios independientes comunicándose vía HTTP.

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
| User balances    |           | External APIs    |
| Database storage |           | Caching layer    |
+--------+---------+           +---------+--------+
|
v
+------------------+
| Transactions     |
| Transfer logic   |
+------------------+

````

---

### Design Principles

- Service Isolation
- Single Responsibility Principle (SRP)
- Stateless Authentication
- External API Abstraction

---

## 🧩 Microservices Breakdown

### 🔐 Auth Service

Gestiona identidad y autenticación.

**Responsabilidades:**
- Registro y login
- Generación de JWT
- Configuración de seguridad

**Endpoints:**

```
POST /auth/register
POST /auth/login

```

---

### 💰 Wallet Service

Gestiona balances de usuario.

**Responsabilidades:**
- Persistencia de wallets
- Consulta de balances
- Operaciones básicas (deposit)

**Modelo:**

```
Wallet

* id
* userId
* balance
* currency
* createdAt
```

**Endpoints:**

```

GET /wallet/balance
POST /wallet/deposit
```

---

### 🔄 Transactions Service

Gestiona transferencias entre usuarios.

**Responsabilidades:**
- Transferencias seguras
- Validación de saldo
- Historial de transacciones

**Modelo:**

```
Transaction

* id
* senderId
* receiverId
* amount
* timestamp
* status
```

**Endpoints:**

```
POST /transactions/transfer
GET /transactions/history
```

---

### ₿ Crypto Proxy Service

Abstracción de APIs externas (ej: CoinGecko).

**Responsabilidades:**
- Fetch de precios
- Caching
- Rate limiting
- Evitar exposición directa desde frontend

**Endpoint:**

```
GET /crypto/prices
````

---

## 🛠️ Tech Stack

### Backend
- Java
- Spring Boot
- Spring Security
- JWT
- REST APIs
- OpenAPI / Swagger

### Infrastructure
- Docker
- Docker Compose

### Testing
- JUnit
- Mockito
- Integration Tests

### Frontend (optional)
- React / Next.js

---

## 🗄️ Database Strategy

### PostgreSQL (Recommended)
- ACID compliance
- Ideal para transacciones financieras

### MySQL / MariaDB
- Alternativa estable y sencilla

### MongoDB (Optional Use)
- Cache de precios crypto
- Logs / analytics

---

## 🧭 Development Roadmap

### Sprint 1 — Auth
- JWT + Spring Security
- Register/Login
- Tests básicos

### Sprint 2 — Wallet
- Modelo Wallet
- Persistencia
- Seguridad con JWT

### Sprint 3 — Crypto
- Integración CoinGecko
- Caching
- Endpoint de precios

### Sprint 4 — Transactions
- Transferencias
- Validaciones
- Atomicidad

### Sprint 5 — DevOps
- Dockerización
- docker-compose
- Tests de integración
- Logging + OpenAPI

---

## ▶️ Running the Project

```bash
git clone https://github.com/yourusername/fintech-micro-ecosystem.git
cd fintech-micro-ecosystem
docker-compose up --build
````

Servicios incluidos:

* Auth Service
* Wallet Service
* Transactions Service
* Crypto Proxy
* Database

---

## 📄 API Documentation

Disponible en:

```
http://localhost:8080/swagger-ui.html
```

---

## 📁 Project Structure

```
fintech-micro-ecosystem
│
├── auth-service
├── wallet-service
├── transaction-service
├── crypto-proxy-service
│
├── docker-compose.yml
├── README.md
└── docs
```

---

## 🎯 Learning Outcomes

Este proyecto demuestra:

* Diseño de microservicios
* APIs seguras con JWT
* Integración externa
* Arquitectura desacoplada
* Preparación para producción

---

## 🔮 Future Improvements

* API Gateway (Spring Cloud Gateway)
* Service Discovery
* Event-driven architecture (Kafka)
* Kubernetes deployment
* Rate limiting
* Observabilidad (Prometheus + Grafana)
* CI/CD

---

## 📜 License

MIT

