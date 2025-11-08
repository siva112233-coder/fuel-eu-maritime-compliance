# 🚢 Fuel EU Maritime — Compliance Dashboard

A full-stack web application that calculates, tracks, and manages **Fuel EU Compliance** metrics for maritime vessels based on GHG intensity and energy consumption.  
It includes functionality for:

- ✅ Compliance Balance (CB) calculation  
- ✅ Banking surplus credits across years  
- ✅ Pooling ships to offset deficits  
- ✅ Route baseline comparison and emissions monitoring  

The platform follows **Hexagonal Architecture (Ports & Adapters)** on both frontend and backend, ensuring clean separation of concerns, testability, and maintainability.

---

## 📌 Features

| Module | Description |
|--------|-------------|
| **Routes** | View all registered routes, set baseline, filter data |
| **Compare** | Compare baseline vs other ships, % difference, compliance flag |
| **Banking** | Store surplus CB and apply it to cover deficits |
| **Pooling** | Group ships into a pool to redistribute surplus/deficits |
| **Database** | Backed by Neon PostgreSQL + Prisma ORM |
| **UI** | React + TypeScript + TailwindCSS dashboard |

---

## 🧠 Core Compliance Formula

| Metric | Formula |
|--------|---------|
| **Target GHG Intensity (2025)** | `89.3368 gCO₂e/MJ` |
| **Energy in Scope (MJ)** | `fuelConsumption (t) × 41,000` |
| **Compliance Balance (CB)** | `(Target − ActualGHG) × EnergyInScope` |
| **Positive CB** | ✅ Surplus credits |
| **Negative CB** | ❌ Deficit — must bank or pool to comply |

---

## 🏗️ Architecture Summary — Hexagonal Structure

The application is built using **Ports & Adapters / Hexagonal Architecture**:

