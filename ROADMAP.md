# Agency Roadmap

> Last updated: 2026-05-10

This roadmap describes the evolution of Agency from terminal-first runtime to full cross-platform working organization. Each version has a clear thesis, completion criteria, and explicit non-goals.

---

## V1 — Terminal-First Local Office ✅

**Thesis:** A developer can install Agency in one command, boot a local office, staff it with agents, and watch autonomous work happen in a beautiful terminal UI.

**Status:** Shipped

### V1 Completed

| Feature | Evidence |
|---------|----------|
| Terminal CLI/TUI | `cmd/agency.go`, `internal/tui/` — iMessage bubbles, sidebar, overview, dialogs |
| Local runtime | `Procfile`, `scripts/build-daemons` — Redis + Overmind + 4 daemon types |
| Provider routing | `internal/agency/routing.go` — 5 providers, hard gates, soft scoring |
| GIST cognitive layer | `internal/agency/gist_core.go` — causal compression, elastic stretch |
| Approvals, bulletin, ledger | `internal/agency/ledger.go`, `consensus.go` — append-only, quorum, commit certificates |
| Voice synthesis | `internal/agency/voice.go` — Kokoro TTS map, prosody, macOS `say` fallback |
| Genesis wizard | `internal/agency/genesis.go` — natural language → staffed office |
| One-command install | `install` script — Go, Redis, Overmind, clone, build, link |
| Release proof | `scripts/live-release-proof`, `scripts/verify-release-proof` |

### V1 Explicit Non-Goals
- Cloud hosting or SaaS offering
- Web dashboard
- Mobile apps
- Real-time collaboration between multiple human users
- Plugin marketplace

---

## V2 — Desktop, Voice, and Docker Parity 🚧

**Thesis:** The terminal runtime becomes a substrate. A native macOS app provides a windowed experience. Voice reaches product quality. Docker packaging achieves parity with local runtime.

**Target:** Q3 2026

### V2 Features

| Feature | Description | Status |
|---------|-------------|--------|
| **macOS Desktop App** | SwiftUI window into the local office: bubbles, bulletin, voice, approvals, agent status | 🚧 Design |
| **IPC Transport Layer** | Unix socket server exposing ledger events + approval actions to local clients | 🚧 Design |
| **Product-Quality Voice** | Full Kokoro integration with install script, model download, prosodic adaptation per signal kind | 🚧 Partial |
| **Docker Parity** | Docker Compose achieves full feature parity with local Redis + Overmind path | 🚧 Optional packaging exists |
| **Versioned Constitutions** | Bump constitution version without full re-genesis; affected roles re-plan only | 🚧 Design |
| **Adversarial Reviewer Agent** | Auto-spawned reviewer challenges proposals before finalization | 🚧 Design |
| **Agent Spawning** | Tier-2 actors create child actors at runtime | 🚧 Design |
| **Timezone Schedule Windows** | Honor business hours config in cron expressions | 🚧 Design |
| **Replay Harness** | Simulate what agents would do given any historical ledger window | 🚧 Design |

### V2 Completion Criteria
- [ ] macOS app runs `agency office boot` and shows live TUI-equivalent experience
- [ ] Voice install is one command and works out of the box on macOS
- [ ] Docker Compose passes the same live-release-proof as local runtime
- [ ] Constitution versioning works without data migration
- [ ] At least one V2 feature (adversarial reviewer or agent spawning) is live

### V2 Non-Goals
- iOS/Android apps (V3)
- Web dashboard (V3)
- Multi-office federation (V3+)
- Plugin marketplace (V4)

---

## V3 — Web, Mobile, and Multi-Office 🎯

**Thesis:** Agency expands beyond the single developer's machine. Web control plane for remote management. Mobile companions for approvals on the go. Multiple offices can federate.

**Target:** Q1 2027

### V3 Features

| Feature | Description |
|---------|-------------|
| **Web Control Plane** | React/Next.js dashboard: org viewer, approval lane, schedule editor (visual cron tree), ledger/log inspector, multi-office admin |
| **WebSocket Transport** | Remote clients subscribe to Redis event bus via WebSocket — same schema as IPC |
| **iPad/iPhone Companion** | Approvals, bulletin, agent status, quick triggers, emergency stop/resume. Not full parity. |
| **Context Snapshot Sync** | New clients catch up instantly via `ContextSnapshot` on connect |
| **Multi-Office Federation** | Multiple offices coordinating across Redis channels with shared ledger segments |
| **Encrypted Vault** | Server-side credential storage for cloud deployments |
| **OAuth Provider Support** | Official OAuth flows for providers that support native app auth |

### V3 Completion Criteria
- [ ] Web dashboard can create an office, view agents, and approve actions
- [ ] Mobile app can receive push notifications for supervised actions
- [ ] Two offices on different machines can share a ledger segment
- [ ] All V1 features accessible from web and mobile surfaces

### V3 Non-Goals
- SaaS pricing or billing (V4)
- Enterprise SSO/SAML (V4)
- Custom agent marketplace (V4)
- Third-party hosting platform (V4)

---

## V4 — Platform and Ecosystem 🔮

**Thesis:** Agency becomes infrastructure. Hosted options, enterprise features, and an ecosystem of shareable roles, constitutions, and tools.

**Target:** 2027+

### V4 Features

| Feature | Description |
|---------|-------------|
| **Hosted Agency** | Managed cloud instances with SLA |
| **Enterprise SSO** | SAML, OIDC, SCIM provisioning |
| **Role Marketplace** | Community-contributed role archetypes with ratings |
| **Tool Bindings SDK** | Third-party tools publish MCP-compatible bindings |
| **Audit Compliance** | SOC 2 Type II, GDPR compliance features |
| **Advanced Analytics** | Office performance dashboards, agent efficiency metrics |

---

## How We Prioritize

1. **Local-first always.** Cloud is additive, not replacement.
2. **Terminal is canonical.** Other surfaces are windows into the same runtime.
3. **Ledger is truth.** Any feature that breaks ledger integrity is vetoed.
4. **Voice is humanizing.** Every surface should support voice where appropriate.
5. **Privacy by design.** Local routing preferred. Secrets never in ledger.

---

## Contributing to the Roadmap

- Open a [Discussion](https://github.com/ETEllis/agency/discussions) for feature ideas
- Open an [Issue](https://github.com/ETEllis/agency/issues) for specific V2/V3 feature requests
- Comment on existing issues to help prioritize

Roadmap decisions are made by maintainers with community input. We ship V1 before designing V4.
