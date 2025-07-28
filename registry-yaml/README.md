# Registry YAML Files

This directory contains the YAML definitions for the GEDCOM Tag Extension in the format required by the FamilySearch GEDCOM registry.

## Structure

```
registry-yaml/
├── structure/          # Tag and structure definitions
│   ├── _TAG.yaml      # Tag record definition
│   ├── _TAG_ref.yaml  # Tag reference (substructure)
│   ├── _COLOR.yaml    # Color attribute
│   ├── _ATTR.yaml     # Generic attribute
│   └── _VALUE.yaml    # Attribute value
├── enumeration/       # (Currently empty - no enumerations defined)
└── enumeration-set/   # (Currently empty - no enumeration sets defined)
```

## Definitions

### Record Type
- `_TAG` - The tag record that defines a reusable organizational marker

### Structures
- `_TAG` (as substructure) - References a tag record to apply it
- `_COLOR` - Specifies the visual color for a tag
- `_ATTR` - Generic vendor-specific attribute
- `_VALUE` - Value for a generic attribute

## Registry Submission

These files should be submitted to the FamilySearch GEDCOM registry at:
https://github.com/FamilySearch/GEDCOM-registries

Follow the registry submission process documented in their repository.