# 💡 UX Flow: Send a Tip – Mintlayer Tipping App

This document outlines the high-level user flow for the tipping app prototype.

---

## 🧭 User Journey

### 1. **Launch Web App**
- User navigates to the app via browser (mobile or desktop).
- Clean, intuitive UI is presented.

### 2. **Enter Recipient Information**
- User inputs:
  - Username  
  - Wallet address  
  - Or scans a QR code

### 3. **Select Token Type**
- Choose between:
  - **ML** (Mintlayer token)
  - **BTC** (via Lightning Network)

### 4. **(Optional) Enable zk-Thunder**
- Toggle on for:
  - Privacy
  - Faster transaction via zkRollup Layer 3

### 5. **Enter Tip Amount**
- User specifies amount (with minimum of 0.00001).

### 6. **Submit Tip**
- App:
  - Validates inputs
  - Packages payload as JSON
  - Sends it to backend via `POST /api/send-tip`

### 7. **Process Tip (Backend Flow)**
- Backend checks:
  - Recipient validity
  - Token type
  - zk-Thunder preference
- Executes:
  - Atomic swap or Lightning RPC (for BTC)
  - Mintlayer RPC call (for ML)
  - ZK-based execution if zk-Thunder is enabled

### 8. **Receive Confirmation**
- User sees:
  - Success message with TXID
  - Error alert if something failed

---

## 🔧 Technical Notes

- All actions are client-side JavaScript using `fetch()` for backend interaction.
- Wallet connection is excluded in MVP for compatibility.
- Future versions may support:
  - Wallet connect (Mintlayer extension / Web3)
  - NFT rewards
  - Validator engagement analytics

---

📌 This flow ensures compatibility with Mintlayer infrastructure while staying simple enough for beta testing and rapid feedback.
