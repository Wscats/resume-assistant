
<p align="center">
  <h1 align="center">📝 Resume Assistant</h1>
  <p align="center">
    <strong>AI-powered clawbot skill for resume polishing, job customization, multi-format export, and professional scoring.</strong>
  </p>
  <p align="center">
    <a href="./LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
    <img src="https://img.shields.io/badge/Version-1.0.0-green.svg" alt="Version: 1.0.0">
    <img src="https://img.shields.io/badge/Platform-clawbot-purple.svg" alt="Platform: clawbot">
    <img src="https://img.shields.io/badge/Language-EN%20%7C%20ZH-orange.svg" alt="Language: EN | ZH">
  </p>
  <p align="center">
    <a href="./README_ZH.md">🇨🇳 中文文档</a> · <a href="./SKILL.md">📖 Skill Spec</a> · <a href="./examples/usage.md">💡 Usage Examples</a>
  </p>
</p>

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔍 **Polish** | 40+ checklist review covering grammar, action verbs, quantification, formatting, and more |
| 🎯 **Customize** | Tailor your resume for any specific job posting with gap analysis and keyword optimization |
| 📤 **Export** | Convert to 5 formats (Word, Markdown, HTML, LaTeX, PDF) × 4 professional templates |
| 📊 **Score** | 100-point professional evaluation with 5 dimensions, strengths, weaknesses, and action plan |

## 🚀 Quick Start

### In clawbot (Direct Usage)

Simply type slash commands in a clawbot conversation:

```
/resume polish
Please polish my resume:

John Doe
Senior Frontend Engineer | 5 years experience
Skills: JavaScript, React, Vue, Node.js
...
```

### All Commands at a Glance

| Command | Purpose | Required Input |
|---------|---------|----------------|
| `/resume polish` | Fix errors, improve wording | Resume content |
| `/resume customize` | Tailor for a specific job | Resume content + Job description |
| `/resume export` | Convert to Word/MD/HTML/LaTeX/PDF | Resume content + Format |
| `/resume score` | Evaluate and get improvement plan | Resume content |

---

## 📖 How It Works

Resume Assistant is a **clawbot skill** — a structured prompt package that AI agents can load and execute. It contains:

- **System prompt** defining the AI's persona and quality standards
- **Command-specific prompts** with detailed instructions for each task
- **Templates** for resume styles and export formats
- **Skill manifest** (`skill.json` / `skill.yaml`) describing commands, arguments, and configuration

```
User Input ──► Command Router ──► Load Prompts ──► LLM ──► Structured Output
                  │
                  ├── /resume polish    → prompts/polish.md
                  ├── /resume customize → prompts/customize.md
                  ├── /resume export    → prompts/export.md
                  └── /resume score     → prompts/score.md
```

---

## 🏗️ Project Structure

```
resume-assistant/
├── skill.json              # Skill manifest (JSON format)
├── skill.yaml              # Skill manifest (YAML format)
├── SKILL.md                # Skill specification (English)
├── SKILL_ZH.md             # Skill specification (Chinese)
├── LICENSE                 # MIT license
│
├── prompts/                # AI prompt files
│   ├── system.md           # System-level prompt (always loaded)
│   ├── polish.md           # Polish command prompt
│   ├── customize.md        # Customize command prompt
│   ├── export.md           # Export command prompt
│   └── score.md            # Score command prompt
│
├── templates/              # Resume & export templates
│   ├── professional.md     # Classic professional style
│   ├── modern.md           # Modern creative style
│   ├── minimal.md          # Clean minimal style
│   ├── academic.md         # Academic/research style
│   └── export/
│       ├── resume.html     # HTML export template
│       └── resume.tex      # LaTeX export template
│
└── examples/               # Sample resumes & usage guide
    ├── usage.md            # Detailed usage examples
    ├── sample-resume-en.md # English sample resume
    ├── sample-resume-zh.md # Chinese sample resume
    └── sample-resume-weak.md # Weak resume (for scoring demo)
```

---

## 🔧 Integration Guide

### Option 1: Register as a Skill in Your AI Agent

```json
{
  "skills": [
    {
      "name": "resume-assistant",
      "path": "./skills/resume-assistant",
      "manifest": "skill.json"
    }
  ]
}
```

### Option 2: Build Prompts Programmatically

```python
def build_prompt(command, args):
    system_prompt = load_file("prompts/system.md")
    command_prompt = load_file(f"prompts/{command}.md")

    messages = [
        {"role": "system", "content": system_prompt + "\n\n" + command_prompt},
        {"role": "user", "content": args["resume_content"]}
    ]
    return messages
```

### Option 3: REST API

```bash
curl -X POST https://your-agent-api.com/skills/resume-assistant/polish \
  -H "Content-Type: application/json" \
  -d '{
    "resume_content": "Your resume content...",
    "language": "en"
  }'
```

### Option 4: LangChain / LlamaIndex

```python
from langchain.tools import Tool

resume_tools = [
    Tool(
        name="resume_polish",
        description="Polish and improve resume with 40+ checklist items",
        func=lambda input: agent.run_skill(
            "resume-assistant", "polish",
            {"resume_content": input, "language": "en"}
        )
    ),
    # ... more tools for score, customize, export
]
```

> 📖 For complete integration details, see [SKILL.md](./SKILL.md)

---

## 📋 Recommended Workflow

```
┌─────────────────┐
│   Start Here    │
└────────┬────────┘
         ▼
   Have a resume? ──YES──► /resume score  (know where you stand)
         │                       │
         NO                      ▼
         │               /resume polish  (fix issues)
         ▼                       │
  Write one first               ▼
  using templates        Have a target job?
         │                  │         │
         ▼                 YES        NO
  /resume polish            │         │
         │                  ▼         │
         │          /resume customize │
         │                  │         │
         └──────────────────┼─────────┘
                            ▼
                     /resume export ──► Word / Markdown / HTML / LaTeX / PDF
```

**Pro Tips:**

1. 🎯 **Start with scoring** if you have an existing resume — know where you stand
2. ✨ **Polish first** to fix all basic issues before customizing
3. 🔄 **Customize per application** — don't use one resume for all jobs
4. 📊 **Score again** after polish + customize to see improvement
5. 📤 **Export last** — get content perfect before formatting
6. 📝 **Use Markdown** as your working format — it converts cleanly to all others

---

## 🎨 Templates

| Template | Style | Best For |
|----------|-------|----------|
| `professional` | Classic navy, serif headings | Finance, consulting, law |
| `modern` | Teal accents, creative layout | Tech, startups, marketing |
| `minimal` | Clean monochrome, dense content | Senior roles, engineering |
| `academic` | Formal serif, multi-page | Faculty, research, PhD |

---

## 🌏 Language Support

- **English (en)** — Default language, optimized for international job markets
- **Chinese (zh)** — Full CJK support with China-specific resume conventions

Chinese-specific features:
- Proper CJK font handling in HTML/LaTeX export
- Chinese resume conventions (photo, age, education priority)
- Half-width/full-width punctuation normalization
- Chinese-English mixed typesetting optimization

---

## 📊 Scoring Dimensions

When you use `/resume score`, your resume is evaluated across 5 dimensions:

| Dimension | Weight | What It Measures |
|-----------|--------|------------------|
| Content Quality | 30 pts | Achievements, metrics, relevance |
| Structure & Formatting | 25 pts | Layout, hierarchy, whitespace |
| Language & Grammar | 20 pts | Action verbs, tense, grammar |
| ATS Optimization | 15 pts | Keywords, parsability, standard headings |
| Impact & Impression | 10 pts | Overall impression, unique value |

Grades: **A+ (90-100)** · **A (80-89)** · **B (70-79)** · **C (60-69)** · **D (50-59)** · **F (<50)**

---

## 🤝 Contributing

Contributions are welcome! Here are some ways you can help:

- 🐛 Report bugs or suggest features via Issues
- 📝 Improve prompts for better AI output quality
- 🎨 Add new resume templates
- 🌍 Add support for more languages
- 📖 Improve documentation

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE).
