# Clinic Management System - Database Design (ER Diagram)

## Project Overview

This project presents a database design for a modern clinic system that manages doctors, patients, appointments, consultations, diagnostic tests, reports, and payments.

The system is designed to handle:

* doctor and patient management
* appointment scheduling
* consultation tracking
* diagnostic test workflow
* report generation
* payment handling

The goal is to build a clean and scalable structure that reflects real clinic operations.

---

## Problem Understanding

This is not just an appointment booking system.

The key challenge is modeling the real-world flow:

| Concept         | Behavior                                |
| --------------- | --------------------------------------- |
| Doctor          | Can handle multiple patients            |
| Patient         | Can visit multiple times                |
| Appointment     | Booking request (may or may not happen) |
| Consultation    | Actual visit with doctor                |
| Diagnostic Test | Prescribed during consultation          |
| Report          | Generated after test completion         |

The design separates **appointment, consultation, and diagnostics** clearly.

---

## Core Entities

### User

Stores both doctors and patients.

* name, email, phone
* role (doctor / patient)

---

### Doctor

Represents doctors in the clinic.

* linked to user
* linked to speciality

---

### Patient

Represents patients.

* linked to user

---

### Speciality

Defines doctor expertise.

* name (cardiologist, neurologist, etc.)

---

### Appointment

Represents booking between patient and doctor.

* scheduled time
* status (scheduled, completed, cancelled)

---

### Consultation

Represents actual doctor visit.

* linked to appointment
* status tracking

---

### Diagnostic Test

Tests prescribed during consultation.

* test name
* status (prescribed, completed, cancelled)
* submission time

---

### Report

Generated after diagnostic test.

* linked to patient
* linked to consultation
* linked to test
* report content

---

### Payment

Tracks payments in the system.

* amount
* status (pending, completed, failed, refunded)
* method

---

## Relationships (Cardinality)

* One User → One Doctor
* One User → One Patient
* One Speciality → Many Doctors
* One Patient → Many Appointments
* One Doctor → Many Appointments
* One Appointment → One Consultation
* One Patient → Many Payments
* One Patient → Many Reports
* One Consultation → Many Reports
* One Diagnostic Test → One Report

---

## Key Design Decisions

### 1. Appointment vs Consultation Separation

Appointment = booking
Consultation = actual visit

This avoids mixing planned vs completed interactions.

---

### 2. Diagnostic Flow Design

Consultation → Diagnostic Test → Report

This models real clinic workflow clearly.

---

### 3. Role-Based User System

Single user table handles both:

* doctors
* patients

This avoids duplication.

---

### 4. Clean Separation of Concerns

* reports are separate from tests
* payments are independent
* consultation is not mixed with appointment

This keeps the system scalable.

---

## Project Structure

```
ClinicManagementSystem/
│
├── ER-diagram.png
├── eraser-link.txt
└── README.md
```

---

## Tools Used

* Eraser (for ER diagram design)

---

## Future Improvements

* Add prescription management
* Support multiple tests per consultation (with junction table)
* Add report file storage (PDF, images)
* Introduce billing per consultation
* Add department management

---

## Author

Tejas

---

## Final Note

This design focuses on clarity, normalization, and real-world clinic workflow.

Built to reflect how a simple clinic system can evolve into a structured and scalable platform.
