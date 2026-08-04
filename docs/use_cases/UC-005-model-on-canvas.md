# Use Case: Model on a Free-Form Canvas

## Overview

**Use Case ID:** UC-005
**Use Case Name:** Model on a Free-Form Canvas
**Primary Actor:** Modeler
**Goal:** Sketch ideas freely using blocks, sticky notes, images, and connections that are not constrained by the ArchiMate relationship rules, useful for brainstorming before formalizing a view
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler creates a new canvas within a folder, optionally starting from a saved canvas template.
2. System creates the canvas and opens it for editing.
3. Modeler adds blocks, sticky notes, and images to the canvas.
4. Modeler adds free-form notes and hint text to a block to capture supporting information.
5. Modeler draws connections between shapes on the canvas.
6. Modeler arranges and styles the shapes and connections.
7. System saves the canvas content and layout together with the model.

## Alternative Flows

### A1: Save the Canvas as a Reusable Template

**Trigger:** Modeler chooses to save the current canvas as a template (step 7)
**Flow:**

1. Modeler names the template and chooses a template collection to save it in.
2. System stores the canvas layout as a reusable template.
3. Use case ends.

## Postconditions

### Success Postconditions

- The canvas, its shapes, connections, notes, and layout are saved with the model
- A canvas saved as a template is available for use as a starting point for future canvases

### Failure Postconditions

- The canvas is unchanged
- System reports an error to the actor

## Business Rules

### BR-013: Canvas Connections Are Unconstrained

Unlike connections on an ArchiMate view (BR-008), connections drawn on a canvas are not checked against the ArchiMate relationship validity rules and do not create ArchiMate relationship concepts in the model.
