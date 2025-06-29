# Airbnb Clone – Backend Feature Requirements

## 📌 Purpose

This document outlines the detailed requirements for three key backend features of the Airbnb Clone project: **User Authentication**, **Property Management**, and **Booking System**. It includes API endpoints, input/output formats, validation rules, and performance expectations.

---

## 1️⃣ User Authentication

### 🔐 Feature Description
Handles user registration and login for guests, hosts, and admins.

### 📥 Endpoints

#### POST /api/auth/register
- **Input (JSON):**
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "strongPassword123",
  "phone_number": "08012345678",
  "role": "guest"
}
