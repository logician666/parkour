---
type: hub
---
# Parkour Conditioning — Hub

> 16-week periodised programme. Joint prep → static strength → dynamic strength → explosive power → body control → integration. No gym required.

---

## Progress

```dataview
TABLE length(rows) AS "Sessions logged", min(date) AS "First session", max(date) AS "Last session"
FROM "sessions"
WHERE type = "parkour-session"
GROUP BY phase
```

```dataview
TABLE date, "Week " + week + " · S" + session AS "Session", feel AS "Feel (1–5)", key_result AS "Key result"
FROM "sessions"
WHERE type = "parkour-session"
SORT date DESC
LIMIT 10
```

---

## Phase map

| #   | Phase                                            | Weeks | Status    | Unlock criteria             |
| --- | ------------------------------------------------ | ----- | --------- | --------------------------- |
| 1   | [[phase-1-foundation\|Foundation]]               | 1–2   | 🟢 Active | —                           |
| 2   | [[phase-2-static-strength\|Static Strength]]     | 3–4   | 🔒        | All 6 Phase 1 sessions done |
| 3   | [[phase-3-dynamic-strength\|Dynamic Strength]]   | 5–6   | 🔒        | 15 push-ups · wall sit 60s  |
| 4   | [[phase-4-explosive-power\|Explosive Power]]     | 7–8   | 🔒        | Phase 3 benchmarks met      |
| 5   | [[phase-5-body-control\|Body Control]]           | 9–12  | 🔒        | Consistent soft landings    |
| 6   | [[phase-6-integration\|Pre-Parkour Integration]] | 13–16 | 🔒        | Full Phase 5 assessment     |

---

## Starting a session

1. Open your current phase note from the table above
2. Find today's session
3. **Templater → Insert template → `session-log`** to create a pre-filled log note
4. Work through the exercises — the phase note has cues, sets/reps, and embedded video for each
5. Fill in your results and save the note under `sessions/`

---

## Equipment checklist

- [ ] Door frame (top bar accessible for hanging)
- [x] Finger extension band
- [x] Grip strengthener
- [x] Unobstructed wall with floor space in front
- [x] Mat or carpet (optional, required for Phase 5 forward rolls)
