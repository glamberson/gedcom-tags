# Design Rationale for GEDCOM Tag Extension

## Problem Statement

Every major genealogy software platform implements some form of tagging, categorization, or color-coding system:

- **GRAMPS**: Full hierarchical tag objects with color and priority
- **Family Tree Maker**: 16 predefined colors and research flags
- **RootsMagic**: Groups with 15 color sets
- **Ancestry.com**: Visual groups and color markers
- **Legacy Family Tree**: Research tags and to-do items
- **MyHeritage**: Labels and smart matches

However, GEDCOM has no mechanism to preserve this organizational metadata. When users export their data, all tags, colors, and categorizations are lost. This forces users to recreate their organizational system in each software platform.

## Why This Matters

Tags serve critical organizational functions:
- **Research Status**: Track what needs review, what's verified
- **DNA Matches**: Mark confirmed genetic connections
- **Projects**: Organize research by family lines or goals
- **Data Quality**: Flag questionable or disputed information
- **Visual Navigation**: Use colors to quickly identify record types

Without tag preservation, users lose hundreds of hours of organizational work during software migrations.

## Design Principles

### 1. Minimal Core Specification
We define only what's necessary for interoperability:
- Tag identifier (NAME)
- Optional color (6-digit hex)
- Generic extension mechanism

### 2. Maximum Flexibility
- Tags can be applied to ANY record type
- No limits on number of tags
- Vendors can add any attributes they need

### 3. Transport, Not Business Logic
We specify how to move tag data, not how to use it:
- No prescribed tag meanings
- No required tag hierarchies
- No color semantics

### 4. Vendor Innovation
The _ATTR mechanism allows unlimited vendor-specific features without specification changes.

## Key Design Decisions

### Why _TAG not _CATG?
- **_TAG**: Industry standard term, immediately recognizable
- **_CATG**: Less intuitive, requires explanation
- The SCHMA.TAG overlap is a minor technical detail

### Why 6-Digit Hex Only?
- Unambiguous representation
- Universal parsing support
- No conversion conflicts
- Sufficient precision (16.7M colors)
- Single format prevents incompatibility (no "green" vs #00FF00 conflicts)
- Transport spec requires deterministic behavior

### Why Optional Color?
- Not all tags need visual representation
- Allows text-only implementations
- Supports accessibility needs

### Why Generic Attributes?
- Can't predict all vendor needs
- Allows innovation without spec changes
- Natural selection determines useful attributes

## Compatibility Strategy

### Round-trip Preservation
Systems must preserve all tag data, even if not displayed, ensuring no data loss during import/export cycles.

### Graceful Degradation
Systems that don't support tags simply ignore them - core genealogical data remains intact.

### Progressive Enhancement
As more systems adopt the extension, tag portability improves without breaking existing workflows.

## Future Considerations

The generic _ATTR mechanism allows the extension to evolve through vendor innovation rather than specification changes. Common patterns may emerge organically and could be standardized in future versions if needed.

## Comparison with Alternatives

### Why Not Extend NOTE?
- NOTE is for textual information, not categorization
- No visual component
- Doesn't match user mental models

### Why Not Use TYPE?
- TYPE is context-specific
- Can't create universal categorization
- No mechanism for colors or attributes

### Why Not Multiple Extensions?
- One extension for all tagging needs
- Simpler implementation
- Consistent across vendors

## Success Metrics

This extension succeeds when:
1. Users can move between software without losing tags
2. Vendors can innovate with tag features
3. Implementation remains simple
4. Tag data round-trips reliably