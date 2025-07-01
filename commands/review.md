# /review - Comprehensive Code Review

Perform thorough code review across all repositories for current work:

1. **Identify Changed Files**

- Run `git status` in each repository
- Check `git diff` for uncommitted changes (not file by file, but overall in the repo)
- Review `git log --oneline -5` for recent commits
- **Compare feature branch to develop: `git diff develop...HEAD`**
- **Show all changes in feature branch: `git diff develop`**

2. **Security Review**

- Input validation on all boundaries
- Principle of least privilege (IAM, database access)
- Encryption in transit and at rest
- Audit logging for sensitive operations
- No hardcoded secrets or credentials

3. **Architecture & Design**

- Follows KISS, YAGNI, DRY principles
- Single responsibility, <300 lines per file
- Consistent with existing patterns
- No premature optimization or over-engineering

4. **Code Quality**

- Professional naming conventions
- Error handling implemented
- Logging added for debugging
- No eslint-disable or code smells
- Tests cover new functionality

5. **Business Impact**

- Solves actual business problem
- Aligns with ISO 27001 compliance needs
- Considers startup budget constraints
- Performance implications assessed

6. **Documentation**

- Code is self-documenting
- Complex logic explained
- API changes documented
- Breaking changes highlighted

**OUTPUT FORMAT:**
Either:

**✅ APPROVED: Ready for merge**
[describe what is good]

Or:

**❌ NEEDS CHANGES:**

**File:** path/to/file.ts **Line:** 42
(always newline)
**Issue:** Missing input validation
(always newline)
**Why:** Security vulnerability
(always newline)
**Fix:** Add zod schema validation
(always 2 newlinse)
**File:** path/to/other-file.ts **Line:** 33
(always newline)
**Issue:** other issue
(always newline)
**Why:** other reason
(always newline)
**Fix:** other fix
