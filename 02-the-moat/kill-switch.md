# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Floot.com | H | 1. Export and secure the full GitHub repository. 2. Rebuild deployment pipeline outside Floot using other AI builder or self-hosted infrastructure. 3. Move all environment variables, secrets, and API keys into independent infrastructure management. 4. Ensure database and auth systems are decoupled from Floot-specific services. 5. Restore core Bookerful booking flows independently of Floot within 48 hours |
| **Abstraction** | Heavy reliance on Floot, with OpenAI and SDK integrations | H | 1. Abstract all AI calls behind a unified internal service layer. 2. Add multi-model support for: OpenAI, Anthropic, Google Gemini 3. Store prompts, tools, and workflow logic independently from provider APIs 4. Ensure critical AI flows can fail over between providers without major product rewrites |
| **Routing** | Depends on a narrow scope of external integrations for routing | H | 1. Ensure all critical customer relationship data is exportable and portable 2. Implement redundant communication channels including: calendar sync/export, SMS notifications, email notifications 3. Allow providers to maintain direct ownership of customer contact lists and communication history 4. Position internal community and messaging features as relationship-enhancing layers rather than isolated communication silos 5. Preserve the ability for providers to reach customers outside Bookerful if platform outages or routing disruptions occur |
| **Eval** | Limited formal structure for evaluating quality | M | 1. Create benchmark test suites for core workflows: booking, rescheduling, reminders, customer communication 2. Track: booking success rate, AI correction rate, customer satisfaction, no-show reduction 3. Build human-review workflows for failed or ambiguous AI interactions 4. Establish provider comparison testing to evaluate model quality across OpenAI, Anthropic, and Gemini |

## Portability Score
<!-- Ready / Partial / Locked -->

## If Floot doubles pricing tomorrow:
<!-- What's your 48-hour response? -->
That would not affect ability to continue relying on Floot as Bookerful's primary vendor, but would trigger a search for alternatives.

## If Floot ships a competing product:
<!-- What's defensible that they can't replicate? -->
If Floot launched a competing product, Bookerful’s defense would be to aggressively decouple its infrastructure while deepening its proprietary relationship intelligence, vertical-specific workflows, and community-driven customer experience — positioning Bookerful as a trusted business operating layer rather than a generic AI booking tool.
