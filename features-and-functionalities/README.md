## 1. **Feature & Functional Specification Document**

This document clearly **describes what each feature does**, what endpoints are needed, data flow, validations, and how different components interact.

### Structure of the Document

---

### **2. Functional Modules**

### Diagram 

![Backend requirements diagram](features-and-functionalities/requirements.drawio.png)


#### **A. User Authentication**

* **Features**:

  * Register (as host or guest)
  * Login (JWT & OAuth)
  * Logout
  * Password reset
* **Endpoints**:

  ```
  POST /api/register
  POST /api/login
  POST /api/logout
  POST /api/forgot-password
  POST /api/oauth/google
  ```
* **Validations**:

  * Email format
  * Password strength
  * Unique email/username

---

#### **B. Property Management**

* **Features**:

  * Create listing (title, description, location, price, images, availability)
  * Edit listing
  * Delete listing
* **Endpoints**:

  ```
  POST /api/listings
  PUT /api/listings/:id
  DELETE /api/listings/:id
  GET /api/listings/:id
  GET /api/listings?filters
  ```
* **Validations**:

  * Host only can create/edit
  * Required fields: title, location, price
  * Image format and size check

---

#### **C. Search & Filtering**

* **Features**:

  * Search by location
  * Filter by price, amenities, guest count, etc.
  * Pagination
* **Endpoint**:

  ```
  GET /api/listings?location=lagos&minPrice=100&maxPrice=500&guests=4&amenities=wifi,pool&page=1
  ```

---

#### **D. Booking System**

* **Features**:

  * Create a booking
  * Cancel a booking
  * View booking status (pending, confirmed, completed)
  * Prevent double bookings
* **Endpoints**:

  ```
  POST /api/bookings
  GET /api/bookings/:id
  DELETE /api/bookings/:id
  GET /api/user/bookings
  ```
* **Validations**:

  * Date overlap check
  * Guest only can book
  * Check if property is available

---

#### **E. Payment Integration**

* **Features**:

  * Guest pays via Stripe/PayPal
  * Host receives payout after stay
  * Refunds for cancellations
* **Endpoints**:

  ```
  POST /api/payments/create-session
  POST /api/payments/webhook
  GET /api/payments/status/:bookingId
  ```
* **Security**:

  * Use Stripe SDK/Webhooks
  * Validate payment status before marking booking confirmed

---

#### **F. Reviews & Ratings**

* **Features**:

  * Guest can review after completed booking
  * Host can respond
* **Endpoints**:

  ```
  POST /api/reviews
  GET /api/listings/:id/reviews
  POST /api/reviews/:id/respond
  ```

---

#### **G. Notifications**

* **Email + In-app notifications**:

  * On booking confirmation
  * On cancellations
  * On payment success
* **Tech**:

  * Nodemailer / SendGrid / Firebase for in-app

---

#### **H. Admin Dashboard**

* **Features**:

  * View all users
  * Delete or suspend user/listing
  * View payment activity
* **Endpoints**:

  ```
  GET /api/admin/users
  GET /api/admin/listings
  DELETE /api/admin/user/:id
  ```
