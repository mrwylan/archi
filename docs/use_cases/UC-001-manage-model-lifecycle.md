# Use Case: Manage Model Lifecycle

## Overview

**Use Case ID:** UC-001
**Use Case Name:** Manage Model Lifecycle
**Primary Actor:** Modeler
**Secondary Actor:** Automation Tool
**Goal:** Create, open, save, and close an architecture model so modelling work can begin, be preserved, and be resumed later
**Status:** Implemented

## Preconditions

- To open a model, a previously saved model is available
- To save or close a model, a model is currently open

## Main Success Scenario

1. Modeler chooses to start a new architecture model.
2. System creates an empty model containing the standard set of top-level folders for organizing content.
3. System opens the model and displays it as the active model.
4. Modeler makes changes to the model.
5. Modeler chooses to save the model.
6. System writes the current state of the model to persistent storage.
7. System marks the model as having no unsaved changes.

## Alternative Flows

### A1: Open an Existing Model

**Trigger:** Modeler chooses to open a previously saved model instead of creating a new one (step 1)
**Flow:**

1. Modeler selects an existing model, either from storage or from a list of recently used models.
2. System loads the model.
3. System opens the model and displays it as the active model.
4. Use case continues at step 4.

### A2: Save Location Not Yet Known

**Trigger:** The model has never been saved before (step 5)
**Flow:**

1. System prompts the Modeler to choose a name and location for the model.
2. Modeler provides the name and location.
3. Use case continues at step 6.

### A3: Save a Copy Under a New Name or Location

**Trigger:** Modeler chooses to save the model as a copy (step 5)
**Flow:**

1. Modeler provides a new name and/or location.
2. System writes the model to the new location as a separate model.
3. System makes the new copy the active model.
4. Use case ends.

### A4: Close Model

**Trigger:** Modeler chooses to close the active model (any step)
**Flow:**

1. System checks whether the model has unsaved changes.
2. If unsaved changes exist, system asks the Modeler to save, discard, or cancel.
3. System closes the model and removes it from the active workspace.
4. Use case ends.

### A5: Automated Creation, Load, or Save

**Trigger:** An Automation Tool triggers model creation, loading, or saving instead of a Modeler (step 1 or step 5)
**Flow:**

1. Automation Tool supplies the required parameters (e.g. a source model and a destination path) non-interactively.
2. System performs the requested creation, load, or save operation without an interactive workspace.
3. Use case ends.

## Postconditions

### Success Postconditions

- The model exists in memory and is available for further modelling work
- Once saved, the model is durably stored and can be reopened later
- The unsaved-changes indicator is cleared immediately after a save

### Failure Postconditions

- The model file on storage remains unmodified
- System reports an error to the actor

## Business Rules

### BR-001: Standard Folder Structure

A newly created model is pre-populated with one top-level folder per standard category: Strategy, Business, Application, Technology, Motivation, Implementation & Migration, Other, Relations, and Views.

### BR-002: Unsaved Changes Must Be Confirmed

A model with unsaved changes must not be closed without the actor being given the choice to save, discard, or cancel the close.
