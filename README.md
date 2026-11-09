# n8n Infrastructure & Reliability

> 🇧🇷 [Versão em português abaixo](#-português)

The operational layer behind 36 production workflows: self-hosted n8n on a VPS (Docker + Traefik), backups, error alerting and AI spend guardrails.

**Result: 10 errors in 3,788 executions (99.4% success), Oct 8–28, 2026.**

| File | What it does |
|---|---|
| `01-weekly-backup` | Every Sunday exports all workflows via the n8n API to Drive, keeping the last 8 |
| `02-ai-cost-circuit-breaker` | Every 15 min, no AI: if a Gemini flow runs too often (loop), disables it and alerts; warns at R$ 50 and R$ 63 of the R$ 70 monthly cap |
| `03-error-alert-email` | Error workflow → e-mail to IT |
| `04-error-alert-chat-rate-limited` | Error workflow → Chat DM, max 1 alert per flow per hour |

**Stack:** n8n, Docker, Traefik, VPS, n8n REST API, Google Drive, Google Chat. Credentials and IDs were removed.

---

## 🇧🇷 Português

A camada de operação por trás de 36 workflows em produção: n8n próprio numa VPS (Docker + Traefik), backup semanal, alertas de erro e freio de gasto com IA. Resultado: 10 erros em 3.788 execuções (99,4% de sucesso). Workflows sanitizados.
