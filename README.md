# Task-2-Albin-Biju


#  Vaccination Tracker — Backend Core (`app.py`)

This file serves as the centralized backend engine for the **Vaccination Tracker** web application built using **Python Flask** and connected to a **MySQL** relational database.
---

## 🛠️ Technology Stack & Connectors
* **Framework Backend:** Flask 3.x (Python Micro-framework)
* **Relational Database Engine:** MySQL Server
* **Database Driver Connector:** `flask_mysqldb`
* **Data Serialization:** JavaScript Object Notation (JSON) payloads

---

##  API Blueprint & Core Operations

### 1. View Engine Routing Controllers
Renders server-side semantic HTML views located inside the user template directory workspace:
* `GET /` & `/logout` — Entry gateway login interface portal.
* `GET /register` — New account user onboarding registration screen.
* `GET /dashboard` & `/nurse/dashboard` — Secure role-restricted tracking control panels.
* `GET /records` / `/schedule` / `/bookings` / `/addrecord` / `/updaterecord` — Modular immunization utility pages.

### 2. Functional REST API Handlers

####  Security & Session Services
* **`POST /api/register`** — Registers fresh account profiles. Emails initialized with a **`nur`** string prefix automatically receive administrative **`nurse`** credentials; otherwise, they default to a **`patient`** role assignment.
* **`POST /api/login`** — Authenticates incoming client credentials and returns core session context maps (`user_id`, `username`, `role`) on a successful match.

####  Booking & Schedules Pipeline
* **`POST /api/booking`** — Commits future reservation dates into the `appointments` storage schema container.
* **`GET /api/get_bookings`** — Provisions calendar card data streams. Appending an active patient filter (`?user_id=...`) cleanly isolates personal schedules, while omitting it maps all system reservations for administrative nurses.
* 
####  Clinical Records Management
* **`POST /api/addrecord`** — Commits vaccine compliance logs into the database records. Implements an identity verification safeguard: drops requests targeting administrative staff IDs, confirms the patient exists, and triggers a rollback block on case-insensitive name mismatches to keep clinical logs accurate.
* **`GET /api/records`** — Dynamically builds history tracking ledgers. Streamlines output depending on authorization scope (isolated patient history vs. full global master logs).
* **`GET /api/get_record_by_patient/<int:patient_id>`** — Fetches the single most recent medical transaction row mapped to a target Patient ID to automatically populate updating interfaces.
* **`PUT /api/updaterecord/<int:record_id>`** — Executes safe, non-breaking modifications on an existing record row matching the specified primary key integer ID.

