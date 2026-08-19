# Use Case: Export Model Data

## Overview

**Use Case ID:** UC-007
**Use Case Name:** Export Model Data
**Primary Actor:** Modeler
**Secondary Actor:** Automation Tool
**Goal:** Publish the model, or a view within it, to a format another tool or audience can consume
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler chooses to export the model to a spreadsheet (CSV).
2. Modeler chooses a destination and which content to include.
3. System writes the elements, relationships, folders, and properties to CSV files at the chosen destination.

## Alternative Flows

### A1: Export to a Standard Interchange Format

**Trigger:** Modeler chooses to export to the Open Exchange Format instead of CSV (step 1)
**Flow:**

1. Modeler chooses a destination file.
2. System writes the model to the destination in the standard interchange format so it can be opened by another ArchiMate-compliant tool.
3. Use case ends.

### A2: Export a View as an Image

**Trigger:** Modeler chooses to export a single view instead of the whole model (step 1)
**Flow:**

1. Modeler selects the view and an output format (raster image, SVG, or PDF).
2. Modeler chooses a destination.
3. System renders the view and writes it to the destination in the chosen format.
4. Use case ends.

### A3: Automated Export

**Trigger:** An Automation Tool triggers the export instead of a Modeler (step 1)
**Flow:**

1. Automation Tool supplies the model, the export format, and the destination non-interactively.
2. System performs the export and reports the outcome without an interactive destination prompt.
3. Use case ends.

## Postconditions

### Success Postconditions

- The chosen content is written to the destination in the requested format
- The model itself is unchanged by exporting

### Failure Postconditions

- No output file is written, or a partial output file is removed
- System reports an error to the actor
