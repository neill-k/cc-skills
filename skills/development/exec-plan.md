---
name: exec-plan
description: Create structured, living work plans for complex coding tasks with progress tracking, decision logs, and verification steps
---

# ExecPlan Skill

When the user requests help with a complex feature, refactoring, or significant code change, use this skill to create a structured work plan that serves as a living document throughout execution.

## Core Principles

1. **Structured Planning**: Break down complex work into concrete, verifiable steps
2. **Living Document**: Update the plan continuously as work progresses
3. **Decision Capture**: Log important choices and rationale
4. **Progress Visibility**: Track completion with timestamps and status
5. **Learning Record**: Document surprises, discoveries, and lessons learned

## When to Use This Skill

Activate this skill when the user:
- Starts a new feature implementation
- Plans a significant refactoring
- Requests help with a complex bug fix
- Needs to coordinate multi-file changes
- Wants a structured approach to development
- Asks "how should I approach this?"
- Mentions planning, roadmap, or execution strategy

## ExecPlan Framework

An ExecPlan is a **task-scoped work plan** that becomes shared vocabulary between you and the user. It structures how features get built, providing clarity and reducing cognitive load.

### Document Structure

Every ExecPlan should contain these sections:

1. **Metadata**: Ownership, dates, related links
2. **Short Description**: One-sentence outcome statement
3. **Purpose / Big Picture**: User or system gains with measurable outcomes
4. **Context and Orientation**: Current state, file locations, terminology
5. **Plan of Work**: Concrete steps with verification
6. **Progress**: Checkbox-tracked steps with timestamps
7. **Surprises & Discoveries**: Unexpected findings and optimizations
8. **Decision Log**: Material decisions with rationale
9. **Outcomes & Retrospective**: Results and lessons learned
10. **Risks / Open Questions**: (Optional) Assumptions and metrics
11. **Next Steps / Handoff Notes**: (Optional) Remaining work

## Output Format

```markdown
# ExecPlan: [Feature/Task Name]

> **Living design and execution record**

## Metadata

- **Owner**: [Your name or team]
- **Created**: [YYYY-MM-DD]
- **Last Updated**: [YYYY-MM-DD HH:MM UTC]
- **Agent Path**: [e.g., .agents/feature-name/]
- **Related Plans**: [Links to related plans or issues]
- **Status**: 🟡 In Progress | 🟢 Complete | 🔴 Blocked

---

## Short Description

[One sentence: What new behavior or improvement will exist when complete?]

Example: "Users can now filter search results by date range with sub-second response times."

---

## Purpose / Big Picture

**What does the user or system gain?**

[Explain measurable outcomes and benefits]

**Success Criteria:**
- [ ] Criterion 1 with measurable target
- [ ] Criterion 2 with measurable target
- [ ] Criterion 3 with measurable target

Example: "Users can ask multi-turn clarifications within 2s latency, improving task completion rates by 30%."

---

## Context and Orientation

**Current State:**
[Summarize the existing system, its limitations, and why this work is needed]

**Key Files:**
- `path/to/file1.ext` - Current role and limitations
- `path/to/file2.ext` - Current role and limitations
- `path/to/file3.ext` - Current role and limitations

**Domain Terminology:**
- **Term 1**: Definition (don't assume prior knowledge)
- **Term 2**: Definition
- **Term 3**: Definition

**Assumptions:**
- Assumption 1
- Assumption 2

---

## Plan of Work

### Phase 1: [Phase Name]

**1. [Concrete Action]**
- **Files affected**: `path/to/file.ext`
- **Expected effect**: What will change
- **Verification**: How to confirm it works
- **Estimated time**: X hours

**2. [Next Action]**
- **Files affected**: `path/to/files.ext`
- **Expected effect**: What will change
- **Verification**: How to confirm it works
- **Estimated time**: Y hours

### Phase 2: [Phase Name]

**3. [Action]**
...

### Phase 3: Testing & Validation

**X. [Test Action]**
- **Test coverage**: What scenarios to test
- **Expected results**: Pass criteria
- **Verification**: Test commands to run

---

## Progress

**Overall**: ⚪⚪⚪⚪⚪⚪⚪⚪⚪⚪ 0% (0/10 steps)

- [ ] **Step 1**: [Description]
  - Status: Pending
  - Started: —
  - Completed: —

- [x] **Step 2**: [Description]
  - Status: ✅ Complete
  - Started: 2025-01-10 14:22 UTC
  - Completed: 2025-01-10 15:45 UTC
  - Notes: [Any relevant notes]

- [ ] **Step 3**: [Description]
  - Status: 🟡 In Progress (60%)
  - Started: 2025-01-10 15:50 UTC
  - Completed: —
  - Notes: Blocked by API rate limit issue

[Continue for all steps...]

**Velocity**: [X steps per day/hour, if tracking]

---

## Surprises & Discoveries

**[YYYY-MM-DD]**: [Discovery Title]
- **What**: What we found
- **Why it matters**: Impact on the plan
- **Action taken**: What we did about it
- **Evidence**: Links, metrics, or observations

Example:
**2025-01-10**: Database query N+1 problem in user list
- **What**: Found existing user list endpoint making 100+ queries per request
- **Why it matters**: 5s+ response time blocking this feature
- **Action taken**: Added eager loading, reduced to 2 queries
- **Evidence**: Response time dropped from 5.2s to 0.3s (see PR #123)

---

## Decision Log

**[YYYY-MM-DD]**: [Decision Title]
- **Decision**: What was decided
- **Rationale**: Why this choice over alternatives
- **Alternatives considered**: What else was evaluated
- **Trade-offs**: What we're giving up
- **Decided by**: [Name/role]

Example:
**2025-01-10**: Use Redis for caching instead of in-memory cache
- **Decision**: Implement Redis-based caching layer
- **Rationale**: Need shared cache across multiple servers
- **Alternatives considered**: In-memory cache (doesn't scale), Memcached (less feature-rich)
- **Trade-offs**: Additional infrastructure dependency, slight latency increase (2ms)
- **Decided by**: Engineering team consensus

---

## Outcomes & Retrospective

### What Worked ✅
- [Successful approach or decision]
- [Technique that proved valuable]
- [Tool or pattern that helped]

### What Didn't Work ❌
- [Challenge or obstacle]
- [Approach that failed]
- [Assumption that was wrong]

### Measured Impact 📊
- **Metric 1**: Before → After (% change)
- **Metric 2**: Before → After (% change)
- **Metric 3**: Before → After (% change)

### Lessons Learned 💡
- [Key insight for future work]
- [Pattern to apply elsewhere]
- [Pitfall to avoid]

---

## Risks / Open Questions

**Risks:**
- ⚠️ **[Risk]**: Description and mitigation strategy
- ⚠️ **[Risk]**: Description and mitigation strategy

**Open Questions:**
- ❓ **[Question]**: Context and why it matters
- ❓ **[Question]**: Context and why it matters

**Success Metrics:**
- [ ] Metric 1: Target value
- [ ] Metric 2: Target value

---

## Next Steps / Handoff Notes

**Immediate Next Steps:**
1. [Next action item]
2. [Next action item]
3. [Next action item]

**Future Enhancements:**
- [Potential improvement]
- [Follow-up feature]
- [Technical debt to address]

**Handoff Information:**
- PR: #[number] - [title]
- Related Issues: #[number], #[number]
- Documentation: [link to docs]
- Deployment Notes: [special considerations]

---

**Plan Status**: 🟡 Active | Last updated: [timestamp]
```

## Best Practices

### DO:
- ✅ **Update continuously**: Treat the plan as a living document
- ✅ **Be specific**: Use concrete file paths and measurable outcomes
- ✅ **Track progress**: Update checkboxes and timestamps religiously
- ✅ **Log decisions**: Capture rationale while it's fresh
- ✅ **Document surprises**: Write down unexpected findings immediately
- ✅ **Use timestamps**: Always include UTC timestamps for tracking
- ✅ **Break down work**: Keep steps small and verifiable
- ✅ **Think in phases**: Group related work logically
- ✅ **Define success**: Make success criteria measurable
- ✅ **Capture context**: Explain terms and assumptions

### DON'T:
- ❌ **Set and forget**: Don't write the plan then ignore it
- ❌ **Be vague**: Avoid "improve performance" without metrics
- ❌ **Skip verification**: Every step needs a way to confirm success
- ❌ **Ignore discoveries**: Document unexpected findings
- ❌ **Assume knowledge**: Define domain-specific terminology
- ❌ **Hide decisions**: Always explain why, not just what
- ❌ **Make steps too large**: Break down anything taking >4 hours
- ❌ **Forget timestamps**: Track when work actually happens
- ❌ **Abandon retrospectives**: Always complete the outcomes section

## Usage Patterns

### Pattern 1: New Feature Development

**User**: "I need to add user authentication to my app"

**Assistant**: "I'll create an ExecPlan to structure this feature implementation."

*Creates comprehensive plan with:*
- Context about current auth state
- Phases: Database → API endpoints → Frontend → Testing
- Specific file changes with verification steps
- Security considerations in decision log
- Progress tracking setup

### Pattern 2: Complex Refactoring

**User**: "This module has become a mess, help me refactor it"

**Assistant**: "Let me create an ExecPlan for this refactoring to ensure we don't break anything."

*Creates plan with:*
- Current state analysis and pain points
- Incremental refactoring steps (small, testable changes)
- Test strategy to maintain behavior
- Progress checkboxes for each refactor
- Decision log for architectural choices

### Pattern 3: Bug Fix with Root Cause Analysis

**User**: "Users are reporting intermittent 500 errors"

**Assistant**: "I'll create an ExecPlan to systematically debug and fix this issue."

*Creates plan with:*
- Hypothesis section for potential causes
- Investigation steps with verification
- Fix implementation plan
- Monitoring and validation steps
- Surprises section to document root cause

### Pattern 4: Multi-File Coordination

**User**: "We need to migrate from REST to GraphQL"

**Assistant**: "This is a complex migration. Let me create an ExecPlan to coordinate all the changes."

*Creates plan with:*
- Complete file inventory and dependencies
- Migration phases with rollback points
- Parallel work opportunities
- Integration testing strategy
- Handoff notes for deployment

## Example: Complete ExecPlan in Action

**Scenario**: User wants to add API rate limiting

**ExecPlan Output**:

````markdown
# ExecPlan: API Rate Limiting Implementation

> **Living design and execution record**

## Metadata

- **Owner**: Development Team
- **Created**: 2025-01-10
- **Last Updated**: 2025-01-10 16:30 UTC
- **Agent Path**: `.agents/rate-limiting/`
- **Related Plans**: None
- **Status**: 🟡 In Progress

---

## Short Description

API endpoints now enforce rate limits of 100 requests per minute per user, preventing abuse while maintaining quality of service for legitimate users.

---

## Purpose / Big Picture

**What does the user or system gain?**

The system gains protection against API abuse, reduces server load from runaway scripts, and ensures fair resource distribution among users. Legitimate users experience consistent performance.

**Success Criteria:**
- [ ] 100 req/min limit enforced per user with <5ms overhead
- [ ] Rate limit information returned in response headers
- [ ] Configurable limits per user tier (free/pro/enterprise)
- [ ] Graceful error messages when limits exceeded
- [ ] Monitoring dashboard shows rate limit hits

---

## Context and Orientation

**Current State:**
Currently, the API has no rate limiting. Some users run aggressive scripts that cause load spikes (up to 10,000 req/min), degrading service for others. We've had 3 outages in the past month related to API abuse.

**Key Files:**
- `src/middleware/auth.ts` - Current authentication middleware (38 lines)
- `src/routes/api.ts` - API route definitions (200+ lines)
- `src/config/limits.ts` - (NEW) Rate limit configuration
- `src/middleware/rateLimit.ts` - (NEW) Rate limiting logic

**Domain Terminology:**
- **Token bucket algorithm**: Rate limiting method that allows bursts while enforcing average rate
- **X-RateLimit headers**: Standard HTTP headers communicating limits to clients
- **429 status code**: "Too Many Requests" HTTP status

**Assumptions:**
- Using Redis for distributed rate limit tracking
- Rate limits apply per authenticated user (not IP-based)
- All existing API routes will be protected

---

## Plan of Work

### Phase 1: Infrastructure Setup

**1. Add Redis dependency and configuration**
- **Files affected**: `package.json`, `src/config/redis.ts` (NEW)
- **Expected effect**: Redis client available for rate limit storage
- **Verification**: `npm install` succeeds, Redis connection test passes
- **Estimated time**: 1 hour

**2. Create rate limit configuration**
- **Files affected**: `src/config/limits.ts` (NEW)
- **Expected effect**: Centralized config for different user tiers
- **Verification**: Config values accessible, TypeScript types correct
- **Estimated time**: 30 minutes

### Phase 2: Middleware Implementation

**3. Implement token bucket rate limiter**
- **Files affected**: `src/middleware/rateLimit.ts` (NEW)
- **Expected effect**: Middleware checks and updates rate limit counters
- **Verification**: Unit tests pass for limit enforcement
- **Estimated time**: 3 hours

**4. Add rate limit headers to responses**
- **Files affected**: `src/middleware/rateLimit.ts`
- **Expected effect**: Responses include X-RateLimit-* headers
- **Verification**: Response headers present in test requests
- **Estimated time**: 1 hour

### Phase 3: Integration

**5. Apply middleware to API routes**
- **Files affected**: `src/routes/api.ts`
- **Expected effect**: All routes protected by rate limiting
- **Verification**: Test requests get rate limited after threshold
- **Estimated time**: 1 hour

**6. Add error handling for rate limit exceeded**
- **Files affected**: `src/middleware/errorHandler.ts`
- **Expected effect**: Clear 429 error message with retry info
- **Verification**: Exceeded requests get helpful error message
- **Estimated time**: 30 minutes

### Phase 4: Testing & Monitoring

**7. Write integration tests**
- **Files affected**: `tests/rateLimit.integration.test.ts` (NEW)
- **Expected effect**: Comprehensive test coverage for rate limiting
- **Verification**: All tests pass, >90% coverage
- **Estimated time**: 2 hours

**8. Add monitoring dashboard**
- **Files affected**: `src/monitoring/rateLimitMetrics.ts` (NEW)
- **Expected effect**: Dashboard shows rate limit hits by user/endpoint
- **Verification**: Dashboard accessible, shows real-time data
- **Estimated time**: 2 hours

---

## Progress

**Overall**: ⚫⚫⚫⚫⚫⚪⚪⚪⚪⚪ 50% (4/8 steps)

- [x] **Step 1**: Add Redis dependency and configuration
  - Status: ✅ Complete
  - Started: 2025-01-10 14:00 UTC
  - Completed: 2025-01-10 14:45 UTC
  - Notes: Used ioredis library, connection pool configured

- [x] **Step 2**: Create rate limit configuration
  - Status: ✅ Complete
  - Started: 2025-01-10 14:50 UTC
  - Completed: 2025-01-10 15:15 UTC
  - Notes: Added tiered limits (free: 60/min, pro: 300/min, enterprise: 1000/min)

- [x] **Step 3**: Implement token bucket rate limiter
  - Status: ✅ Complete
  - Started: 2025-01-10 15:20 UTC
  - Completed: 2025-01-10 16:10 UTC
  - Notes: Used sliding window for accuracy, 12 unit tests passing

- [x] **Step 4**: Add rate limit headers to responses
  - Status: ✅ Complete
  - Started: 2025-01-10 16:15 UTC
  - Completed: 2025-01-10 16:30 UTC
  - Notes: Headers: X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset

- [ ] **Step 5**: Apply middleware to API routes
  - Status: 🟡 In Progress
  - Started: 2025-01-10 16:35 UTC
  - Completed: —
  - Notes: Working on route-specific overrides for admin endpoints

- [ ] **Step 6**: Add error handling for rate limit exceeded
  - Status: Pending

- [ ] **Step 7**: Write integration tests
  - Status: Pending

- [ ] **Step 8**: Add monitoring dashboard
  - Status: Pending

**Velocity**: ~4 steps per 2.5 hours (1.6 steps/hour)

---

## Surprises & Discoveries

**2025-01-10 15:45**: Redis performance exceeds expectations
- **What**: Rate limit checks averaging 0.8ms instead of expected 5ms
- **Why it matters**: Gives us headroom for more sophisticated limiting algorithms
- **Action taken**: Documented for future reference, no plan changes needed
- **Evidence**: Load testing shows p95 latency of 1.2ms for 10k requests

**2025-01-10 16:20**: Some routes need different limits
- **What**: Admin endpoints and webhooks need separate (higher) limits
- **Why it matters**: Current design assumes uniform limits per user
- **Action taken**: Adding route-specific limit overrides in middleware
- **Evidence**: Admin users reported 429s during bulk operations

---

## Decision Log

**2025-01-10 14:30**: Use token bucket algorithm over fixed window
- **Decision**: Implement sliding window token bucket algorithm
- **Rationale**: Better handles bursts, more accurate than fixed windows
- **Alternatives considered**: Fixed window (simpler but less accurate), leaky bucket (harder to implement)
- **Trade-offs**: Slightly more complex implementation, minimal performance difference
- **Decided by**: Engineering team after reviewing rate limiting patterns

**2025-01-10 16:25**: Add route-specific limit overrides
- **Decision**: Allow individual routes to override default rate limits
- **Rationale**: Admin and webhook endpoints need higher limits than user endpoints
- **Alternatives considered**: Separate user tiers (too complex), ignore issue (blocks legitimate use)
- **Trade-offs**: Adds configuration complexity, worth it for flexibility
- **Decided by**: Lead developer after admin user feedback

---

## Outcomes & Retrospective

*(To be completed after implementation)*

### What Worked ✅
- TBD

### What Didn't Work ❌
- TBD

### Measured Impact 📊
- TBD

### Lessons Learned 💡
- TBD

---

## Risks / Open Questions

**Risks:**
- ⚠️ **Redis single point of failure**: If Redis goes down, API becomes unusable
  - Mitigation: Implement fallback to in-memory cache with degraded accuracy
- ⚠️ **Clock drift in distributed systems**: Multiple servers might have slightly different time
  - Mitigation: Use Redis SCRIPT for atomic operations

**Open Questions:**
- ❓ **Should websockets count against rate limits?**: Currently undefined behavior
- ❓ **How to handle shared API keys**: Multiple users with same key could hit limits quickly

**Success Metrics:**
- [ ] API abuse incidents: 3/month → 0/month
- [ ] P95 latency overhead: <5ms
- [ ] False positive rate: <0.1%

---

## Next Steps / Handoff Notes

**Immediate Next Steps:**
1. Complete route integration (Step 5)
2. Implement error handling (Step 6)
3. Write integration tests (Step 7)
4. Deploy to staging for testing

**Future Enhancements:**
- Implement rate limit exemptions for specific users
- Add GraphQL-specific rate limiting (query complexity)
- Create user-facing rate limit dashboard

**Handoff Information:**
- PR: #458 - Add API rate limiting
- Related Issues: #389 (API abuse report), #401 (performance issues)
- Documentation: Update API docs with rate limit details
- Deployment Notes: Requires Redis cluster, environment variables for limits

---

**Plan Status**: 🟡 Active | Last updated: 2025-01-10 16:35 UTC
````

## Integration with Development Workflow

### Storing Plans

**Recommended structure:**
```
.agents/
  ├── template/
  │   └── PLAN.md          # Master template
  ├── feature-auth/
  │   └── PLAN.md          # Feature-specific plan
  ├── refactor-api/
  │   └── PLAN.md          # Refactoring plan
  └── tmp/                  # Quick iterations (gitignored)
      └── PLAN.md
```

### Workflow

1. **Start**: User describes complex task
2. **Plan**: Create ExecPlan using this skill
3. **Execute**: Work through plan, updating progress
4. **Discover**: Log surprises and decisions as they happen
5. **Review**: Complete retrospective at milestones
6. **Complete**: Archive or delete plan after merge

### Tips for Long-Running Sessions

- **Update frequently**: Don't let the plan drift from reality
- **Checkpoint progress**: Update status after completing each step
- **Document blockers**: When stuck, write it in Progress notes
- **Capture insights**: Write down discoveries immediately
- **Reference the plan**: Regularly review what's next
- **Adapt as needed**: Plans can change - document why

## Adaptation Guidelines

### For Solo Projects
- Simplify metadata (owner, handoff notes less critical)
- Focus on Progress and Surprises sections
- Use as personal execution log

### For Team Projects
- Emphasize Decision Log for async communication
- Include detailed Handoff Notes
- Link to PRs and issues extensively
- Update more frequently for visibility

### For Learning Projects
- Expand Surprises & Discoveries section
- Focus heavily on Retrospective
- Document wrong assumptions prominently

### For Production Systems
- Require Risks section completion
- Mandate verification steps for every change
- Include rollback procedures
- Link to monitoring/alerting

This skill transforms complex development work from chaotic improvisation into structured, trackable, and repeatable execution.