# Week 2 – Advanced Prompt Engineering & LLM Applications

AI Internship project covering prompt engineering techniques and a working "Enterprise AI Copilot" built on top of a small, free, open language model.

## Overview

This project walks through the core prompting techniques used in production LLM systems — zero-shot, few-shot, chain of thought, tree of thoughts, ReAct, function calling, structured output, tool calling, prompt optimization, prompt injection, and guardrails — and then applies them in a single working assistant.

The assistant, called the Enterprise AI Copilot, can:

- Query a company database (SQLite)
- Generate SQL from plain English questions
- Draft emails
- Schedule calendar events (real `.ics` files)
- Search the internet (DuckDuckGo, no API key)
- Call a live external API (Open-Meteo weather)
- Generate PDF reports
- Route a request to the correct tool automatically

## Model

**Qwen2.5-1.5B-Instruct** is used throughout. It is free, fully public (no access request or gated license), and small enough to run on a Colab free-tier T4 GPU without quantization. This keeps the notebook usable by anyone without a paid account or special permissions.

## Repository Structure

```
.
├── notebook/
│   └── Week2_Enterprise_AI_Copilot.ipynb
├── outputs/
│   ├── prompt_evaluation_results.csv
│   ├── copilot_test_log.csv
│   ├── engineering_department_report.pdf
│   └── scheduled_event.ics
├── docs/
│   └── submission_notes.md
├── README.md
└── requirements.txt
```

## How to Run

1. Open `notebook/Week2_Enterprise_AI_Copilot.ipynb` in Google Colab.
2. Set the runtime to **T4 GPU** (`Runtime > Change runtime type > T4 GPU`). The notebook also runs on CPU, just slower.
3. Run all cells top to bottom (`Runtime > Run all`). No manual edits are required.
4. Generated files (CSV logs, the PDF report, and the calendar file) appear in the Colab file browser and can be downloaded from there.

## Requirements

All packages are installed automatically inside the first code cell of the notebook. The pinned versions are also listed in `requirements.txt` for reference.

## Notes on Real vs. Fallback Implementations

Every tool in the copilot is a genuine, working implementation:

| Tool | Implementation |
|---|---|
| Database query | Real SQLite database (in-memory, seeded with sample data) |
| SQL generation | Model-generated SQL executed against the real database |
| Email drafting | Real MIME email message built with Python's `email` library |
| Email sending | Left commented out in the notebook, since sending requires a personal mailbox login that cannot be shipped in a public notebook |
| Calendar scheduling | Real `.ics` file generated with `icalendar`, importable into any calendar app |
| Internet search | Real DuckDuckGo search via the free `ddgs` library, no API key |
| External API call | Real free weather API (Open-Meteo, no key required) |
| Report generation | Real PDF file generated with `fpdf2` |

## Author

Ammar — BS Artificial Intelligence, University of Lahore
