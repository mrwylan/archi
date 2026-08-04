# Use Case: Manage Model Structure

## Overview

**Use Case ID:** UC-002
**Use Case Name:** Manage Model Structure
**Primary Actor:** Modeler
**Goal:** Create, organize, describe, and remove the elements and folders that make up the model so the model tree reflects the intended architecture
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler selects a folder in the model tree and chooses to create a new element of a specific type.
2. System creates the element with a default name inside the selected folder.
3. Modeler renames the element.
4. Modeler selects the element and opens its details.
5. Modeler edits the element's documentation and custom properties.
6. System saves the changes to the element.
7. Modeler organizes the model tree by creating additional folders and moving elements and folders into them.
8. Modeler searches or filters the model tree to locate elements or relationships by name or type.

## Alternative Flows

### A1: Rename, Duplicate, Cut, Copy, or Paste

**Trigger:** Modeler selects one or more elements, relationships, or folders and chooses a structural editing action (step 7)
**Flow:**

1. Modeler chooses to rename, duplicate, cut, copy, or paste the selection.
2. System applies the change and updates the model tree.
3. Use case continues at step 7.

### A2: Explore an Element's Relationships

**Trigger:** Modeler chooses to explore the relationships of a selected element (step 4)
**Flow:**

1. System displays the elements connected to the selected element, grouped by incoming and outgoing relationships.
2. Modeler drills down into a connected element to continue exploring from there.
3. Use case continues at step 4.

### A3: Delete Elements, Relationships, or Folders

**Trigger:** Modeler chooses to delete a selection (step 7)
**Flow:**

1. System determines whether any selected item, or anything it contains, is displayed on a view.
2. If so, system warns the Modeler that the deletion will also remove those visual references.
3. Modeler confirms the deletion.
4. System removes the selected items, along with everything they cascade to per BR-004 and BR-006.
5. Use case continues at step 7.

### A4: Generate a View from Selected Elements

**Trigger:** Modeler chooses to generate a view from a set of selected elements (step 7)
**Flow:**

1. System creates a new view containing the selected elements and the relationships that connect them.
2. System opens the generated view.
3. Use case ends; continues in UC-003 Edit Architecture Diagram.

## Postconditions

### Success Postconditions

- The model tree reflects the created, renamed, moved, or deleted elements and folders
- Element documentation and custom properties are persisted with the element

### Failure Postconditions

- The model tree is unchanged
- System reports an error to the actor

## Business Rules

### BR-003: Relationships Are Not Created Directly

A new relationship concept is never created directly in the model tree; it comes into existence only when the Modeler draws a connection between two elements on a view (see UC-003 Edit Architecture Diagram).

### BR-004: Deleting an Element Cascades to Its Relationships

Deleting an element also deletes every relationship connected to it, and this cascades recursively to any relationship connected to one of those relationships.

### BR-005: Deleting a Folder Cascades to Its Contents

Deleting a folder deletes all elements, relationships, views, and subfolders it contains, following BR-004 for any contained elements.

### BR-006: Deletion Removes Visual References

Deleting an element, relationship, or view also removes every visual reference to it from any view that displays it. Deleting a view also removes any shape elsewhere that references that view.

### BR-007: Standard Folders Cannot Be Deleted

Only folders created by the Modeler can be deleted; the standard top-level folders (Strategy, Business, Application, Technology, Motivation, Implementation & Migration, Other, Relations, Views) cannot be removed.
