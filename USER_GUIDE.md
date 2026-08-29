# Vanilla Retail — Complete User & Operations Manual

Welcome to the **Vanilla Retail Operations Platform**. This manual provides comprehensive instructions for store managers, supervisors, cashiers, and technical administrators on installing, configuring, using, and troubleshooting the **Vanilla Retail POS Cashier** and **Vanilla Retail Operations Center** software suite.

---

## 📋 Table of Contents
1. [System Overview](#-system-overview)
2. [Default Login Credentials](#-default-login-credentials)
3. [Installation & Uninstallation](#-installation--uninstallation)
4. [Terminal Pairing & Authentication Flow](#-terminal-pairing--authentication-flow)
5. [Using the Applications](#-using-the-applications)
   - [Operations Center (Manager App)](#operations-center-manager-app)
   - [POS Cashier App](#pos-cashier-app)
6. [Timezone & Data Standards](#-timezone--data-standards)
7. [Best Practices: What to Do & What to Avoid](#-best-practices-what-to-do--what-to-avoid)
8. [Troubleshooting & Support](#-troubleshooting--support)

---

## 🏛️ System Overview

Vanilla Retail is an enterprise-grade retail management and point-of-sale platform consisting of two native Windows applications connected to a secure cloud backend:

1. **Vanilla Retail Operations Center (Manager App)**
   - Used by store managers and administrative staff.
   - Core functions: Sales analytics, live store dashboard, product catalog management, inventory control, store reports, cashier pairing authorization, and store discussions.

2. **Vanilla Retail POS Cashier App**
   - Used by cashiers and sales representatives at checkout terminals.
   - Core functions: Fast checkout/new sales, receipt generation, order history, inventory lookup, and manager assistance discussions.

---

## 🔐 Default Login Credentials

Upon initial installation, use the pre-configured system administrative credentials below:

| Application | Role | Default Username | Default Password |
| :--- | :--- | :--- | :--- |
| **Operations Center** | Store Manager | `manager` | `manager@123` |
| **POS Cashier App** | Main Cashier | `cashier` | `cashier@123` |

> ⚠️ **IMPORTANT**: After your first login, we strongly recommend changing these passwords via the **Settings** screen in each respective application. Password changes are stored permanently and persist across system restarts, app updates, and server redeployments.

---

## 📦 Installation & Uninstallation

### Installing the Applications
1. Locate the setup installers:
   - `VanillaCashier_Setup_v1.0.0.exe` (or `VanillaRetail-Cashier-Setup.exe`)
   - `VanillaOperationsCenter_Setup_v1.0.0.exe` (or `VanillaRetail-OperationsCenter-Setup.exe`)
2. Double-click the installer for the application you wish to install.
3. Accept the License Agreement and Privacy Policy from Vanilla Softwares.
4. Keep the **"Create a desktop shortcut"** box checked (selected by default) for convenient access.
5. Click **Install**, then click **Finish** to launch.

### Clean Uninstallation
Both applications cleanly unregister from Windows and erase all cached application data upon uninstall:
1. Open Windows **Settings** (`Win + I`) ➔ **Apps** ➔ **Installed apps** (or Control Panel ➔ Programs and Features).
2. Search for **Vanilla Retail**.
3. Select **Vanilla Retail POS Cashier** or **Vanilla Retail Operations Center** and click **Uninstall**.
4. The uninstaller will purge all binary files, shortcuts, local application data (`%LOCALAPPDATA%\Vanilla Retail`), and saved credentials.

---

## 🔄 Terminal Pairing & Authentication Flow

To ensure high operational security, Cashier terminals require authorized pairing with the Operations Center:

### Pairing Step-by-Step
1. **Cashier Terminal Login**:
   - Open the **POS Cashier App**.
   - Enter your Cashier password and click **Login**.
   - The 15-minute pairing countdown timer will **only start after correct password verification**.
   - A 6-digit Pairing Code (PIN) is displayed on the screen.

2. **Operations Center Authorization**:
   - Open the **Operations Center App** and log in as Manager.
   - Navigate to **Settings** ➔ **Terminal Pairing** or click the **Pair Terminal** prompt.
   - Enter the 6-digit PIN displayed on the Cashier screen and click **Pair Terminal**.

3. **Active Pairing**:
   - The Cashier terminal immediately transitions to the active POS dashboard.
   - The terminal remains securely paired for operational transactions.

### Unpairing / Disconnecting Terminals
- If a terminal is unpaired from the Operations Center, the Cashier terminal receives an immediate real-time unpair command, safely logs out the user, and returns to the initial authentication screen.

---

## 🖥️ Using the Applications

### Operations Center (Manager App)
- **Dashboard**: View live sales summaries, total revenue today vs. yesterday, order volume, inventory valuation, and top-performing products.
- **Orders**: Monitor all orders created across terminals, filter by status (Pending, Completed, Cancelled), and review transaction details.
- **Products**: Add new products, edit pricing, barcode SKUs, categories, and manage product availability.
- **Inventory**: Monitor stock levels, set low-stock thresholds, and record stock adjustments with audit notes.
- **Reports**: Generate hourly sales distribution charts, daily revenue reports, and payment method breakdowns.
- **Discussions**: Real-time communication channel with cashier terminals for price approvals, voids, or store inquiries.
- **Settings**: Manage terminal pairings, store details, and update Manager credentials.

### POS Cashier App
- **Dashboard / Register**: Quick summary of today's transactions and quick links to checkout.
- **New Sale (Checkout)**: Search or scan products, adjust quantities, apply discounts, select payment methods (Cash, Card, Mobile Payment), and complete transactions.
- **My Orders**: View previous transactions processed on the current terminal and print/reissue receipts.
- **Discussions**: Send instant messages or assistance requests to the Manager's Operations Center.
- **Settings**: View terminal pairing status and change Cashier password.

---

## ⏰ Timezone & Data Standards

- **Official System Timezone**: All business metrics, daily report resets, transaction timestamps, and printed receipts strictly use **Tennessee Knoxville Time (Eastern Time ET / EST / EDT)**.
- **Daily Reset**: "Today's Revenue" and "Orders by Hour" reset automatically at 00:00 (Midnight) Knoxville Time.

---

## 🛡️ Best Practices: What to Do & What to Avoid

### ✅ WHAT TO DO
* **DO** change the default passwords (`manager@123` and `cashier@123`) immediately after deployment.
* **DO** ensure the host computer has an active internet connection for real-time cloud data synchronization.
* **DO** log out of the terminal when leaving the checkout station unattended.
* **DO** use the clean Windows Uninstaller if you need to perform a full reset or reinstallation.

### ❌ WHAT TO AVOID
* **DO NOT** manually delete files inside `%LOCALAPPDATA%\Vanilla Retail` while the application is running.
* **DO NOT** share 6-digit terminal pairing codes with unauthorized staff members.
* **DO NOT** force-close the app during an active transaction sync.
* **DO NOT** adjust system clock time manually on client computers; the server handles exact UTC and Knoxville time alignment.

---

## ❓ Troubleshooting & Support

| Issue | Cause | Solution |
| :--- | :--- | :--- |
| **"Failed to load dashboard / 500 error"** | Network connectivity issue or transient cloud cold-start. | Click the **Retry** button on top right of the dashboard. Ensure internet connection is active. |
| **"Could not load stats — check API connection"** | Terminal lost connection to cloud backend. | Verify your internet connection. Click **Retry**. If persistent, restart the application. |
| **Pairing Code Timer Started Unexpectedly** | Previously resolved in latest build. | The timer now starts strictly **after** valid password entry. If code expires (15 min), click **Regenerate Code**. |
| **Changed Password Reverting to Default** | Credentials cache out of sync. | Resolved in latest version. Password changes are written to persistent local storage. Ensure you click **Save Password**. |
| **Cashier Terminal Stuck After Unpairing** | Real-time signal drop. | Click **Logout** on Cashier terminal or restart the app to return to login screen. |
| **Installer fails or permission denied** | Insufficient administrative rights. | Right-click the installer `.exe` file and select **"Run as administrator"**. |

---

*Vanilla Retail Platform © 2026 Vanilla Softwares. All rights reserved.*
