# Code Standards

Consistency makes our codebase maintainable. These are our coding standards and best practices.

## General Principles

1. **Readability > Cleverness** - Code is read more than written
2. **Simple > Complex** - Choose the simplest solution that works
3. **Explicit > Implicit** - Be clear about intent
4. **Tested > Untested** - If it's not tested, it's broken

## Language-Specific Standards

### JavaScript/TypeScript

#### Style Guide
We follow [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) with these modifications:

```javascript
// ✅ Good: Clear naming
const getUserById = async (userId: string) => {
  const user = await db.users.findById(userId);
  return user;
};

// ❌ Bad: Unclear naming
const get = async (id) => {
  const u = await db.users.findById(id);
  return u;
};
```

#### Key Rules
- Use `const` by default, `let` when needed, never `var`
- Prefer async/await over promises
- Use TypeScript for new code
- Functional components for React
- 2 spaces for indentation

### Python

Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) with these additions:

```python
# ✅ Good: Clear and typed
def calculate_total(items: List[Item]) -> Decimal:
    """Calculate total price for items including tax."""
    subtotal = sum(item.price for item in items)
    return subtotal * Decimal("1.08")

# ❌ Bad: No types, unclear
def calc(i):
    t = 0
    for x in i:
        t += x.price
    return t * 1.08
```

#### Key Rules
- Use type hints for function signatures
- Docstrings for all public functions
- 4 spaces for indentation
- Max line length: 88 (Black formatter)

## Code Review Standards

### What We Look For

#### Must Have
- [ ] **Works** - Feature/fix functions correctly
- [ ] **Tested** - Appropriate test coverage
- [ ] **Secure** - No security vulnerabilities
- [ ] **Performant** - No obvious performance issues

#### Should Have
- [ ] **Readable** - Clear variable/function names
- [ ] **Documented** - Complex logic explained
- [ ] **Consistent** - Follows team patterns
- [ ] **Maintainable** - Easy to modify later

### Review Process

1. **Self-review** first - Check your own PR
2. **Request review** from appropriate teammate
3. **Address feedback** promptly
4. **Re-request** after changes
5. **Merge** after approval

### Giving Feedback

```markdown
# Good feedback
"Consider extracting this logic into a separate function for reusability.
Here's an example: [code snippet]"

# Less helpful
"This code is messy."
```

## Testing Standards

### Test Coverage Requirements
- New features: 80% minimum
- Bug fixes: Must include regression test
- Refactoring: Maintain existing coverage

### Test Structure
```javascript
describe('UserService', () => {
  describe('createUser', () => {
    it('should create a user with valid data', async () => {
      // Arrange
      const userData = { name: 'John', email: 'john@example.com' };
      
      // Act
      const user = await UserService.createUser(userData);
      
      // Assert
      expect(user.id).toBeDefined();
      expect(user.name).toBe('John');
    });

    it('should throw error for invalid email', async () => {
      // Test edge cases
    });
  });
});
```

## Git Standards

### Commit Messages
Follow [Conventional Commits](https://www.conventionalcommits.org/):

```bash
# Good commits
feat: add user authentication
fix: resolve memory leak in image processor
docs: update API documentation
refactor: simplify database connection logic
test: add tests for payment service

# Bad commits
fixed stuff
WIP
update
asdf
```

### Branch Naming
```bash
feature/add-user-auth
fix/memory-leak-images
chore/update-dependencies
hotfix/critical-payment-bug
```

## Documentation Standards

### Code Comments
```javascript
// ✅ Good: Explains WHY
// We need to retry 3 times because the external API
// occasionally fails with transient network errors
const MAX_RETRIES = 3;

// ❌ Bad: Explains WHAT (obvious from code)
// Set MAX_RETRIES to 3
const MAX_RETRIES = 3;
```

### Function Documentation
```typescript
/**
 * Calculates the shipping cost based on weight and destination.
 * 
 * @param weight - Package weight in kilograms
 * @param destination - ISO country code
 * @returns Shipping cost in USD
 * @throws {InvalidDestinationError} If destination is not supported
 * 
 * @example
 * calculateShipping(2.5, 'US') // Returns 15.99
 */
function calculateShipping(weight: number, destination: string): number {
  // Implementation
}
```

## Performance Standards

### Frontend
- Initial load: < 3 seconds
- Interaction response: < 100ms
- Lighthouse score: > 90

### Backend
- API response: < 200ms (p50)
- Database queries: < 100ms
- Background jobs: < 5 minutes

### Optimization Checklist
- [ ] Minimize bundle size
- [ ] Optimize images
- [ ] Cache appropriately
- [ ] Paginate large datasets
- [ ] Index database queries

## Security Standards

### Never Do This
```javascript
// ❌ NEVER commit secrets
const apiKey = "sk_live_abc123def456";

// ❌ NEVER trust user input
const query = `SELECT * FROM users WHERE id = ${req.params.id}`;

// ❌ NEVER disable security features
process.env["NODE_TLS_REJECT_UNAUTHORIZED"] = 0;
```

### Always Do This
```javascript
// ✅ Use environment variables
const apiKey = process.env.API_KEY;

// ✅ Parameterize queries
const query = 'SELECT * FROM users WHERE id = $1';
db.query(query, [req.params.id]);

// ✅ Validate input
const schema = Joi.object({
  email: Joi.string().email().required(),
  age: Joi.number().min(0).max(120)
});
```

## Accessibility Standards

- All images need alt text
- Forms need labels
- Keyboard navigation support
- ARIA labels where needed
- Color contrast ratio: 4.5:1 minimum

## Monitoring & Logging

### What to Log
```javascript
// ✅ Good: Actionable information
logger.info('Payment processed', { 
  userId, 
  amount, 
  transactionId 
});

// ❌ Bad: Sensitive information
logger.info('User logged in', { 
  email, 
  password // NEVER log passwords!
});
```

### Error Handling
```javascript
try {
  await processPayment(order);
} catch (error) {
  // Log error with context
  logger.error('Payment processing failed', {
    error: error.message,
    orderId: order.id,
    userId: order.userId,
    stack: error.stack
  });
  
  // Handle gracefully
  throw new PaymentError('Payment could not be processed');
}
```

## Tools & Automation

### Linters & Formatters
- **JavaScript/TS**: ESLint + Prettier
- **Python**: Black + Pylint
- **CSS**: Stylelint
- **Markdown**: markdownlint

### Pre-commit Hooks
```bash
# .pre-commit-config.yaml
- repo: local
  hooks:
    - id: lint
      name: Lint
      entry: npm run lint
    - id: test
      name: Test
      entry: npm test
```

## Exceptions

Sometimes we need to break these rules. When you do:
1. Document why in a comment
2. Get team agreement
3. Create a ticket to fix later (if temporary)

## Questions?

- Standards questions: #engineering on Slack
- Suggest changes: Open a PR to this doc
- Architecture decisions: Weekly tech sync

Remember: These standards help us work better together. They're not rules for rules' sake! 🎯