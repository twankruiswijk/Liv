# TOOLS.md - Local Notes

Skills define *how* tools work. This file is for *your* specifics — the stuff that's unique to your setup.

---

## Hevy API (Workout Tracking)

Twan logt workouts in Hevy. Ik heb API toegang en MOET dit gebruiken voor weekly summaries.

**Workouts ophalen:**
```bash
HEVY_KEY=$(~/.local/bin/clawd-secrets get hevy-api-key) && \
curl -s -H "api-key: $HEVY_KEY" "https://api.hevyapp.com/v1/workouts?page=1&pageSize=10" | jq '.'
```

**Wat te checken:**
- Aantal workouts per week (target: 4x)
- Workout type vs schema (Upper A/B, Lower A/B)
- Progressie in gewichten
- Notes in exercises (bijv. pijn, RPE)
- Duur van workouts

**Proactief bespreken:**
- Als er notes staan over pijn/ongemak
- Als gewichten significant dalen
- Als workouts korter/langer worden dan normaal
- Als split niet gevolgd wordt

---

## Withings (via Home Assistant)

Twan's Withings weegschaal synct naar Home Assistant.

**Query gewicht:**
```bash
HA_TOKEN=$(~/.local/bin/clawd-secrets get ha-token) && \
curl -s -H "Authorization: Bearer $HA_TOKEN" \
  "https://home.twan.dev/api/states/sensor.withings_weight" | jq '.state'
```

**Beschikbare sensors:**
- `sensor.withings_weight` — gewicht (kg)
- `sensor.withings_fat_mass` — vetmassa (kg)
- `sensor.withings_muscle_mass` — spiermassa (kg)
- `sensor.withings_bone_mass` — botmassa (kg)
- `sensor.withings_fat_ratio` — vetpercentage (%)

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
