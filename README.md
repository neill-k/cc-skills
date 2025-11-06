# CC Skills Marketplace

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](https://github.com/your-org/cc-skills/releases)
[![Skills](https://img.shields.io/badge/skills-2-orange.svg)](#available-skills)

> A skills marketplace for Claude Code featuring production-grade development methodologies: ExecPlan for structured task planning and REPL-Driven Development for interactive Clojure programming

## ✨ Features

### ExecPlan
- **📋 Structured Planning**: Living work plans for complex development tasks
- **📊 Progress Tracking**: Checkbox-tracked steps with timestamps and velocity metrics
- **📝 Decision Logging**: Capture important choices, rationale, and trade-offs
- **🔍 Discovery Documentation**: Log surprises, discoveries, and lessons learned
- **✅ Verification Steps**: Concrete validation for every change

### REPL-Driven Development (Clojure)
- **⚡ Live Coding**: Immediate feedback with Clojure 1.12 REPL workflow
- **💬 Rich Comment Blocks**: Living documentation and interactive exploration
- **🔄 State Management**: Mount, Integrant, Component patterns for long-running sessions
- **🎯 Bottom-Up Design**: Build and compose small functions with continuous testing
- **🔍 Data Inspection**: Portal, tap>, and CIDER integration for visualization
- **🧪 TDD Integration**: Combine REPL exploration with test-driven development

### Marketplace
- **🔍 Smart Discovery**: Browse, search, and filter skills by category and tags
- **📦 Easy Installation**: Simple commands to install and activate skills
- **🚀 Ready to Use**: Production-grade skills with comprehensive examples

## 📋 Table of Contents

- [Installation](#installation)
- [Quick Start](#quick-start)
- [Available Commands](#available-commands)
- [Available Skills](#available-skills)
- [Usage Examples](#usage-examples)
- [Creating Your Own Skills](#creating-your-own-skills)
- [Contributing](#contributing)
- [License](#license)

## 🚀 Installation

### Step 1: Add the Marketplace

In Claude Code, register this marketplace:

```bash
/plugin marketplace add your-org/cc-skills
```

Replace `your-org` with your actual GitHub organization or username.

### Step 2: Install the Plugin

```bash
/plugin install cc-skills-marketplace@your-org
```

### Step 3: Verify Installation

Run the skills command to see the marketplace:

```bash
/skills
```

You should see a welcome message with available commands.

## 🏃 Quick Start

### Browse All Available Skills

```bash
/skills-browse
```

This displays all skills organized by category with descriptions, difficulty levels, and installation commands.

### Search for Specific Skills

```bash
/skills-search testing
```

Find skills related to testing, or search for any topic:

```bash
/skills-search code review
/skills-search productivity
/skills-search api
```

### Get Detailed Information

```bash
/skills-info task-breakdown
```

View comprehensive information about a specific skill including usage guidance and examples.

### Install a Skill

```bash
/skills-install task-breakdown
```

Once installed, simply mention the skill in your requests:
- "Use the Task Breakdown skill to plan this feature"
- "Apply Code Review Checklist to this PR"

## 📚 Available Commands

| Command | Description |
|---------|-------------|
| `/skills` | Main hub - overview and quick start guide |
| `/skills-browse` | Browse all skills by category |
| `/skills-search <query>` | Search skills by name, tags, or description |
| `/skills-info <skill-id>` | Get detailed information about a skill |
| `/skills-install <skill-id>` | Install a skill to your environment |

## 🎨 Available Skills

### 💻 Development (2 skills)

#### ⭐ ExecPlan
Create structured, living work plans for complex coding tasks with progress tracking, decision logs, and verification steps.

- **ID**: `exec-plan`
- **Difficulty**: Intermediate
- **Time**: 10-20 minutes to create plan, ongoing for updates
- **Install**: `/skills-install exec-plan`

**What is ExecPlan?**

ExecPlan is a planning methodology that transforms complex development work from chaotic improvisation into structured, trackable, and repeatable execution. It provides a comprehensive framework for:

- **Task-Scoped Work Plans**: Break down features, refactorings, and bug fixes into concrete steps
- **Living Documentation**: Plans that evolve with your work, not static documents
- **Progress Visibility**: Checkbox tracking with timestamps and velocity metrics
- **Decision Capture**: Log important choices, rationale, and trade-offs as you make them
- **Discovery Documentation**: Record surprises, optimizations, and lessons learned
- **Verification Steps**: Every change has a concrete way to validate it works

**When to Use ExecPlan:**

- Implementing new features (especially multi-file changes)
- Planning significant refactorings
- Debugging complex, systemic issues
- Coordinating team development work
- Maintaining long-running development sessions
- Any task that will take more than a few hours

**ExecPlan Structure:**

Every plan includes:
1. **Metadata** - Ownership, dates, status tracking
2. **Purpose & Success Criteria** - What you're building and why
3. **Context & Orientation** - Current state, key files, terminology
4. **Plan of Work** - Concrete steps with verification
5. **Progress Tracking** - Real-time completion status
6. **Surprises & Discoveries** - Unexpected findings
7. **Decision Log** - Material choices with rationale
8. **Outcomes & Retrospective** - Results and lessons learned

---

#### ⭐ REPL-Driven Development with Clojure
Master REPL-driven development workflow for Clojure 1.12 with live coding, rich comment blocks, state management, and iterative design.

- **ID**: `repl-driven-clojure`
- **Difficulty**: Intermediate
- **Time**: 15-30 minutes to learn, ongoing practice
- **Install**: `/skills-install repl-driven-clojure`

**What is REPL-Driven Development?**

REPL-Driven Development is an interactive programming approach that provides immediate feedback as you write code. This skill covers the complete Clojure 1.12 workflow with modern best practices:

- **Live Coding**: Write functions and test them instantly in the REPL
- **Rich Comment Blocks**: Document explorations with `(comment ...)` forms
- **State Management**: Handle long-running sessions with Mount, Integrant, or Component
- **Bottom-Up Design**: Build small, tested functions and compose into larger systems
- **Data Inspection**: Visualize data with Portal, tap>, and CIDER inspector
- **Clojure 1.12 Features**: Method values, qualified methods, param tags, array syntax

**When to Use REPL-Driven Development:**

- Writing any Clojure code (it's the standard workflow)
- Exploring new libraries or APIs
- Debugging complex data transformations
- Building systems incrementally
- Rapid prototyping and experimentation
- Learning Clojure or onboarding new developers
- Combining with TDD for robust development

**Key Techniques Covered:**

1. **REPL Workflow** - Read, Evaluate, Print, Loop cycle
2. **Rich Comment Blocks** - Living documentation and examples
3. **Design Journals** - Document decisions and rationale
4. **State Management** - Mount, Integrant, Component patterns
5. **Namespace Management** - Reloading and refresh strategies
6. **Data Inspection** - Portal, tap>, CIDER inspector
7. **Performance** - Criterium benchmarking
8. **Debugging** - Scope capture and tap debugging
9. **Editor Integration** - CIDER, Calva, Cursive workflows
10. **Common Pitfalls** - Stale state, circular deps, side effects

---

## 💡 Usage Examples

### Example 1: Planning a New Feature

```
You: I need to add API rate limiting to protect against abuse

Claude: I'll create an ExecPlan to structure this implementation.

[Claude generates comprehensive plan with:]
- Current state analysis (no rate limiting, experiencing abuse)
- Phases: Infrastructure Setup → Middleware → Integration → Testing
- Specific file changes (package.json, config/limits.ts, middleware/rateLimit.ts)
- Verification steps for each change
- Progress tracking with checkboxes
- Decision log for algorithm choice (token bucket vs fixed window)
```

### Example 2: Complex Refactoring

```
You: This authentication module is a mess with 800 lines in one file. Help me refactor it.

Claude: Let me create an ExecPlan for this refactoring to ensure we maintain behavior.

[Claude provides structured plan with:]
- Context: Current pain points and why refactoring is needed
- Incremental steps that preserve functionality
- Test-first approach to validate behavior
- Progress tracking for each extraction
- Surprises section to document unexpected dependencies
```

### Example 3: Debugging Systemic Issues

```
You: Users are reporting intermittent 500 errors. Help me debug this.

Claude: I'll create an ExecPlan for systematic investigation and resolution.

[Claude creates plan with:]
- Hypothesis section for potential root causes
- Investigation steps with verification at each stage
- Fix implementation once root cause is identified
- Monitoring and validation steps
- Decision log for chosen solution approach
```

### Example 4: Coordinating Multi-File Changes

```
You: We're migrating from REST to GraphQL across the entire API surface.

Claude: This is complex. Let me create an ExecPlan to coordinate all the changes.

[Claude develops comprehensive migration plan:]
- Complete file inventory with dependencies
- Migration phases with rollback points
- Parallel work opportunities for team members
- Integration testing strategy
- Handoff notes for deployment and monitoring
```

### Example 5: Clojure REPL-Driven Feature Development

```
You: I need to build a user authentication system in Clojure. Help me use REPL-driven development.

Claude: I'll guide you through building this feature with REPL-driven development using Clojure 1.12.

[Claude provides interactive workflow:]
1. Start REPL and connect your editor
2. Define data specs for validation
3. Build hash-password function, test in REPL immediately
4. Create register-user function with inline testing
5. Build authenticate function, verify with mock data
6. Use rich comment blocks to document experiments
7. Codify successful experiments as formal tests
8. Integrate with state management (Mount/Integrant)

[Shows complete code with rich comment blocks demonstrating:]
- Spec validation tested interactively
- Password hashing verified in REPL
- Mock database for rapid iteration
- Authentication flow tested with various inputs
- Final test suite based on REPL explorations
```

### Example 6: Exploring Clojure 1.12 Features

```
You: Show me how to use the new Clojure 1.12 qualified method syntax.

Claude: I'll demonstrate Clojure 1.12's unified method syntax with REPL examples.

[Claude provides interactive examples:]
- Qualified instance methods: (String/length "hello")
- Method values as functions: (map String/length ["foo" "bar"])
- Constructor syntax: (java.util.ArrayList/new)
- Param tags for type hints
- Array class syntax updates (String* vs String-*)
- Complete REPL session showing real usage patterns
```

## 🛠️ Creating Your Own Skills

Want to add custom skills to the marketplace? Here's how:

### Skill Structure

Each skill is a markdown file with YAML frontmatter:

```markdown
---
name: my-skill
description: Brief description of what the skill does and when to use it
---

# My Skill Name

When the user [trigger conditions], use this skill to [what the skill does].

## When to Use This Skill

Activate this skill when the user:
- [Condition 1]
- [Condition 2]
- [Condition 3]

## Instructions

[Detailed instructions for Claude to follow when this skill is activated]

## Output Format

[Expected output structure]

## Best Practices

### DO:
- ✅ [Best practice 1]
- ✅ [Best practice 2]

### DON'T:
- ❌ [Anti-pattern 1]
- ❌ [Anti-pattern 2]

## Examples

[Concrete examples of the skill in action]
```

### Adding Your Skill

1. **Create the skill file** in the appropriate category directory:
   - `skills/productivity/my-skill.md`
   - `skills/development/my-skill.md`
   - `skills/testing/my-skill.md`
   - `skills/documentation/my-skill.md`

2. **Update the registry** in `registry/skills-catalog.json`:

```json
{
  "id": "my-skill",
  "name": "My Skill Name",
  "description": "Brief description",
  "category": "productivity",
  "author": "Your Name",
  "version": "1.0.0",
  "tags": ["tag1", "tag2"],
  "path": "skills/productivity/my-skill.md",
  "featured": false,
  "difficulty": "beginner",
  "estimatedTime": "5-10 minutes"
}
```

3. **Test your skill** by installing and using it

4. **Submit a pull request** (see Contributing section)

## 🤝 Contributing

Contributions are welcome! We're looking for:

- **New skills** across all categories
- **Improvements** to existing skills
- **Bug fixes** in commands or registry
- **Documentation** enhancements
- **Examples** and use cases

### How to Contribute

1. **Fork the repository**

2. **Create a feature branch**
   ```bash
   git checkout -b feature/new-skill-name
   ```

3. **Make your changes**
   - Add new skills or improve existing ones
   - Update the registry if adding/modifying skills
   - Test your changes

4. **Commit your changes**
   ```bash
   git commit -m 'Add new skill: [skill-name]'
   ```

5. **Push to your fork**
   ```bash
   git push origin feature/new-skill-name
   ```

6. **Open a Pull Request**
   - Describe your changes
   - Explain why the skill is useful
   - Include examples of the skill in action

### Skill Quality Guidelines

Skills should be:
- ✅ **Clear**: Easy to understand and follow
- ✅ **Comprehensive**: Cover all important cases
- ✅ **Practical**: Solve real-world problems
- ✅ **Well-structured**: Follow the skill template
- ✅ **Production-ready**: Include best practices and examples
- ✅ **Tested**: Verified to work as intended

## 📊 Marketplace Stats

- **Total Skills**: 2
- **Categories**: 4 (Productivity, Development, Testing, Documentation)
- **Featured Skills**: 2 (ExecPlan, REPL-Driven Development)
- **Difficulty Levels**: Intermediate (2)
- **Languages Covered**: Language-agnostic (ExecPlan), Clojure 1.12 (REPL-Driven)

## 🗺️ Roadmap

### v1.1 (Planned)
- [ ] Add ExecPlan templates for common scenarios (API development, refactoring, bug fixes)
- [ ] REPL-Driven Development templates for common Clojure patterns
- [ ] Additional Clojure skills: spec-driven development, test.check property testing
- [ ] Create ExecPlan CLI tool for easier plan management
- [ ] Add plan archiving and retrieval system

### v1.2 (Planned)
- [ ] Add 5-10 additional skills across all categories
- [ ] Productivity: Task breakdown, meeting notes, time tracking
- [ ] Testing: Test generation, coverage analysis, TDD workflows
- [ ] Documentation: README generation, API docs, code documentation
- [ ] More language-specific REPL workflows (Python, JavaScript, Elixir)
- [ ] Implement skill dependencies and skill collections

### v2.0 (Future)
- [ ] ExecPlan analytics (velocity tracking, completion patterns)
- [ ] REPL session recording and replay
- [ ] Team collaboration features (shared plans, handoffs)
- [ ] Integration with project management tools
- [ ] Plan diff and version history
- [ ] Multi-language support for international teams
- [ ] Interactive skill tutorials and guided walkthroughs

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### Getting Help

- **Documentation**: See individual skill files for detailed usage
- **Issues**: [GitHub Issues](https://github.com/your-org/cc-skills/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-org/cc-skills/discussions)

### Frequently Asked Questions

**Q: How do I activate a skill after installing it?**
A: Simply mention the skill by name in your request to Claude. For example:
- "Create an ExecPlan for implementing user authentication"
- "Use REPL-Driven Development to build this Clojure feature"
- "Guide me through the REPL workflow for this problem"

**Q: Where should I store ExecPlans?**
A: Recommended structure is `.agents/[feature-name]/PLAN.md` for feature-specific plans, with a template at `.agents/template/PLAN.md`. Quick iterations can go in `.agents/tmp/` (add to `.gitignore`).

**Q: Do I need to complete every section of an ExecPlan?**
A: Core sections (Metadata, Description, Purpose, Context, Plan, Progress) are essential. Risks/Open Questions and Handoff Notes are optional. Adapt based on your needs - solo projects need less than team projects.

**Q: Do I need to know Clojure to use the REPL-Driven Development skill?**
A: Basic Clojure knowledge helps, but this skill includes explanations of Clojure 1.12 features and can guide beginners through REPL workflows. It's useful for both learning and mastering advanced techniques.

**Q: Which Clojure editors work with the REPL-Driven skill?**
A: The skill covers CIDER (Emacs), Calva (VS Code), and Cursive (IntelliJ) with specific key bindings and workflows for each. Choose the editor you're comfortable with.

**Q: Can I use these skills together?**
A: Absolutely! Use ExecPlan to structure a complex Clojure project, then apply REPL-Driven Development techniques during implementation. They complement each other perfectly.

**Q: How do I update a skill?**
A: Currently, re-install with `/skills-install <skill-id>`. Automatic updates are planned for v1.2.

**Q: Can I customize skills for my team?**
A: Yes! Fork this repository and modify the skill files or create your own. Your team can install from your private marketplace.

**Q: Should I use ExecPlan for small tasks?**
A: ExecPlan is designed for complex tasks (multi-file changes, long-running work). For simple tasks under a few hours, it may be overkill. Use your judgment.

**Q: How long should ExecPlan sessions last?**
A: The methodology has enabled successful sessions of 30+ minutes up to 1 hour. Break very large projects into multiple ExecPlans (one per feature/phase).

**Q: Are skills free?**
A: Yes, all skills in this marketplace are open-source and free to use under the MIT license.

## 🙏 Acknowledgments

- Inspired by the [Anthropic Skills Repository](https://github.com/anthropics/skills)
- Built for the [Claude Code](https://claude.ai/code) community
- Thanks to all contributors who have added skills and improvements

---

**Made with ❤️ for the Claude Code community**

Start exploring: `/skills-browse` or `/skills-search <topic>`
