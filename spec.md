# spec.md

# Crypto Vault – Product Specification (MVP)

## 1. Product Overview

**Crypto Vault** is a DeFi-first personal finance dashboard built on Solana.  
Core value proposition: unified cross-asset tracking with advanced Solana yield analytics and strategy simulation.

Traditional finance (TradFi) features exist as extensions (premium add-ons), while Solana/DeFi functionality is the core product.

Target timeline: 1–2 weeks agent-driven MVP.

---

## 2. Core Principles

- DeFi-first architecture
- Non-custodial (no private keys stored)
- Unified ledger model
- GDPR-ready
- Secure by default
- Mobile-responsive
- Deployable on Vercel (Next.js full-stack)
- TypeScript everywhere

---

## 3. User Roles

### Free User
- Manual entries
- Connect 1 Solana wallet (Phantom)
- On-chain history (last 30 days)
- Real-time yield tracking (no historical)
- 10 OCR receipts/month
- Mobile companion (no alerts)
- No Plaid

### Premium User ($4.99/month)
- Plaid bank sync
- Unlimited OCR
- Alerts (push/email/Telegram)
- Multi-wallet support
- Historical yield analytics
- Strategy simulator (LP backtesting)
- Advanced reporting (CSV/PDF export)
- Protocol comparisons

---

## 4. Core Feature Set

---

## 4.1 Authentication & User Management

- Clerk authentication (email, OAuth)
- Role-based access (free vs premium)
- GDPR consent on signup
- Account deletion (hard delete + cascade)

---

## 4.2 Solana / DeFi Features (Core)

### Wallet Connect
- Phantom wallet connect
- Multi-wallet (premium)
- Store wallet address only
- No private keys

### On-Chain Transaction History
- Powered by Helius API
- Filterable by:
  - Date range
  - Token
  - Program/protocol
  - Transaction type (swap, LP, stake)
- Last 30 days free
- Full history premium

### Yield Tracking

Protocols (MVP):
- Jupiter
- Orca

Features:
- Real-time APR display
- Position value
- Impermanent loss estimation
- USD equivalent

Free:
- Live data only

Premium:
- Historical yield chart
- Protocol comparison
- Yield trend analysis

---

## 4.3 Strategy Simulator (Premium)

Backtest LP positions:

Inputs:
- Token pair
- Entry date
- Exit date
- Initial capital
- Fee APR assumption

Outputs:
- PnL
- Impermanent loss
- Fee earnings
- Final value vs HODL

Limitations:
- No predictive AI
- Historical approximation via price feeds

---

## 4.4 Unified Ledger Model

All transactions stored in single `transactions` table.

Types:
- manual
- bank
- solana

Core fields:
- id
- user_id
- source_type
- chain_id
- tx_hash
- protocol
- category
- amount
- token_symbol
- fiat_value_usd
- timestamp
- metadata (JSON)

Supports:
- Net worth calculation
- Cross-asset analytics
- Budgeting (future)

---

## 4.5 TradFi Extensions

### Manual Entries (Free)
- Add income/expense
- Categorize
- Edit/delete

### Plaid Sync (Premium)
- Account linking
- Daily sync job
- Transaction ingestion
- No bank credentials stored

### OCR (Receipts)

Free:
- 10/month

Premium:
- Unlimited

Pipeline:
- Upload image
- Server-side OCR (Tesseract)
- Extract:
  - Merchant
  - Date
  - Amount
- Create transaction draft

---

## 4.6 Alerts (Premium)

- Yield drop alerts
- Large transaction alerts
- Budget threshold alerts
- Delivery:
  - Email
  - Push (Expo)
  - Telegram bot

---

## 4.7 Reporting

Premium:
- CSV export
- PDF summary
- Tax-ready summary (basic categorization)

---

## 5. Mobile Companion (Expo)

Features:
- Quick manual transaction
- View net worth
- View yield summary
- Push notifications (premium)

---

## 6. Security & Compliance

- HTTPS only
- Encryption at rest (Postgres)
- No private key storage
- GDPR:
  - Data export endpoint
  - Data delete endpoint
- 2-year transaction retention
- Audit logs:
  - Login
  - Wallet connect
  - Transaction create/update/delete

---

## 7. Edge Cases

- Wallet disconnect
- API rate limiting (Helius)
- Duplicate transaction ingestion
- Plaid webhook failures
- Token price missing
- OCR parsing failure
- Protocol API downtime

---

## 8. Risks

- Yield data inaccuracies
- Impermanent loss approximation
- Helius dependency
- Regulatory changes

---

## 9. Non-Goals (MVP)

- Custody
- Trading execution
- On-chain signing
- Complex derivatives
- AI financial advice