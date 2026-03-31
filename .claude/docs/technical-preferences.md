# Technical Preferences

<!-- Populated by /setup-engine. Updated as the user makes decisions throughout development. -->
<!-- All agents reference this file for project-specific standards and conventions. -->

## Engine & Language

- **Engine**: Unity 2021.3.11f1 (LTS)
- **Language**: C#
- **Rendering**: URP 17.0.3
- **Physics**: PhysX (Unity built-in)

## Naming Conventions

- **Classes**: PascalCase (e.g., `PlayerController`)
- **Public fields/properties**: PascalCase (e.g., `MoveSpeed`)
- **Private fields**: _camelCase (e.g., `_moveSpeed`)
- **Methods**: PascalCase (e.g., `TakeDamage()`)
- **Events**: PascalCase with On prefix (e.g., `OnHealthChanged`)
- **Files**: PascalCase matching class (e.g., `PlayerController.cs`)
- **Prefabs**: PascalCase (e.g., `PlayerCharacter.prefab`)
- **Constants**: PascalCase or UPPER_SNAKE_CASE

## Performance Budgets

- **Target Framerate**: 90 FPS (PICO VR requirement)
- **Frame Budget**: 11.1ms
- **Draw Calls**: <100 per frame
- **Memory Ceiling**: <4GB

## Testing

- **Framework**: NUnit (Unity Test Framework)
- **Minimum Coverage**: [TO BE CONFIGURED]
- **Required Tests**: AI service integration, VR interaction, networking, balance formulas

## Forbidden Patterns

<!-- Add patterns that should never appear in this project's codebase -->
- [None configured yet — add as architectural decisions are made]

## Allowed Libraries / Addons

<!-- Add approved third-party dependencies here -->
- [None configured yet — add as dependencies are approved]

## Architecture Decisions Log

<!-- Quick reference linking to full ADRs in docs/architecture/ -->
- [No ADRs yet — use /architecture-decision to create one]
