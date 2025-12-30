# Code Review Skill
## Systematic Code Analysis with Evidence Collection

*"Read with intent. Question with purpose. Document with care."*

---

## Purpose

Conduct thorough code reviews by:
- Following a systematic review checklist
- Collecting evidence of issues and strengths
- Running verification commands
- Producing actionable feedback

---

## When to Use

- Reviewing PRs or patches
- Auditing code quality
- Security review
- Performance analysis
- Onboarding code understanding

---

## Prerequisites

- File tools (read)
- Terminal tools (run tests, linters)
- **Tier 2** (read + execute)

---

## Protocol

### Step 1: Setup

1. Create REVIEW.yml to track the review
2. Identify files to review
3. Note review focus (security? performance? style?)

### Step 2: First Pass — Overview

1. List all changed/target files
2. Understand the purpose (PR description, commit messages)
3. Note initial impressions

### Step 3: Deep Review

For each file:
1. Read the code
2. Check against review criteria
3. Note findings (issues, questions, praise)
4. Run relevant checks

### Step 4: Verification

1. Run tests
2. Run linters
3. Check for regressions
4. Verify claims in PR description

### Step 5: Synthesize

1. Compile findings into REVIEW.md
2. Prioritize issues (blocking, important, minor)
3. Provide actionable feedback

---

## Core Files

### REVIEW.yml
```yaml
review:
  name: "PR #123: Add user authentication"
  status: "in_progress"
  started: "2025-12-30"
  
focus:
  - security
  - correctness
  - maintainability

files:
  - path: "src/auth/login.ts"
    status: "reviewed"
    issues: 2
    
  - path: "src/auth/middleware.ts"
    status: "in_progress"
    issues: 0
    
  - path: "tests/auth.test.ts"
    status: "pending"
    issues: 0

findings:
  blocking:
    - id: "B1"
      file: "src/auth/login.ts"
      line: 45
      type: "security"
      summary: "Password compared with == instead of constant-time compare"
      details: "Timing attack vulnerability"
      
  important:
    - id: "I1"
      file: "src/auth/login.ts"
      line: 23
      type: "correctness"
      summary: "Missing null check on user lookup"
      details: "Will throw if user not found"
      
  minor:
    - id: "M1"
      file: "src/auth/middleware.ts"
      line: 12
      type: "style"
      summary: "Inconsistent naming: authUser vs authenticatedUser"

  praise:
    - file: "tests/auth.test.ts"
      note: "Excellent edge case coverage"

verification:
  tests:
    ran: true
    passed: true
    command: "npm test"
    
  linter:
    ran: true
    passed: false
    issues: 3
    command: "npm run lint"
```

### REVIEW.md
```markdown
# Code Review: PR #123 — Add User Authentication

## Summary

Overall: **Needs Changes** (1 blocking issue)

| Severity | Count |
|----------|-------|
| 🚫 Blocking | 1 |
| ⚠️ Important | 1 |
| 💡 Minor | 1 |

---

## Blocking Issues

### B1: Timing Attack Vulnerability
**File:** `src/auth/login.ts:45`  
**Type:** Security

Password comparison uses `==` which is vulnerable to timing attacks.

**Current:**
```typescript
if (password == storedHash) { ... }
```

**Suggested:**
```typescript
import { timingSafeEqual } from 'crypto';
if (timingSafeEqual(Buffer.from(password), Buffer.from(storedHash))) { ... }
```

---

## Important Issues

### I1: Missing Null Check
**File:** `src/auth/login.ts:23`  
**Type:** Correctness

User lookup result not checked for null before accessing properties.

---

## Minor Issues

### M1: Inconsistent Naming
**File:** `src/auth/middleware.ts:12`  
**Type:** Style

Mix of `authUser` and `authenticatedUser` naming.

---

## Praise 🎉

- Excellent test coverage for edge cases in `tests/auth.test.ts`

---

## Verification Results

| Check | Status |
|-------|--------|
| Tests | ✅ Passed |
| Linter | ⚠️ 3 issues |

---

## Recommendation

**Request changes** — Please fix the timing attack vulnerability (B1) before merge.
```

---

## Review Checklist

### Security
- [ ] Input validation
- [ ] Output encoding
- [ ] Authentication checks
- [ ] Authorization checks
- [ ] Sensitive data handling
- [ ] Injection vulnerabilities
- [ ] Timing attacks

### Correctness
- [ ] Logic errors
- [ ] Edge cases handled
- [ ] Null/undefined handling
- [ ] Error handling
- [ ] Race conditions
- [ ] Resource cleanup

### Maintainability
- [ ] Code clarity
- [ ] Appropriate comments
- [ ] Consistent naming
- [ ] DRY (no duplication)
- [ ] Single responsibility
- [ ] Testability

### Performance
- [ ] Algorithmic complexity
- [ ] Memory usage
- [ ] Database queries
- [ ] Caching considerations
- [ ] Unnecessary operations

---

## Finding Severity

| Level | Meaning | Action |
|-------|---------|--------|
| 🚫 Blocking | Must fix before merge | Request changes |
| ⚠️ Important | Should fix, or explain | Request changes |
| 💡 Minor | Nice to fix | Comment only |
| 🎉 Praise | Good work! | Celebrate |

---

## Commands

| Intent | Action |
|--------|--------|
| "Start review" | Create REVIEW.yml |
| "Review file X" | Read, analyze, note findings |
| "Run tests" | Execute test suite |
| "Run linter" | Execute linter |
| "Add finding" | Append to REVIEW.yml |
| "Compile review" | Generate REVIEW.md |

---

## Outputs

- REVIEW.yml with structured findings
- REVIEW.md with formatted feedback
- Verification results
- Prioritized action items
