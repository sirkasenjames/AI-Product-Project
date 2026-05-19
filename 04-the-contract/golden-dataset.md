# Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | “Book me for next Tuesday after 3 PM” | Correctly identifies next Tuesday + available slots after 3 PM | N | Rule |
| 2 | “Move my tattoo appointment to sometime after work next week” | Suggests evening availability next week without canceling existing booking prematurely | Y | LLM |
| 3 | “Cancel my appointment but keep my deposit on file” | Cancels appointment while preserving deposit status| Y | Rule |
| 4 | “I can’t do Fridays anymore because of school pickup” | Updates scheduling preferences without modifying unrelated appointments | Y | LLM |
| 5 | “Can you squeeze me in earlier if someone cancels?” | Adds user to cancellation waitlist without overwriting confirmed bookings | N | Rule |

**Adversarial rows included:** ambiguous time phrasing, conflicting availability, double-booking attempts, emotional/frustrated customer language, contradictory scheduling instructions

**Coverage gaps identified by partner:** timezone handling, multilingual scheduling, recurring appointment edge cases, partial reschedule + service modification requests

## Confidence UX Design

**Approach:** Show tiered confidence levels and escalate ambiguous scheduling or business-critical actions to confirmation or human review when confidence is low.

**High confidence (>90%): Automatically suggest and confirm scheduling actions, Execute routine booking/rescheduling workflows, Generate reminders and confirmations autonomously
**Medium confidence (70-90%):** Present recommended actions with confirmation step, Ask clarifying follow-up questions before finalizing workflow, Surface multiple possible interpretations
**Low confidence (<70%):** Avoid autonomous execution, Escalate to human/provider confirmation, Trigger clarification prompts or manual review workflows

**User control surface:** 
Users can: review proposed booking changes before confirmation, manually override AI recommendations, edit generated messages, disable autonomous scheduling actions, access appointment history and communication logs

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | >95% scheduling correctness |Successful booking/reschedule completion rate | <90% |
| Hallucination rate | <2% | Invalid or fabricated booking/action attempts | >5% |
| Latency (p95) | <5 seconds | AI response completion time | >8 seconds |
| Drift velocity | <10% workflow degradation per major model/provider update | Golden dataset regression testing | >15% |

## HITL Architecture
<!-- When does a human step in? What's the escalation path? -->
Human review is triggered for: ambiguous scheduling requests, payment/deposit disputes, conflicting calendar states, low-confidence AI actions, customer complaints, moderation or trust/safety concerns, failed workflow execution

Providers maintain final approval authority over business-critical actions and customer communication workflows.

## Red-Team Findings
*What failure mode did your partner find that you missed?*
Failure mode identified: The AI occasionally interprets conversational intent too aggressively and attempts to modify appointments before clarifying ambiguous customer language (e.g. “maybe move me to Friday” interpreted as a confirmed reschedule request).

Mitigation: Introduce confirmation checkpoints and confidence thresholds before executing calendar-modifying actions.
