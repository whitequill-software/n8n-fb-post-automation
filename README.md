# Facebook Post Automation — Make.com Workflow

A daily-triggered make.com workflow that automatically picks a property image from Google Drive, generates an AI-written caption using a RAG-based knowledge base, and publishes the post to a Facebook Page.

---

## Workflow Overview

![Facebook Post Automation n8n canvas](docs/screenshots/canvas.png)

---

## What It Does

This workflow runs on a daily schedule and:

1. **Picks an image** from a designated Google Drive folder (property listing photos)
2. **Generates a caption** using an AI model with retrieval-augmented generation (RAG) — drawing from a knowledge base of property details, selling points, and brand tone
3. **Posts to Facebook** via the Facebook Graph API, publishing the image and caption to a business Page

Built for a real estate marketing use case — automating the daily social media posting workflow for condominium property listings.

---

## Why I Built This

Daily social media posting for real estate is time-consuming and repetitive. This workflow removes the manual work of selecting images and writing captions, while keeping the output on-brand through RAG — so the AI writes from actual property knowledge, not generic text.

It demonstrates how AI automation can handle a real, recurring business task end-to-end with minimal human input.

---

## My Role

**AI Workflow Designer • Prompt Engineer • Automation Architect**

- Workflow architecture and scheduling design
- RAG knowledge base design (property details + brand tone)
- Caption generation prompt design
- Google Drive image pipeline
- Facebook Graph API integration
- Portfolio documentation

---

## Tech Stack

- **Automation:** make.com
- **AI:** LLM with RAG (retrieval-augmented generation)
- **Image Source:** Google Drive
- **Publishing:** Facebook Graph API
- **Trigger:** Daily schedule

---

## Workflow Architecture

```
Daily Schedule Trigger
   ↓
Google Drive — pick image
   ↓
RAG — retrieve property context
   ↓
AI caption generation
   ↓
Facebook Graph API
   ↓
Post published to Facebook Page
```

---

## Key Design Decisions

- **RAG over generic prompting** — caption quality is grounded in actual property data, not hallucinated details
- **Google Drive as image source** — images are pre-organized by property, making selection predictable and automatable
- **Daily trigger** — zero manual intervention required once set up
- **Facebook Graph API** — direct publishing without third-party scheduling tools

---

## Current Status

Working and in active use for a real estate marketing workflow.

---

## Portfolio Notes

This project demonstrates:

- End-to-end workflow automation in make.com
- RAG integration for grounded, on-brand AI output
- Real business use case (not a demo)
- Google Drive + Facebook Graph API integration
- Practical AI automation for content marketing

---

## Contact

Portfolio: https://sites.google.com/view/featheredworks/home  
GitHub: https://github.com/whitequill-software
