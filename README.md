# ROI Justification Engine™ — NOFA Business Consulting, LLC

A client‑ready, **manual vs. AI** cost comparison tool that models **Year‑1** costs (including one‑time setup) and ongoing monthly operations. It produces **executive‑ready PDFs**, supports **Provider Mode** (private insights), and is **white‑label** for other AI solution providers.

> **Invented:** October 4, 2025  
> **File:** `index.html` (single‑page app, CDN‑hosted assets — no build step)

---

## ✨ Features

- **Manual vs. AI** comparison per task, monthly, and **Year‑1** totals
- **One‑time setup** + integration + prompt‑eng + migration + retraining
- **Market‑aware wages** (industry, region, labor market swing)
- **Risk/error modeling** (error rates, cost per error, risk buffer)
- **AI Task Specification** box with template & copy‑to‑clipboard
- **Provider Mode** (private toolbox & insights; auto‑hidden in PDF)
- **Charts** (Year‑1 total & AI cost split) via Chart.js
- **Export Client PDF** (html2canvas + jsPDF)
- **No build required** — Tailwind via CDN, minimal custom CSS

---

## 🗂 Project Structure

This MVP is a single file:

```
index.html   # All markup, styles, and JS in one place
```

You can rename the HTML file or drop it into any static hosting environment.

---

## 🚀 Quick Start

1. **Open locally**  
   Double‑click `index.html` to open in your browser.

2. **Fill the inputs**  
   - Client details  
   - Task / Workflow name (short label)  
   - **AI Task Specification** (describe the project for model analysis)  
   - Volume, rates, and setup/ops assumptions

3. **Click “Calculate”**  
   The summary cards, comparison table, and charts will populate.

4. **Export PDF**  
   Click **Export Client PDF**. Provider‑only sections are hidden automatically.

---

## 🧮 Modeling Details

### Manual Workflow (per task)
```
manual_per_task = (manual_hours × manual_rate)
                  + manual_extras
                  + (manual_error_rate × error_cost)
```

### AI‑Assisted Workflow (per task)
```
ai_per_task = ((ai_processing_hours + ai_review_hours) × ai_rate)
              + model_cost_per_task
              + (qa_sample_pct × qa_minutes/60 × qa_rate)
              + (ai_error_rate × error_cost)
```

### Monthly
```
manual_monthly = tasks_per_month × manual_per_task
ai_monthly_ops = tasks_per_month × ai_per_task
                 + ai_subscription_fee      # your SaaS/markup
                 + (eval_hours × eval_rate) # monitoring
```

### Year‑1 (includes one‑time setup)
```
setup_total = setup_cost
              + (integration_hours × integration_rate)
              + (prompt_eng_hours × prompt_eng_rate)
              + data_migration
ai_year_ops  = ai_monthly_ops × months
ai_year_1    = ai_year_ops + setup_total + retraining_per_year
manual_year  = manual_monthly × months
```

### Risk Buffer
```
risk_multiplier = 1 + (risk_buffer_pct / 100)
ai_year_1   *= risk_multiplier
manual_year *= risk_multiplier
```

### Amortized Monthly Explainer (for the UI only)
```
ai_monthly_explainer = ai_monthly_ops
                       + (setup_total / amort_months)
                       + (retraining_per_year / months)
```

### ROI & Break‑Even
```
year_1_savings = manual_year - ai_year_1
roi_pct        = ((manual_monthly - ai_monthly_ops) / ai_subscription_fee) × 100
breakeven_mo   = ceil(setup_total / max(1, manual_monthly - ai_monthly_ops))
```

> **Note:** ROI % is based on savings **relative to your monthly fee** (common for pricing justification).

---

## 🧰 Provider Mode (Private)

- Toggle via **Provider Mode** button.  
- Add your **capabilities keywords** (e.g., `bid, estimate, proposal`).  
- If the client’s task name doesn’t match, the app suggests expanding your toolbox (or partnering with **NOFA AI**).  
- **Hidden in PDFs** automatically.

---

## 📝 AI Task Specification (for model analysis)

Use the large **AI Task Specification** textarea to describe the project so an AI model can analyze it. Click **Insert template** for a guided outline:

- Objective / business outcome  
- Inputs & sources (files, systems, APIs)  
- Workflow steps  
- Acceptance criteria (definition of done)  
- Constraints (SLA, budget, compliance)  
- Edge cases  
- Outputs (format, delivery, recipients)

This text is included in the **Executive Summary** and the **PDF**.

---

## 🎨 White‑Labeling

- Replace the **brand name** in the header.  
- Optionally add a logo image block.  
- The layout uses a **full‑bleed gradient** background (`.bg-fancy`) and minimal custom CSS.
- All styles are **Tailwind CDN utilities** + a few small CSS helpers — no build step required.

---

## 🌐 Deployment

**Option A — Netlify (drag‑and‑drop):**
1. Create a Netlify account.
2. Drag the folder with `index.html` into the dashboard.
3. Get an instant HTTPS URL. Add a custom domain if desired.

**Option B — GitHub Pages:**
1. Push `index.html` to a repo.
2. Repo → Settings → Pages → set source to `main` / root.
3. Use the provided Pages URL or add a custom domain.

**Option C — Any static host:**
- Upload `index.html` to S3/CloudFront, Firebase Hosting, Vercel, your own Nginx, etc.

---

## 🔧 Customization

Open `index.html` and look for these sections:

- **Heuristic presets:** `industryBaseRates`, `regionFactors`, `marketFactors`  
  Tune to your markets or wire to live data later.
- **Default values:** input `value="..."` attributes.
- **Charts:** `drawCharts(...)` if you want different chart types or colors.
- **PDF:** `exportClientPDF()` uses html2canvas & jsPDF; you can add a watermark or cover page.

---

## 🛡️ Privacy & Data

- This MVP runs **entirely in the browser** by default.  
- No data leaves the device unless you connect external APIs.  
- When adding APIs later (e.g., BLS wages, Indeed job data), disclose usage in your privacy policy.

---

## 🐛 Troubleshooting

- **Charts don’t load** → check internet (Chart.js via CDN).  
- **PDF doesn’t download** → allow pop‑ups or try Chrome.  
- **Layout looks off** → hard refresh (clear cache).  
- **Accidentally revealed provider notes** → export again; the app hides `.provider-only` during PDF.

---

## 🗺️ Roadmap Ideas

- Preset selector (Industry/Region/Market) → autofill inputs  
- Multi‑scenario comparison tabs & CSV/JSON export  
- Live labor/wage feeds (BLS/ONS), token cost models per LLM  
- Scenario saving (localStorage or backend)  
- Role‑based access for providers vs clients

---

## ⚖️ License & Trademark

- Copyright © NOFA Business Consulting, LLC.
- **ROI Justification Engine™** is a trademark of NOFA Business Consulting, LLC.
- You may white‑label for your clients with permission. For commercial licensing, contact NOFA.

---

## 📮 Support

Questions or customization requests?  
**Website:** https://nofabusinessconsulting.com  
**Owner:** NOFA Business Consulting, LLC
