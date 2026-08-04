# Use Case: Manage Model Templates

## Overview

**Use Case ID:** UC-009
**Use Case Name:** Manage Model Templates
**Primary Actor:** Modeler
**Goal:** Start new modelling work from a reusable starting point, and share a finished model as a starting point for others
**Status:** Implemented

## Preconditions

- None to browse and use templates
- A model is open to save it as a template

## Main Success Scenario

1. Modeler browses the gallery of available model templates, organized into collections.
2. Modeler selects a template.
3. System creates a new model pre-populated with the template's content.
4. System opens the new model as the active model.

## Alternative Flows

### A1: Save the Current Model as a Template

**Trigger:** Modeler chooses to save the current model as a template instead of starting from one (step 1)
**Flow:**

1. Modeler names the template and chooses which collection to save it into.
2. System stores a copy of the current model as a new template in that collection.
3. Use case ends.

## Postconditions

### Success Postconditions

- A new model is created from the chosen template and becomes the active model
- A model saved as a template becomes available in the gallery for future use

### Failure Postconditions

- No new model is created, or no template is saved
- System reports an error to the actor
