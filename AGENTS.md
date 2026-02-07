## Project Overview

<add>

## Git

- Commits: Conventional Commits (feat|fix|refactor|build|ci|chore|docs|style|perf|test).
- Safe by default: `git status/diff/log`. Push only when user asks.
- Branch changes require user consent.
- Don't commit, and push; stop + ask.
- Don’t delete/rename unexpected stuff; stop + ask.
- No amend unless asked.

## Mindset

- Fix root cause (not band-aid).
- Unsure: read more code; if still stuck, ask w/ short options.
- Conflicts: call out; pick safer path.
- Write idiomatic, simple, maintainable code. Always ask yourself if this is the most simple intuitive solution to the problem. 
- If code is very confusing or hard to understand:
  1. Try to simplify it.
  2. Add an ASCII art diagram in a code comment if it would help.
- Clean up unused code ruthlessly. If a function no longer needs a parameter or a helper is dead, delete it and update the callers instead of letting the junk linger.

