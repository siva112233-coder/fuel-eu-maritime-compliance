# Fuel EU Compliance Dashboard

A full-stack web application that calculates and manages **Fuel EU compliance metrics** for ships based on greenhouse gas (GHG) intensity and energy consumption.  
It supports:

- ✅ Compliance Balance (CB) calculation per ship and year  
- ✅ Banking of surplus CB for future usage  
- ✅ Pooling between ships to balance deficits with surpluses  
- ✅ Persistent storage using Neon PostgreSQL + Prisma ORM  

---

## 🔍 Overview

The **Fuel EU Compliance Dashboard** enables monitoring of maritime vessel emissions against the target GHG intensity mandated by the FuelEU regulation.

The platform provides:

| Module | Purpose |
|--------|---------|
| **Compliance Calculation** | Computes CB (surplus/deficit) per ship per year |
| **Banking** | Stores surplus CB for later usage |
| **Pooling** | Allows multiple ships to redistribute surplus CB |
| **Database-backed Storage** | Fully persistent via Neon PostgreSQL and Prisma |

---

## 🧠 Core Compliance Formulas

| Metric | Formula |
|--------|---------|
| **Target GHG Intensity (2025)** | `89.3368 gCO₂e / MJ` |
| **Energy in Scope (MJ)** | `fuelConsumption × 41,000` |
| **Compliance Balance (CB)** | `(Target − ActualIntensity) × EnergyInScope` |
| **Interpretation** | Positive CB → Surplus, Negative CB → Deficit |

---

## 🏗️ Architecture Summary (Hexagonal)

This project follows **Hexagonal Architecture (Ports & Adapters)** for modularity, testability, and decoupled logic.

| Layer | Responsibility | Example Components |
|--------|---------------|--------------------|
| **Core Domain** | Business entities + invariants | `Route`, `Compliance` |
| **Application Layer** | Use cases & business workflows | `ComplianceService`, `PoolService` |
| **Ports (Interfaces)** | Defines boundary contracts | `ComplianceRepositoryPort` |
| **Adapters (Implementations)** | Connects ports to DB, HTTP, UI | `CompliancePostgresAdapter` |
| **Infrastructure** | Server, DB connection, framework config | `Express`, `Prisma`, `TSX` |

✅ Benefits: Loose coupling, replaceable adapters, testable core logic, framework-independent domain.

