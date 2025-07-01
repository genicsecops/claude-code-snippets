# Start Pure TDD Mode

**ACTIVATE TDD MODE**: Follow Test-Driven Development strictly. This is the core practice.

## FUNDAMENTAL RULE

**NO PRODUCTION CODE WITHOUT A FAILING TEST.** Every line of production code must be written in response to a failing test.

## STRICT RED-GREEN-REFACTOR CYCLE

### 🔴 RED Phase - Write Failing Test

1. Write ONE test for desired behavior
2. Test must fail for the RIGHT reason
3. **STOP** - No production code until test fails

### 🟢 GREEN Phase - Make Test Pass  

1. Write MINIMUM code to make test pass
2. Resist urge to write more than needed
3. **STOP** - Assess refactoring next

### 🔄 REFACTOR Phase - Assess & Improve

1. **ALWAYS ASSESS**: Would refactoring improve the code?
2. If YES: Refactor while keeping tests green
3. If NO: Move to next test
4. All tests must still pass after refactoring

## KEY TDD PRINCIPLES

### Test Behavior, Not Implementation

- Test through **public functions only** (exported functions)
- Never test internal/private functions directly
- Focus on "what it does", not "how it does it"

```typescript
// ✅ Test behavior through public API
expect(processOrder(order)).toEqual({ status: 'completed', total: 100 });

// ❌ Don't test internals
expect(calculateTax).toHaveBeenCalled();
```

### Minimal Implementation

- Write only enough code to pass current test
- Don't anticipate future requirements
- Don't add features "while you're there"

### Refactoring Assessment

- Only refactor if it genuinely improves the code
- If code is already clean → don't refactor
- Common improvements: unclear names, duplication, complex logic

## TDD VIOLATIONS TO PREVENT

**NEVER:**

- Write production code before failing test
- Write multiple tests before making first one pass  
- Skip the refactor assessment step
- Test implementation details instead of behavior
- Add functionality without a test driving it

## TDD WORKFLOW

### Before Writing Production Code

```
🛑 CHECK: Is there a failing test demanding this code?
If NO → Write the test first
If YES → Write minimal implementation
```

### After Test Passes

```
🔄 ASSESS: Would refactoring add value?
If YES → Refactor, verify tests pass
If NO → Move to next test
```

### Progress Format

```
🔴 RED: [Test description] - FAILING
🟢 GREEN: [Minimal implementation] - PASSING  
🔄 REFACTOR: [Assessment] - [Action taken]
```

## EXAMPLE TDD CYCLE

```typescript
// 🔴 RED: Write failing test
it("should calculate order total with tax", () => {
  const order = { items: [{ price: 100 }], taxRate: 0.1 };
  expect(calculateTotal(order)).toBe(110);
});
// FAILS - calculateTotal doesn't exist

// 🟢 GREEN: Minimal implementation
const calculateTotal = (order) => {
  const subtotal = order.items.reduce((sum, item) => sum + item.price, 0);
  return subtotal + (subtotal * order.taxRate);
};
// PASSES

// 🔄 REFACTOR: Assess
// Code is clear and simple - no refactoring needed
// Move to next test
```

## SESSION COMPACT/SUMMARY

When creating a summary for a new session, **include this TDD mode** so strict TDD continues.

**Confirm you understand and have activated pure TDD mode.**
