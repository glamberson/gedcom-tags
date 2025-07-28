# GEDCOM Tag Extension Specification

## Abstract

This document defines a GEDCOM 7 extension for organizational tags that can be applied to any record type. Tags provide visual categorization through optional colors and support vendor-specific attributes for enhanced functionality.

## Extension Identifier

`https://gedcom.io/terms/v7/_TAG`

## Purpose

Modern genealogy software universally implements tagging or categorization systems, but these are lost during GEDCOM export. This extension preserves:

- User-defined organizational tags
- Visual color coding
- Software-specific tag attributes
- Tag applications across all record types

## Structure Definition

### Tag Record (_TAG)

A tag is a top-level record that defines a reusable organizational marker.

```abnf
tag-record = "@" XREF "@" "_TAG" 1*LINE-FEED
             1*tag-content

tag-content = tag-name /
              tag-color /
              tag-attribute

tag-name = "1 NAME " 1*CHAR 1*LINE-FEED

tag-color = "1 _COLOR " color-value 1*LINE-FEED
color-value = "#" 6HEXDIG
HEXDIG = DIGIT / "A" / "B" / "C" / "D" / "E" / "F" /
                "a" / "b" / "c" / "d" / "e" / "f"

tag-attribute = "1 _ATTR " attribute-name 1*LINE-FEED
                "2 _VALUE " attribute-value 1*LINE-FEED
```

### Tag Application

Tags are applied to records using the `_TAG` substructure:

```abnf
tag-application = "1 _TAG @" XREF "@" 1*LINE-FEED
                  [tag-date]
                  [tag-note]

tag-date = "2 DATE " date-value 1*LINE-FEED
tag-note = "2 NOTE " 1*CHAR 1*LINE-FEED
```

## Required Fields

### NAME (Required)
- **Purpose**: Human-readable identifier for the tag
- **Cardinality**: [1:1]
- **Example**: `1 NAME Research Complete`

## Optional Fields

### _COLOR (Optional)
- **Purpose**: Visual representation of the tag
- **Format**: 6-digit hexadecimal color (#RRGGBB)
- **Cardinality**: [0:1]
- **Example**: `1 _COLOR #00FF00`
- **Notes**: Case-insensitive, no spaces

### _ATTR (Optional)
- **Purpose**: Vendor-specific attributes
- **Cardinality**: [0:M]
- **Structure**: Name-value pairs
- **Example**:
  ```gedcom
  1 _ATTR priority
  2 _VALUE high
  ```

## Tag Application Rules

1. Tags can be applied to ANY record type
2. Multiple tags per record are allowed
3. Same tag can be applied to multiple records
4. Application can include date and note

## Examples

### Basic Tag Definition
```gedcom
0 @T1@ _TAG
1 NAME Verified
```

### Tag with Color
```gedcom
0 @T2@ _TAG
1 NAME DNA Match
1 _COLOR #FF00FF
```

### Tag with Vendor Attributes
```gedcom
0 @T3@ _TAG
1 NAME Priority Research
1 _COLOR #FF0000
1 _ATTR priority
2 _VALUE 1
1 _ATTR category
2 _VALUE genealogy.research
```

### Applied to Individual
```gedcom
0 @I1@ INDI
1 NAME John /Smith/
1 _TAG @T2@
2 DATE 15 DEC 2024
2 NOTE 3rd cousin match on Ancestry, 45cM shared
```

### Applied to Source
```gedcom
0 @S1@ SOUR
1 TITL 1850 US Census
1 _TAG @T3@
```

### Complete Example
```gedcom
0 HEAD
1 GEDC
2 VERS 7.0
1 SCHMA
2 TAG _TAG https://gedcom.io/terms/v7/_TAG

0 @T1@ _TAG
1 NAME Brick Wall
1 _COLOR #8B0000

0 @T2@ _TAG
1 NAME DNA Confirmed
1 _COLOR #00FF00
1 _ATTR test_type
2 _VALUE Y-DNA
1 _ATTR haplogroup
2 _VALUE R1b

0 @I1@ INDI
1 NAME William /Thompson/
1 _TAG @T1@
2 DATE 5 JAN 2025
2 NOTE Cannot find parents despite extensive research
1 _TAG @T2@
2 DATE 15 MAR 2024
```

## Import/Export Requirements

### Import
1. MUST preserve all _TAG records
2. MUST maintain tag references
3. MUST accept any valid 6-digit hex color
4. SHOULD preserve all _ATTR entries
5. MAY map to internal tag system

### Export  
1. MUST include all user-defined tags
2. MUST export colors as 6-digit hex
3. SHOULD include relevant _ATTR
4. MUST maintain referential integrity

## Compatibility Considerations

### Round-trip Preservation
- Systems MUST preserve unrecognized _ATTR entries
- Systems MUST maintain tag applications even if not displayed

### Graceful Degradation
- Systems not supporting tags will ignore _TAG records
- No data loss for core genealogical information

## Best Practices

1. Use descriptive tag names
2. Limit tags to organizational purposes
3. Document tag meanings for collaboration
4. Use standard color choices for common concepts

## Version History

- 0.1.0 (2025-01-28): Initial draft specification