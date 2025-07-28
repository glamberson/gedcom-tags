# Changelog

All notable changes to the GEDCOM Tag Extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2025-01-28

### Added
- Initial specification for _TAG record type
- NAME field for tag identification (required)
- _COLOR field for visual representation (optional)
- _ATTR mechanism for vendor-specific attributes
- Support for tag application to any record type
- Comprehensive documentation:
  - Full technical specification
  - Design rationale document
  - Migration guide for developers and users
  - Glossary of terms
  - Contributing guidelines
- Example GEDCOM files:
  - basic.ged - Simple tag usage
  - advanced.ged - Complex scenarios with vendor attributes
  - gramps-compatibility.ged - Hierarchical tags example
- YAML definitions for GEDCOM registry submission

### Design Decisions
- Chose _TAG over _CATG for clarity
- Standardized on 6-digit hex colors only
- Made color optional to support text-only uses
- Used generic _ATTR mechanism for extensibility
- Allowed application to any record type

### Known Limitations
- No built-in hierarchy support (use _ATTR)
- No predefined tag meanings
- No color name support (hex only)
- No tag inheritance mechanism

[0.1.0]: https://github.com/genealogy-ai/gedcom-tags/releases/tag/v0.1.0