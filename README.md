# ✈️ Airline Booking Microservices System

A scalable airline booking backend built using a **microservices architecture**.  
Handles flight search, booking, and notifications using **REST APIs + RabbitMQ**.

---

## 🔗 Services & Repositories

| Service | Responsibility | Link |
|--------|----------------|------|
| API Gateway | Routing, entry point | https://github.com/dhiman31/API_Gateway |
| Auth Service | Authentication, JWT | https://github.com/dhiman31/Auth_Service |
| Flight Service | Flight search & data | https://github.com/dhiman31/Flights-And-Search-Service |
| Booking Service | Booking & transactions | https://github.com/dhiman31/Booking_Service |
| Reminder Service | Email notifications | https://github.com/dhiman31/Reminder_Service |

---

## 📌 Overview

A real-world style system where services are independent and communicate via:
- REST APIs (synchronous)
- RabbitMQ (asynchronous)

### Flow
- Search flights  
- Book tickets  
- Validate seats  
- Send notifications  

---

## ✨ Features

- Flight search with filters  
- Real-time seat availability  
- Secure authentication (JWT)  
- Booking confirmation emails  
- Automated reminders  

---

## 🏗️ Tech Stack

- Node.js, Express  
- MySQL (Sequelize ORM)  
- RabbitMQ  
- Nodemailer, Node-Cron  
- AWS (EC2, RDS, Load Balancer)  

---

## 🔄 Workflow

1. Search → Gateway → Flight Service  
2. Booking → Gateway → Booking → Flight Service → DB  
3. Notification → Booking → Queue → Reminder → Email  

---

## 🚀 Run Locally

### Prerequisites
- Node.js  
- MySQL  
- RabbitMQ  

---

### 1. Clone Repositories

```bash
git clone https://github.com/dhiman31/API_Gateway
git clone https://github.com/dhiman31/Auth_Service
git clone https://github.com/dhiman31/Flights-And-Search-Service
git clone https://github.com/dhiman31/Booking_Service
git clone https://github.com/dhiman31/Reminder_Service
```

---

### 2. Create Databases

```sql
CREATE DATABASE auth_db;
CREATE DATABASE booking_db;
CREATE DATABASE flights_search_db;
```

---

### 3. Setup Environment Variables (.env)

#### API Gateway
```
PORT=3005
AUTH_SERVICE=http://localhost:7000
BOOKING_SERVICE=http://localhost:5000
FLIGHT_SERVICE=http://localhost:3000
```

#### Auth Service
```
PORT=7000
JWT_KEY=secret
SALT=abc123
DB_SYNC=true
```

#### Flight Service
```
PORT=3000
DB_SYNC=true
```

#### Booking Service
```
PORT=5000
DB_SYNC=true
FLIGHT_SERVICE_PATH=http://localhost:3000
USER_SERVICE_PATH=http://localhost:7000
MESSAGE_BROKER_URL=amqp://localhost
```

#### Reminder Service
```
PORT=3004
EMAIL_ID=your_email
EMAIL_PASS=your_password
MESSAGE_BROKER_URL=amqp://localhost
```

---

### 4. Install & Run (each service)

```bash
npm install
npx sequelize db:migrate
npm start
```

---

### ▶️ Startup Order

MySQL → RabbitMQ → Auth → Flight → Reminder → Booking → Gateway  

---

### 🌐 Access

http://localhost:3005

---

## ☁️ Deployment

- EC2 for services  
- RDS for MySQL  
- Load Balancer for Gateway  
- Auto Scaling enabled  

---

## 📡 Sample APIs

```bash
GET  /home
POST /flightservice/api/v1/flights
```