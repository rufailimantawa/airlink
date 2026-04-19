# Airlink

> Digital connectivity simplified

## Overview

Airlink is a programmable connectivity platform that enables users and developers to provision, manage, and monetize eSIM-based mobile data globally

Built as an API-first infrastructure layer, Airlink abstract the complexity of telecom integrations and provides a simple interface for:

- eSIM provisioning
- Plan management
- Usage tracking
- Billing and payments

The platform is designed to serve:

- **Individuals** needing seamless global connectivity
- **Businesses** managing distributed teams or customers
- **Developers** embedding mobile data into applications, devices, or services

### Core Idea

Airlink act as:

> Connectivity-as-a-Service (CaaS)

Similar to how modern platforms abstract payments and messaging, Airlink abstract mobile network access into programmable interface.

### Key Capabilities

- Global eSIM provisioning
- API-first integration for developers
- Built-in wallet and billing system
- Usage monitoring and analytics

### Vision

To become the connectivity layer for the internet economy, enabling:

- Borderless communication
- Embedded connectivity in apps and devices
- Scalable telecom infrastructure across Africa, EMEA, and beyond

### Positioning

Airlink sits at the intersection of:

- Telecom infrastructure
- Fintech (payments & billing)
- Developer platforms (API & integrations)

---

## MVP Architecture

### 1. Core Service

#### API Backend

> The Spinal cord

The central system coordinating all operations and external integrations.

#### Why Go: `No debate here`

- High perfomance (network-heavy system)
- Excellent concurrency model (for provisioning, billing, webhooks)
- Strong ecosystem for backend systems

---

### 2. Data Layer

#### PostgreSQL (Primary DB)

> Reliable. Simple. Scalable

Used for:

- Users & Accounts
- eSIM records
- Plans
- Orders & Transactions

#### Redis (Cache Layer: Optional)

> Improves performance for frequently accessed data

Used for

- Plans caching
- Sessions
- Rate limiting

#### Object Storage

> Critical component

Use Cloudflare R2 for:

- QR codes storage
- Activation payloads
- Static assets

### 3. Frontend

Stack: Vite + React

**Core Features**:

- User authentication (Signup, Login, Password Reset, & Identity Verification)
- Purchase eSIM
- View QR code
- Monitor usage

### 4. Mobile App (Optional for MVP)

Start with:

- PWA (Progressive Web App)

Later

- Native apps (Android / iOS)

### 5. External Services

#### eSIM Provider

Primary integration point for:

- eSIM provisioning
- Profile management
- Activation

#### Payment Gateway

- Paystack
- Flutterwave
- SquadCo

#### Email/SMS (Transactional)

- SendGrid
- Twilio
- SquadCo

### 6. API Design

#### Auth

```http
POST /auth/register
POST /auth/login
POST /auth/refresh
PUT  /auth/request-password-reset
POST /auth/reset-password
```

#### Plans

```http
GET /plans
GET /plans/:id
```

#### eSIM

```http
POST /esim
GET  /esim/:id
GET  /esim/:id/qr
```

#### Orders

```http
POST /orders/esim
```

#### Wallet

```http
GET  /wallet
POST /wallet/topup
```

### 7. Deployment Stack

#### MVP Infrastructure

- **Backend:** Go
- **Database:** Managed PostgreSQL
- **Cache:** Redis
- **Storage:** Cloudflare R2

#### Hosting Options

- Render (cloud-friendly)
- AWS (market dominant)
- Oracle Cloud (cost-effective)
- DigitalOcean

### 8. MVP Stack Summary

| Layer    | Tech                  |
|----------|-----------------------|
| Backend  | Go (modular monolith) |
| Database | PostgreSQL            |
| Cache    | Redis (optional)      |
| Storage  | Cloudflare R2         |
| Frontend | Vite + React          |
| Payments | Payment Gateway       |
| eSIM     | Provider API          |
| Infra    | Simple cloud setup    |

---

### 9. Milestones Roadmap

#### Week 1

- Project setup
- Database schema

#### Week 2-3

- Core API structure
- Basic endpoints
- Authentication system

#### Week 4

- eSIM provider integration
- Webhook handling

#### Week 5

- Order flow implementation
- Billing (wallet system)

#### Week 6

- Frontend integration
- QR code delivery

#### Week 7

- Testing & bug fixes
- Deployment

#### Week 8

- Launch

## MVP Build Order

1. [ ] Database schema
2. [ ] Models + repos layer
3. [ ] Auth service
4. [ ] eSIM provider service and integration
5. [ ] Order service
6. [ ] Billing service (wallet)
