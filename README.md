# ⚽ FM Team Manager — Highway Star 4-2-3-1

A single-file web app that replaces your Excel player-evaluation workbook for Football Manager.
It uses **your own scoring model** (same weights, same numbers — Marcus Jones still scores 11.03) and adds:

- 👥 **Squad** — every player scored 0–20 for his role (sort / filter / change role)
- ⚽ **Best XI** — strongest legal Highway Star 4-2-3-1 on a pitch + bench + best youth option per slot
- 🌱 **Youth & Training** — young players worth developing, with a verdict
- 🗑️ **Release list** — who to sell/release and why
- 📈 **Progression** — attribute gains vs an older snapshot
- 🗂️ **History** — all snapshots + score over time + settings
- 🏆 **Tactics** — full Highway Star 4-2-3-1 setup to stop losing
- 📖 **Notice** — how it works + every metric defined

Everything runs in the browser. **No server, no account, no data leaves your device.**

---

## Use it locally (right now)
Double-click `index.html`. That's it. It already contains your current 84-player squad.

## The 6-month routine (refresh your data)
1. In FM, open your squad view with all attributes **and** your `Position/Role/Duty` column.
2. **Print Screen → Web page / Text** → FM saves `Untitled.html`.
3. App → **📥 Update data** → drop that file in (or paste it). Every tab recomputes.
4. Click **📌 Save current as snapshot** so Progression & History have a dated point.

## Move data between PC and phone
- On PC press **💾 Backup** → it downloads a `.json`.
- Email it / put it in Drive → open it on your phone → press **↩ Restore**.

---

## Put it online (free public link, works on mobile)

### Option A — GitHub Pages (the "link" you wanted)
1. Create a free account at <https://github.com> if you don't have one.
2. Click **New repository** → name it e.g. `fm-team-manager` → **Public** → **Create**.
3. On the repo page click **Add file → Upload files** → drag in `index.html` (and this `README.md`) → **Commit changes**.
4. Go to **Settings → Pages** → under *Build and deployment*, Source = **Deploy from a branch**, Branch = **main**, folder = **/ (root)** → **Save**.
5. Wait ~1 minute. Your link appears at the top of the Pages screen:
   `https://YOURNAME.github.io/fm-team-manager/`
6. Open that link on your phone, add it to your home screen. Done.

To update the app later: **Add file → Upload files** → drop a new `index.html` → commit. Pages redeploys automatically.

> Your squad **data** lives in each browser (localStorage) + your backup files — it is **not** stored in the GitHub repo, so the public repo only contains the app, not your save details.

### Option B — keep it private
Same as above but make the repo **Private**. Note: GitHub Pages on a private repo needs a paid plan; for free private use, just run `index.html` locally and sync with backup files.

---

## How the score works
For a player in a role:

```
Score = ( foot points + Σ attribute × role-weight ) ÷ role-max × 20
```

- **foot points** — Very Strong 10, Strong 8, Fairly Strong 6, Reasonable 4, Weak 2, Very Weak 0 (left + right)
- **role-weight** — your per-role attribute weights (e.g. an Inside Forward weights Pace 1.0, Acceleration 1.0, Aggression 0.15)
- **role-max** — your per-role maximum (IF = 212, etc.)

It is a **fit** rating (how well his attributes suit that role), not the player's potential.

## The 7 roles → Highway Star 4-2-3-1
| Slot | Role |
|---|---|
| GK | SK – Defend |
| D R / D L | FB – Attack |
| D C ×2 | BPD – Defend |
| DM ×2 | DM – Support |
| AM R / AM L | IF – Support |
| AM C | AM – Attack |
| ST | AF – Attack |

Built from `FM25_Evaluation_Joueurs.xlsx`. The app is the dynamic replacement for that workbook.
