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

![Architecture-diagram](/assets/architecture-diagram.png)

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

### 🖥️ Backend
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=Spring-Security&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)
![REST API](https://img.shields.io/badge/REST_API-025E8C?style=for-the-badge&logo=fastapi&logoColor=white)
![Swagger](https://img.shields.io/badge/-Swagger-%23C1272D?style=for-the-badge&logo=swagger&logoColor=white)

---

### 🧪 Testing
![JUnit 5](https://img.shields.io/badge/Junit5-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![Mockito](https://img.shields.io/badge/Mockito-6DB33F?style=for-the-badge&logo=google-cloud&logoColor=white)
![Integration Tests](https://img.shields.io/badge/Integration_Tests-orange?style=for-the-badge&logo=testcafe&logoColor=white)

---

### 🐳 Infrastructure
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/docker_compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

### 🌐 Frontend (Optional)
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Next.js](https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)

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

