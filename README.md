<br/>
<div align="center">
  <h1 align="center">DDP Medical Portal Automation</h1>
  <p align="center">
    <strong>A professional Python RPA tool & Desktop App to automate order entries on the DDP Medical Portal (Acumatica).</strong>
  </p>
</div>

<hr />

## 📖 Overview

The **DDP Medical Portal Automation** suite streamlines the repetitive process of entering medical orders from Google Sheets directly into the DDP Medical Portal. 

What began as a command-line utility has now evolved into a **fully featured Desktop Application**. It intelligently handles logging into the portal, building complex orders, managing shipping locations, and safely pausing for human review—all wrapped in a sleek, non-blocking Graphical User Interface (GUI).

---

## ✨ Features

- 🖥️ **Modern Desktop GUI:** Built with `CustomTkinter` and multi-threading, providing a beautiful dark-mode interface, real-time logging terminal, and interactive controls without browser locking.
- ⚙️ **Dynamic Settings Engine:** Manage your `DDP Username`, `Password`, `Google Sheet URLs`, and `Credentials.json` securely from within the app, saving directly to `.env`.
- 📊 **Google Sheets Integration:** Automatically fetches pending orders (SNS & VN types) and intelligently updates row statuses and colors upon completion or failure.
- 🤖 **Advanced Acumatica Automation:**
  - Robust product code searching and cart management.
  - Smart JS fallbacks to bypass blocking overlays and stale elements.
  - Intelligent Location Selection: Automatically retrieves or cleanly adds new patient shipping locations.
- 🧑‍💻 **Human-in-the-Loop Validation:** The bot automatically pauses at the final Checkout stage. A glowing button prompts the user to manually verify and submit the order before the script finalizes the backend sheets.

---

## 🚀 Installation & Setup

### 1. Prerequisites
- **Python 3.8+**
- **Google Chrome** installed locally.
- Google Cloud Service Account credentials (`credentials.json`) for Google Sheets API access.

### 2. Prepare Environment
Clone the repository and install the standard dependencies:
```bash
git clone <repository-url>
cd "DDP Medical Portal Automation"

# Install fundamental and GUI dependencies
python -m pip install -r requirements.txt
python -m pip install customtkinter python-dotenv pyinstaller
```

*(Ensure related packages like `selenium`, `google-api-python-client`, `google-auth-httplib2`, and `google-auth-oauthlib` are present).*

### 3. Compiling the Application (Standalone EXE)
To achieve the best user experience, compile the Python code into an Executive (`.exe`) file:
```bash
python -m PyInstaller --noconsole --onefile --name "DDP_RPA_Bot" gui.py
```
After the build completes, your application will be available in the `dist` folder: `dist/DDP_RPA_Bot.exe`.

---

## 💻 Usage Guide

### Desktop Interface (Recommended)
1. Launch `DDP_RPA_Bot.exe`.
2. Navigate to the **System Settings** tab and ensure your Username, Password, and Google Sheet links are populated. Choose your `credentials.json` file.
3. Return to the **Dashboard**, select either **SNS Orders** or **VN Orders**, and click **Start Automation**.
4. Monitor the live terminal. When prompted for human review, the app will pause and an orange **Confirm Submission & Continue** button will appear.
5. Review the order in the visible Chrome window, click "Submit Order", and finally click the orange Confirm button in the app to proceed to the next record!

### Command Line Interface (Legacy Support)
If you prefer running the automation directly from the terminal without the GUI, you can leverage the original entry point:

```bash
# To process SNS orders (default)
python main.py --sns

# To process VN orders
python main.py --vn
```

---

## 📁 Architecture Overview

- `gui.py` — The professional graphical frontend and threaded execution manager.
- `main.py` — The core orchestrator managing standard order loops and callbacks.
- `portal_automation.py` — The Selenium WebDriver class carrying the complex interaction logic for the Acumatica web portal.
- `sheets_client.py` — Custom wrapper for Google Sheets API communication.
- `config.py` — Dynamic configuration loader evaluating `.env` on startup.

---
*Developed for unparalleled stability and accuracy in Medical Data Entry.*
