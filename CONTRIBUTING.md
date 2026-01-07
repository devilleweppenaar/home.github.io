# Contributing

This is a personal website repository. These guidelines are primarily for my own reference.

## Commit messages

- **Lowercase**: Start with a lowercase letter
- **Past tense**: "updated profile image" not "update profile image"
- **Descriptive**: Be clear about what changed
- **Concise**: Keep under 50 characters to avoid truncation on GitHub
- **No prefixes**: No `feat:`, `fix:`, etc.
- **No emojis**

### Examples

Good:
- `updated profile image alt text`
- `fixed accessible warning`
- `improved icon styling`

Avoid:
- `Update profile image` (uppercase)
- `update profile` (imperative mood)
- `🎨 style: Update the profile styling` (emoji + prefix)

## Commit signing

All commits must be signed. This is enforced by branch protection rules on main.

## Git configuration

The repository uses a GitHub noreply email for privacy:
```bash
git config user.email "11049609+devilleweppenaar@users.noreply.github.com"
```

This keeps personal email addresses private while maintaining commit verification on GitHub.
