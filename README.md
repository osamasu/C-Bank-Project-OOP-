<div align="center">

# 🏦 C++ Bank Management System

**A console-based banking application built with Object-Oriented Programming in C++17**

![Language](https://img.shields.io/badge/language-C%2B%2B17-00599C?logo=cplusplus&logoColor=white)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows&logoColor=white)
![IDE](https://img.shields.io/badge/IDE-Visual%20Studio%202022-5C2D91?logo=visualstudio&logoColor=white)
![Type](https://img.shields.io/badge/type-Console%20Application-informational)

</div>

---

## 📖 Overview

**BankProjectOOP** is a fully-featured, file-persisted banking system built entirely in native C++ to demonstrate practical Object-Oriented Design: class hierarchies, encapsulation, permission-based access control, and clean separation between data models, business logic, and presentation (console UI screens).

It simulates a real bank's back office — client accounts, staff/admin users with granular permissions, money transfers, and a live currency exchange desk — all without any external database or framework, using flat-file storage.

## ✨ Features

**👤 Client Management**
- Add, update, delete, find, and list bank clients
- View total balances across all accounts

**💰 Transactions**
- Deposit and withdraw funds
- Transfer money between client accounts
- Full transfer transaction log

**🔐 Users & Permissions**
- Admin and staff user accounts with a fine-grained, bitmask-based permission system
- Each menu option is dynamically shown or hidden based on the logged-in user's rights
- Login audit trail (who logged in, and when)

**💱 Currency Exchange**
- Maintain a list of currencies and exchange rates
- Find and update currency rates on the fly

## 🖼️ Screenshots

<div align="center">

**Login Screen**
<img width="1235" height="659" alt="Login screen" src="https://github.com/user-attachments/assets/7dc0bd3a-8fda-461a-8f5d-b223494a2c8b" />

**Main Menu**
<img width="1241" height="661" alt="Main menu" src="https://github.com/user-attachments/assets/660f18b1-5a40-4d07-a764-4e0247ac181b" />

**Find Client**
<img width="1123" height="655" alt="Find client screen" src="https://github.com/user-attachments/assets/a0481479-d299-4cc2-b8f6-f9068e62dba0" />

**Transactions Menu**
<img width="1159" height="666" alt="Transactions menu" src="https://github.com/user-attachments/assets/4a6cb650-539e-42a7-a42c-0a97e4c923df" />

**Currency Exchange**
<img width="1176" height="658" alt="Currency exchange screen" src="https://github.com/user-attachments/assets/0cbe57d6-de10-4d7e-94f2-c08d9ef86242" />

**Manage Users**
<img width="1149" height="663" alt="Manage users screen" src="https://github.com/user-attachments/assets/9a3bf765-a17d-47a9-a729-955868a35325" />

</div>

## 🏗️ Architecture

```
BankProjectOOP/
├── main.cpp              # Entry point — launches the login screen
├── Global.h              # Global session object (CurrentUser)
├── Models/                # Domain / data layer
│   ├── clsPerson.h        # Base class: name, email, phone
│   ├── clsBankClient.h    # Client accounts (balance, deposit/withdraw/transfer, file CRUD)
│   ├── clsBankUser.h      # System users/admins (permission bitmask, auth, file CRUD)
│   ├── clsCurrency.h      # Currency exchange rates, file CRUD
│   ├── clsDate.h          # Custom date library (leap years, arithmetic, formatting)
│   └── clsPeriod.h        # Date-range utilities built on clsDate
├── Screens/                # Presentation layer — 25 console UI screens
│   ├── clsLoginScreen.h, clsMainMenu.h        # Login & main navigation
│   ├── clsAdd/Delete/Update/FindClientScreen.h # Client CRUD screens
│   ├── clsDeposit/Withdraw/TransferScreen.h    # Transaction screens
│   ├── clsAdd/Delete/Update/FindUserScreen.h   # User management screens
│   └── clsCurranciesListScreen.h, ...          # Currency exchange screens
├── Utilities/               # Cross-cutting helpers
│   ├── clsInputValidate.h  # Input validation
│   ├── clsString.h         # String helpers
│   └── clsUtili.h          # Misc utilities & basic encryption
└── *.txt                    # Flat-file data stores (Clients, Users, Currencies, Logs)
```

### Design Highlights
- **Inheritance** — `clsBankClient` and `clsBankUser` both extend a shared `clsPerson` base class.
- **Encapsulation** — each model owns its own file I/O (`Save`, `Find`, `Update`, `Delete`), keeping persistence logic out of the UI layer.
- **Permission-driven UI** — `clsBankUser::enPermissions` is a bitmask enum; menus are built dynamically per logged-in user, so staff only see what they're allowed to use.
- **Separation of concerns** — `Models/` never touches `cout`/`cin`; all console I/O lives in `Screens/`.

### Key Model Classes

| Class | Responsibility |
|---|---|
| `clsPerson` | Base class for shared person attributes (name, email, phone) |
| `clsBankClient` | Bank account holder — balance, deposit/withdraw/transfer, client persistence |
| `clsBankUser` | System user/admin — credentials, permission bitmask, login history |
| `clsCurrency` | Currency exchange rate records and lookups |
| `clsDate` | Custom date arithmetic and formatting (no `<ctime>` dependency) |
| `clsPeriod` | Date-range operations built on top of `clsDate` |

## 🚀 Getting Started

### Prerequisites
- **Windows** with **Visual Studio 2022** (toolset v143)
- **C++17** standard support (included with VS2022)

### Build & Run
```bash
# Clone the repository
git clone https://github.com/<your-username>/C-Bank-Project-OOP-.git

# Open the solution in Visual Studio
cd C-Bank-Project-OOP-
start BankProjectOOP.sln
```
1. In Visual Studio, select the **Debug** or **Release** configuration (x64 or Win32).
2. Build the solution (`Ctrl+Shift+B`).
3. Run (`Ctrl+F5`) — the application starts at the login screen.

## 🧭 Usage

1. **Log in** with a valid username/password (stored in `Users.txt`).
2. The **Main Menu** adapts to your permissions — e.g., a teller might only see Client and Transaction options, while an admin also sees User Management.
3. Navigate submenus to manage clients, process deposits/withdrawals/transfers, exchange currencies, or review login history.
4. Choose **Logout** to end the session.

## 🛠️ Tech Stack

- **Language:** C++17
- **UI:** Native Windows console (no external UI framework)
- **Persistence:** Flat `.txt` files, one per entity (clients, users, currencies, logs)
- **Build System:** MSBuild via Visual Studio 2022

## 👤 Author

Built by **osamasu** — feel free to explore, fork, and reach out with feedback or questions.
