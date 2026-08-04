# Use Case: Edit Architecture Diagram

## Overview

**Use Case ID:** UC-003
**Use Case Name:** Edit Architecture Diagram
**Primary Actor:** Modeler
**Goal:** Visually compose a view that shows a chosen set of elements and the relationships between them, so the architecture can be communicated and understood
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler creates a new view within a folder.
2. System creates an empty view and opens it for editing.
3. Modeler places an element on the view, either by dragging it from the model tree or by drawing a new one from a palette of concept types.
4. System adds a shape representing the element to the view, creating the underlying element first if it did not already exist in the model.
5. Modeler draws a connection between two shapes on the view, choosing the type of relationship to create.
6. System validates that the chosen relationship type is permitted between the two concept types, creates the relationship in the model, and displays it as a connection on the view.
7. Modeler arranges, resizes, and styles the shapes and connections on the view.
8. System saves the appearance and layout together with the view.

## Alternative Flows

### A1: Relationship Type Not Permitted

**Trigger:** The chosen relationship type is not valid between the two selected concept types (step 6)
**Flow:**

1. System rejects the connection and informs the Modeler which relationship types are permitted between the two concepts.
2. Use case continues at step 5 or ends.

### A2: Restrict the View to a Viewpoint

**Trigger:** Modeler applies a viewpoint to the view (any step)
**Flow:**

1. Modeler selects a named viewpoint.
2. System restricts which element and relationship types can be added to the view to those permitted by the viewpoint, and visually de-emphasizes any existing content that falls outside it.
3. Use case continues at step 3.

### A3: Reuse an Existing Relationship

**Trigger:** A relationship of the chosen type already exists in the model between the two underlying concepts (step 6)
**Flow:**

1. System adds the existing relationship as a connection on the view instead of creating a duplicate relationship.
2. Use case continues at step 7.

### A4: Remove a Shape from the View Only

**Trigger:** Modeler removes a shape or connection from the view without deleting the underlying concept (step 7)
**Flow:**

1. System removes the visual shape or connection from the view.
2. System leaves the underlying element or relationship in the model, still accessible from the model tree and any other view.
3. Use case continues at step 7.

### A5: Export the View as an Image

**Trigger:** Modeler chooses to export the current view (step 7)
**Flow:**

1. Use case continues in UC-007 Export Model Data (Export a View as an Image).

## Postconditions

### Success Postconditions

- The view, its shapes, its connections, and their layout and styling are saved with the model
- Any new elements or relationships created while editing the view also appear in the model tree

### Failure Postconditions

- The view is unchanged
- System reports an error to the actor, explaining why a connection could not be created

## Business Rules

### BR-008: Relationship Validity Matrix

The system only permits a relationship type to be drawn between two concept types if that combination is allowed by the ArchiMate specification's relationship validity rules; every source/target concept type pair has its own fixed set of permitted relationship types.

### BR-009: One Relationship Instance Per Concept Pair and Type

Drawing a connection between two concepts that are already connected by a relationship of the same type reuses the existing relationship rather than creating a duplicate.

### BR-010: Viewpoints Restrict, Not Delete

Applying a viewpoint to a view only restricts which types can be freely added and how existing out-of-scope content is displayed; it never deletes model content.
