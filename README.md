# Airline-Booking
# ✈️ Airline Booking Microservices System

A distributed backend system for managing flight search, bookings, and notifications using a microservices architecture.

Built with Node.js, Express, MySQL, and RabbitMQ (AWS-ready).

---

## 🔗 Services & Repositories

| Service | Description | Link |
|--------|-------------|------|
| API Gateway | Central routing, request handling, auth proxy | https://github.com/dhiman31/API_Gateway |
| Auth Service | User authentication, JWT handling | https://github.com/dhiman31/Auth_Service |
| Flight Service | Flight data, search, filters | https://github.com/dhiman31/Flights-And-Search-Service |
| Booking Service | Booking flow & transactions | https://github.com/dhiman31/Booking_Service |
| Reminder Service | Email notifications & scheduling | https://github.com/dhiman31/Reminder_Service |

---

## 📌 Overview

This project demonstrates a real-world airline booking backend where features are split into independent services.

It supports:
- Flight search  
- Ticket booking  
- Seat management  
- Email notifications & reminders  

Uses REST APIs + RabbitMQ for async communication.

---

## ✨ Features

### User Features
- Search flights with filters  
- Real-time seat availability  
- Secure authentication (JWT)  
- Booking confirmation emails  
- Automated reminders  

### Technical Features
- API Gateway (single entry point)  
- Event-driven architecture (RabbitMQ)  
- Background jobs (cron)  
- Scalable cloud-ready design  

---

## 🏗️ Tech Stack

- Backend: Node.js, Express  
- Database: MySQL (Sequelize)  
- Messaging: RabbitMQ  
- Email/Jobs: Nodemailer, Node-Cron  
- Cloud: AWS (EC2, RDS, Load Balancer)  

---

## 🔄 System Flow

1. Search → Gateway → Flight Service  
2. Booking → Gateway → Booking → Flight Service → DB  
3. Notification → Booking → Queue → Reminder → Email  

---

## 🚀 Run Locally

### Requirements
- Node.js  
- MySQL  
- RabbitMQ  

### Setup

```bash
npm install
npx sequelize db:migrate
npm start