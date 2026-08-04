# Use Case: Validate Model

## Overview

**Use Case ID:** UC-010
**Use Case Name:** Validate Model
**Primary Actor:** Modeler
**Goal:** Find modelling issues — errors, warnings, and points worth reviewing — so the model can be cleaned up before it is relied on
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler chooses to validate the model.
2. System checks the model against the full set of validation checks and collects every issue found.
3. System groups the issues into Errors, Warnings, and Advice, and displays them together with an explanation of each.
4. Modeler selects an issue.
5. System navigates to the affected element, relationship, or view.
6. Modeler corrects the underlying model to resolve the issue.

## Alternative Flows

### A1: No Issues Found

**Trigger:** No validation check reports an issue (step 3)
**Flow:**

1. System reports that the model has no known issues.
2. Use case ends.

## Postconditions

### Success Postconditions

- Every issue detected by a validation check is presented to the Modeler with an explanation
- The Modeler can navigate from an issue directly to the affected model content

### Failure Postconditions

- No validation results are displayed
- System reports an error to the actor

## Business Rules

### BR-016: Possible Duplicate Element

The system flags a warning when the same name is used more than once for elements of the same type, since duplicate names may indicate an accidental duplicate element (duplicate names are permitted, not blocked).

### BR-017: Empty View

The system flags a warning when a view contains no elements or relationships.

### BR-018: Invalid Relationship

The system flags an error when a relationship on a view is of a type not allowed between its two connected concept types, per BR-008.

### BR-019: Inconsistent Junction

The system flags a warning when a junction's incoming and outgoing relationships are not all of the same type.

### BR-020: Nesting Without a Semantic Relationship

The system flags an issue when one element is displayed visually nested inside another on a view, but the two elements have no relationship of a type that supports nesting (Composition, Aggregation, Assignment, Access, Realization, or Specialization).

### BR-021: Unused Element or Relationship

The system flags a warning when an element or relationship exists in the model but does not appear on any view.

### BR-022: Concept Outside Its Viewpoint

The system flags an issue when a view restricted to a viewpoint (BR-010) contains an element or relationship type that the viewpoint does not permit.
