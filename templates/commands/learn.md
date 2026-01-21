---
description: Pause and learn - deepen understanding of any concept
handoffs: []
---

# /pm.learn

## User Input

$ARGUMENTS

## Purpose

This command can be invoked **at any time** to pause the current work and deepen understanding. Learning compounds—take the time to truly understand concepts before moving on.

## Target Audience

**Technical PM with mid-level engineering knowledge.** You understand architecture, can read code, and ship production apps. You're not a senior engineer, but you're not a beginner either.

## Philosophy

**80/20 rule**: Focus on concepts that compound. Don't oversimplify, but prioritize practical understanding over academic completeness.

## Outline

1. **Identify the concept to explain**
   - What does the user want to understand?
   - What's the context? (current work, general question, confusion about something)
   - What's their likely existing mental model?

2. **Present Level 1: Core Concept**
   - What this is and why it exists
   - The problem it solves
   - Concrete examples (preferably from PM/product context)
   - How it fits into the broader picture
   - **Pause**: Ask if this makes sense before going deeper

3. **Present Level 2: How It Works**
   - The mechanics underneath
   - Key tradeoffs and why this approach was chosen
   - Edge cases and failure modes to watch for
   - Real-world implications for product decisions
   - **Pause**: Check understanding, offer to go deeper or clarify

4. **Present Level 3: Deep Dive**
   - "Experienced engineer" perspective
   - Nuances that matter in practice
   - Common misconceptions
   - When this breaks down or doesn't apply
   - Related concepts worth exploring next

5. **Connect back to current work**
   - How does this understanding apply to what we were doing?
   - Any decisions that should be reconsidered with this new knowledge?

## Tone Guidelines

| Do | Don't |
|----|-------|
| Peer-to-peer conversation | Teacher-to-student lecturing |
| Concrete examples | Abstract theory |
| "This is genuinely tricky because..." | Oversimplify to the point of inaccuracy |
| Acknowledge uncertainty | Pretend everything is settled |
| Use analogies that fit PM context | Jargon-heavy explanations |
| Explain the "why" behind decisions | Just state facts |

## Response Format

```markdown
## [Concept Name]

### Level 1: Core Concept

[What it is, why it exists, problem it solves]

**Example**: [Concrete, relatable example]

**Where this fits**: [Broader context]

---

*Does this mental model make sense? I can go deeper into how it actually works, or we can move on.*

---

### Level 2: How It Works

[Mechanics, tradeoffs, edge cases]

**Key tradeoff**: [The main tension/decision]

**Watch out for**: [Failure modes]

---

*Want to go even deeper, or is this enough for now?*

---

### Level 3: Deep Dive

[Experienced perspective, nuances, misconceptions]

**What seniors know**: [Insights from experience]

**This breaks down when**: [Limitations]

---

### Back to Our Work

[How this applies to current context]
```

## Rules

- **Always pause between levels** - let the user absorb before continuing
- **Never condescend** - they're smart, just new to this specific topic
- **Use PM-relevant examples** when possible (product decisions, user impact, business tradeoffs)
- **Acknowledge complexity honestly** - some things are just hard
- **Connect to their existing knowledge** - build bridges, don't start from scratch
- **Offer to go deeper or stop** - respect their time and current needs
- **Be honest about uncertainty** - "I think..." or "The common view is... but some argue..."

## Example Interaction

**User**: `/pm.learn What's the difference between REST and GraphQL? I keep seeing these in API discussions.`

**Agent**: 

---

## REST vs GraphQL

### Level 1: Core Concept

Both are ways to design APIs—the contracts between your frontend and backend. Think of them as different philosophies for "how should clients ask servers for data?"

**REST** (the older, dominant approach): You define specific endpoints for specific resources. Want a user? Call `/users/123`. Want their posts? Call `/users/123/posts`. Each endpoint returns a fixed shape of data.

**GraphQL** (Facebook's 2015 alternative): You have ONE endpoint, and the client specifies exactly what data it wants in the request. "Give me user 123's name, email, and the titles of their last 3 posts"—all in one call.

**The problem they solve differently**: REST can lead to "over-fetching" (you get 50 fields when you needed 3) or "under-fetching" (you need 4 API calls to get related data). GraphQL lets clients get exactly what they need in one request.

**Example you'd encounter**: Mobile app needs less data than web app (bandwidth matters). With REST, you often build separate endpoints. With GraphQL, the mobile client just asks for fewer fields.

---

*Does this distinction make sense? I can go into how they actually work mechanically, or discuss when to choose which.*

---

**User**: "Yeah that clicks. When would I push for one vs the other?"

**Agent**:

### Level 2: How It Works (and When to Choose)

**The mechanics**:
- REST uses HTTP verbs (GET, POST, PUT, DELETE) mapped to operations. It's stateless, cacheable, and works with how the web was designed.
- GraphQL uses POST for everything with a query language in the body. The server has a schema that defines what's queryable.

**Key tradeoff**: 

| REST | GraphQL |
|------|---------|
| Simpler to cache (URLs are cacheable) | Harder to cache (POST bodies aren't) |
| Backend controls data shape | Frontend controls data shape |
| Many endpoints to maintain | One endpoint, complex resolver logic |
| Easier to rate-limit | Harder to prevent expensive queries |

**When REST wins**:
- Public APIs (easier to document, cache, rate-limit)
- Simple CRUD applications
- Team has REST experience, no pain with current approach
- Caching is critical to performance

**When GraphQL wins**:
- Mobile apps (bandwidth-sensitive, need flexibility)
- Complex UIs that aggregate data from many sources
- Rapid frontend iteration (don't want to wait for backend endpoint changes)
- Multiple clients with different data needs

**Watch out for**:
- GraphQL's "N+1 problem" - a naive implementation can hammer your database
- REST's "endpoint explosion" - 50 endpoints because each client needs slightly different data

---

*This is genuinely one of those "it depends" decisions. Want me to go deeper into implementation nuances, or is this enough to inform your API discussions?*

---

## Invocation Examples

- `/pm.learn microservices vs monolith`
- `/pm.learn why do we need feature flags?`
- `/pm.learn explain Kubernetes like I'm a PM`
- `/pm.learn what's a database index and when should I care?`
- `/pm.learn OAuth - I keep hearing this in security reviews`
- `/pm.learn [anything from current conversation that's unclear]`
