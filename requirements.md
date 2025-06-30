
# Airbnb Clone - Project Documentation

This markdown file contains all backend-related documentation required for the ALX Airbnb Clone project, including features, use case diagram overview, user stories, data flow explanation, process flowcharts, and detailed technical requirements.

---

## 📁 features-and-functionalities/README.md

### Airbnb Clone - Backend Features and Functionalities

This document outlines all the backend features and functionalities required to build a scalable and robust Airbnb Clone application. The functionalities have been categorized into:

- Core Functionalities
- Technical Requirements
- Non-Functional Requirements

#### 🔑 Core Functionalities

1. **User Management**
   - User registration (guest/host)
   - Secure login (JWT, OAuth)
   - Profile management

2. **Property Listings**
   - Add, edit, and delete property listings
   - Manage availability, pricing, and amenities

3. **Search and Filtering**
   - Search by location, price, guests, and amenities
   - Pagination support for large datasets

4. **Booking Management**
   - Book properties
   - Prevent double bookings
   - Cancel bookings, view statuses

5. **Payment Integration**
   - Secure payment processing (Stripe, PayPal)
   - Host payouts
   - Multi-currency support

6. **Reviews and Ratings**
   - Guests review properties
   - Hosts respond to reviews
   - Reviews tied to completed bookings

7. **Notifications**
   - Email and in-app notifications for key events

8. **Admin Dashboard**
   - Manage users, bookings, payments, and listings

#### 🛠️ Technical Requirements

- Relational database (PostgreSQL/MySQL)
- RESTful API
- JWT-based authentication and RBAC
- Cloud file storage for images
- Integration with email services (SendGrid, Mailgun)
- Error handling and logging

#### 🚀 Non-Functional Requirements

- Modular and scalable architecture
- Security best practices
- Performance optimization (Redis caching, optimized queries)
- Testing: Unit, Integration, API testing

---

## 📁 use-case-diagram/README.md

### Airbnb Clone - Use Case Diagram

This directory contains the use case diagram for the Airbnb Clone backend project.

#### 📌 Overview

The diagram visualizes the key actors and their interactions with the system.

#### 👤 Actors

- Guest
- Host
- Admin

#### Use Cases

- Register/Login
- Update Profile
- List Property
- Search Property
- Book Property
- Cancel Booking
- Make Payment
- Leave Review
- Manage Users (admin)
- Manage Bookings/Payments (admin)

---

## 📁 user-stories/user-stories.md

### Airbnb Clone - User Stories

#### 👤 Guest User Stories

1. As a guest, I want to create an account so that I can book properties on the platform.
2. As a guest, I want to securely log in using my email and password so that I can access my account.
3. As a guest, I want to search for available properties so that I can find a place to stay.
4. As a guest, I want to book a property for specific dates so that I can reserve it.
5. As a guest, I want to cancel my booking so that I can get a refund if eligible.
6. As a guest, I want to make a secure payment so that my reservation is confirmed.
7. As a guest, I want to leave a review so that I can share my experience.

#### 👤 Host User Stories

8. As a host, I want to list my property so that guests can book it.
9. As a host, I want to edit or remove my listing so that I can manage my space.
10. As a host, I want to view my bookings so that I can prepare for guests.
11. As a host, I want to receive payouts so that I can earn income.
12. As a host, I want to respond to reviews so that I can address feedback.

#### 👤 Admin User Stories

13. As an admin, I want to manage users so that I can maintain platform integrity.
14. As an admin, I want to monitor bookings so that I can ensure everything runs smoothly.
15. As an admin, I want to track payments so that I can manage financial issues.

---

## 📁 data-flow-diagram/README.md

### Airbnb Clone - Data Flow Diagram (DFD)

#### Purpose

The DFD shows the interaction between external entities (users), processes (like registration, booking), and data stores (such as the user database).

#### Entities

- Users
- Property Listings
- Bookings
- Payments
- Reviews

#### Processes

- Registration/Login
- Property Management
- Booking Flow
- Payment Processing
- Notifications

---

## 📁 flowcharts/README.md

### Airbnb Clone - Flowcharts

#### Example Process: User Registration

This flowchart visualizes the logic for registering a new user.

Steps:
- Form submission
- Input validation
- Email verification
- Password hashing
- Save to DB
- Return response
- Send confirmation email

---

## 📝 requirements.md

### Airbnb Clone - Backend Feature Requirements

#### 1. User Authentication

**Endpoints:**
- POST `/api/auth/register`
- POST `/api/auth/login`

**Validations:**
- Unique email, strong password

**Security:**
- JWT, bcrypt, 24hr token expiry

#### 2. Property Management

**Endpoints:**
- POST `/api/properties`
- PUT `/api/properties/:id`
- DELETE `/api/properties/:id`

**Validations:**
- Auth required, only hosts allowed

**Storage:**
- Cloud image storage

#### 3. Booking System

**Endpoints:**
- POST `/api/bookings`
- GET `/api/bookings/my`

**Validations:**
- Date conflicts, guest limits

**Status Flow:**
- pending → confirmed → completed/cancelled

**Security:**
- Guests only, JWT protected

---

### ✅ Summary Table

| Feature              | HTTP Method | Endpoint                | Auth Required | Role-Based? | Status Codes     |
|----------------------|-------------|-------------------------|----------------|-------------|------------------|
| Register User        | POST        | /api/auth/register      | ❌             | ❌           | 201, 400         |
| Login User           | POST        | /api/auth/login         | ❌             | ❌           | 200, 401         |
| Create Property      | POST        | /api/properties         | ✅             | ✅ Host       | 201, 403         |
| Book a Property      | POST        | /api/bookings           | ✅             | ✅ Guest      | 201, 409         |
| View My Bookings     | GET         | /api/bookings/my        | ✅             | ✅ Guest      | 200, 403         |
