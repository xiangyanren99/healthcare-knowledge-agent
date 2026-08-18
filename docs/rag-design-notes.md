# RAG Design Notes

## Retrieval vs. Generation

Retrieval failure occurs when the system provides the model with incorrect or insufficient evidence.

Generation failure occurs when appropriate evidence is retrieved but the model generates an incorrect or unsupported response.

## Grounding

The Northstar agent uses configured synthetic policy and training documents as its approved knowledge sources.

A citation does not guarantee that every statement in a response is grounded. Version 3 demonstrated this when the agent cited the Missed Visit Policy but incorrectly extended billing guidance to mileage reimbursement.

## Allow Ungrounded Responses Experiment

The setting was tested both on and off.

Turning it off did not prevent the reimbursement extrapolation and negatively affected clarification behavior.

The setting was therefore left enabled, while stricter grounding and ambiguity requirements were implemented in Version 4 and evaluated through regression tests.

## Version 4

Version 4 added:
- Explicit restrictions against extending rules to related concepts
- Clearer criteria for multi-step formatting
- Stronger ambiguity handling
- Additional few-shot examples

Version 4 passed all targeted regression tests and two unseen generalization tests.