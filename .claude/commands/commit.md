# Commit Command

Create well-formatted git commits for the Life Timeline project with conventional commit messages.

## Usage

```
/commit
/commit --no-verify
```

## What this command does

1. **Analyzes Changes**: Reviews staged and unstaged files to understand what changed
2. **Stages Files**: Automatically stages relevant files if none are staged
3. **Categorizes Changes**: Determines the type of change based on files modified
4. **Creates Commit Message**: Generates a conventional commit message with appropriate emoji
5. **Commits Changes**: Creates the git commit with the generated message

## Commit Types for Life Timeline Project

Based on the project's focus on personal timeline data and visualization:

- **feat** (✨): New life events, device entries, or timeline features
  - Adding new gadgets, life milestones, or family members
  - New timeline visualization features
  - Configuration enhancements

- **fix** (🐛): Bug fixes in timeline display or data
  - Correcting dates, device specs, or timeline positioning
  - Fixing JavaScript errors or CSS issues
  - Data consistency corrections

- **docs** (📝): Documentation updates
  - README updates
  - CLAUDE.md improvements
  - Comment additions or clarifications

- **style** (💄): Visual improvements or formatting
  - CSS styling changes
  - Color scheme updates
  - Layout improvements
  - Code formatting (HTML/CSS/JS)

- **refactor** (♻️): Code restructuring without changing functionality
  - JavaScript refactoring
  - HTML structure improvements
  - CSS organization

- **chore** (🔧): Maintenance tasks
  - Configuration updates
  - File reorganization
  - Build or deployment changes

## Life Timeline Specific Guidelines

### Data Changes
- **Device Updates**: Use `feat` for new devices, `fix` for corrections
- **Life Events**: Use `feat` for new milestones, `fix` for date/detail corrections
- **Family Members**: Use `feat` when adding new family member entries

### Visual Changes
- **Timeline Display**: Use `style` for visual improvements, `fix` for display bugs
- **Color Coding**: Use `style` for new device type colors or visual enhancements

### File-Specific Patterns
- **life.md changes**: Usually `feat` (new entries) or `fix` (corrections)
- **index.html changes**: `feat` (new features), `style` (CSS), `fix` (bugs)
- **config.json changes**: `chore` (settings) or `feat` (new configuration options)

## Commit Message Format

```
<type>: <description>

[optional body]

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

### Examples

```bash
feat: add iPhone 15 Pro Max entry for Zain
fix: correct MacBook Pro purchase date for Najmi
style: improve device color coding in timeline
docs: update README with new setup instructions
chore: update configuration for timeline display
```

## Best Practices

1. **Be Specific**: Mention which family member or device type when relevant
2. **Use Present Tense**: "add iPhone entry" not "added iPhone entry"
3. **Keep Under 72 Characters**: For the first line of commit message
4. **Atomic Commits**: One logical change per commit
5. **Consistent Naming**: Use device names as they appear in life.md

## File Staging Logic

The command will automatically stage files based on:
- **life.md**: Always stage if modified (contains the timeline data)
- **index.html**: Stage if contains functionality changes
- **config.json**: Stage if configuration changes are made
- **README.md, CLAUDE.md**: Stage documentation updates

## Pre-commit Validation

Since this is a simple HTML/CSS/JS project without complex tooling:
- Validates that life.md follows the expected markdown format
- Checks that config.json is valid JSON
- Ensures index.html has no obvious syntax errors
- Verifies timeline data consistency where possible