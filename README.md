
# Healthy Recipe Generator App (Lovable + Supabase + OpenAI)

## Built without writing manual code using modern AI tools.

No CS degree. No coding bootcamp. Just a clear idea, the right tools, and a bit of patience.

This repo documents my learning journey through Episode 1 of the No-Code App Development course — where I went from "what even is a back end?" to having a live, working recipe app with user login and AI-generated output.

---

## What I Built

A **healthy recipe generator** where users enter their food preferences, allergies, deficiencies, and cuisine type — and get back a full recipe, a shopping list, and a YouTube tutorial link.

Built with **Lovable** for the front end, **Supabase** for the back end, and **OpenAI** for the AI output. Took one session. No code written manually.

---

## Features

- **Personalized recipe generation** — users input their food preferences, allergies, dietary deficiencies, and cuisine type
- **Step-by-step recipes** — each result includes cooking instructions, serving size, and preparation time
- **Smart shopping list** — ingredients are listed automatically after every generation
- **YouTube tutorial link** — each recipe links out to a relevant cooking video
- **User authentication** — sign up and log in via email/password or Google
- **Saved recipes** — logged-in users can save and revisit their favourite results
- **Mobile responsive** — works on any browser, phone or desktop, without installing anything
- **AI-powered output** — recipes are generated live through the OpenAI API, not pulled from a static database

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         User (Browser)                          │
└───────────────────────────────┬─────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Lovable (Front End)                           │
│                                                                 │
│   React + TypeScript + Tailwind CSS                             │
│   ─────────────────────────────────                             │
│   • User input form  (preferences, allergies, cuisine)          │
│   • Recipe display   (steps, shopping list, YouTube link)       │
│   • Auth UI          (sign up, log in, Google OAuth)            │
│   • Saved recipes    (personal dashboard)                       │
└──────────────┬──────────────────────────┬───────────────────────┘
               │                          │
               ▼                          ▼
┌──────────────────────────┐  ┌───────────────────────────────────┐
│   Supabase (Back End)    │  │       OpenAI API                  │
│                          │  │                                   │
│  • Auth & user sessions  │  │  • Receives user preferences      │
│  • Profiles table        │  │  • Returns AI-generated recipe    │
│  • Saved recipes table   │  │  • Called via Supabase            │
│  • Row-level security    │  │    edge function                  │
│  • Realtime sync         │  │                                   │
└──────────────────────────┘  └───────────────────────────────────┘
```

**How a recipe request flows:**

1. User fills in the form and clicks **Generate**
2. Lovable sends the input to a Supabase edge function
3. The edge function calls the OpenAI API with the user's details
4. OpenAI returns a structured recipe response
5. Lovable renders the result — steps, ingredients, and tutorial link
6. If the user is logged in, they can save it to their profile

---

## How It All Connects — The Build Flow

```
┌─────────────────────────────────────────┐
│  PLAN                                   │
│                                         │
│   Define your idea                      │
│   Problem · audience · goal             │
│            │                            │
│            ▼                            │
│   Grok → PRD                            │
│   Refine idea into a structured prompt  │
└─────────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────────┐
│  BUILD                                  │
│                                         │
│   Lovable → front end                   │
│   Generate UI from prompt               │
│            │          ↑                 │
│            ▼          │ fix errors      │
│   Supabase → back end │ (repeat as      │
│   Auth · database · storage  needed)   │
│            │                            │
│            ▼                            │
│   OpenAI API → AI output                │
│   Recipes generated on demand           │
└─────────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────────┐
│  SHIP                                   │
│                                         │
│   Publish                               │
│   Live URL · mobile ready               │
└─────────────────────────────────────────┘
```

The loop between Build steps is normal — errors happen, you ask Lovable to fix them, and you move on.

---

## The Stack

| Tool | What It Does |
|---|---|
| [Lovable](https://lovable.dev) | Turns prompts into working front-end code |
| [Supabase](https://supabase.com) | Database, authentication, storage — all free to start |
| [Grok](https://grok.com) | Helped refine the idea into a proper prompt |
| [OpenAI API](https://platform.openai.com) | Powers the actual recipe generation |

---

## What I Learned (Chapter by Chapter)

**Chapter 1 — The basics, explained simply**
Front end is what you see. Back end is everything behind it. A database stores your data. An API is just two apps talking to each other. That's it. That's the foundation.

**Chapter 2 — Building the UI with Lovable**
Lovable takes your prompt and writes the code for you. The trick is writing a good prompt — which I did by first running my idea through Grok to generate a proper Product Requirement Document, then feeding that into Lovable.

**Chapter 3 — Connecting Supabase**
Supabase handles user sign-ups, stores data, and manages authentication. Lovable connects to it directly and even creates your database tables on its own. I just had to understand what was happening — not how to do it manually.

**Chapter 4 — What's next**
Building one app is a start, not a finish. The real path is interning, building consistently, and sharing the work publicly.

---

## Key Learnings

- **Prompt engineering for AI app builders** — the quality of your prompt decides the quality of your output. Vague in, vague out.
- **Connecting front-end tools with backend services** — Lovable and Supabase talk to each other through an integration; you just have to authorise it and tell them what tables to create.
- **Understanding authentication and databases** — Supabase handles user sessions, stores profile data, and ties every saved recipe back to the right account automatically.
- **Using APIs to generate dynamic content** — OpenAI doesn't serve pre-written recipes; it generates a new one each time based on what the user typed. That's what makes it feel personal.

---

## How I Structured My Prompts in Lovable

Lovable works best when your prompt has four clear parts:

```
Context     → What am I building and for whom?
Task        → What do I want done right now?
Guidelines  → Any preferences or style notes?
Constraints → What should it NOT touch or change?
```

Vague prompts give vague results. The more specific you are, the less back-and-forth you need.

---

## The Honest Part

Watching one video or reading one README will not make you ready to freelance or get hired. What it will do is give you a foundation — vocabulary, mental models, and a working project you actually built.

From here, the plan is simple:
- Keep building small things
- Intern somewhere to see how teams actually work
- Post progress on LinkedIn and GitHub
- Accept that the tools will keep changing and stay curious anyway

---

## Resources

- [Lovable Docs](https://docs.lovable.dev)
- [Supabase Docs](https://supabase.com/docs)
- [Grok](https://grok.com) — free, no login needed
- [Mobbin](https://mobbin.com) — great for researching what competitors have already built



---

*Built while learning. Shared so others don't have to start from zero.*
