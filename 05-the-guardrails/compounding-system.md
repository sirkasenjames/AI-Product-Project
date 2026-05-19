# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Booking behavior loop | Appointment history, preferred times, service frequency, cancellations | Better AI scheduling recommendations and rebooking prompts | Y | active |
| Client relationship loop | Messages, community posts, provider notes, client preferences | More personalized follow-ups, retention campaigns, and service suggestions | Y | active |
| Growth intelligence loop | Revenue trends, no-shows, repeat bookings, campaign performance | Smarter business insights, churn alerts, and upsell recommendations | Y | missing |

**Broken loop identified by partner:** Growth insights may not improve unless customer outcomes are tracked after AI recommendations.
**Fix plan:** Track whether AI suggestions lead to rebookings, retained clients, reduced no-shows, or increased revenue.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->
Bookerful is designed around a shared relationship graph where scheduling, messaging, customer behavior, marketing activity, and business intelligence continuously reinforce one another. Booking behavior informs retention workflows; messaging history informs customer sentiment and personalization; community participation informs loyalty and engagement scoring; and revenue/performance trends inform AI growth recommendations. Rather than isolating scheduling, communication, and business operations into separate systems, Bookerful connects them into a unified context layer that improves recommendations, automation quality, and customer relationship continuity over time.

## Governance Policy

**Scope:** AI-assisted booking, rescheduling, messaging, reminders, retention recommendations, and business growth insights.  
**Autonomy boundaries:** AI can suggest and draft; it should require confirmation before modifying appointments, sending sensitive messages, issuing refunds, or changing payment/deposit status.  
**Escalation triggers:** Low confidence, conflicting calendar data, angry customer language, payment disputes, cancellation/deposit issues, suspected abuse, or ambiguous scheduling intent.  
**Audit cadence:** Weekly during beta; monthly after launch.  
**Regulatory exposure (EU AI Act / other):** Low-to-moderate; mostly consumer communication, privacy, data portability, marketing consent, payments, and AI transparency.  

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->
Recommended topology: Orchestrator + specialist agents.

Booking Agent: handles appointment booking/rescheduling.  
Messaging Agent: drafts replies, reminders, and updates.  
Retention Agent: identifies churn risk and rebooking opportunities.  
Growth Agent: surfaces revenue, loyalty, and campaign insights.  
Safety/Escalation Agent: detects uncertainty, conflict, or risky actions.

The orchestrator routes tasks to the right agent and blocks high-risk actions until user/provider confirmation.

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| Floot | Product/build platform | H | govern |
| OpenAI | AI inference | M | govern |
| Supabase or Floot DB | Database / customer data | H | govern |

**Total tools found:** 3
**Tools after triage:** 3
**Estimated hidden spend:** Low during development; likely increases with AI usage, database growth, SMS/email volume, and hosting scale.
