# Enterprise Multi-Tenant Task Management Platform

A robust, scalable SaaS solution catering to project and task workflows for organizations of any size. Built with state-of-the-art technologies such as **Node.js**, **Express**, **React**, and **PostgreSQL**, the entire stack is containerized via **Docker** for uniform and production-ready deployment.

---

## ✨ Core Capabilities

- **Data Segregation by Tenant:** Ensures each organization's records are completely isolated  
- **Role-Based Permissions:** Supports `super_admin`, `tenant_admin`, and `user` roles  
- **Strong Authentication:** Secure JWT-based login (24-hour token expiry), with bcrypt-hashed credentials  
- **Extensive REST API:** 19 endpoint suite enables full CRUD and management workflows  
- **Subscription Controls:** Account and project limits per organization, enforced per their subscription  
- **Action Auditing:** Sensitive and critical operations automatically logged  
- **Modern React UI:** Handles protected routing, state management, and streamlined user navigation  
- **Automated DB Setup:** Schema migrations and seed data on deployment  
- **Docker-Native Design:** All components run as independent containers via Docker Compose  

---

## 🏗️ Platform Structure

```
Frontend (React SPA)
        ↓
API Layer (Node.js + Express)
        ↓
Database (PostgreSQL)
```

- Frontend: **http://localhost:3000**
- API: **http://localhost:5000/api**
- Database: **localhost:5432**

---

## 🚀 Getting Started

### Prerequisites
- Install Docker & Docker Compose  
- Node.js (18+), if developing outside of containers

### Start the System

```bash
docker-compose up -d
```

Platform access:
- UI: http://localhost:3000  
- API: http://localhost:5000/api  
- Database: localhost:5432  

### Check Container Status

```bash
docker-compose ps
```

### Shut Down Services

```bash
docker-compose down
```

---

## 📱 Using the Platform

### Demo User Accounts

**Super Admin**
- Email: superadmin@system.com  
- Password: Admin@123  

**Tenant Admin (Demo Tenant)**
- Email: admin@demo.com  
- Password: Demo@123  
- Tenant: demo  

**Regular Users**
- user1@demo.com / User@123  
- user2@demo.com / User@123  
- Tenant: demo  

---

### Organization Registration

Utilize the **Register** feature to set up new organizations and their administrator.

### Managing Users

- View users by organization  
- Add new users with specific roles  
- Edit or update user profiles  
- Remove users as necessary  

### Project Lifecycle

- Set up and administer projects  
- Edit or archive projects  
- Permanently delete as needed  

### Task Management

- Add tasks within projects  
- Set priority and update status  
- Edit or remove tasks at will  

---

## 📚 API Overview

Comprehensive details in **docs/API.md**.

### Example API Interactions

**User Login**

```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "admin@demo.com",
    "password": "demo123",
    "tenantSubdomain": "demo"
  }'
```

**Project Creation**

```bash
curl -X POST http://localhost:5000/api/tenants/{tenantId}/projects \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "My Project",
    "description": "Project description",
    "status": "active"
  }'
```

---

## 🔐 Auth Flow

1. Credentials submitted
2. Server issues JWT (valid 24 hours)
3. Client includes token in request header
4. Token validated on every API call
5. Expired tokens prompt for re-login

---

## 📊 Data Model

- **Tenant:** Organization and subscription information  
- **User:** Account, role, and tenant linkage  
- **Project:** Tenant-owned projects  
- **Task:** Individual actions tied to projects  
- **AuditLog:** Unalterable event records  

---

## 🧪 Testing & Verification

To execute complete integration tests:

```bash
node integration-test.js
```

All 19 endpoints are validated using scenario-based tests.

---

## 📁 Folder Structure

```
frontend/        # React web app
backend/         # Express + TypeScript APIs
docs/            # Documentation
docker-compose.yml
integration-test.js
submission.json
README.md
```

---

## 🔧 Environment Variables

### Backend

- DATABASE_URL  
- JWT_SECRET  
- NODE_ENV  

### Frontend

- VITE_API_URL (must point to the backend API)

Defaults are set for Docker-based deployment scenarios.

---

## 🛡 Security Features

- Passwords hashed with bcrypt  
- JWT (HS256) for authentication  
- Input validation enforced by Zod  
- Role-based permissions  
- All queries are tenant-scoped  
- Operations fully logged (audit)  
- Strict CORS setup  
- Containers run as non-root processes  

---

## 📦 Plans & Limits

| Plan | Users Limit | Project Limit | Included Features |
|------|-------------|---------------|------------------|
| Free | 5           | 2             | Basic set        |
| Pro  | 50          | 10            | Full access      |
| Enterprise | Unlimited | Unlimited  | Complete suite   |

All quotas are strictly enforced by the backend.

---

## 🐳 Docker Shortcuts

```bash
docker-compose up -d --build
docker logs backend -f
docker-compose down
docker-compose down -v
docker-compose build backend
```

---

## 🧠 Tech Used

React, Vite, Node.js, Express, TypeScript, PostgreSQL, Prisma, JWT, bcryptjs, Zod, Jest, Docker

---

## 🐛 Troubleshooting Tips

- **Startup issues:** Check logs and rebuild containers if necessary  
- **Database slow:** Allow time, then restart services  
- **Frontend not connecting:** Verify backend API path configuration  
- **Unauthorized errors:** JWT token may have expired; log in again  

---

## 📝 Other Notes

- All datetimes use UTC  
- Emails are unique within tenants  
- System provisions super_admins  
- Demo data is auto-seeded  
- JWT is stored in browser localStorage  

---

## ✨ Standout Features

✔ Tenant isolation at all levels  
✔ Hierarchical role permissions  
✔ Secure JWT authentication  
✔ Subscription-aware operation  
✔ Automatic migrations  
✔ Action audit logging  
✔ Ready-to-run Docker deployment  

---