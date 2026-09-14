# SwiftTrack Logistics — Cloud ERP Deployment & Systems Integration

Official repository for the cloud deployment and database integration of the SwiftTrack Logistics Enterprise Resource Planning (ERP) platform.

##  System Architecture Overview
* **ERP Core:** Odoo 19 Community Edition
* **Database Management System:** PostgreSQL 16
* **Cloud Infrastructure:** Oracle Cloud Infrastructure (OCI) — Always Free Ubuntu 22.04 LTS Instance
* **CMS Website:** WordPress (Elementor) Integration via Odoo Client Portal (`/web/login`)

---

##  Installation & Cloud Setup Instructions

### 1. Server Environment Provisioning
Connect to the remote cloud server via SSH terminal:
```bash
ssh -i /path/to/private_key.key ubuntu@<YOUR_CLOUD_SERVER_IP>
