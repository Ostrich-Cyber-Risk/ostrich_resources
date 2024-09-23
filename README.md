# Guide to Creating Your Own Assessment Content

To create a custom assessment content file, follow this structured layout to ensure compatibility with the Ostrich Assess platform. Below is a breakdown of the general structure, which can serve as a template for creating your own assessment.

## General Structure

```json
{
  "descriptor": {
    "assessment-key": "UNIQUE_KEY",
    "title": "ASSESSMENT_TITLE",
    "ostrich-version": "A",
    "item-label": "ITEM_LABEL"
  },
  "outline": {
    "FUNCTION_ID": {
      "CATEGORY_ID": {
        "SUBCATEGORY_ID": {},
        "question-count": "COUNT_IN_CATEGORY"
      },
      // Additional CATEGORIES go here
      "question-count": "TOTAL_COUNT_IN_FUNCTION"
    },
    // Additional FUNCTIONS go here
    "question-count": "TOTAL_COUNT"
  },
  "nodes": {
    "FUNCTION_ID": {
      "name": "FUNCTION_NAME",
      "text": "FUNCTION_DESCRIPTION"
    },
    "CATEGORY_ID": {
      "name": "CATEGORY_NAME",
      "text": "CATEGORY_DESCRIPTION>"
    },
    "SUBCATEGORY_ID": {
      "text": "SUBCATEGORY_DESCRIPTION",
      "maturity": [{
        "text": "MATURITY_TEXT",
        "value": "VALUE_0_TO_100"
      }],
      "process": [{
        "text": "PROCESS_TEXT",
        "value": "VALUE_0_TO_100"
      }],
      "coverage": "COVERAGE_TEXT",
      "references": [{
        "ref": "REFERENCE_TEXT"
      }],
      "guidance": "SUBCATEGORY_GUIDANCE",
      "examples": [{
        "ex": "EXAMPLE_TEXT"
      }]
    }
    // Additional nodes for subcategories, categories, and functions.
  }
}
```

### Descriptor Block

- **assessment-key**: A unique identifier for the assessment.
- **title**: The title of the assessment, to be displayed in-app.
- **ostrich-version**: Should be "A"
- **item-label**: A name displayed in the client for items within the assessment (e.g., "control", "question").

### Outline Block

This section gives the overall structure of the assessment.

- **Function, Category, and Subcategory IDs**: These are strings that serve as identifies for assessment questions grouped by topic. Each ID identifies an entry in the "nodes" list, below.
    - CATEGORY_ID
      must start with
      FUNCTION_ID,
      and
      SUBCATEGORY_ID
      must start with
      CATEGORY_ID.
      (e.g. Function: "FN", Category: "FN.CA", Subcategory: "FN.CA-1")
- **question-count**: The total number of subcategories within a section of the outline.

### Nodes Block

This section contains detailed information about each item:

- **name**: The formal name of the function, category, or subcategory.
- **text**: A description or the actual text of the item.
- **maturity**: (For subcategories) An array of objects detailing the maturity levels and values.
- **process**: (For subcategories) An array of objects detailing the process text and values.
- **coverage**: (Optional) Additional information about the scope of the item, to be shown above a 0-100 slider.
- **references**: (Optional) A list of references related to the question.
- **guidance**: Additional guidance or explanation.
- **examples**: Illustrative examples to clarify the subcategory or guidance.
