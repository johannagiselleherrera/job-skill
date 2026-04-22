# job-fit — Claude Skill

A custom Claude skill that analyzes job postings against your professional profile, flags potential red flags, and drafts personalized cover letters — all in one go.

Built as part of an AI/PM learning path by a Project Manager transitioning into AI-augmented workflows.

---

## What it does

When you paste a job posting, **job-fit** will:

1. **Analyze the fit** — Compares the role's requirements against your profile (tools, seniority, methodology, industry focus, and more)
2. **Flag red flags** — Identifies concerns like vague compensation, unrealistic expectations, culture signals, or mismatched scope
3. **Draft a cover letter** — Generates a tailored, personalized cover letter based on your background and the specific role

---

## Who it's for

This skill was built for a PM with ~1 year of experience in software development startups, with a background in Scrum/Kanban, client-facing projects, and tools like Jira, Confluence, Azure DevOps, and Notion — but you can adapt it to your own profile by editing the `SKILL.md`.

---

## How to install

1. Download the `.skill` file from this repo
2. Go to [claude.ai](https://claude.ai) → **Settings → Skills**
3. Click **"Add skill"** and upload the file
4. Done — Claude will now have access to the skill in your conversations

---

## How to use it

Once installed, just paste a job posting into Claude and ask:

> *"Can you analyze this job posting with the job-fit skill?"*

Or simply paste the posting — Claude will recognize when to apply the skill automatically.

---

## Example output

Given a job posting, the skill produces something like:

```
FIT ANALYSIS
- Strong match on methodology (Scrum, Kanban)
- Tool overlap: Jira, Confluence ✓
- Seniority: aligned with 1-2 years experience
- Gap: role mentions PMP certification (not currently held)

RED FLAGS
⚠ Salary listed as "competitive" with no range
⚠ Responsibilities span PM + BA + QA — potential scope creep

COVER LETTER
[personalized draft based on your profile and the role]
```

---

## Customization

To adapt this skill to your own profile, open `SKILL.md` and update the section that describes the candidate background. No coding knowledge required — it's plain text.

---

## About

Built by **Johanna Giselle Herrera** — Project Manager exploring the intersection of AI, UX, and product strategy.

Currently learning: Claude Skills · MCPs · Claude Code

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/johanna-giselle-herrera/)

---

*Part of an ongoing AI/PM upskilling journey. More skills coming soon.*
