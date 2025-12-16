# Contributing to Logseq Tone

First off, thank you for considering contributing to Logseq Tone! 🎉

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Submitting Pull Requests](#submitting-pull-requests)
- [Development Setup](#development-setup)
- [Theme Development Guidelines](#theme-development-guidelines)
- [Color Palette Philosophy](#color-palette-philosophy)
- [Testing Your Changes](#testing-your-changes)

## Code of Conduct

This project adheres to a simple code of conduct: be respectful, constructive, and collaborative. We're all here to make this theme better.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When creating a bug report, include:

- **A clear, descriptive title**
- **VS Code version** (Help → About)
- **Theme variant** (Light or Dark)
- **Screenshot** showing the issue
- **Steps to reproduce** the problem
- **Expected vs actual behavior**

**Example:**
```markdown
## Bug: Markdown links are hard to read in Light theme

**Environment:**
- VS Code: 1.85.0
- Theme: Logseq Tone Light

**Steps:**
1. Open a Markdown file
2. Add a link: `[text](url)`
3. Link color is too light

**Expected:** Links should be clearly visible
**Actual:** Links blend into background

[Screenshot attached]
```

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, include:

- **Clear, descriptive title**
- **Detailed explanation** of the enhancement
- **Why it would be useful** to most users
- **Examples** from other themes (optional)

### Submitting Pull Requests

1. **Fork** the repository
2. **Create a branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the guidelines below
4. **Test thoroughly** in both Light and Dark variants
5. **Commit** with clear, descriptive messages:
   ```bash
   git commit -m "feat: improve markdown heading visibility"
   ```
6. **Push** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
7. **Open a Pull Request** with:
   - Clear description of changes
   - Screenshots (before/after if visual)
   - Testing checklist completed

## Development Setup

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/)

### Setup Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/logseq-tone-theme.git
   cd logseq-tone-theme
   ```

2. **Install dependencies:**
   ```bash
   npm install -g @vscode/vsce
   ```

3. **Open in VS Code:**
   ```bash
   code .
   ```

4. **Test the theme:**
   - Press `F5` to launch Extension Development Host
   - In the new window: `Ctrl+K Ctrl+T` → Select "Logseq Tone Light" or "Logseq Tone Dark"

5. **Package for testing:**
   ```bash
   vsce package
   ```

## Theme Development Guidelines

### File Structure

```
logseq-tone-theme/
├── themes/
│   ├── logseq-light-theme.json    # Light variant
│   └── logseq-dark-theme.json     # Dark variant
├── package.json                    # Extension manifest
├── README.md                       # Main documentation
├── CONTRIBUTING.md                 # This file
├── CHANGELOG.md                    # Version history
└── LICENSE                         # MIT License
```

### Color Guidelines

#### Light Theme Philosophy
- **Background:** Pure white (`#FFFFFF`) for clarity
- **Syntax:** Monochromatic gray scale (`#9CA3AF` → `#1F2937`)
- **Subtle differences:** Only 1-2 shades between similar elements
- **Links/Accents:** Logseq blue (`#1781E3`) for interactive elements

#### Dark Theme Philosophy
- **Background:** Logseq's signature dark teal (`#002B36`)
- **Syntax:** Harmonious teal/cyan gradient (`#5E7A82` → `#E8F4F7`)
- **Monochromatic:** All syntax stays within the teal family
- **Links/Accents:** Logseq teal (`#16A085`) for interactive elements

### Key Principles

1. **Subtlety First:** Syntax colors should be distinguishable but not distracting
2. **Consistency:** Both themes should follow the same logical structure
3. **Accessibility:** Maintain WCAG AA contrast ratios for readability
4. **Logseq DNA:** Stay true to Logseq's design language
5. **Base4Tone Inspiration:** Low-contrast, monochromatic syntax

### Editing Theme Files

Theme files are JSON with two main sections:

#### 1. UI Colors (`colors`)
Controls VS Code interface elements:
```json
{
  "colors": {
    "editor.background": "#FFFFFF",
    "editor.foreground": "#1F2937",
    // ... more UI elements
  }
}
```

**Important UI Elements:**
- `editor.*` - Editor area
- `sideBar.*` - File explorer
- `statusBar.*` - Bottom bar
- `tab.*` - File tabs
- `panel.*` - Terminal/Output panels

#### 2. Syntax Colors (`tokenColors`)
Controls code highlighting:
```json
{
  "tokenColors": [
    {
      "scope": ["comment"],
      "settings": {
        "foreground": "#9CA3AF",
        "fontStyle": "italic"
      }
    }
  ]
}
```

**Key Token Scopes:**
- `comment` - Comments
- `keyword` - Language keywords
- `string` - String literals
- `variable` - Variables
- `entity.name.function` - Functions
- `entity.name.type` - Classes/Types

### Color Selection Process

When choosing colors:

1. **Check existing colors** in Logseq's codebase
2. **Maintain the monochromatic gradient**
3. **Test with multiple languages** (JavaScript, Python, Markdown, etc.)
4. **Verify contrast ratios** using tools like [WebAIM](https://webaim.org/resources/contrastchecker/)
5. **Document the reasoning** in your PR

### Common Token Scopes Reference

```javascript
// Comments
"comment", "punctuation.definition.comment"

// Keywords
"keyword", "storage.type", "storage.modifier"

// Strings
"string", "string.quoted"

// Functions
"entity.name.function", "meta.function-call", "support.function"

// Variables
"variable", "variable.other", "variable.parameter"

// Classes/Types
"entity.name.type", "entity.name.class", "support.type"

// Constants
"constant.numeric", "constant.language"

// Tags (HTML/XML)
"entity.name.tag", "meta.tag"

// Markdown
"markup.heading", "markup.bold", "markup.italic", "markup.underline.link"
```

## Testing Your Changes

### Before Submitting

Test your changes against this checklist:

- [ ] Tested in **Light** variant
- [ ] Tested in **Dark** variant
- [ ] Checked with **JavaScript/TypeScript**
- [ ] Checked with **Python**
- [ ] Checked with **HTML/CSS**
- [ ] Checked with **Markdown**
- [ ] Verified **readability** in different lighting conditions
- [ ] Confirmed **UI elements** are properly colored
- [ ] No **console errors** in Extension Development Host
- [ ] Theme **packages successfully** with `vsce package`

### Testing Workflow

1. **Open test files:**
   ```bash
   # Create sample files for testing
   touch test.js test.py test.md test.html
   ```

2. **Launch Extension Development Host:**
   - Press `F5` in VS Code
   - Select your theme in the new window

3. **Check different scenarios:**
   - Syntax highlighting
   - UI elements (sidebar, tabs, panels)
   - Find/replace dialogs
   - Git diff colors
   - Terminal colors
   - Peek/hover views

4. **Compare with Logseq:**
   - Open Logseq app
   - Compare color choices
   - Ensure thematic consistency

## Version Numbering

We follow [Semantic Versioning](https://semver.org/):
- **MAJOR** (1.0.0): Breaking changes
- **MINOR** (0.1.0): New features, backward compatible
- **PATCH** (0.0.1): Bug fixes

## Commit Message Guidelines

Use clear, descriptive commit messages:

```
<type>: <subject>

<optional body>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, colors
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance

**Examples:**
```bash
feat: add better markdown link colors
fix: improve terminal foreground contrast
docs: update color palette documentation
style: adjust comment color in dark theme
```

## Need Help?

- 📖 Check existing [Issues](https://github.com/yourusername/logseq-tone-theme/issues)
- 💬 Start a [Discussion](https://github.com/yourusername/logseq-tone-theme/discussions)
- 📧 Contact the maintainer

## Recognition

All contributors will be:
- Listed in the project README
- Credited in release notes
- Given our eternal gratitude 🙏

---

Thank you for making Logseq Tone better! 🎨✨
