# Use Case: Import Model Data

## Overview

**Use Case ID:** UC-006
**Use Case Name:** Import Model Data
**Primary Actor:** Modeler
**Secondary Actor:** Automation Tool
**Goal:** Bring content from an external source — another architecture model, a spreadsheet, or a standard interchange file — into the currently open model
**Status:** Implemented

## Preconditions

- A model is open
- The source file to import exists and is readable

## Main Success Scenario

1. Modeler chooses to import another architecture model into the currently open model.
2. Modeler selects the source model file.
3. System compares every element, relationship, folder, view, and profile in the source model against the currently open model.
4. System previews which items are new and which already exist.
5. Modeler confirms the import.
6. System adds the new items to the currently open model and updates the existing ones that matched.

## Alternative Flows

### A1: Import from a Spreadsheet (CSV)

**Trigger:** Modeler chooses to import from CSV files instead of another model (step 1)
**Flow:**

1. Modeler selects CSV files describing elements, relationships, and properties.
2. System validates that the files are well-formed and reports any rows it cannot parse.
3. System creates or updates the corresponding elements, relationships, and properties in the currently open model.
4. Use case ends.

### A2: Import from a Standard Interchange File

**Trigger:** Modeler chooses to import an Open Exchange Format file instead of another model (step 1)
**Flow:**

1. Modeler selects the interchange file.
2. System validates the file against the interchange format's schema and reports any errors.
3. System creates the model content it describes as a new model, or merges it into the currently open model.
4. Use case ends.

### A3: Automated Import

**Trigger:** An Automation Tool triggers the import instead of a Modeler (step 1)
**Flow:**

1. Automation Tool supplies the source file and target model path non-interactively.
2. System performs the import and reports the outcome without an interactive preview.
3. Use case ends.

### A4: Source File Cannot Be Parsed

**Trigger:** The source file is not in the expected format (step 2 or 3)
**Flow:**

1. System reports which parts of the file could not be understood.
2. Use case ends; no content is imported.

## Postconditions

### Success Postconditions

- New items from the source are added to the model
- Items that already existed in the model are updated to match the source
- Nothing outside the imported scope is changed

### Failure Postconditions

- The currently open model is unchanged
- System reports which part of the import failed

## Business Rules

### BR-014: Objects Are Matched, Not Duplicated

When importing another model, an object already present in the target model is recognized by its identifier (or, for a profile, by its name together with the concept type it specializes) and is updated in place; only objects with no match are added as new.
