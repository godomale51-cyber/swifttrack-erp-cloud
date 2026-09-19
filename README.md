# SwiftTrack Logistics — Cloud ERP Deployment & Systems Integration

Official repository for the cloud deployment and database integration of the SwiftTrack Logistics Enterprise Resource Planning (ERP) platform.

---

## 📌 System Architecture & Details

* **ERP Core:** Odoo 19 Community Edition
* **Database Management System:** PostgreSQL 16
* **Cloud Infrastructure:** Amazon Web Services (AWS Free Tier) — Ubuntu 24.04 LTS
* **Containerization:** Docker & Docker Compose
* **Live Deployment URL:** `http://13.61.148.2:8069`

---

## 🔑 Assessor Credentials

* **URL:** `http://13.61.148.2:8069`
* **Database Name:** `Godwin`
* **Username:** `assessor@swone.com`
* **Password:** `SWOne2026!`

---

## 🚀 Deployment Steps

### Step 1: AWS EC2 Provisioning & Security
1. Provisioned an Ubuntu 24.04 LTS instance on AWS EC2.
2. Configured Inbound Security Group rules (`launch-wizard-1`):
   * **SSH (22):** Remote terminal management.
   * **Custom TCP (8069):** Odoo web interface traffic.
   * **HTTP (80) & HTTPS (443):** Standard web access.

### Step 2: Docker Environment Setup
Connected to the EC2 instance via SSH and initialized Docker:
### Step 3: Database Restoration & Admin Setup
1. Transferred local PostgreSQL dump (`Godwin.sql`) to EC2 via SCP.
2. Restored the database dump into the Docker PostgreSQL container:
3. 3. Secured access by updating the administrator password directly in PostgreSQL:
   4. 4. Restarted the Odoo web container to refresh asset bundles:
      5. ---

## 🛠️ Challenges Faced & Solutions

1. **Database Dump Version Mismatch & User Access Locks:**
* *Problem:* Restored local database preserved original login credentials, blocking access.
* *Solution:* Executed SQL commands directly within the PostgreSQL container using `psql` to override password hashes for administrator access (`id=2`).

2. **Asset Bundle Caching & Security Group Timeouts:**
* *Problem:* Page load timeouts occurred due to blocked inbound port `8069` and cached asset bundles in Odoo.
* *Solution:* Updated AWS Security Group inbound rules to allow Custom TCP port `8069` globally (`0.0.0.0/0`) and appended `?debug=assets` to force Odoo to rebuild its static assets.
