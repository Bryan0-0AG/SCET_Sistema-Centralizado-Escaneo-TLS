# 🔐 TCSS - TLS Centralized Scanning System

> A TLS/SSL certificate monitoring and analysis tool for multiple domains, featuring an interactive dashboard and real-time risk classification.

---

## 📋 Description

**TCSS** is a Python application that centralizes TLS certificate scanning across a list of domains, analyzes their security configuration (TLS version, cipher suites, expiration date, issuer) and presents the results in an interactive web dashboard built with **Plotly Dash**.

The system automatically classifies the risk level of each domain (`LOW`, `MEDIUM`, `HIGH`, `CRITICAL`) based on detected cipher suites and certificate expiration proximity, enabling security teams to make fast, prioritized decisions.

---

## 🗂️ Project Structure

```
TCSS_TLS-Centralized-Scanning-System/
│
├── main.py                  # Entry point — launches the dashboard at localhost:8050
├── config.py                # Global configuration (ports, ciphers, colors, paths)
│
├── scanner/                 # TLS scanning module
├── domain/                  # Domain management and registration
├── dashboard/               # Dash dashboard components
└── storage/
    ├── TLS.SCAN_Domains.csv        # Historical scan results
    └── Registered_Domains.json    # List of domains to monitor
```

---

## ⚙️ Features

- **Multi-port scanning**: Analyzes the most security-relevant ports (443, 80, 22, 445, 3389, 21, 8080).
- **Cipher suite classification**: Automatically detects insecure (`RC4`, `DES`, `3DES`, `NULL`, `EXPORT`), moderate (`AES128`, `SHA1`), and secure (`AES256`, `CHACHA20`, `SHA256`) cipher suites.
- **Color-coded risk levels**: Intuitive visual display with color coding per risk level.
- **Interactive dashboard**: Web interface with results table, filters, and navigation between sections (Dashboard, Table, Admin).
- **Result persistence**: Scans are saved in CSV and JSON formats for historical reference.
- **Configurable timezone**: Timestamps defaulted to `America/Bogota`.

---

## 🚀 Installation & Usage

### Requirements

- Python 3.8+
- The following libraries (install via `pip`):

```bash
pip install dash plotly pytz
```

### Run the dashboard

```bash
python main.py
```

Then open your browser at:

```
http://127.0.0.1:8050
```

---

## 📊 Risk Classification

| Level    | Color            | Criteria                                        |
|----------|------------------|-------------------------------------------------|
| LOW      | 🟢 Green         | Secure ciphers, valid certificate               |
| MEDIUM   | 🟡 Yellow        | Moderate ciphers or expiration approaching      |
| HIGH     | 🟠 Dark Orange   | Weak cipher suites detected                     |
| CRITICAL | 🔴 Red           | Insecure ciphers or expired certificate         |

---

## 📁 Data Storage

Results are automatically saved with the following columns:

| Column         | Description                              |
|----------------|------------------------------------------|
| Domain         | Scanned domain name                      |
| Scan date      | Date and time of the scan                |
| TLS            | Detected TLS protocol version            |
| Expires in     | Days remaining until certificate expiry  |
| Issuer         | Certificate Authority (CA)               |
| Cipher         | Detected cipher suite                    |
| Risk           | Classified risk level                    |
| Notes          | Additional analysis observations         |

---

## 🛠️ Technologies Used

- **Python** — Core language
- **Plotly Dash** — Framework for the interactive web dashboard
- **pytz** — Timezone management
- **CSV / JSON** — Lightweight result storage

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Bryan0-0AG**  
Personal cybersecurity and TLS infrastructure monitoring project.