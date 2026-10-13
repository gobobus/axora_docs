---
icon: building-shield
---

# Policies and Workflows

Router applies group policies at two checkpoints: before a request leaves the gateway for a model, and before a model response is returned to the requester.

## Request and response lifecycle

{% stepper %}
{% step %}
## Submit a request

An employee, application, or agent submits a request to Router.
{% endstep %}

{% step %}
## Evaluate the outbound policy

The outbound checkpoint evaluates the group's policy and handles the request, including transformation where configured.
{% endstep %}

{% step %}
## Send the processed request

Router sends the processed request to the selected model.
{% endstep %}

{% step %}
## Receive the model response

The referencing model returns a response.
{% endstep %}

{% step %}
## Evaluate the inbound policy

The inbound checkpoint evaluates and handles the response, including restoring previously replaced content where applicable.
{% endstep %}

{% step %}
## Return and record the result

Axora Router returns the result and records the processing trace.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The workflows above explain the product's documented behavior. This sequence describes the gateway's control point. It does not mean that traffic bypassing Router is inspected.
{% endhint %}

## Policy actions

| Action               | Meaning                                                                  |
| -------------------- | ------------------------------------------------------------------------ |
| **Allow**            | Pass the request or response.                                            |
| **Observe**          | Pass it while recording evidence and alerts.                             |
| **Tokenize**         | Replace identified sensitive values with placeholders before forwarding. |
| **Block**            | Reject the request or response.                                          |
| **Route**            | Use an enterprise-approved internal model instead of an external one.    |
| **Require Approval** | Pause processing and enter an approval workflow.                         |

Rules apply according to the group's policy and the processing stage. They can consider text, organizational dictionaries, content type, the target model, and region. Local-model analysis can support tasks such as identifying named entities.

## Tokenization and restoration

Here, **tokenization** means replacing sensitive values with placeholders. It does not mean counting a language model's input or output tokens.

In the documented workflow, Router keeps the mapping between an identified value and its placeholder at the gateway. The external model receives the transformed content, and the inbound checkpoint can restore the values when returning the result.

This mechanism applies to values identified and transformed by the active policy. It is not a guarantee that every sensitive detail in an arbitrary document will be detected. Other text and context still need to be assessed against the organization's data-handling rules.

## Example: contract review

An employee submits a contract containing a name and identity-document number. The group's policy identifies those fields and replaces them with placeholders before forwarding the request.

The model reviews the transformed contract and returns its response with the placeholders preserved. Router uses the gateway-side mapping to restore the identified values in the response returned to the employee.

The administrator can inspect the trace across processing stages. In this example, the original values that were replaced are not sent to the external model.

## Example: role-based AI access in a law firm

A law firm may organize employees by role or project sensitivity. Each group can have its own channels, quotas, and handling rules.

| Example group                | Example channel access           | Example policy                                                                            |
| ---------------------------- | -------------------------------- | ----------------------------------------------------------------------------------------- |
| Partners and senior lawyers  | Multiple approved model channels | Replace client names, matter numbers, and project identifiers; observe remaining traffic. |
| Lawyers and legal assistants | A subset of approved channels    | Replace personal identifiers and account information; block highly sensitive content.     |
| Interns                      | A restricted channel             | Apply stricter rules and a smaller quota.                                                 |
| Sensitive-project team       | An approved internal model       | Route client-confidential material internally.                                            |

An organization can use its own client-name dictionaries, project codes, and identifier formats alongside personal-data detection.

{% hint style="info" %}
These are policy examples, not default role templates or a claim of a deployed law-firm customer.
{% endhint %}

## Audit and policy refinement

The audit view provides filtering by time, user, model, and decision status. A trace shows key inputs and outputs so administrators can understand how content was handled.

A team can start by observing a selected workflow, review actual traffic and policy matches, and then introduce more restrictive handling where appropriate. Auditable traces should be treated as potentially sensitive data and managed under the organization's access and retention practices.

For the difference between gateway controls, agent action protection, and adversarial testing, see [..](../ "mention").
