# Artificial Intelligence — Project 1: Rule-Based AI Chatbot 🤖
**DecodeLabs | Industrial Training Kit | Batch 2026**

> "An LLM without rules is a hallucination engine. Today, we build the
> skeleton that holds the intelligence." — Project 1 Briefing

---

## 1. Goal (as per brief)
Create a rule-based chatbot that responds to predefined user inputs using
explicit control flow — no machine learning, no external APIs. Pure
deterministic logic ("white box" AI).

## 2. Key Requirements (from spec) — Status
| Requirement | Status | Where it's implemented |
|---|---|---|
| Handle greetings & exit commands | ✅ | `Chatbot.EXIT_WORDS`, `greeting` intent |
| If-else / rule logic for responses | ✅ | `RuleEngine.resolve()` (priority rule engine, not a raw if-elif ladder) |
| Run in a continuous loop | ✅ | `Chatbot.run()` → `while True` |
| Input loop (continuous while cycle) | ✅ | `run()` |
| Sanitization (case & whitespace) | ✅ | `sanitize()` |
| Knowledge base: dictionary, 5+ intents | ✅ | 10 intents defined in `_build_intents()` |
| Fallback: default response for unknowns | ✅ | "I do not understand that yet." |
| Exit strategy: clean break command | ✅ | `exit / quit / bye / goodbye / stop` |

## 3. Advanced Features (beyond the base spec)
The deck explicitly calls the **if-elif ladder an anti-pattern** (O(n),
high technical debt) and recommends **dictionary/hash-map lookup (O(1))**.
This build goes further:

- **Regex-based multi-pattern intents** — one intent can match many phrasings
  ("hi", "hello", "hey", "namaste"), not just one exact string.
- **Fuzzy typo correction** (`difflib`) — "thnks" still resolves to `thanks`.
- **Slot filling / context memory** — bot captures and remembers your name,
  personalizes later replies.
- **Feedback capture** — `feedback: <text>` is logged to `chat_log.txt`.
- **Full conversation logging** with timestamps.
- **Priority-ordered rule engine** — `Intent` + `RuleEngine` classes instead
  of a flat if/elif chain (matches the deck's "Industrial Architect" advice).
- **Session analytics** — on exit, tells you which intent fired most.

This still satisfies the deck's **"Strategic Necessity of the White Box"**
slide: full traceability (input → logic → output), zero hallucination risk,
100% hard-coded — nothing probabilistic.

## 4. Project Structure
```
rule_based_chatbot_project/
├── chatbot.py        # Main program — run this
├── README.md          # This file
├── requirements.txt   # Dependencies (none — stdlib only)
└── chat_log.txt        # Auto-created on first run (conversation + feedback log)
```

## 5. How to Run
Requires Python 3.9+ (no external packages needed — pure standard library).

```bash
python3 chatbot.py
```

Try these inputs:
```
hello
my name is Soni
what's the time
what's the date
what can you do
feedback: this bot is great
thnks
how are you
are you an ai
exit
```

## 6. Roadmap — Where This Leads (per the deck)
The PDF explicitly frames Project 1 as the "Discrete Mapping (Exact Match)"
stage. The next stage (Project 2, per the deck's "Conceptual Bridge" slide)
moves from **exact-match dictionary keys → semantic embeddings (vectors)**,
i.e. a real NLP/vector-similarity chatbot. This project is intentionally
the deterministic "control layer" / guardrail foundation that a future
LLM-based system would sit behind (see the deck's "AI Guardrails" slide —
frameworks like NVIDIA NeMo / Llama Guard occupy this same architectural
position).

## 7. Author 
Name: Soni
Batch: 2026 | Powered by DecodeLabs
📞 +91 89330 06408 | ✉ decodelabs.tech@gmail.com | 🌎 www.decodelabs.tech
📍 Greater Lucknow, India
