# Reflection: Using AI to Build AlxPolly

AI played a significant and practical role in building this project. Rather than replacing engineering judgment, it amplified it—accelerating routine work, helping me reason through trade-offs, and catching small mistakes before they became big ones. Below I summarize what worked well, what felt limiting, and what I learned about prompting, reviewing, and iterating with AI.

What worked well:

AI was excellent at scaffolding boilerplate and nudging me toward sensible patterns. For example, it generated initial component structures for authentication and poll flows, set up TypeScript types across `lib/types`, and suggested a clear folder layout in `app/` and `components/`. It also produced quick drafts for service wrappers around Supabase, including edge-case reminders (like handling null sessions and mapping RLS constraints back to the UI). These starting points saved hours.

Another high-value use case was documentation. The assistant helped outline sections for this README, clarified setup steps, and reminded me to include environment, troubleshooting, and testing notes. Turning tacit knowledge into explicit documentation is usually a drag; with AI, the cost of “writing it down” was much lower.

AI also served as an always-available reviewer. Before commits, I asked for potential failure modes or missing validations. It surfaced cases like double-submission on forms, race conditions around optimistic updates, and the need to guard server components from client-only assumptions. These nudges improved code quality while keeping review cycles short.

What felt limiting:

AI occasionally hallucinated APIs or file locations, especially around Supabase client helpers and Next.js App Router semantics. If I accepted suggestions verbatim without verifying imports and runtime contexts (server vs client), I would introduce subtle bugs. The remedy was to keep prompts grounded in the actual codebase and to ask targeted follow-ups like “show me where this function should live” or “adapt to an RSC-safe pattern.”

Another constraint was specificity. Vague prompts led to generic answers. The quality of results correlated tightly with how precisely I described the desired behavior, constraints, and existing interfaces. When I shared actual file paths and snippets, the assistant responded with much more accurate edits.

What I learned about prompting, reviewing, and iterating:

First, treat AI like a pair programmer who thrives on context. Paste the relevant function signatures, show the error messages, and state non-functional constraints (performance, accessibility, DX). The more concrete the prompt, the better the output.

Second, iterate in small, testable steps. Ask for a focused change, apply it, run the app, and then ask for the next improvement. This reduces the surface area for mistakes and makes it easier to spot regressions. It also keeps commit history clean and narrative.

Third, keep ownership of correctness. AI accelerates but does not guarantee accuracy. I made a habit of verifying generated code against the TypeScript compiler, checking RLS assumptions in SQL, and aligning UI behavior with product intent. The assistant is at its best when used to propose options; I still decided which one fit.

Lastly, use AI to improve communication artifacts, not just code. Well-structured READMEs, clear commit messages, and concise docstrings make future work cheaper. Let AI draft them, then edit for voice and precision.

Overall, AI meaningfully sped up delivery and improved code quality when I provided context-rich prompts and kept a tight feedback loop. The key is disciplined collaboration: supply real code, ask precise questions, validate results, and let AI handle the heavy lifting around scaffolding and documentation while you retain architectural judgment.


