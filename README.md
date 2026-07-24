# Digital Pumice 🪨

> **Continuous Automated Personal Data Scrubbing & Opt-Out Engine**

`digital-pumice` is an open-source, privacy-first automated tool designed to continuously discover, opt-out, and scrub your sensitive Personally Identifiable Information (PII)—including home addresses, phone numbers, email aliases, family associations, and public record markers—from data brokers, people-search websites, and web scrapers.

Just as a pumice stone wears away rough surfaces, **Digital Pumice** continuously smooths away your online privacy footprint, ensuring that once your data is removed, it stays removed.

---

## ⚡ Key Features

- **Continuous PII Monitoring**: Constantly scans data broker networks, public registries, and people-search engines for new or re-listed entries containing your address, phone number, or name.
- **Automated Opt-Out Engine**: Programmatically submits legal opt-out and removal requests (under CCPA, GDPR, CPRA, and state privacy acts) to dozens of major data aggregators.
- **Re-listing Prevention Guard**: Data brokers frequently re-acquire public records and recreate profiles. Digital Pumice runs scheduled background audits to trigger fresh removal requests whenever data reappears.
- **Zero-Knowledge Local Hashing**: Your identity profile (addresses, phone numbers, SSN fragments) is stored strictly locally in encrypted, zero-knowledge storage. Scans use privacy-preserving match tokens.
- **Verification & Audit Ledger**: Tracks the exact status of every opt-out request (Pending, Submitted, Confirmed, Rejected, Verified Removed) with clear audit trails.

---

## 🏗 System Architecture

```
                       +-------------------------------+
                       |    Encrypted Local Profile    |
                       | (Addresses, Phones, Aliases)  |
                       +---------------+---------------+
                                       |
                                       v
                       +---------------+---------------+
                       |   Digital Pumice Core Engine  |
                       +---------------+---------------+
                                       |
         +-----------------------------+-----------------------------+
         |                             |                             |
         v                             v                             v
+------------------+         +-------------------+         +-------------------+
|  Data Broker     |         |  Opt-Out Request  |         |  Verification &   |
|  Scanner         |         |  Automator        |         |  Re-list Monitor  |
+--------+---------+         +---------+---------+         +---------+---------+
         |                             |                             |
         v                             v                             v
+------------------+         +-------------------+         +-------------------+
| Whitepages,      |         | Automated Web &   |         | Periodic Re-Scan  |
| Spokeo, Radaris, |         | Email Removal     |         | Escalation        |
| Intelius, etc.   |         | Workflows         |         | Alerts            |
+------------------+         +-------------------+         +-------------------+
```

---

## 🛠 Supported Data Broker Categories

| Category | Aggregators & Brokers Covered | Actions Taken |
| :--- | :--- | :--- |
| **People Search** | Spokeo, Whitepages, FastPeopleSearch, BeenVerified, Radaris, Intelius, TruthFinder | Automated opt-out form submission & email confirmation link processing |
| **Public Record Aggregators** | LexisNexis, Verisk, InstantCheckmate, PeopleLooker | Legal suppression requests & identity verify opt-outs |
| **B2B / Contact Brokers** | ZoomInfo, Apollo.io, RocketReach, Lusha | Business record opt-outs & email pattern suppression |
| **Background Check Sites** | CheckPeople, USSearch, InstantCheckmate | FCPA & State Privacy opt-out requests |

---

## 🚀 Quick Start

### Prerequisites

- Node.js (v18+) or Python (3.10+)
- Docker (optional, for running continuous background daemon)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/digital-pumice.git
cd digital-pumice

# Install dependencies (Node environment example)
npm install
```

### Configuration

Create a local `.env` or `config.yaml` file to define your PII matching parameters (stored encrypted locally):

```yaml
profile:
  full_name: "Jane Doe"
  previous_names: ["Jane Smith"]
  phone_numbers:
    - "+1-555-019-2834"
  addresses:
    - street: "123 Main St"
      city: "San Francisco"
      state: "CA"
      zip: "94105"
  emails:
    - "jane.doe@example.com"
settings:
  scan_frequency: "daily"   # daily, weekly, monthly
  auto_confirm_emails: true # automatically process confirmation links
```

---

## 💻 Usage & CLI Commands

```bash
# Run a dry-run privacy exposure scan
npx digital-pumice scan

# Execute opt-out submission across all matched brokers
npx digital-pumice scrub

# Launch continuous monitoring daemon
npx digital-pumice monitor --daemon

# Generate a removal verification summary report
npx digital-pumice report --format markdown
```

---

## 🔒 Security & Privacy Guarantees

- **No Remote Telemetry**: `digital-pumice` does not send your data to any centralized server. All requests originate directly from your client network interface.
- **Local Vault Encryption**: Local config files are encrypted using AES-256-GCM derived from your personal master passphrase.
- **Open & Auditable**: Every request header, payload, and API call is fully open source and transparent.

---

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details on submitting pull requests, adding new data broker opt-out modules, and improving scanning algorithms.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

<!-- Engine Status: Active - July 24, 2026 -->

