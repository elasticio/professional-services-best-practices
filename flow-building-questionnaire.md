# Table of Contents

* **General Information**
  * Description
  * Communication Methods
  * Deadlines
* **Systems to Integrate**
  * Description
  * Direction
  * Documentation
  * Test Access
* **Integration Flows**
  * Objects
  * Schema
  * Mapping
  * Process
  * Flow Initialization
  * Expected Load

<br>

# General Information

## Description
Please describe the primary purpose of this integration.

---

...

---

## Communication Methods
What is the most effective way for you to communicate with us during flow development (Email, Slack, etc.)?

---

...

---

## Deadlines
If there are any deadlines, please specify them here for each phase of the integration:

---

* Development:
* Testing:
* Staging:
* Production:

---

# Systems to Integrate

## Description
Which systems are you planning to integrate?

---

*

---

## Direction
Should the integration be one-directional (System A -> System B), or will it be bidirectional (System A <-> System B)?

---

...

---

## Documentation
If you have online links to technical documentation, please list them below or attach them to your response.

---

*

---

## Test Access
In most cases, we will require test access to the systems you intend to integrate. If acceptable, please provide credentials and authentication methods here, or indicate your preferred method for sharing this information.

---

...

---

# Integration Flows

## Objects
How many and which specific objects are you planning to integrate?

---

*

---

## Schema
If the provided documentation does not include the object schema, it would be helpful if you could provide it here (or as an attachment).

---

*

---

## Mapping
To facilitate integration, we will need the mapping. Please fill in this [file](https://docs.google.com/spreadsheets/d/1j20lLokIcplK0YsUE5KYIwwno0km26947tCuXVw1qng/edit?usp=sharing) and attach it to your response.

In the file, you will find the following fields:
 * **Object name** - Name of the object
 * **System A field UI name** - Name of the object field as found in the user interface of the source system
 * **System A field API name** - Name of the object field that will be received from the API of the source system
 * **System A field type** - Type of the field from the source system (e.g., number, string, boolean...)
 * **System B field UI name** - Name of the object field as found in the user interface of the destination system
 * **System B field API name** - Name of the object field that will be received from the API of the destination system
 * **System B field type** - Type of the field from the destination system (e.g., number, string, boolean...)
 * **Hardcoded value** - If the destination system requires any fields that are not present in the source system but can be hardcoded, please enter the value here.
 * **Notes** - Here you can provide additional details, such as:
   * If `System A` value equals `X`, then in `System B` we should input `Y`.
   * `System B` has a limit of 16 characters for this field—values from `System A` should be truncated accordingly.
   * The value in `System B` is a concatenation of fields X and Y from `System A`.

## Process
Describe the step-by-step process of the integration for each object.

The first step usually determines the initialization of the flow:
 * Based on a timer - collect new records every 10 minutes
 * Based on webhooks - the third-party system initiates a request to start the process

---
Object A

*
Object B

*
...

---
