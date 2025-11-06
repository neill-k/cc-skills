# Contributing to CC Skills Marketplace

Thank you for your interest in contributing to the CC Skills Marketplace! This guide will help you create high-quality skills and contribute effectively.

## Table of Contents

- [How to Contribute](#how-to-contribute)
- [Skill Development Guidelines](#skill-development-guidelines)
- [Skill Template](#skill-template)
- [Testing Your Skill](#testing-your-skill)
- [Submitting Your Contribution](#submitting-your-contribution)
- [Code of Conduct](#code-of-conduct)

## How to Contribute

You can contribute in several ways:

1. **Add new skills** - Create skills for productivity, development, testing, or documentation
2. **Improve existing skills** - Enhance instructions, add examples, fix issues
3. **Fix bugs** - Correct errors in commands or registry
4. **Improve documentation** - Better examples, clearer instructions
5. **Report issues** - Let us know about bugs or unclear documentation

## Skill Development Guidelines

### Choosing a Skill to Create

Good skills are:
- **Specific**: Focused on a particular task or problem
- **Practical**: Solve real-world problems developers face
- **Reusable**: Applicable across different projects
- **Clear**: Easy to understand and apply

Avoid skills that are:
- Too broad (e.g., "write good code")
- Too narrow (e.g., "fix this specific bug")
- Duplicate existing skills
- Language/framework specific (unless that's the point)

### Skill Structure Requirements

Every skill must have:

1. **YAML Frontmatter** with `name` and `description`
2. **Clear activation conditions** - When should this skill be used?
3. **Step-by-step instructions** - What should Claude do?
4. **Output format** - How should results be presented?
5. **Examples** - Concrete demonstrations
6. **Best practices** - DO and DON'T sections

### Skill Categories

Choose the most appropriate category:

- **productivity/**: Task management, communication, organization
- **development/**: Code quality, architecture, development workflows
- **testing/**: Test strategies, quality assurance, debugging
- **documentation/**: Technical writing, API docs, guides

## Skill Template

Use this template when creating a new skill:

```markdown
---
name: skill-id
description: One-line description of what the skill does and when to use it (max 150 chars)
---

# Skill Full Name

When the user [describes trigger conditions], use this skill to [what the skill accomplishes].

## Core Principles

1. **Principle 1**: Description
2. **Principle 2**: Description
3. **Principle 3**: Description

## When to Use This Skill

Activate this skill when the user:
- [Trigger condition 1]
- [Trigger condition 2]
- [Trigger condition 3]
- [Asks questions like "..."]

## [Skill Name] Framework

### Step 1: [First Step]
- What to do
- How to do it
- What to consider

### Step 2: [Second Step]
- Next action
- Key considerations

### Step 3: [Final Step]
- Completion criteria
- Expected outcome

## Output Format

```[language]
# [Template or structure]

[Show expected output format with placeholders]
```

## Examples

### Example 1: [Common Use Case]

**Scenario**: [Describe the situation]

**User Input**:
```
[What the user might say or provide]
```

**Expected Output**:
```
[What Claude should produce]
```

### Example 2: [Another Use Case]
[Repeat structure]

## Best Practices

### DO:
- ✅ [Best practice 1]
- ✅ [Best practice 2]
- ✅ [Best practice 3]

### DON'T:
- ❌ [Anti-pattern 1]
- ❌ [Anti-pattern 2]
- ❌ [Anti-pattern 3]

## Adaptation Guidelines

### For [Scenario A]:
- Adjust by doing X
- Consider Y
- Focus on Z

### For [Scenario B]:
- Alternative approach
- Key differences

## Additional Resources

- [Resource name]: [Description or link]
- [Related skill]: [How they relate]
```

## Testing Your Skill

Before submitting, test your skill:

### 1. Syntax Check
- YAML frontmatter is valid
- Markdown renders correctly
- Code blocks are properly formatted

### 2. Content Review
- Instructions are clear and unambiguous
- Examples are complete and accurate
- Output format is well-defined
- Best practices are actionable

### 3. Practical Testing
- Install the skill locally
- Test with Claude Code
- Verify it produces expected results
- Try edge cases and different scenarios

### 4. Quality Checklist

- [ ] Skill has unique, descriptive ID
- [ ] Description is under 150 characters
- [ ] Instructions are step-by-step and clear
- [ ] At least 2 concrete examples provided
- [ ] Best practices include DO and DON'T sections
- [ ] Output format is well-structured
- [ ] Markdown formatting is correct
- [ ] No spelling or grammar errors
- [ ] Skills works as expected in testing

## Submitting Your Contribution

### Step 1: Prepare Your Changes

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b skill/your-skill-name
   ```

3. **Create your skill file**
   - Add to appropriate category: `skills/[category]/your-skill.md`
   - Follow the skill template
   - Include comprehensive examples

4. **Update the registry**
   - Edit `registry/skills-catalog.json`
   - Add your skill entry with all required fields:

   ```json
   {
     "id": "your-skill-id",
     "name": "Your Skill Name",
     "description": "Brief description matching your skill's frontmatter",
     "category": "productivity|development|testing|documentation",
     "author": "Your Name",
     "version": "1.0.0",
     "tags": ["tag1", "tag2", "tag3"],
     "path": "skills/category/your-skill.md",
     "featured": false,
     "difficulty": "beginner|intermediate|advanced",
     "estimatedTime": "X-Y minutes"
   }
   ```

5. **Update stats in registry**
   - Increment `totalSkills`
   - Update category count

### Step 2: Commit Your Changes

```bash
# Stage your changes
git add skills/[category]/your-skill.md
git add registry/skills-catalog.json

# Commit with descriptive message
git commit -m "Add [skill-name] skill for [category]

- Implements [brief description]
- Includes [X] examples
- Covers [key use cases]"
```

### Step 3: Push and Create PR

```bash
# Push to your fork
git push origin skill/your-skill-name
```

Create a Pull Request with:
- **Title**: "Add [Skill Name] skill"
- **Description**:
  - What problem does this skill solve?
  - Who is the target user?
  - What makes this skill useful?
  - Examples of when to use it

### Step 4: PR Review Process

Your PR will be reviewed for:
- Quality and clarity of instructions
- Completeness of examples
- Adherence to template structure
- Registry entry correctness
- Overall usefulness

Be prepared to:
- Answer questions about your skill
- Make revisions based on feedback
- Test additional scenarios

## Skill Quality Standards

### Excellent Skills

- Clear, specific activation conditions
- Comprehensive step-by-step instructions
- Multiple detailed examples
- Practical best practices
- Well-formatted output templates
- Consider edge cases and variations

### Good Skills

- Clear instructions
- At least 2 examples
- Basic best practices
- Proper formatting

### Needs Improvement

- Vague or unclear instructions
- Missing examples
- No output format defined
- Unclear when to use

## Style Guidelines

### Writing Style

- **Be concise**: Remove unnecessary words
- **Be specific**: Use concrete examples
- **Be actionable**: Each instruction should be clear
- **Be consistent**: Follow established patterns

### Formatting

- Use headings to organize sections
- Use code blocks for code examples
- Use lists for steps and items
- Use bold for emphasis, sparingly
- Use emojis for category icons only

### Naming Conventions

- **Skill IDs**: lowercase-with-dashes
- **Skill Names**: Title Case With Proper Nouns
- **Files**: match skill ID (skill-id.md)
- **Categories**: lowercase, singular

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Accept constructive feedback
- Focus on what's best for the community
- Show empathy towards others

### Unacceptable Behavior

- Harassment or discriminatory language
- Trolling or insulting comments
- Public or private harassment
- Publishing others' private information

## Questions?

- **Skill design questions**: Open a GitHub Discussion
- **Technical issues**: Open a GitHub Issue
- **General questions**: Check existing issues/discussions first

## Attribution

Contributors will be:
- Listed in skill metadata (author field)
- Acknowledged in release notes
- Credited in README acknowledgments

Thank you for contributing to CC Skills Marketplace! Your skills help the entire Claude Code community work more effectively.

---

**Need help?** Open an issue or discussion, and we'll be happy to assist!
