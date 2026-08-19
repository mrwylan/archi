# Use Case: Visualize Element Relationships

## Overview

**Use Case ID:** UC-011
**Use Case Name:** Visualize Element Relationships
**Primary Actor:** Modeler
**Goal:** Understand how a chosen element connects to the rest of the model by exploring its relationships as an interactive graph, without needing an existing view
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler selects an element and chooses to visualize its relationships as a graph.
2. System displays a graph centered on the selected element, showing the elements it is directly related to.
3. Modeler drills down into a connected element to expand the graph further from there.
4. System adds that element's connections to the graph.
5. Modeler navigates back up to a previous point in the exploration.

## Alternative Flows

### A1: Export the Graph as an Image

**Trigger:** Modeler chooses to export or copy the current graph (step 3)
**Flow:**

1. System renders the current graph and writes it to an image file, or copies it to the clipboard.
2. Use case ends.

## Postconditions

### Success Postconditions

- The graph reflects the current relationships of the explored elements
- Exploring the graph does not change the model

### Failure Postconditions

- No graph is displayed
- System reports an error to the actor
