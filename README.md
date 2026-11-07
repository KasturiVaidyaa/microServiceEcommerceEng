# Microservices E-Commerce Application

A full-stack e-commerce application built using a microservices architecture. The project uses independent backend services, Apache Kafka for event-driven communication, MongoDB for data storage, and a Next.js frontend.

## Tech Stack

**Frontend**
- Next.js
- React
- Tailwind CSS
- Zustand

**Backend**
- Node.js
- Express.js
- MongoDB
- Mongoose
- Apache Kafka
- KafkaJS

**Integrations and Tools**
- Docker and Docker Compose
- Stripe for payment integration
- Resend for email services
- Kafka UI for monitoring Kafka

## Project Structure

```text
microServiceEcommerceEng/
│
├── analytic-service/
├── cart-service/
├── email-service/
├── order-service/
├── payment-service/
├── product-service/
│
├── frontend/
│
├── docker-compose.yml
├── package.json
├── package-lock.json
└── .gitignore
```

## Prerequisites

Install the following before running the project:

- Node.js and npm
- Docker Desktop
- Git

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/KasturiVaidyaa/microServiceEcommerceEng.git
cd microServiceEcommerceEng
```

### 2. Install dependencies

Install the root dependencies:

```bash
npm install
```

Install backend dependencies:

```bash
cd analytic-service
npm install
cd ../cart-service
npm install
cd ../email-service
npm install
cd ../order-service
npm install
cd ../payment-service
npm install
cd ../product-service
npm install
```

Install frontend dependencies:

```bash
cd ../frontend
npm install
cd ..
```

### 3. Configure environment variables

Create a `.env` file in each backend service directory by copying its `.env.example` file.

Example for PowerShell:

```powershell
Copy-Item analytic-service/.env.example analytic-service/.env
Copy-Item cart-service/.env.example cart-service/.env
Copy-Item email-service/.env.example email-service/.env
Copy-Item order-service/.env.example order-service/.env
Copy-Item payment-service/.env.example payment-service/.env
Copy-Item product-service/.env.example product-service/.env
```

Update the environment variables with your local configuration and valid API credentials where required.

**Environment variables used:**

| Service | Variables |
|---|---|
| Analytics | `MONGO_URI` |
| Cart | `MONGO_URI` |
| Email | `MONGO_URI`, `RESEND_API_KEY` |
| Order | `MONGO_URI` |
| Payment | `MONGO_URI`, `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET`, `FRONTEND_URL`, `ORDER_SERVICE_URL` |
| Product | `MONGO_URI` |

Never commit actual `.env` files or API keys to GitHub.

### 4. Start Docker services

From the project root, run:

```bash
docker compose up -d
```

This starts the infrastructure services:

- Three Kafka brokers
- Kafka UI
- MongoDB

To check running containers:

```bash
docker ps
```

To stop the containers:

```bash
docker compose down
```

### 5. Start the backend services

Open a separate terminal for each service.

**Analytics Service**

```bash
cd analytic-service
node index.js
```

**Cart Service**

```bash
cd cart-service
node index.js
```

**Email Service**

```bash
cd email-service
node index.js
```

**Order Service**

```bash
cd order-service
node index.js
```

**Payment Service**

```bash
cd payment-service
node index.js
```

**Product Service**

```bash
cd product-service
node index.js
```

### 6. Start the frontend

Open another terminal:

```bash
cd frontend
npm run dev
```

Open the application at:

http://localhost:3000

## Local Development URLs

| Component | URL |
|---|---|
| Frontend | http://localhost:3000 |
| Kafka UI | http://localhost:8080 |
| MongoDB | mongodb://localhost:27017 |
| Kafka Broker 1 | localhost:9092 |
| Kafka Broker 2 | localhost:9094 |
| Kafka Broker 3 | localhost:9095 |

## Important Notes

- Start Docker infrastructure before starting the backend services.
- Make sure MongoDB and Kafka are running before launching services that depend on them.
- Configure valid Stripe and Resend credentials to use their respective integrations.
- Each backend service has its own environment configuration.
- The actual `.env` files are excluded from version control.

## License

Refer to the original repository for license information.