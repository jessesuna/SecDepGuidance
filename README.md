# Security Deployment Guidance Tool

This tool provides deployment guidance for Microsoft's security products and helps track implementation progress.

## Content Structure

### Recommendations Format
Each security component in `recommendations.md` follows this structure:
```markdown
### Component Name {#ComponentID}
**Why it's important:**
- Key benefit 1
- Key benefit 2
- Additional benefits...

**Implementation Steps:**
1. Major Step One
   - Sub-step detail
   - Sub-step detail
   ...
2. Major Step Two
   ...

**Learn More:**
- [Documentation Link](url)
- [Additional Resources](url)
```

### Assessment Questions
Questions are defined in `questions.json`:
```json
{
    "questions": [
        {
            "id": "ComponentID",  // Matches the ID in recommendations.md
            "text": "Question text?",
            "description": "Additional context for the question",
            "docLink": "https://learn.microsoft.com/...",
            "children": ["ChildID1", "ChildID2"]  // Optional: IDs of dependent components
        }
    ]
}
```

#### Parent-Child Relationships
- Use the `children` property to define dependencies between components
- Only define relationships on the parent question
- Child questions will be automatically hidden when parent is marked as "Yes"
- Example relationships:
  ```json
  {
      "id": "CA",  // Conditional Access
      "children": ["MFA", "CloudID"]  // CA depends on MFA and Cloud Identity
  },
  {
      "id": "XDR",  // Extended Detection and Response
      "children": ["DID", "MDO", "MDCA", "MDE", "MDVM"]  // XDR includes multiple Defender products
  }
  ```

### Features
- **Implementation Steps Toggle:** Show/hide detailed implementation steps
- **PDF Export:** Generate a formatted PDF including:
  - Current deployment status
  - Mermaid diagram visualization
  - Prioritized recommendations
  - Clickable documentation links
- **Deployment Visualization:** Interactive diagram showing:
  - Deployed components (green)
  - Pending components (pink)
  - Component relationships

### File Organization
- `index.html`: Main application and UI logic
- `questions.json`: Assessment questions and component relationships
- `recommendations.md`: Component documentation and implementation steps
- `DetailedDiagram.md`: Full deployment visualization
- `SimplifiedDiagram.md`: Condensed deployment visualization

## Making Updates

### Adding a New Component
1. Add component documentation to `recommendations.md`
2. Add assessment question to `questions.json`
3. Update parent-child relationships if needed
4. Update Mermaid diagrams in both `DetailedDiagram.md` and `SimplifiedDiagram.md`
5. Add component to appropriate deployment phase

### Updating Existing Content
1. Locate the component in `recommendations.md`
2. Update documentation while maintaining the established format
3. Update corresponding question in `questions.json`
4. Update parent-child relationships if dependencies change
5. Update diagram relationships if component dependencies change

### Best Practices
- Maintain consistent component IDs across all files
- Define relationships only on parent components
- Keep implementation steps clear and actionable
- Verify all documentation links
- Test parent-child behavior after making relationship changes
- Test PDF export after making changes
- Update both detailed and simplified diagrams

## Development Notes
- The tool uses vanilla JavaScript for better maintainability
- Mermaid.js for diagram rendering
- jsPDF for PDF generation
- Marked for Markdown parsing

## Future Improvements
1. Add search functionality
2. Implement content versioning
3. Add print stylesheet
4. Improve PDF formatting
5. Add unit tests
6. Add TypeScript support
7. Implement proper build process
8. Add linting and code formatting
