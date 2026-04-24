# Parkour Conditioning Trainer

> A 16-week periodized conditioning program. Now maintained as an Obsidian vault under `parkour/`. The original TSX React app is archived below for reference.

**Obsidian vault:** [[parkour/_hub|Parkour — Command Centre]]
**Original source file (archived):** `~/Downloads/parkour_trainer.tsx`

---

## How to run it locally

```bash
# One-time setup
npx create-react-app parkour-app --template typescript
cd parkour-app

# Replace src/App.tsx with parkour_trainer.tsx content
# Then:
npm start
```

App opens at `http://localhost:3000`. Progress is persisted in `localStorage` under key `parkour_trainer_v2`.

---

## Program architecture

| Phase | Name | Weeks | Goal |
|-------|------|-------|------|
| 1 | Foundation | 1–2 | Joint prep, baseline mobility, deep stabilisers |
| 2 | Static Strength | 3–4 | Isometric endurance, push strength, wall support |
| 3 | Dynamic Strength | 5–6 | Full ROM strength, explosive hip extension |
| 4 | Explosive Power | 7–8 | Nervous system — rapid force production |
| 5 | Body Control | 9–12 | Balance, precision, quadrupedal flow, spatial awareness |
| 6 | Pre-Parkour Integration | 13–16 | Flowing circuits — readiness assessment |

Phases are gated. Each unlocks only when the prior phase criteria are met.

---

## Phase unlock criteria

```
Phase 1 → 2  :  All 6 sessions complete (3 sessions × 2 weeks)
Phase 2 → 3  :  15 push-ups in one set + wall sit 60s
Phase 3 → 4  :  (defined in app)
Phase 4 → 5  :  Consistent soft landings assessed
Phase 5 → 6  :  Full programme assessment
```

---

## Phase 1 — Session map

### Week 1, Session 1 — Joint Prep & Crawl
- Wrist Circles & Flexor Stretch
- Ankle Circles & Calf Raises
- Bear Crawl
- Finger Band Extensions

### Week 1, Session 2 — Hip Mobility & Core Activation
- Deep Squat Hold
- Dead Bug
- Glute Bridge
- Passive Hang (Door Frame Grip)

### Week 1, Session 3 — Movement Patterns
- Hip Hinge (RDL pattern)
- Lateral Lunge
- Plank
- Quadruped Shoulder Taps

> Weeks 2 sessions mirror Week 1 — same exercises, log improvement.

---

## Phase 2 — Session map

### Week 3, Session 1 — Push & Hold
- Incline Push-Up (wall)
- Wall Sit
- Hollow Body Hold
- Wall-Supported Handstand Hold

### Week 3, Session 2 — Posterior Chain & Grip
- Single-Leg Glute Bridge
- Grip Strengthener (slow squeeze)
- Reverse Nordic Curl (assisted)
- Finger Band — Isolated Finger Extensions

### Week 3, Session 3 — Full Body Integration
- Push-Up (max reps, stop 2 before failure)
- Squat Jump (low intensity)
- Side Plank

---

## Session log

Use this to track manually if not using the app.

| Date | Phase | Session | Key result | Notes |
|------|-------|---------|------------|-------|
|      |       |         |            |       |

---

## Design notes

- **Logging types:** `quality` (1–5), `time` (seconds), `reps` (count/set)
- **Storage:** `localStorage` key `parkour_trainer_v2` — clears on browser data wipe; export logs manually if needed
- **Phases 3–6** sessions exist as stubs in the data structure but content is not yet populated
- **Equipment assumed:** door frame for hangs, finger extension band, grip strengthener, wall

---

## Obsidian integration (optional plugins)

To track sessions inside Obsidian without using the app:

| Plugin | Purpose | Install |
|--------|---------|---------|
| **Tasks** | Checkbox-based session tracking with due dates | Community plugins → search "Tasks" |
| **Dataview** | Query session logs from daily notes into a summary table | Community plugins → search "Dataview" |
| **Templater** | Generate a pre-filled session note per workout | Community plugins → search "Templater" |

### Minimal session template (Templater)

Create `Templates/parkour-session.md`:

```
---
date: <% tp.date.now("YYYY-MM-DD") %>
type: parkour-session
phase: 
week: 
session: 
---

## Session: <% tp.date.now("YYYY-MM-DD") %>

**Phase:**   
**Week / Session:**   

| Exercise | Result | Notes |
|----------|--------|-------|
|          |        |       |

**How I felt:** 
**What to improve:**
```

Then use Dataview to aggregate:

````dataview
TABLE date, phase, week, session
FROM "1-daily" OR "0-unique"
WHERE type = "parkour-session"
SORT date DESC
````

---

*Tool authored for home-equipment parkour conditioning. No gym required.*
