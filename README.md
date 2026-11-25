# ResumeNest: Headline A/B Test with Flagsmith

ResumeNest is a demo landing page for a free resume builder for students and freshers (30 days free). I used **Flagsmith Experimentation** to run a real A/B test on its headline.

**Live app:** https://eishu0607-cmd.github.io/Togglewar-app/
**Hackathon:** Toggle Wars, Track 01 (Test Something Real)

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
5. A small box confirms the "sign up". It is a demo, so no real account is created.

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
