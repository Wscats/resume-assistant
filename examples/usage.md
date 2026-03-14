# Resume Assistant — Usage Examples

## Quick Reference

| Command | Purpose | Required Input |
|---------|---------|----------------|
| `/resume polish` | Fix errors, improve wording, checklist review | resume content |
| `/resume customize` | Tailor for a specific job | resume content + job description |
| `/resume export` | Convert to Word/MD/HTML/LaTeX/PDF | resume content + format |
| `/resume score` | Evaluate and get improvement plan | resume content |

---

## Example 1: Polish a Resume

**Command:** `/resume polish`

**Input:**
```
resume_content: |
  I am a software engineer with 5 years experience. I worked at Google
  where I was responsible for building web applications. I helped improve
  the system performance. I also managed some team members.

  Education: BS Computer Science, Stanford University, 2018
  Skills: Python, Java, React, SQL, AWS

language: en
```

**What you get:**
- 📋 40+ item checklist review with ✅/❌/⚠️ for every item
- ✨ Fully polished resume with strong action verbs and metrics
- 📝 Categorized change list: 🔴 Critical → 🟡 Major → 🟢 Minor → 💡 Suggestions
- 📖 Action verb and quantification guidance

---

## Example 2: Customize for a Job

**Command:** `/resume customize`

**Input:**
```
resume_content: [your existing polished resume]

job_description: |
  Senior Frontend Engineer at Meta
  Requirements:
  - 5+ years of frontend development experience
  - Expert in React, TypeScript, and modern CSS
  - Experience with large-scale web applications
  - Strong web performance optimization skills
  - Experience with design systems and component libraries

language: en
```

**What you get:**
- 🎯 Detailed job requirements analysis
- 📊 Gap analysis table mapping each requirement to your resume
- ✨ Tailored resume with keywords optimized
- 🔑 Keyword coverage report (before vs. after)
- 💡 Cover letter talking points + interview prep notes

---

## Example 3: Export to Multiple Formats

**Command:** `/resume export`

**Input:**
```
resume_content: [your resume in Markdown]
format: html
template: modern
```

**Available formats:**

| Format | Extension | Best For |
|--------|-----------|----------|
| `markdown` | .md | Editing, version control, GitHub |
| `html` | .html | Web viewing, browser → PDF |
| `word` | .docx | ATS submission, recruiter preference |
| `latex` | .tex | Academic, professional typesetting |
| `pdf` | .pdf | Final submission, universal format |

**Available templates:**

| Template | Style | Industries |
|----------|-------|------------|
| `professional` | Classic navy, serif headings | Finance, consulting, law |
| `modern` | Teal accents, creative layout | Tech, startups, marketing |
| `minimal` | Clean monochrome, dense | Senior roles, engineering |
| `academic` | Formal serif, multi-page | Faculty, research, PhD |

---

## Example 4: Score an Existing Resume

**Command:** `/resume score`

**Input:**
```
resume_content: [your resume]
target_role: Senior Software Engineer at FAANG
language: en
```

**What you get:**
- 📊 Score out of 100 with letter grade (A+ to F)
- 📈 Breakdown across 5 dimensions:
  - Content Quality (30 pts)
  - Structure & Formatting (25 pts)
  - Language & Grammar (20 pts)
  - ATS Optimization (15 pts)
  - Impact & Impression (10 pts)
- ✅ Top 3 strengths with specific examples
- 🔧 Priority-ranked improvements with Before → After rewrites
- 🎯 Role fit assessment with competitive percentile estimate
- 📋 5-step action plan with effort estimates

---

## Recommended Workflow

```
┌─────────────┐
│ Start Here  │
└──────┬──────┘
       ▼
┌──────────────┐     Have a resume?
│ /resume score│◄─── YES ──────────────┐
└──────┬───────┘                       │
       ▼                               │
┌──────────────┐                       │
│/resume polish│◄─── NO (write first)──┘
└──────┬───────┘
       ▼
┌────────────────┐   Have a target job?
│/resume customize│◄── YES
└──────┬─────────┘
       ▼
┌──────────────┐
│/resume export │──► Word / Markdown / HTML / LaTeX / PDF
└──────────────┘
```

**Pro tips:**
1. **Start with scoring** if you have an existing resume — know where you stand
2. **Polish first** to fix all basic issues before customizing
3. **Customize per application** — don't use one resume for all jobs
4. **Score again** after polish + customize to see improvement
5. **Export last** — get content perfect before formatting
6. **Use Markdown** as your working format — it converts cleanly to all others
