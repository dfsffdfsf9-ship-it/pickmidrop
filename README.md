# 🎀 PickmiDrop

> **"Spin the wheel, win the trash, feed your pet, repeat."**  
> A desktop gambling parody/simulator game concept designed for Steam, inspired by *MusorDrop* (*TrashDrop*).

---

## 🎓 Школьная демонстрация проекта (Quick School Demo)

Для быстрой и надежной демонстрации проекта на уроке или защите:

### Способ 1: Без установки (Мгновенный запуск в любом браузере)
1. Откройте папку проекта: `PickmiDrop`.
2. Дважды кликните по файлу **`index.html`** (или откройте его через Chrome / Edge / Яндекс.Браузер).
3. Промо-страница с темной фиолетовой темой, постером и интерактивной рулеткой откроется моментально без подключения к интернету или серверам.

### Способ 2: Через Vite / npm
Если на компьютере установлен Node.js:
```bash
cd PickmiDrop
npm install
npm run dev
```
Страница будет доступна по адресу `http://localhost:5173/`.

### Сценарий показа для презентации:
1. **Логотип и стиль**: покажите рулетку с бантом (символ самоиронии и стиля «Pick-me»).
2. **Слоган**: *«Испытай удачу!»* и промо-текст: *«Открывай кейсы. Получай дропы.»*.
3. **Рекламный постер**: раздел постера с ключевыми особенностями игры.
4. **Интерактивный блок «Твой дроп ждёт!»**: нажмите кнопку *«🎡 Крутить рулетку»*, чтобы показать симуляцию выпадения дропа (мусор из бесплатного кейса, яйцо питомца или тайный нож).
5. **Безопасность**: подчеркните, что в проекте нет реальных платежей и ставок — это игровой симулятор-пародия.

---

## 🎡 About The Project

**PickmiDrop** is an odds-based desktop application integrating Steam authentication and Steam inventory mechanics. Players can open cases, spin odds-based roulettes, upgrade items, unlock achievements, and interact with community systems.

### 🎀 Brand & Logo Concept
* **Logo**: A roulette wheel decorated with an oversized cute pink/pastel satin bow (ribbon) — juxtaposing high-stakes gambling aesthetics with playful "pick-me" irony.
* **Mascot / Pet System**: Tamagotchi-style pet hatched from rare egg drops.

---

## ✨ Key Features & Mechanics

| Feature | Description |
| :--- | :--- |
| **Steam Integration** | Steam OpenID login, Steamworks API integration, and Steam Inventory Service / trade bot connectivity for CS & Dota 2 skins. |
| **Engaging Voice-Overs** | Dynamic, humorous voice commentary and announcer packs reacting to roulette spins, near-misses, big wins, and disastrous losses. |
| **"Free Case" (100% Trash)** | A daily/free case brimming with worthless, absurd junk items (consumer grade sprays, broken p250 sand dunes, rusty dota bracers). |
| **Odds-Based Upgrade / Tier-Up** | Stake low-tier skins for a calculated percentage chance to upgrade into higher-tier knives, gloves, arcanas, or immortals. |
| **The "Depression Test"** | An interactive mini-game / quiz assessing the player's psychological state after losing a 90% upgrade streak, awarding snarky badges and consolation tokens. |
| **Pity System** | Escalating odds guarantee a high-tier drop or egg drop after a designated threshold of consecutive unboxed low-tier skins. |
| **Egg & Pet System** | Chance to hatch a companion pet from drop eggs. Feed duplicate/unwanted skins to keep it alive and happy. In return, the pet grants temporary buffs (e.g. +1.5% upgrade odds). Note: Pets have a limited lifespan and expire if neglected! |
| **Telegram Community Integration** | Live broadcast channel for jackpot drops, promo code drops, daily announcements, and user community rankings. |
| **Steam Achievements** | Unlock milestones such as *"Rock Bottom"*, *"Gordon Gekko of Sand Dunes"*, *"Pet Hoarder"*, and *"Failed at 99%"*. |

---

## 🛠 Tech Stack Overview & Key Tool Versions

For reproducible builds and environment consistency (see [ENVIRONMENT.md](file:///c:/Users/sladk/Downloads/PickmiDrop/ENVIRONMENT.md) for full details):

- **Node.js**: `v20.18.0 LTS` (specified in [`.nvmrc`](file:///c:/Users/sladk/Downloads/PickmiDrop/.nvmrc) and [`package.json`](file:///c:/Users/sladk/Downloads/PickmiDrop/package.json) `"engines"`)
- **npm**: `v10.8.2` (`>= 10.2.0`)
- **Vite**: `^5.2.11`
- **React**: `^18.3.1`
- **TypeScript**: `^5.4.5`
- **Tailwind CSS**: `^3.4.3`
- **Steam Integration**: [`steamworks.js`](https://github.com/GreenheartGames/steamworks.js) (`^0.3.1`)
- **Audio Engine**: [`howler`](https://github.com/goldfire/howler.js) (`^2.2.4`) & Web Audio API
- **State Management**: [`zustand`](https://github.com/pmndrs/zustand) (`^4.5.2`)

---

## 🔒 Security & Secrets Policy
- **No secrets in git**: Real Steam API keys, Telegram bot tokens, and server secrets must **NEVER** be committed.
- [`.env.example`](file:///c:/Users/sladk/Downloads/PickmiDrop/.env.example) contains only non-sensitive development mock defaults and placeholders.
- [`.gitignore`](file:///c:/Users/sladk/Downloads/PickmiDrop/.gitignore) prevents accidental commits of `.env*`, `*.pem`, `*.key`, `*.cert`, `*.pfx`, and private credentials.

---

## 🚀 Getting Started & Launch Instructions

### 1. Prerequisites
Ensure you have the following installed on your development machine:
- [Node.js](https://nodejs.org/) (v20.x or higher recommended)
- [Rust](https://www.rust-lang.org/tools/install) (if running via Tauri desktop runner)
- [Git](https://git-scm.com/)
- Steam Client running on desktop with an active Steam account (required for Steamworks dev API mocking)

### 2. Clone the Repository
```bash
git clone https://github.com/your-org/pickmidrop.git
cd pickmidrop
```

### 3. Install Dependencies
```bash
npm install
```

### 4. Configure Environment Variables
Copy the `.env.example` file to `.env`:
```bash
cp .env.example .env
```
Fill in the required configuration variables:
```env
# Steam Configuration
STEAM_APP_ID=480 # 480 is Spacewar for local development testing
STEAM_API_KEY=your_steam_web_api_key_here

# Telegram Integration
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
TELEGRAM_CHANNEL_ID=@pickmidrop_news

# Application Settings
VITE_APP_TITLE=PickmiDrop
VITE_ENABLE_MOCK_STEAM=true # Set to true to test without active Steamworks connection
```

### 5. Launch in Development Mode
To start the application locally with hot-reloading:

```bash
# Run web preview
npm run dev

# Or run desktop app window
npm run tauri:dev # (or `npm run electron:dev`)
```

### 6. Build for Production / Steam Release
```bash
npm run build
npm run tauri:build
```
Binaries and installers will be generated under `src-tauri/target/release/bundle/`.

---

## 📁 Repository Structure

```text
pickmidrop/
├── .github/
│   ├── PULL_REQUEST_TEMPLATE.md    # PR checklist and format
│   └── workflows/                  # CI / CD build and lint checks
├── docs/
│   ├── ARCHITECTURE.md             # System design and drop probability models
│   └── STEAM_INTEGRATION.md        # Steamworks SDK and trade mechanics
├── public/
│   ├── audio/                      # Voice-overs and sound FX
│   └── icons/                      # App logos (roulette + bow)
├── src/
│   ├── assets/                     # Sprites, animations, skin textures
│   ├── components/
│   │   ├── Roulette/               # Spinning wheel component & physics
│   │   ├── CaseOpening/            # Free trash case & crate opening UI
│   │   ├── Upgrade/                # Odds-based tier-up system
│   │   ├── Pet/                    # Egg incubator & skin feeding Tamagotchi
│   │   ├── DepressionTest/         # Interactive mini-quiz
│   │   └── Achievements/           # Steam achievement notifications
│   ├── hooks/                      # Steam API, audio player hooks
│   ├── services/                   # Telegram bot client, Steam trade logic
│   └── store/                      # Zustand state for inventory, pity counters
├── .env.example
├── CONTRIBUTING.md                 # Branching rules, commit format, and PR rules
├── TEAM_ACCESS.md                  # Access setup checklist and role matrix
├── LICENSE
├── package.json
└── README.md
```

---

## 🤝 Contribution & Team Workflow

To ensure code quality and seamless team collaboration:
- **Continuous Integration (CI)**: All pushes and PRs are automatically checked by GitHub Actions. Read our [**CI/CD Documentation (docs/CI_CD.md)**](file:///c:/Users/sladk/Downloads/PickmiDrop/docs/CI_CD.md).
- **Local Checks**: Run `npm test` or `npm run validate` locally before opening a PR.
- Please read our [**Branching & Commit Guidelines (CONTRIBUTING.md)**](file:///c:/Users/sladk/Downloads/PickmiDrop/CONTRIBUTING.md).
- Follow the [Conventional Commits](https://www.conventionalcommits.org/) standard.
- All code changes must go through Pull Requests with at least 1 peer approval.
- See [**Team Access Guide (TEAM_ACCESS.md)**](file:///c:/Users/sladk/Downloads/PickmiDrop/TEAM_ACCESS.md) for Steamworks and repository onboarding.

---

## 📄 License
Internal proprietary project for the PickmiDrop Dev Team. All rights reserved.
