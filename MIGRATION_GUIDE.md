# Migration Guide

## For Software Developers

### Basic Implementation

1. **Define Schema**
   ```gedcom
   1 SCHMA
   2 TAG _TAG https://gedcom.io/terms/v7/_TAG
   ```

2. **Import Tags**
   - Parse _TAG records into internal tag objects
   - Store NAME and _COLOR (if present)
   - Preserve all _ATTR entries for round-trip

3. **Apply Tags**
   - Process _TAG references on all record types
   - Map to internal tagging system
   - Maintain tag-record associations

4. **Export Tags**
   - Create _TAG records for all user tags
   - Convert internal colors to 6-digit hex
   - Include relevant _ATTR for your features

### Mapping Examples

#### GRAMPS
```python
# Import
if tag_color:  # GRAMPS uses 12-digit
    gramps_color = f"#{tag_color}0000"  # Extend to 12
    
# Export  
if gramps_tag.color:  # 12-digit to 6
    gedcom_color = gramps_tag.color[:7]  # Truncate
```

#### RootsMagic (Predefined Colors)
```sql
-- Map color index to hex
CASE color_index
  WHEN 1 THEN '#FF0000'  -- Red
  WHEN 2 THEN '#00FF00'  -- Green
  WHEN 3 THEN '#0000FF'  -- Blue
  -- etc.
END
```

### Advanced Features

#### Hierarchical Tags
```gedcom
0 @T1@ _TAG
1 NAME Research
0 @T2@ _TAG  
1 NAME ToDo
1 _ATTR parent_tag
2 _VALUE @T1@
```

#### Auto-application Rules
```gedcom
0 @T1@ _TAG
1 NAME DNA Match
1 _ATTR auto_apply_rule
2 _VALUE "confidence > 90 AND shared_cM > 20"
```

## For End Users

### Preparing for Export

1. **Review Your Tags**
   - Consolidate duplicate tags
   - Ensure tags have descriptive names
   - Assign colors for visual organization

2. **Check Software Support**
   - Verify your software supports the extension
   - Update to the latest version
   - Check export settings

3. **Test with Small Dataset**
   - Export a few tagged records
   - Import into target software
   - Verify tags transferred correctly

### After Import

1. **Verify Tag Transfer**
   - Check that all tags imported
   - Verify colors display correctly
   - Note any missing attributes

2. **Adjust for New Software**
   - Some features may differ
   - Colors might map differently
   - Hierarchies may need recreation

3. **Report Issues**
   - Contact software vendor
   - Provide example files
   - Describe expected behavior

## Common Scenarios

### Migrating from Non-Supporting Software

If your current software doesn't support the extension:
1. Document your tags manually
2. Export standard GEDCOM
3. Recreate tags in new software
4. Future exports will preserve them

### Merging Tagged Files

When combining files with tags:
1. Check for duplicate tag names
2. Reconcile color differences
3. Merge similar tags
4. Update record references

### Color Considerations

- Some software limits color choices
- Colors may display differently
- Consider colorblind-friendly palettes
- Use names, not just colors

## Troubleshooting

### Tags Not Appearing
- Check SCHMA declaration
- Verify _TAG record format
- Ensure references use @ symbols

### Colors Not Displaying
- Confirm 6-digit hex format
- Check for # prefix
- Verify no spaces in color value

### Attributes Missing
- Some vendors may not import all _ATTR
- Core NAME and _COLOR should always work
- Check vendor documentation

## Best Practices

1. **Use Descriptive Names**
   - "Immigration Research" not "Tag1"
   - Include purpose in name
   - Avoid special characters

2. **Document Your System**
   - Keep a list of tag meanings
   - Note color significance
   - Document any hierarchies

3. **Regular Backups**
   - Export with tags regularly
   - Test imports periodically
   - Keep versioned backups

4. **Vendor Communication**
   - Request feature support
   - Report bugs promptly
   - Share use cases