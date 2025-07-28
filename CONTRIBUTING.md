# Contributing to gedcom-tags

We welcome contributions to improve the GEDCOM Tag Extension! This document provides guidelines for contributing.

## How to Contribute

### Reporting Issues

1. **Check existing issues** first to avoid duplicates
2. **Use a clear title** that describes the problem
3. **Provide examples** showing the issue
4. **Suggest solutions** if you have ideas

### Suggesting Enhancements

1. **Describe the use case** - why is this needed?
2. **Provide real examples** from genealogy software
3. **Consider compatibility** with existing implementations
4. **Keep it simple** - complexity should have clear benefits

### Pull Requests

1. **Fork the repository** and create a feature branch
2. **Make focused changes** - one feature per PR
3. **Update documentation** for any changes
4. **Add examples** showing new features
5. **Test your changes** with GEDCOM validators

## What We're Looking For

### Documentation Improvements
- Clarifications to the specification
- Additional examples
- Migration guides for specific software
- Translations

### Example Files
- Real-world usage scenarios
- Software-specific examples
- Edge case demonstrations
- Test cases

### Community Feedback
- Implementation experiences
- Software compatibility reports
- Use case documentation
- Best practices

## What We're NOT Looking For

### Core Specification Changes
The core specification (NAME + _COLOR + _ATTR) is intentionally minimal. We're unlikely to accept:
- New required fields
- Changes to color format
- Modifications to _ATTR mechanism

### Vendor-Specific Features
- These belong in _ATTR, not the core spec
- Document them in examples instead
- Share for community benefit

### Business Logic
- Tag meanings or semantics
- Required tag hierarchies  
- Color significance rules

## Development Process

### 1. Discuss First
For significant changes:
- Open an issue for discussion
- Get community feedback
- Reach consensus before implementing

### 2. Implementation
- Follow existing formatting
- Match documentation style
- Include clear examples

### 3. Review Process
- All changes require review
- Address feedback constructively
- Be patient - genealogy standards move carefully

## Code of Conduct

### Be Respectful
- Consider diverse perspectives
- Appreciate volunteer efforts
- Keep discussions professional

### Be Inclusive
- Welcome newcomers
- Explain genealogy-specific concepts
- Consider international users

### Be Collaborative
- Build on others' ideas
- Credit contributions
- Share knowledge freely

## Testing

### Validation
- Ensure examples pass GEDCOM 7 validation
- Test with multiple validators
- Verify character encoding

### Compatibility
- Test imports in available software
- Document any issues found
- Share workarounds

## Documentation Standards

### Specification Format
- Use clear, unambiguous language
- Provide ABNF notation where applicable
- Include practical examples

### Examples
- Use realistic data
- Show common use cases
- Demonstrate edge cases
- Include comments explaining features

### File Naming
- Use descriptive names
- Follow existing patterns
- Include version numbers where relevant

## Questions?

- Open an issue for clarification
- Check existing documentation first
- Be specific about confusion points

Thank you for contributing to genealogical data portability!