# Use Case: Generate Model Report

## Overview

**Use Case ID:** UC-008
**Use Case Name:** Generate Model Report
**Primary Actor:** Modeler
**Secondary Actor:** Automation Tool
**Goal:** Produce a shareable, human-readable report describing the model's elements, relationships, views, and properties
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler chooses to generate a report for the model.
2. Modeler chooses which parts of the model to include.
3. System previews the report.
4. Modeler confirms generation and chooses a destination.
5. System renders the report, including the model's structure, element and relationship details, and view images, and writes it to the destination.

## Alternative Flows

### A1: Generate from a Custom Report Template

**Trigger:** Modeler chooses to generate the report from a custom report template instead of the standard report (step 1)
**Flow:**

1. Modeler selects a report template and an output format.
2. System populates the template with data from the model.
3. System renders the populated template to the chosen output format and writes it to the destination.
4. Use case ends.

### A2: Automated Report Generation

**Trigger:** An Automation Tool triggers report generation instead of a Modeler (step 1)
**Flow:**

1. Automation Tool supplies the model, template choice, and destination non-interactively.
2. System generates the report without an interactive preview.
3. Use case ends.

## Postconditions

### Success Postconditions

- A report file is written to the destination, reflecting the model's state at the time of generation
- The model itself is unchanged by generating a report

### Failure Postconditions

- No report file is written, or a partial file is removed
- System reports an error to the actor

## Business Rules

### BR-015: Report Reflects a Point in Time

A generated report is a snapshot of the model at the moment of generation; it is not kept in sync with later changes to the model.
