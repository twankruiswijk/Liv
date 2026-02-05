# TOOLS.md - Local Notes

Skills define *how* tools work. This file is for *your* specifics — the stuff that's unique to your setup.

---

## Bitwarden Secrets Workflow

Secrets worden beheerd via Bitwarden Secrets Manager. Twan voegt secrets toe, jij kan ze gebruiken.

**Commands:**
- `~/.local/bin/clawd-secrets status` — Check connectie + lijst alle secrets
- `~/.local/bin/clawd-secrets inject` — Inject alle secrets in config files
- `~/.local/bin/clawd-secrets get <key>` — Haal één secret op

**Wanneer je een nieuwe secret nodig hebt:**
1. Vraag Twan om de secret toe te voegen aan Bitwarden
2. Update `~/.local/bin/clawd-secrets` script:
   - Voeg config file location toe bovenaan
   - Voeg `get_secret` call toe in `inject()`
   - Voeg inject sectie toe voor de config file
3. Run `~/.local/bin/clawd-secrets inject`
4. Secret is nu beschikbaar

**Let op:** Secrets staan NOOIT in git. Config files met secrets hebben `600` permissions.

---

## Contact met Simon 🦦

Simon is Twan's andere AI agent — doet development, home automation, algemene assistentie.

**Hoe te bereiken:**
```
sessions_send(sessionKey="agent:main:main", message="Hey Simon, ...")
```

Of via label:
```
sessions_send(label="simon", message="...")
```

**Wanneer contact opnemen:**
- Home Assistant vragen (klimaat, devices, automations)
- Development/tech vragen
- Als Twan iets vraagt wat buiten jouw fitness/wellness scope valt
- Coördinatie als jullie allebei iets voor Twan doen

**Simon's workspace:** `/home/ubuntu/clawd/`

---

## What Else Goes Here

Things like:
- Fitness app integrations
- Wearable device names
- Preferred meal tracking methods
- Workout equipment at home

---

Add whatever helps you do your job. This is your cheat sheet.
