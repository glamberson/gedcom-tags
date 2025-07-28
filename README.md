# gedcom-tags

**Version:** 0.1.0

This repository contains a proposed [FamilySearch GEDCOM](https://gedcom.io/specs/) extension for implementing a universal tagging system across all genealogical record types.

This extension enables GEDCOM 7 to preserve organizational tags (with colors and vendor-specific attributes) that are commonly used in modern genealogy software but lost during GEDCOM export.

## Quick Example

Traditional GEDCOM loses all tagging information:
```gedcom
0 @I1@ INDI
1 NAME John /Smith/
# DNA Match tag is lost
# Research priority tag is lost
```

With the Tag Extension:
```gedcom
0 HEAD
1 SCHMA
2 TAG _TAG https://gedcom.io/terms/v7/_TAG

0 @T1@ _TAG
1 NAME DNA Match
1 _COLOR #00FF00

0 @T2@ _TAG
1 NAME Research Priority
1 _COLOR #FF0000
1 _ATTR priority
2 _VALUE high

0 @I1@ INDI
1 NAME John /Smith/
1 _TAG @T1@
2 DATE 2024-12-15
2 NOTE 3rd cousin match on Ancestry
1 _TAG @T2@
```

## Documentation

- [Specification](tag-extension.md) - Complete technical specification
- [Design Rationale](DESIGN_RATIONALE.md) - Why this extension exists
- [Examples](examples/) - Sample GEDCOM files using the extension
- [Migration Guide](MIGRATION_GUIDE.md) - How to adopt this extension
- [Glossary](GLOSSARY.md) - Terms and definitions

## Features

- **Universal Application**: Tags can be applied to any GEDCOM record type
- **Visual Organization**: Optional color support using 6-digit hex codes
- **Vendor Flexibility**: Generic attribute mechanism for software-specific features
- **Round-trip Preservation**: Maintains tag data through import/export cycles

## Minimal Implementation

The simplest valid tag:
```gedcom
0 @T1@ _TAG
1 NAME To Review
```

## Status

This extension is currently in **DRAFT** status and seeking community feedback.

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This specification is licensed under [CC-BY-SA-4.0](LICENSE).