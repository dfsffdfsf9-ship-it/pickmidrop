# 🔐 Team Access & Permission Management: PickmiDrop

This document defines the team access matrix, required permissions across platforms, and the onboarding checklist to ensure every team member has the necessary credentials to develop, test, and deploy **PickmiDrop**.

---

## 👥 1. Role-Based Access Matrix

| Role | Repository (GitHub/GitLab) | Steamworks Partner Portal | Telegram Bot / Channel | Secrets Vault (1Password / Vault) |
| :--- | :--- | :--- | :--- | :--- |
| **Project Lead / Admin** | Admin (Owner) | App Admin & Financials | Channel Owner & Bot Admin | Full Access (Production + Staging) |
| **Core Game Developer** | Maintain / Write | Developer (Build Uploads, Steamworks API) | Bot Collaborator (Dev Bot) | Staging / Dev Secrets |
| **Audio & Narrative Designer** | Write (Assets branch) | - | - | Asset CDN / Drive Access |
| **QA / Playtester** | Read / Triage | Release Tester (Steam Beta Branch access) | Channel Subscriber | Staging Build Access |

---

## 🔑 2. Platform Access Setup Checklist

### A. Git Repository Access
- [x] Repository initialized with base branches (`main`, `develop`).
- [ ] Team organization created: `@pickmidrop-devs`.
- [ ] Developers invited with **Write** access.
- [ ] Branch protection rules enabled on `main` and `develop`.
- [ ] CI/CD Runners granted access to repository secrets.

### B. Steamworks Partner Portal
To test Steam integration (Steamworks API, achievements, inventory, cloud saves):
- [ ] Add developers to Steamworks Partner account under the **PickmiDrop** App ID.
- [ ] Grant permissions:
  - *Edit App Metadata*
  - *Publish to Steam* (Lead only)
  - *Manage Steamworks SDK / Dev Build upload*
- [ ] Provide developers with beta test keys or add Steam IDs to the internal dev whitelist.

### C. Telegram Channel & Bot Management
- [ ] Bot created via `@BotFather` (`@PickmiDropBot`).
- [ ] API Token added to team secure password manager.
- [ ] Bot added as Administrator to the official broadcast channel `@pickmidrop_news` with permission to post messages.
- [ ] Webhook URL / dev environment tunneling configured for local test bot.

### D. Environment Variables & Secrets Access
All developers need access to local development secrets. Retrieve `.env.local` via the team vault or contact the team lead:

| Secret Name | Purpose | Distribution |
| :--- | :--- | :--- |
| `STEAM_API_KEY` | Steam Web API authentication for player inventory | Secure Vault |
| `STEAM_APP_ID` | Assigned App ID (or default `480` for local dev) | `.env.example` |
| `TELEGRAM_BOT_TOKEN` | Bot notifications for jackpots & pity drops | Secure Vault |
| `DATABASE_URL` | User profile and persistent pet state (Dev DB) | Secure Vault |

---

## 📋 3. Team Onboarding Steps (For New Developers)

1. **Request Repository Access**: Send your GitHub handle to the team lead to be added to the team group.
2. **Setup SSH Keys**: Configure SSH keys on your GitHub/GitLab account for secure cloning and commits.
3. **Steam Developer Account**: Provide your 64-bit Steam ID (`steamID64`) to receive developer access to the Steamworks sandbox.
4. **Clone & Verify**:
   ```bash
   git clone https://github.com/your-org/pickmidrop.git
   cd pickmidrop
   npm install
   cp .env.example .env
   npm run dev
   ```
5. **Join Team Communications**: Join our Discord / Telegram internal dev group.
