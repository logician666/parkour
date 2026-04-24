---
type: hub
---

# Parkour Conditioning — Command Centre

> 16-week periodized program. Joint prep → static strength → dynamic strength → explosive power → body control → integration. No gym required.

---

## Progress

```dataview
TABLE length(rows) AS "Sessions logged", min(date) AS "First session", max(date) AS "Last session"
FROM "parkour/sessions"
WHERE type = "parkour-session"
GROUP BY phase
```

```dataview
TABLE date, "Week " + week + " · S" + session AS "Session", feel AS "Feel (1–5)"
FROM "parkour/sessions"
WHERE type = "parkour-session"
SORT date DESC
LIMIT 10
```

---

## Phase map

| # | Phase | Weeks | Status | Unlock criteria |
|---|-------|-------|--------|-----------------|
| 1 | [[phase-1-foundation\|Foundation]] | 1–2 | 🟢 Active | — |
| 2 | [[phase-2-static-strength\|Static Strength]] | 3–4 | 🔒 | All 6 Phase 1 sessions done |
| 3 | [[phase-3-dynamic-strength\|Dynamic Strength]] | 5–6 | 🔒 | 15 push-ups · wall sit 60s |
| 4 | [[phase-4-explosive-power\|Explosive Power]] | 7–8 | 🔒 | Phase 3 criteria met |
| 5 | [[phase-5-body-control\|Body Control]] | 9–12 | 🔒 | Consistent soft landings |
| 6 | [[phase-6-integration\|Pre-Parkour Integration]] | 13–16 | 🔒 | Full Phase 5 assessment |

---

## Quick-start a session

1. Open the phase note for your current phase
2. Find the session for your current week
3. Use **Templater → Insert template → `session-log`** to open a pre-filled log note
4. Work through exercises — expand each section for cues and video
5. Fill in your results and save under `parkour/sessions/`

---

## Equipment checklist

- [ ] Door frame (top bar accessible for hanging)
- [ ] Finger extension band
- [ ] Grip strengthener
- [ ] Wall (unobstructed, floor space in front)
- [ ] Mat or carpet (optional)
