# Breakpoint

A competitive social-strategy prison progression game built on Roblox with a Rust-powered backend. Players begin in the lowest security prison and attempt to escape into progressively harder facilities, emphasizing strategy, alliances, betrayal, and reputation-driven progression.

## Inspired By

![Inspiration](https://github.com/user-attachments/assets/5b026dfd-c511-40bc-8582-edae27856d3b)


## Overview

**Breakpoint** is a multiplayer strategy game where:
- Players start in Tier 1 prisons and work toward higher-tier escapes
- Gameplay focuses on forming alliances, strategic planning, and navigating betrayal mechanics
- A persistent reputation system tracks player behavior across seasons
- Competitive leaderboards and prestige rewards recognize top players
- Server-validated escape simulation ensures fair and cheat-resistant gameplay

## Core Features

### 1. **Escape Simulation & Progression**
- Configurable escape probability based on tier difficulty
- Player planning, preparation, and resource management
- Seasonal cycles with limited escape slots per prison
- Tier advancement for successful escapes, demotion for catastrophic failures

### 2. **Reputation System**
- Persistent reputation scoring across seasons
- Betrayal tracking and alliance formation mechanics
- Influence on escape success rates and social standing
- Historical reputation archives for prestige recognition

### 3. **Tier Management**
- Progressive difficulty scaling
- Resource scarcity increases with tier
- Guard complexity and detection mechanics
- Escape slot economy (supply vs. demand)

### 4. **Leaderboards & Seasons**
- Real-time global and tier-specific rankings
- Seasonal resets with prestige badges
- Historical season archives
- Cosmetic and achievement rewards

### 5. **Anti-Cheat & Validation**
- Server-side escape simulation validation
- Anomaly detection for suspicious patterns
- Transaction-safe reward distribution
- Audit trails for moderation

### 6. **Cosmetic Monetization**
- Prison outfit cosmetics
- Escape animation effects
- Prestige badges and seasonal passes
- **No pay-to-win mechanics**

## Tech Stack

- **Backend**: Rust (Axum + Tokio)
- **Client**: Roblox (Luau)
- **Database**: PostgreSQL
- **Cache**: Redis
- **Deployment**: Docker + Cloud Provider
- **API**: REST + WebSocket for real-time updates

## Project Structure

```
breakpoint/
├── backend/                    # Rust backend service
│   ├── src/
│   │   ├── main.rs            # Entry point
│   │   ├── models/            # Data structures
│   │   ├── handlers/          # API request handlers
│   │   ├── services/          # Business logic
│   │   ├── db/                # Database queries and migrations
│   │   ├── simulation/        # Escape simulation engine
│   │   ├── reputation/        # Reputation & betrayal system
│   │   ├── anticheat/         # Anomaly detection
│   │   └── config.rs          # Configuration & constants
│   ├── Cargo.toml
│   └── .env.example
├── game/                       # Roblox game client (Luau)
└── README.md                   # This file
```

## Getting Started

### Prerequisites
- Rust 1.70+
- PostgreSQL 14+
- Redis 6+
- Docker (optional, for containerized deployment)

### Backend Setup

1. **Navigate to the backend directory:**
   ```bash
   cd backend
   ```

2. **Create a `.env` file from the template:**
   ```bash
   cp .env.example .env
   ```

3. **Configure environment variables:**
   ```
   DATABASE_URL=postgresql://user:password@localhost/cellblock_ascension
   REDIS_URL=redis://localhost:6379
   PORT=8080
   RUST_LOG=info
   ```

4. **Set up the database:**
   ```bash
   sqlx migrate run
   ```

5. **Build and run:**
   ```bash
   cargo build --release
   cargo run --release
   ```

### Docker Setup

```bash
docker-compose up --build
```

## API Endpoints (Planned)

### Authentication
- `POST /auth/register` - Create new player account
- `POST /auth/login` - Player authentication
- `POST /auth/logout` - Revoke session

### Player Management
- `GET /players/:id` - Fetch player profile
- `PUT /players/:id` - Update player info
- `GET /players/:id/reputation` - View reputation history

### Escapes
- `POST /escapes/attempt` - Initiate escape attempt
- `GET /escapes/:id` - Retrieve escape result
- `GET /players/:id/escapes` - View player escape history

### Reputation & Alliances
- `POST /alliances` - Form alliance
- `DELETE /alliances/:id` - Disband alliance
- `POST /reputation/betray` - Report betrayal

### Leaderboards
- `GET /leaderboards/global` - Global rankings
- `GET /leaderboards/tier/:tier` - Tier-specific rankings
- `GET /leaderboards/season/:season` - Seasonal rankings
- `GET /seasons/current` - Current season info

### Admin
- `POST /admin/flag-anomaly/:id` - Flag suspicious activity
- `GET /admin/audit/:id` - View audit trail

## Development Workflow

1. **Create a feature branch:**
   ```bash
   git checkout -b feature/escape-simulation
   ```

2. **Make changes and test:**
   ```bash
   cargo test
   cargo clippy
   ```

3. **Format code:**
   ```bash
   cargo fmt
   ```

4. **Commit and push:**
   ```bash
   git push origin feature/escape-simulation
   ```

## Key Modules

### `simulation/`
Escape probability calculation, guard detection, resource constraints.

### `reputation/`
Reputation scoring algorithms, betrayal tracking, alliance management.

### `anticheat/`
Anomaly detection patterns, suspicious activity flagging, validation rules.

### `handlers/`
HTTP handlers for client requests, request validation, response serialization.

### `services/`
Core business logic for escapes, tier progression, leaderboard calculations.

### `db/`
SQL migrations, query builders, transaction management.

## Success Metrics

- Daily Active Users (DAU)
- Tier progression distribution
- Average session duration
- Seasonal retention rate
- Cosmetic purchase conversion rate

## License

[Add your license here]

## Contact & Support

For questions or contributions, reach out to the development team.
