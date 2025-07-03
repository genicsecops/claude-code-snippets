# Pure TDD Mode - Behavior-Driven Testing Only

**ACTIVATE STRICT TDD MODE**: Test-Driven Development with exclusive focus on BEHAVIOR, never implementation.

## 🎯 CORE PRINCIPLE: TEST BEHAVIOR, NOT IMPLEMENTATION

**Every test must describe WHAT the system does, not HOW it does it.**

### ✅ GOOD: Testing Behavior (Business Value)

```typescript
// Tests describe user-visible outcomes
it("should apply 10% discount for orders over $100", () => {
  const order = createOrder([{ price: 150 }]);
  expect(order.getTotal()).toBe(135); // 150 - 15 (10%)
});

it("should send welcome email when user registers", () => {
  const emailService = mockEmailService();
  const user = registerUser("john@example.com", emailService);
  expect(emailService.sentEmails).toContainEqual({
    to: "john@example.com",
    subject: "Welcome!"
  });
});
```

### ❌ BAD: Testing Implementation

```typescript
// Tests that know too much about internals
it("should call calculateDiscount method", () => {
  const spy = jest.spyOn(order, '_calculateDiscount');
  order.getTotal();
  expect(spy).toHaveBeenCalled(); // ❌ Testing HOW, not WHAT
});

it("should set internal state to processed", () => {
  order.process();
  expect(order._state).toBe('processed'); // ❌ Testing private state
});
```

## 🔄 STRICT RED-GREEN-REFACTOR CYCLE

### 🔴 RED Phase - Write ONE Failing Behavior Test

1. **ASK**: "What should the system DO from the user's perspective?"
2. Write test describing desired OUTCOME
3. Test must fail because feature doesn't exist
4. **STOP** - No code until test fails

### 🟢 GREEN Phase - Minimal Implementation

1. Write ONLY enough code to make test pass
2. Implementation details are irrelevant - only the test passing matters
3. **STOP** - Test passes? Move to refactor assessment

### 🔄 REFACTOR Phase - Improve Without Changing Behavior

1. **ASSESS**: Can code be clearer/simpler while maintaining same behavior?
2. Refactor internals freely - tests ensure behavior unchanged
3. All tests must remain green

## 🚫 TDD VIOLATIONS - NEVER DO THIS

- Write code without a failing test
- Test private methods, internal state, or implementation details
- Test that specific methods were called (unless it's an external dependency)
- Write tests that break when refactoring (brittle tests)
- Test getters/setters directly without business context

## 📋 BEHAVIOR TEST CHECKLIST

Before writing any test, ask:

- [ ] Does this test describe a business requirement?
- [ ] Could I change the implementation without breaking this test?
- [ ] Is this testing through the public API only?
- [ ] Would a non-developer understand what this test verifies?
- [ ] Does the test name describe a user-visible behavior?

## 🎯 BEHAVIOR TESTING PATTERNS

### Testing Through Public API Only

```typescript
// ✅ GOOD: Test the result, not the process
class ShoppingCart {
  addItem(item: Item): void
  getTotal(): number
  applyDiscount(code: string): void
}

// Test ONLY these public methods and their outcomes
```

### Testing Side Effects

```typescript
// ✅ GOOD: Verify observable side effects
it("should notify inventory when order is placed", () => {
  const inventory = mockInventory();
  const order = new Order(inventory);
  
  order.place();
  
  expect(inventory.notifications).toContain({
    type: 'ORDER_PLACED',
    items: order.items
  });
});
```

### Testing Error Behavior

```typescript
// ✅ GOOD: Test how system behaves with invalid input
it("should reject orders with invalid credit card", () => {
  const order = createOrder();
  
  expect(() => order.pay(invalidCard)).toThrow("Invalid payment method");
});
```

## 📝 PROGRESS TRACKING FORMAT

```
🔴 RED: [Business behavior description] - FAILING
   Example: "Customer receives 10% discount on first order"
   
🟢 GREEN: [What was implemented] - PASSING
   Example: "Added discount calculation to checkout"
   
🔄 REFACTOR: [Internal improvements] - STILL PASSING
   Example: "Extracted discount logic to strategy pattern"
```

## 🎬 EXAMPLE: Full TDD Cycle for Business Feature

```typescript
// Business Requirement: "Premium customers get free shipping on all orders"

// 🔴 RED: Test the business rule
it("should provide free shipping for premium customers", () => {
  const customer = new Customer({ type: 'premium' });
  const order = new Order({ customer, items: [{ price: 10 }] });
  
  expect(order.getShippingCost()).toBe(0);
});
// FAILS: getShippingCost returns undefined

// 🟢 GREEN: Simplest implementation
class Order {
  getShippingCost() {
    return this.customer.type === 'premium' ? 0 : 5;
  }
}
// PASSES

// 🔄 REFACTOR: Better structure (tests still pass)
class Order {
  getShippingCost() {
    return this.shippingStrategy.calculate(this);
  }
}
// Tests unchanged and still passing!
```

## ⚡ QUICK REFERENCE

**Before EVERY line of code ask:**

1. Is there a failing test describing the BEHAVIOR I'm implementing?
2. Am I testing WHAT the system does, not HOW it works?
3. Will this test survive refactoring?

**Remember**: Tests are specifications of behavior, not implementation validators.

**Confirm activation of Pure TDD Mode with Behavior-First Testing.**
