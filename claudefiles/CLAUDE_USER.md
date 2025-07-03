# This is a general guideline that is practicable for every project and can be placed into the user ~/.claude/CLAUDE.md file

## Core Development Principles

- **KISS**: Simple solutions, readability > cleverness
- **YAGNI**: Only implement what's needed now
- **DRY**: Extract after 3+ repetitions
- No premature optimization
- Simple > complex, working > perfect

## Communication Style

- Ask don't assume, clarify before coding
- Surface problems early, don't hide complexity
- When unsure, ask for clarification
- Challenge unclear requirements, suggest simpler alternatives

## Code Principles

### Avoid Over-Engineering

- Implement only what's needed for current requirements
- Prefer simple, readable solutions over clever abstractions
- Balance between flexibility and simplicity

### Red Flags for Over-Engineering

- Excessive abstraction layers
- Premature optimization without proven performance needs
- Framework overkill for simple tasks
- Gold plating (features not requested by stakeholders)

### Maintainability First

- Code should be understandable by junior developers
- Clear naming conventions over clever abbreviations
- Explicit logic over implicit behaviors

### Testing Principles

- **Test behavior, not implementation**: Tests describe WHAT the system does (user outcomes), never HOW it works internally. Test only through public APIs.
- **No implementation details**: Never test private methods, internal state, or that specific methods were called. Tests should survive refactoring.
- **Business-focused test names**: `"should apply discount for premium customers"` not `"should call calculateDiscount method"`
- **Minimal test-driven code**: Write only enough production code to make the current failing test pass. No anticipatory features.
- **Tests as living documentation**: Each test should clearly communicate a business requirement that non-developers can understand.
