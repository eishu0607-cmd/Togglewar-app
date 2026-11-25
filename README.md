# ResumeNest: Headline A/B Test with Flagsmith

ResumeNest is a free resume builder for students and freshers (30 days free). It is a demo product I built for the Toggle Wars hackathon, and I used **Flagsmith Experimentation** to run a real A/B test on its landing page headline.

**Live app:** https://eishu0607-cmd.github.io/Togglewar-app/
**Hackathon:** Toggle Wars, Track 01 (Test Something Real)

## What the app does

1. A visitor lands on the ResumeNest landing page and sees one of two headlines.
2. They click **Sign Up Free**.
3. The page opens a working **resume builder**. The visitor enters their name, education, skills, projects and achievements, and sees a live resume preview.
4. They download the resume as a PDF with the **Download PDF** button.

There is no login and no server. The visitor's details stay in their own browser. No real accounts are created.

## The experiment

**Question:** Which headline gets more students to click Sign Up Free?

**Hypothesis:** Changing the headline from "Build a professional resume in 10 minutes" to "Land your first internship with a resume recruiters notice" will increase Sign Up clicks by at least 10% within 4 days.

| Version | Headline |
|---|---|
| Control | Build a professional resume in 10 minutes |
| Variant_1 | Land your first internship with a resume recruiters notice |

## How Flagsmith is used

- **Flag:** `hero_headline`, a multivariate flag that holds the two versions.
- **Metric:** `Signup click`. It measures whether a visitor clicks Sign Up Free at least once (Occurrence). The event name is `signup_click`, and higher is better.
- **Experiment:** "Resume Headline Test: Speed vs Internship". 100% of visitors enter the test, split 50% Control and 50% Variant_1.
- **Results:** Flagsmith's built-in Bayesian engine reports exposures, click rate, delta, credible interval and win probability.

## How the app works

1. Each visitor gets a random ID, saved in the browser, so they always see the same version.
2. The Flagsmith JavaScript SDK starts with `enableEvents: true` and that ID.
3. `getExperimentFlag("hero_headline")` serves the headline and records an exposure.
4. Clicking any **Sign Up Free** button sends `trackEvent("signup_click")`.
5. The page then switches to the resume builder, which runs entirely in the browser. The builder is part of the same page, so the click event is sent before anything changes.
6. **Download PDF** uses the browser's print function to save the resume as a PDF.

The whole app is one file, `index.html`, with no build step.

## Setup steps

1. Create a Flagsmith project and connect the managed warehouse for Experimentation.
2. Create a multivariate flag `hero_headline` with a Control value and one variation, split 50 / 50.
3. Create a metric: Occurrence, event name `signup_click`, higher is better.
4. Create an experiment on `hero_headline` with `Signup click` as the primary metric, 100% rollout, split evenly.
5. In `index.html`, put your Flagsmith client-side Environment ID in the `environmentID` field.
6. Host the file on any static host, for example GitHub Pages (Settings, Pages, deploy from the `main` branch).
7. Share the link so real visitors see both versions.

## Results

*(Fill in on Nov 29 from the Flagsmith experiment page.)*

| Variant | Exposures | Click rate | Win probability |
|---|---|---|---|
| Control | | | |
| Variant_1 | | | |

**Winner:**
**What I learned:**

## Tech

HTML, CSS, JavaScript, Flagsmith JavaScript SDK (`@flagsmith/flagsmith`), GitHub Pages.
