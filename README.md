# 🚀 UiPath Performer – ACME System 1 (Work Item 4)

## 📌 Description
This project implements the **Performer** part of the REFramework for the ACME System 1 automation.  
The Performer consumes the WI4 items exported by the **Dispatcher**, generates yearly reports, and updates ACME System 1 accordingly.

---

## 🎯 Goal
- Read WI4 data prepared by the Dispatcher (`WI4Items.xlsx`)  
- Process each record to generate yearly client reports  
- Update ACME System 1 with the processed report results  

---

## 🛠️ Tools & Technologies
- UiPath Studio  
- UiPath Excel Activities  
- UiPath UI Automation Activities  
- REFramework Template  

---

## ⚙️ Workflow Steps
1. **Read WI4 Items** from `Data/WI4Items.xlsx`.  
2. **Log in** to ACME System 1 using credentials (email + password).  
3. For each WI4 item:
   - Generate a **Yearly Report** for the given client.  
   - Upload or update the report in ACME System 1.  
   - Mark the transaction as completed.  
4. **Log out** of ACME System 1 and close all applications.  

---

## ▶️ How to Run
1. Ensure the Dispatcher has been executed and `WI4Items.xlsx` exists in the **Data** folder.  
2. Open the solution in UiPath Studio.  
3. Configure credentials for ACME System 1 in **Orchestrator Assets** or local Config.  
4. Run the Performer.  
5. After completion, verify that reports have been uploaded in ACME System 1.  

---

## 📖 Learning Outcomes
- Using REFramework for Performer workflows  
- Consuming Dispatcher outputs for downstream processing  
- Automating report generation and system updates  
- Working with Orchestrator queues, Excel, and structured data  

---

# 🏗️ REFramework Overview

The Performer uses **Robotic Enterprise Framework** (REFramework):  

- **Built on:** Transactional Business Process template  
- **Architecture:** State Machine layout for automation phases  
- **Features:**  
  - Centralized logging and exception handling  
  - Configurable settings via `Config.xlsx` and Orchestrator assets  
  - Automatic credential retrieval (Orchestrator/Windows Credential Manager)  
  - Queue-driven transaction processing  
  - Automatic screenshot capture on system exceptions  

---

## 🔄 How It Works

### 1. INITIALIZE PROCESS
- `InitAllSettings.xaml` – Load configuration from `Config.xlsx` and assets  
- `GetAppCredential.xaml` – Retrieve credentials securely  
- `InitAllApplications.xaml` – Open and log into ACME System 1  

### 2. GET TRANSACTION DATA
- `GetTransactionData.xaml` – Reads WI4 items from the Dispatcher’s Excel file or Orchestrator queue  

### 3. PROCESS TRANSACTION
- `Process.xaml` –  
  - Generate yearly report  
  - Upload/update in ACME System 1  
- `SetTransactionStatus.xaml` – Updates each transaction’s status (Success / Business Rule Exception / System Exception)  

### 4. END PROCESS
- `CloseAllApplications.xaml` – Log out and close applications  

---

## 📂 For New Projects
- Update `Config.xlsx` with project-specific values  
- Customize:  
  - `InitAllApplications.xaml` / `CloseAllApplications.xaml`  
  - `GetTransactionData.xaml` & `SetTransactionStatus.xaml`  
  - `Process.xaml` with the actual business logic  
