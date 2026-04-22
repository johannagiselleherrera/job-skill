---
name: job-fit
description: >
  Use this skill whenever the user shares a job offer, job posting, or recruiter message and wants to evaluate it, respond strategically, or prepare for the application process. This includes requests like "analyze this offer", "does this role fit me?", "write a cover letter for this", "how do I improve my chances?", "should I apply?", or "help me respond to this recruiter". Always trigger this skill when a job description or offer is present in the context, even if the user only asks one of the components. The skill produces two clearly separated deliverables: (1) a strategic Analysis (fit + recommendations) and (2) a standalone Cover Letter in formal Spanish — ready to copy and send.
---

## What this skill does

Given a job offer or recruiter message, produce **two clearly separated deliverables**:

- **Part A — Analysis**: strategic fit assessment + concrete recommendations
- **Part B — Cover Letter**: standalone, ready-to-send letter in formal Spanish

The two parts must be visually separated with a clear divider so the user can copy the cover letter independently without having to extract it from a wall of analysis.

---

## Step 1 — Read the user's profile

Locate and read the user's profile file. Try these paths in order and use the first one that exists:

1. `~/.claude/memory/user.md` (recommended — user-level memory, cross-platform via home dir expansion)
2. `./.claude/memory/user.md` (project-level memory, relative to current working directory)
3. `./memory/user.md` (fallback, relative to current working directory)

On Windows, `~` resolves to `%USERPROFILE%` (e.g., `C:\Users\<name>`). On macOS/Linux, it resolves to `$HOME`. Do not hardcode any absolute path with a specific username.

If none of the paths above contain a profile file, stop and tell the user:

> No encontré tu perfil en `~/.claude/memory/user.md` ni en `.claude/memory/user.md` del proyecto. Por favor creá uno con tu experiencia, herramientas, metodologías, uso de IA, certificaciones, pretensión salarial y preferencias laborales — o indicame dónde está guardado.

The profile file contains the user's professional data: experience, tools, methodologies, AI usage, certifications, salary expectations, and work preferences. Everything you write must be grounded in this real profile — never invent experience, certifications, or skills the user doesn't have.

**This is the most important rule of the skill.** If a requirement in the offer isn't covered by the user's real experience, say so honestly in the analysis and omit or reframe genuinely in the cover letter. Do not write things like "me encuentro en proceso de formalizar" unless the profile says the user is actually pursuing that specific certification.

---

## Output format

Use this exact two-part structure every time:

```
# 📊 PARTE A — Análisis estratégico

[Analysis content — see structure below]

═══════════════════════════════════════════════════════════

# ✉️ PARTE B — Cover Letter (lista para enviar)

[Cover letter body — see structure below]
```

The `═══` divider matters: it makes the cover letter visually trivial to locate and copy.

---

## Part A — Analysis (structure)

Use tables wherever they improve clarity. The reader is a PM — tables communicate trade-offs faster than prose.

### A.1 Síntesis de la oferta

A one-paragraph summary of what the role actually is, in plain language. Include: position, company/client, modality, location, salary info if available. Useful when the original posting is messy or poorly formatted.

### A.2 Fit — Matches vs. Gaps

Use a two-column or stacked table format. Prefer this structure:

| ✅ Matches | Detalle |
|---|---|
| [Requirement met] | [How her profile covers it — be specific, cite real items from user.md] |

| ⚠️ Gaps / Riesgos | Severidad | Detalle |
|---|---|---|
| [Requirement not met or unclear] | Alto / Medio / Bajo | [What's missing and why it matters] |

**Severity criteria:**
- **Alto**: the gap is on an excluyente (mandatory) requirement
- **Medio**: the gap is on a deseable but likely to surface in interview
- **Bajo**: minor gap, unlikely to block progress

### A.3 Fit general

State the overall verdict as: **Alta**, **Media-Alta**, **Media**, **Media-Baja**, or **Baja**.

Follow with 2–3 sentences of rationale. Be direct — this is a decision-support output.

### A.4 Consideraciones salariales

A short table cross-referencing the offer's modality with her pretension:

| Modalidad de la oferta | Pretensión aplicable | Comentario |
|---|---|---|
| [Contractor / R. Dependencia / No especificado] | [Number from profile] | [Negotiation advice — currency, anchor point, etc.] |

If the salary isn't in the offer, note it as an open point to clarify with the recruiter.

### A.5 Recomendaciones para maximizar chances

Numbered list, 4–7 items. Each item must be:
- **Specific** to this offer (not generic career advice)
- **Actionable** (something she can do before or during the process)
- **Prioritized** — put the highest-leverage items first

Good candidates for recommendations:
- How to reframe her profile for this particular employer/industry
- Portfolio or evidence she should prepare (especially for the AI-use requirement — this is her core differentiator)
- Gaps she could partially close before the interview
- How to handle salary negotiation given the modality
- Questions she should ask the recruiter (esquema de contratación, seniority esperado, rango, stack, autonomía del rol)
- Red flags in the offer worth raising

---

## Part B — Cover Letter (structure)

Standalone letter, ~250–350 words, formal Spanish.

**Do not include a "Buenos Aires, [fecha]" header** — this is a digital-era letter meant for email or form submission. A fecha line adds nothing and clutters the copy.

**Opening**: start with `Estimado/a equipo de [empresa/recruiter si se conoce]:` or `Estimado/a [Name]:` if a recruiter name is available.

**Body (3–4 paragraphs):**

1. Hook — connect her background directly to the role's core need in 1–2 sentences
2. Evidence — 2–3 specific experiences from her profile that map to the most important requirements. Be concrete: sectors (salud, fintech), team sizes, methodologies, tools
3. Differentiator — her use of AI as a productivity and quality accelerator. Describe at least 2 concrete use cases (minutas, reportes, épicas, historias de usuario, monthly reports integrando Jira/Confluence). This is almost always her strongest differentiator for tech PM roles in 2026 — never omit it
4. Close — confident, concrete call to action (conversation, interview, next step). Short

**Signature**: `Saludos cordiales,` + `Johanna Giselle` on its own line.

**Tone rules:**
- Formal register — no tuteo, no emoji, no "soy una persona proactiva" filler
- Every claim must be grounded in user.md
- If the offer has an excluyente that she doesn't meet, handle it honestly — don't ignore it in the letter (interviewer will notice), but don't overapologize either. One sentence acknowledging the path toward it is enough (e.g., mentioning CAPM in progress if it's genuinely in her plan)
- Avoid generic phrases like "estoy muy interesada en la oportunidad" — show interest through substance

---

## Language rules

- **Analysis (Part A)**: Spanish, direct and professional — PM-to-PM register
- **Cover Letter (Part B)**: formal Spanish, polished for a hiring context
- Never mix English into the cover letter unless the offer itself was in English

---

## Common failure modes to avoid

- ❌ Writing "estoy en proceso de certificarme en X" when the profile doesn't say that
- ❌ Inventing industries, tools, or project types not in user.md
- ❌ Generic recommendations ("investigá a la empresa", "preparate bien la entrevista") — these don't help
- ❌ Merging the cover letter into the analysis so it can't be copied cleanly
- ❌ Including a fecha/location header in the cover letter
- ❌ Omitting the AI-usage differentiator in the cover letter
- ❌ Soft-pedaling real gaps in the fit analysis (it has to be honest to be useful for her decision)
