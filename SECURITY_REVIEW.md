# Code Quality and Security Review

## Issues in the original function

- `calc`, `a`, `b`, and `t` are unclear names that hide the function's purpose.
- `0.1` is a magic number and does not explain the VIP discount.
- An API key was hard-coded and printed to the console.
- `var` allows accidental reassignment and has function scope.
- Loose equality (`==`) can produce unexpected type coercion.
- Negative price and quantity values were not validated.

## Dependency security check

This repository has no `package.json`, so `npm audit` could not be run. There are currently no npm dependencies to audit. If dependencies are added later, run `npm audit` and apply safe upgrades with `npm audit fix`.

## Reflection

Secrets must never be committed because Git history can preserve them even after the visible line is deleted. API keys should be rotated immediately if exposed and supplied through environment variables or a secrets store. Dependencies need regular security checks because vulnerable transitive packages can affect an otherwise safe application. Code review and CI catch quality and security problems early and make changes easier to verify consistently.