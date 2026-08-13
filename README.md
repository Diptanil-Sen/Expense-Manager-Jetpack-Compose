# 💰 Expense Tracker — Personal Finance Manager

A personal finance management Android application built entirely with **Jetpack Compose** and **Room Database**. It lets users record income, expenses, and transfers, visualize spending patterns through interactive charts, and stay on budget through smart local notifications.

![Kotlin](https://img.shields.io/badge/Kotlin-1.9-blue.svg?logo=kotlin)
![Compose](https://img.shields.io/badge/Jetpack%20Compose-UI-4285F4?logo=jetpackcompose)
![Room](https://img.shields.io/badge/Room-Database-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 📱 Overview

Managing day-to-day finances is often scattered across notes apps, bank SMS alerts, and memory. This app centralizes that into one offline-first tool — every transaction is stored locally, categorized, and summarized so the user always has an accurate picture of their financial health.

## 🖼️ Screenshots

| Home | Add Transaction | Analysis |
|------|------------------|----------|
| ![Home](screenshots/home.png) | ![Add](screenshots/add_transaction.png) | ![Analysis](screenshots/analysis.png) |

| Empty State | Notification |
|-------------|--------------|
| ![Empty](screenshots/analysis_empty.png) | ![Notification](screenshots/notification.png) |

*(Replace the paths above with your own screenshots — see "Adding Screenshots" below)*

## 🚀 Key Features

- **Full transaction CRUD** — add, edit, and delete income, expense, and transfer entries
- **Category-wise breakdown** — pie chart visualization of spending by category using MPAndroidChart
- **Offline-first storage** — all data persisted locally via Room, no internet dependency
- **Smart budget alerts** via WorkManager background jobs:
  - Low balance warning (below a configurable threshold)
  - Monthly spending limit exceeded
  - Spending milestone notifications
  - Expense-exceeds-income warning
  - Daily reminder if no transaction was logged
- **Material 3 design system** with light/dark theme support
- **Reactive UI** — screen state updates instantly as data changes, no manual refresh needed

## 🧠 Architecture

This project follows **MVVM (Model–View–ViewModel)** with a repository layer, keeping data, business logic, and UI cleanly separated and independently testable.

**Model layer** — `Transaction` data class, `AppDatabase`, `TransactionDao` for local queries, and `TransactionRepository` abstracting data access away from the ViewModel.

**ViewModel layer** — `TransactionViewModel` exposes UI state via `StateFlow`, computes derived values like running balance, and triggers notification logic based on transaction changes.

**View layer** — Composable screens:
- `HomeScreen` — balance overview, income/expense summary, recent transactions
- `AddTransactionScreen` — form for logging a transaction with category and payment mode
- `AnalysisScreen` — monthly insights with category-wise pie charts

**Supporting components** — `WorkManager` for scheduled background checks, `NotificationHelper` for managing notification channels and alert triggers.

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Kotlin |
| UI | Jetpack Compose, Material 3 |
| Architecture | MVVM, Repository Pattern |
| Persistence | Room Database |
| Async | Kotlin Coroutines, StateFlow |
| Charts | MPAndroidChart |
| Background Work | WorkManager |

## ⚙️ Getting Started

```bash
git clone https://github.com/<your-username>/expense-tracker.git
```
1. Open the project in Android Studio (latest stable version recommended)
2. Let Gradle sync complete
3. Run on an emulator or physical device

## 📌 What This Project Demonstrates

- Structuring a Compose app with clean MVVM separation
- Local database design and CRUD operations with Room
- Reactive state management using StateFlow
- Scheduling background work and triggering system notifications
- Data visualization within a mobile UI

## 🔭 Possible Future Improvements

- Cloud backup/sync across devices
- CSV/PDF export of transaction history
- Multi-currency support
- Recurring transaction templates
