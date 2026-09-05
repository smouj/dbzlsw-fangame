# Governance

## Project model

DBZ LSW Fangame uses a maintainer-led, evidence-driven contribution model.

The maintainer is responsible for repository direction, release readiness, public-source boundaries and final merge decisions. Contributors influence the project through issues, research, code review and pull requests.

## Decision principles

When technical options conflict, priority is generally:

1. verified original-game behaviour
2. deterministic and testable architecture
3. faithful visible presentation
4. maintainability and contributor clarity
5. convenience

A visually attractive approximation does not override known ROM evidence. Likewise, unverified ROM claims do not override a working implementation until evidence is sufficient.

## Main branch

`main` represents the current public development state. Changes should arrive through focused pull requests with passing required checks once branch rules are enabled.

## Compatibility of private research and public development

Private/local research may discover facts that are later promoted into this repository. Promotion should carry only redistributable code, derived findings and approved documentation—not raw proprietary material or private workspace history.
