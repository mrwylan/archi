# Use Case: Manage Model Extensions

## Overview

**Use Case ID:** UC-004
**Use Case Name:** Manage Model Extensions
**Primary Actor:** Modeler
**Goal:** Extend the standard ArchiMate notation with organization-specific custom profiles (stereotypes) and clean up the custom property keys used across the model
**Status:** Implemented

## Preconditions

- A model is open

## Main Success Scenario

1. Modeler opens the profiles manager for the model.
2. Modeler creates a new custom profile, choosing the concept type it specializes and giving it a name.
3. Modeler assigns a custom icon to the profile.
4. System saves the profile as part of the model.
5. Modeler applies the profile to one or more elements or relationships of the matching concept type.
6. System displays those concepts using the profile's custom icon and name.

## Alternative Flows

### A1: Delete a Profile

**Trigger:** Modeler deletes a custom profile (step 2 or later)
**Flow:**

1. System removes the profile from the model.
2. System reverts any concept that used the profile to the standard notation for its concept type.
3. Use case ends.

### A2: Manage Custom Property Keys

**Trigger:** Modeler opens the property keys manager instead of the profiles manager (step 1)
**Flow:**

1. System displays every distinct custom property key currently used anywhere in the model.
2. Modeler renames a key; system applies the new key to every property that used the old one.
3. Modeler deletes a key; system removes every property using that key throughout the model.
4. Use case ends.

## Postconditions

### Success Postconditions

- New or edited profiles are saved with the model and available for the Modeler to apply
- Concepts using a profile display its custom name and icon
- Property key renames and deletions are applied consistently across the whole model

### Failure Postconditions

- No profile or property key change is saved
- System reports an error to the actor

## Business Rules

### BR-011: Profile Name Uniqueness Per Concept Type

A profile's name must be unique among the profiles defined for the same concept type.

### BR-012: Deleting a Profile Reverts Its Concepts

Deleting a profile does not delete the elements or relationships that used it; they revert to the standard, unspecialized notation for their concept type.
