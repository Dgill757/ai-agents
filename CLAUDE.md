# CLAUDE.md — AI Agent Guidelines for `ai-agents`

This file provides context, conventions, and instructions for AI assistants (Claude Code and others) working on this repository. Keep it up to date as the project evolves.

---

## Project Overview

**Name:** ai-agents
**Description:** Customer AI Voice Agents — a system for building, deploying, and managing AI-powered voice agents for customer interactions.
**Repository:** `Dgill757/ai-agents`
**Primary Author:** Dgill757 <dangill@summitmarketinggroup.co>

This project is in its **initial phase**. As the codebase grows, update this document to reflect the actual structure, dependencies, and conventions used.

---

## Repository Structure

```
ai-agents/
├── CLAUDE.md          # This file — AI assistant guidelines
└── README.md          # Project overview
```

As development progresses, the expected structure will expand to something like:

```
ai-agents/
├── CLAUDE.md
├── README.md
├── src/               # Source code
│   ├── agents/        # Voice agent implementations
│   ├── config/        # Configuration and environment handling
│   └── utils/         # Shared utilities
├── tests/             # Test files
├── .env.example       # Environment variable template
└── package.json / pyproject.toml / requirements.txt
```

Update this section as directories and files are added.

---

## Development Workflow

### Git Branching

- **Main branch:** `master`
- **Feature/task branches:** Follow the pattern `claude/<description>-<session-id>`
  - Example: `claude/claude-md-mm3trh7rihd6eb87-i9kud`
- Always develop on a designated branch, never directly on `master`.
- Branch names starting with `claude/` are created by Claude Code for automated tasks.

### Branch Workflow

```bash
# Check current branch
git branch

# Create and switch to a new branch
git checkout -b claude/<feature-name>-<session-id>

# Push branch to remote
git push -u origin <branch-name>
```

### Commit Conventions

Write clear, descriptive commit messages. Preferred format:

```
<type>: <short summary>

<optional body with more details>
```

Common types:
- `feat:` — new feature or capability
- `fix:` — bug fix
- `docs:` — documentation changes only
- `refactor:` — code restructuring without behavior change
- `test:` — adding or updating tests
- `chore:` — tooling, config, dependency updates

Example:
```
feat: add voice transcription agent with Whisper integration

Implements real-time audio transcription using OpenAI Whisper.
Supports streaming output and multiple languages.
```

### Push Instructions

Always use:
```bash
git push -u origin <branch-name>
```

On network failures, retry with exponential backoff: 2s, 4s, 8s, 16s.

---

## AI Assistant Instructions

### What Claude Should Do

1. **Read before editing.** Always read a file before modifying it.
2. **Keep changes minimal.** Only make changes directly requested or clearly necessary.
3. **Prefer editing over creating.** Update existing files rather than creating new ones unless truly needed.
4. **Do not create docs/README files** unless explicitly asked.
5. **No over-engineering.** Avoid adding abstractions, helpers, or features beyond what the task requires.
6. **No unsolicited cleanup.** Do not refactor or comment code you did not change.
7. **Confirm before destructive actions.** Deleting files, force-pushing, or resetting changes requires explicit user confirmation.
8. **Never skip git hooks** (`--no-verify`) unless the user explicitly requests it.
9. **Commit on request only.** Do not commit unless the user asks.
10. **Push only to the designated branch.** See the branch specified in the task description.

### What Claude Should Not Do

- Do not push to `master` or any branch not designated in the task.
- Do not generate or guess external URLs.
- Do not add features, error handling, or comments beyond what was asked.
- Do not introduce security vulnerabilities (SQL injection, XSS, command injection, etc.).
- Do not expose secrets, API keys, or credentials in code or commits.

### Security Guidelines

- Never hardcode credentials, tokens, or API keys.
- Use environment variables for all secrets — reference `.env.example` (create one if it doesn't exist).
- Validate all external inputs at system boundaries.
- Follow OWASP Top 10 practices when writing web-facing code.

---

## Technology Stack

> **Status:** Not yet determined. Update this section once the stack is chosen.

Likely candidates given the project description (AI Voice Agents):

| Concern | Options |
|---|---|
| Language | Python, TypeScript/Node.js |
| Voice/STT | OpenAI Whisper, AssemblyAI, Deepgram |
| TTS | ElevenLabs, OpenAI TTS, Google Cloud TTS |
| LLM | Anthropic Claude (claude-sonnet-4-6 / claude-opus-4-6) |
| Telephony | Twilio, Vonage, Plivo |
| Framework | FastAPI, Express.js, LangChain |

**Recommended Claude models** (as of Feb 2026):
- Capable tasks: `claude-opus-4-6`
- Balanced (default): `claude-sonnet-4-6`
- Fast/lightweight: `claude-haiku-4-5-20251001`

---

## Environment Configuration

When environment variables are needed, use a `.env.example` file to document required keys without exposing values:

```
# Example .env.example
ANTHROPIC_API_KEY=
OPENAI_API_KEY=
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
DATABASE_URL=
```

Never commit `.env` or any file containing real secrets.

---

## Testing

> **Status:** No tests exist yet. Update this section when a testing framework is added.

Once a framework is chosen, document:
- How to run tests: `npm test` / `pytest` / etc.
- Test file locations and naming conventions
- Any required environment setup for tests

---

## Running the Project

> **Status:** No runnable code exists yet. Update this section when a start command is defined.

---

## CI/CD

> **Status:** No CI/CD configured yet. Update this section if GitHub Actions or another pipeline is added.

---

## Notes for Future Updates

When this project grows, update the following sections in this file:
- [ ] Repository structure diagram
- [ ] Technology stack decisions
- [ ] Environment variable documentation (`.env.example`)
- [ ] Build, lint, and test commands
- [ ] CI/CD pipeline description
- [ ] Code conventions specific to the chosen language/framework
