# Cost Curve & Pricing Strategy

## Packaging Strategy

| Feature | Description | 
|----------|-----------------|
| Leader Feature | AI-Powered Appointment Booking & Rescheduling |
| Filler Feature | In-App Messaging + Community Space |
| Killer Feature | AI Client Retention & Business Growth Intelligence (Ex. Your balayage clients who don’t rebook within 9 weeks have a 63% churn rate. Recommend sending a soft-touch rebooking message Friday at 3 PM with summer transformation inspiration." |

| Killer Usage % | Bundle or Add-On | 
|----------|-----------------|
| Target: 40%+ | Bundle & Add-On |

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $2-8 | Primary AI costs come from conversational booking, scheduling assistance, AI-generated messaging, retention recommendations, and business insights. Costs scale based on message volume, workflow complexity, and model provider selection (e.g. GPT-4-class vs cheaper lightweight models). Most scheduling interactions are relatively short-context and operationally lightweight compared to coding or research agents.|
| Inference (cascading/triage) | $00.25-2 | Smaller or cheaper models can handle lightweight tasks such as intent classification, routing, reminder generation, spam detection, FAQ handling, and simple conversational responses before escalating to more expensive frontier models. Cascading helps control inference costs while maintaining responsiveness.|
| Infrastructure | $1-5 | Infrastructure includes app hosting, APIs, authentication, real-time messaging, notification systems, deployment services, monitoring, and backend compute. Costs are expected to remain moderate due to the lightweight operational nature of appointment scheduling and messaging workflows.|
| Data/storage | $0.10-1 | Storage costs include customer profiles, appointment history, messaging data, AI conversation history, business analytics, and community interactions. Costs are relatively low early on but may increase as long-term messaging history, uploads, and relationship intelligence accumulate.|
| Human-in-the-loop | $0-3 | Most Bookerful workflows are intended to operate autonomously, but human review may occasionally be required for customer support, failed scheduling edge cases, moderation, trust & safety, or AI quality assurance. Costs may increase if concierge onboarding or white-glove support becomes part of the business model.|
| **Total AI COGS** | $3-6 | Total AI costs include primary conversational scheduling workflows, lightweight routing/triage models, AI-generated messaging, retention recommendations, customer intelligence features, and business growth insights. Costs are expected to remain relatively manageable compared to more inference-heavy AI products because most Bookerful interactions involve short-context operational tasks rather than long-form reasoning or multimodal generation. Long-term margin improvements are expected through model cascading, prompt optimization, caching, selective inference routing, and limiting expensive frontier-model usage to high-value workflows.|

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:** OpenAI GPT-4.1 Mini / GPT-5 Nano
**Frontier model:** OpenAI GPT-5
**Routing rule:** Default all requests to lightweight triage models first. Escalate to frontier models only when interactions require higher reasoning complexity, emotional nuance, multi-step workflow generation, customer retention intelligence, ambiguous scheduling interpretation, or business-critical decision support. Routine booking, reminders, confirmations, and structured operational tasks remain on low-cost models whenever possible.
**Expected cascade ratio:** ~70–90% lightweight triage models, ~10–30% frontier models

## Pricing Model

**Current pricing:** Bookerful is currently in dev, so no defiinitive pricing at the moment.
**Proposed AI pricing:** Starter: $19–39/month, Premium $79–149/month
**Model:** Hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Gross margins compress meaningfully, especially on highly engaged power users and AI-heavy workflows. However, Bookerful’s relatively lightweight operational AI tasks and hybrid pricing structure help limit existential risk compared to more inference-intensive AI businesses. | 1. Increase use of lightweight triage models and cascading workflows. 2. Reduce unnecessary frontier-model usage. 3. Introduce AI usage limits or premium AI tiers for high-volume users. 4. Optimize prompts, caching, and workflow efficiency. 5. Prioritize monetizing high-value. 6. AI growth features over low-value conversational volume. 7. Continue shifting differentiation toward proprietary relationship intelligence and workflow depth rather than raw inference consumption|
| Heaviest segment doubles | Power-user infrastructure and inference costs increase disproportionately, potentially compressing margins if pricing remains flat across all usage tiers. However, increased engagement may also correlate with higher customer value, retention, and expansion revenue opportunities.| 1. Implement tiered AI usage thresholds and scalable pricing. 2. Introduce premium automation and concierge add-ons for high-volume users. 3. Improve workload routing efficiency for repetitive operational tasks. 4. Monitor cost-to-value ratios by customer segment. 5. Align advanced AI automation features with higher-priced plans to ensure margins scale alongside usage | 
Model provider raises prices 50% | AI operating margins compress, particularly if Bookerful is heavily dependent on a single frontier-model provider. Businesses relying on fixed-price plans without usage controls would experience the greatest pressure. | 1. Maintain multi-model provider support across OpenAI, Anthropic, and Gemini ecosystems. 2. Increase routing toward lower-cost models for operational workflows. 3. Re-negotiate pricing structures or migrate selective workloads to more efficient providers. 4. Adjust premium AI pricing tiers if necessary. 5. Continue reducing dependence on expensive frontier models for routine scheduling and messaging tasks|

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):** Bookerful functions primarily as a scheduling, messaging, and business management platform for service-based solopreneurs. Revenue potential is driven largely by subscription access to operational tooling, resulting in moderate pricing power, lower differentiation, and margin pressure from competing calendar and business management platforms.

**After (AI-enabled):** By embedding AI natively into scheduling, customer communication, retention workflows, and business growth intelligence before launch, Bookerful evolves from operational software into an intelligent business operating layer. AI-driven automation, retention optimization, and relationship intelligence increase customer dependence, expansion revenue opportunities, and willingness-to-pay while enabling scalable service delivery without proportional increases in human operational costs.

**Net margin shift:** While AI introduces additional inference and infrastructure costs, Bookerful expects the long-term margin profile to improve through higher-value subscription tiers, expansion revenue from AI-powered workflows, stronger customer retention, and operational leverage created by automation. The platform’s relatively lightweight AI workloads and hybrid pricing model help maintain favorable unit economics compared to more inference-intensive AI businesses.
