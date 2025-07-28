# Glossary

## Tag
A user-defined organizational marker that can be applied to genealogical records for categorization, visual identification, or workflow management.

## Tag Record (_TAG)
A top-level GEDCOM record that defines a reusable tag with a name, optional color, and vendor-specific attributes.

## Tag Reference
A substructure that applies a tag to a record by referencing a tag record's identifier.

## Color Value
A 6-digit hexadecimal color specification in the format #RRGGBB, where RR represents red, GG represents green, and BB represents blue values from 00 to FF.

## Generic Attribute (_ATTR)
A mechanism for vendors to add custom properties to tags without modifying the base specification.

## Round-trip Preservation
The requirement that systems maintain all tag data during import and export, even if they don't display or use certain attributes.

## Graceful Degradation
The principle that systems not supporting tags can still process GEDCOM files containing tag data without errors or data loss.

## Vendor-specific Attributes
Custom properties added by software vendors through the _ATTR mechanism to extend tag functionality for their specific features.

## Tag Application
The act of associating a tag with a genealogical record, optionally including contextual information like date and notes.

## Hierarchical Tags
A vendor-specific feature where tags can have parent-child relationships, implemented through _ATTR rather than the base specification.

## Tag Inheritance
A vendor-specific feature where tags might be automatically applied based on relationships or rules, not part of the base specification.

## Visual Categorization
The use of colors to provide immediate visual distinction between different types of records or research states.

## Tag Portability
The ability to maintain tag information when transferring genealogical data between different software platforms.