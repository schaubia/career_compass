# 🧭 Career Compass

**A genuinely learner-first guide to education and career paths for young people — with an honest look at how AI is reshaping the future of work.**

Not a university rankings tool. Not a marketing page. A practical, opinionated advisor that puts curiosity and real-world skills at the centre.

---

## What it does

Career Compass walks users through a short guided questionnaire and generates a personalised study and career guide based on:

- **Where they are in the world** — 6 global regions, affecting which options and job markets are relevant
- **Their financial situation** — from zero budget (free paths only) to full university budget
- **What genuinely interests them** — 15 interest categories, multi-select, no pressure to pick something "safe"
- **How they prefer to learn** — fully online, hybrid, campus-based, or work-and-learn / apprenticeship

The output includes:

- Tailored learning paths with curated free and low-cost resources (clickable links)
- Honest AI displacement risk data for common job categories
- Per-interest breakdowns of AI risk *and* AI opportunity
- Budget-aware "start this month" recommendations
- A comparison of the best online learning platforms

---

## The philosophy

Most career guidance tools are either university marketing in disguise, or pure job-market optimisation ("pick the highest-paying field"). This app is neither.

The guiding question is: *what does this person want to learn, and what paths make that genuinely possible?*

**Key principles baked in:**

- **Free and low-cost paths are first-class options.** Harvard's CS50, MIT OpenCourseWare, freeCodeCamp, and Kaggle are featured prominently — not as consolation prizes, but as genuinely excellent starting points.
- **AI disruption is addressed honestly.** The app shows automation risk estimates (sourced from McKinsey, Oxford, and WEF research) without either alarmism or false reassurance. It also shows where AI *creates* opportunity.
- **No field is dismissed.** Whether someone is drawn to nursing, agriculture, storytelling, or mathematics — the app takes it seriously and finds real paths.
- **Credentials matter less than knowledge and portfolio.** The recommendations lean toward demonstrated skills over expensive qualifications, especially for tech and design.

---

## Installation

**Requirements:** Python 3.8+

```bash
pip install streamlit
```

No other dependencies are required.

---

## Running the app

```bash
streamlit run career_compass.py
```

The app will open in your browser at `http://localhost:8501`.

---

## Project structure

```
career_compass.py    # Single-file Streamlit application
README.md            # This file
```

The entire application is self-contained in one file. The data (interest categories, learning paths, resources, AI risk data) is defined as Python dictionaries at the top of the file — easy to edit, extend, or translate.

---

## Extending the app

### Adding a new interest category

In `PATH_DB`, add a new key matching exactly one of the strings in the `INTERESTS` list:

```python
PATH_DB["Your new interest"] = {
    "paths": [
        {
            "title": "Path name",
            "why": "Why this is worth pursuing and how it relates to the future of work.",
            "badges": [("Badge label", "green")],  # green / blue / amber / red / gray
            "resources": [
                ("Resource name", "Free · Description", "https://url.com"),
            ]
        }
    ],
    "ai_note": "How AI is disrupting or changing this field.",
    "ai_opportunity": "How AI creates new opportunities in this field."
}
```

Then add the interest name to the `INTERESTS` list.

### Adding a new region

Add a new entry to the `REGIONS` dictionary:

```python
REGIONS["🌏 Your Region"] = "Countries included..."
```

### Updating AI risk data

Edit the `AI_RISK_DATA` list. Each entry is a tuple of:

```python
("Job category label", risk_percentage, "#hexcolor", "Short trend note")
```

Colour guidance: `#E24B4A` (red, high risk >70%), `#BA7517` (amber, medium 40–70%), `#1D9E75` (green, low <40%).

### Updating budget guidance

Edit the `BUDGET_NOTES` dictionary. Keys are `"none"`, `"low"`, `"mid"`, `"full"`.

---

## Data sources

AI displacement risk estimates are drawn from:

- **McKinsey Global Institute** — "The Future of Work After COVID-19" (2021) and "A New Future of Work" (2023)
- **Oxford Martin Programme** — "The Future of Employment: How Susceptible Are Jobs to Computerisation?" (Frey & Osborne, 2013, updated estimates)
- **World Economic Forum** — "Future of Jobs Report" (2023)

Percentages represent estimated share of *tasks* within a job category that are automatable by AI by 2030–2035. They are not predictions that entire professions disappear — they indicate where disruption is fastest and where adaptation is most needed.

---

## Roadmap / ideas for extension

- [ ] Add country-specific scholarship and funding information by region
- [ ] Add a "save my results" feature (PDF export or shareable link)
- [ ] Expand resources with Eastern European-specific options (Bulgarian universities, EU scholarships, Erasmus+)
- [ ] Add a "compare two paths" side-by-side view
- [ ] Add language options (Bulgarian, Spanish, French)
- [ ] Add a mentorship / community links section per field
- [ ] Integrate with a live jobs API to show real demand signals

---

## Licence

Free to use, adapt, and share. If you build on this for a school, NGO, or youth programme — please do. That's exactly the point.
