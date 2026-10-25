# Contributing to YuqueToMarkdown

Thank you for your interest in improving YuqueToMarkdown!

## How to Contribute

1. Fork this repository.
2. Create a topic branch:
   ```bash
   git checkout -b feat/your-feature
   ```
3. Test your changes locally by opening `index.html` in any modern web browser.
4. Keep the tool zero-build and client-side only (no Node.js/Python server dependencies).
5. Submit a Pull Request describing your changes and tests.

## Code Guidelines

- Pure frontend client-side processing only.
- Strict UTF-8 encoding without BOM.
- Preserve backward compatibility with `.lakebook` and `.tar` exports.
