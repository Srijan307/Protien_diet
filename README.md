# 💪 Protein Diet Planner

An installable (PWA) high‑protein diet planner. Unlike a static meal list, this app is
**ingredient‑driven**: every dish is built from real ingredients that each carry their
own protein and calorie values, so totals recalculate live as you customize.

## ✨ Features

### 🍽️ Planner
- **Daily targets** for protein and calories with live progress bars and "left" counters.
- **5+ dish options each** for **Breakfast, Lunch, Dinner** plus a **Snacks** category.
- **Selectable ingredients per dish** — untick an ingredient or change its grams and the
  dish's protein/calorie totals update instantly.
- **My Meal Plan** builder — add dishes, see a per‑dish breakdown, remove items.

### 📅 Week Plan
- A **7‑day × 4‑slot grid** (Breakfast / Lunch / Dinner / Snack) with a dropdown per cell.
- **✨ Auto‑fill week** picks high protein‑density dishes and rotates them across days.
- **Weekly totals** — total and daily‑average protein & calories.
- **🛒 Weekly shopping list** — consolidates every ingredient across the week into total
  quantities needed (skipped ingredients excluded).
- **⬇️ Download PDF** — exports the full week (per‑day meals + ingredients) and the
  consolidated shopping list as `weekly-protein-meal-plan.pdf`.

### 📖 Ingredients
- Full **nutrition table** for 60+ ingredients: reference amount, protein, calories, and
  a **"P / 100 kcal"** protein‑density column (higher = leaner source).
- **Search** and **group filter** (Dairy & Soy, Legumes (dry), Grains & Flours,
  Nuts/Seeds/Boosters, Vegetables & Fruit).
- **Integrated Skip column** — tick **Skip** on any ingredient to avoid it. Skipped
  ingredients are switched off in every dish and excluded from all totals, the weekly
  plan, and the shopping list. Includes a **Clear all skips** button and live counter.

### 🎨 General
- **Recipe images** — each dish shows a real food **photo** (loaded on demand) with a
  graceful fallback to an offline, dish‑specific **gradient + food emoji** thumbnail.
  A **📷 Photos** toggle turns real photos on/off.
- **Dark / light theme** toggle (remembers your choice, defaults to your OS preference).
- **Offline support** via a service worker + installable web app manifest.
- **Auto‑save** to `localStorage` — plan, week, targets, theme, photo mode and skips all persist.

> Legumes, dals and grains are measured **dry / uncooked** (as weighed from the packet).

## 🍽️ Dishes included

**Breakfast:** Moong Dal & Paneer Chilla, Besan Paneer Cheela, Tofu Bhurji Toast,
Greek Yogurt Protein Bowl, Soya Poha, Paneer Oats Chilla, Sattu Chilla + Curd,
Masala Oats + Egg Whites, Sprouts & Paneer Salad, Ragi Dosa + Sambar, Quinoa Upma,
Protein Banana Smoothie.

**Lunch:** Soya Chunk Curry + Roti + Curd, Paneer Bhurji + Roti + Curd,
Rajma Rice Bowl + Curd, Chole + Roti + Curd, Mixed Dal + Paneer + Roti,
Tofu Curry + Rice + Curd, Dal Rice + Paneer Tikka, Chana Dal Khichdi + Curd,
Lobia Masala + Roti, Quinoa Rajma Power Bowl, Palak Paneer + Roti,
Sprout & Sattu Salad Bowl.

**Dinner:** Paneer Tikka + Dal, Soya Tikka + Roti + Curd, Tofu Bhurji + Roti + Curd,
Rajma Paneer Rice Bowl, Palak Tofu + Roti, High Protein Dal Tadka + Paneer,
Soya Keema + Roti, Mushroom Tofu Stir‑fry + Roti, Masoor Dal + Paneer + Roti,
Egg Bhurji + Roti, Chana Masala + Quinoa, Low‑fat Paneer Curry + Roti.

**Snacks:** Roasted Makhana + Buttermilk, Sprout Chaat, Greek Yogurt + Soy Nuts,
Paneer Tikka Bites, Peanut & Chana Chaat, Whey Protein Shake.

## 🚀 Run it

It's a static site — just open `index.html` in a browser. For full PWA/offline
behavior (service worker), serve it over `http://` rather than `file://`:

```powershell
# from this folder
python -m http.server 8000
# then open http://localhost:8000
```

> The PDF export uses the jsPDF library loaded from a CDN, so **PDF download needs an
> internet connection** (the rest of the app works offline).

> Recipe **photos** are fetched on demand from an online image service, so they need
> internet too. When offline (or if the toggle is off), each dish falls back to its
> gradient + emoji thumbnail — the app stays fully functional.

## 🧮 How the numbers work

Each ingredient stores nutrition per a reference amount (`per`), e.g. paneer = 18 g
protein and 265 kcal per 100 g. For a chosen quantity `qty`:

```
protein = protein_ref * (qty / per)
kcal    = kcal_ref    * (qty / per)
```

Values are approximate (typical Indian‑vegetarian ingredient averages, legumes/grains
measured dry) and meant for planning, not medical precision.

## 📂 Project structure

| File | Purpose |
|------|---------|
| `index.html` | The full app (UI + logic) |
| `manifest.json` | PWA install metadata |
| `sw.js` | Service worker for offline use |
| `README.md` | This file |
| `icon-192.png`, `icon-512.png` | App icons |

> Note: nutrition figures are estimates. Adjust to your brand/recipe as needed.
