Individual Work Report – AI-Assisted Specification & Strategic Architecture
Student Details
Name: Avinoam
Part in project: Co-Authoring PRD, Technical Specifications & Strategic Architecture

1. My Part in the Work
Due to my ongoing service as a combat fighter in the reserves (Miluim) throughout the semester, my contribution was heavily weighted towards high-leverage upfront definition and strategic architecture.

To ensure the project could succeed despite our resource constraints, I collaborated closely with Roee on the initial product definition before my deployment. We split the leadership responsibilities to cover both product and engineering needs:

PRD Co-Authoring & Technical Specification: While Roee focused on the high-level product vision and the File Management scope, I took ownership of the System Specifications. I translated the product goals into a rigorous "Source of Truth" using normative technical language (MUST/SHALL). This work defined the critical system behaviors—specifically Auth Gating, Neutral Page Routing, and Onboarding Logic—providing the strict constraints the team worked against in my absence.

Execution Strategy ("The Attack Plan"): I mapped out the architectural strategy to decouple our work streams. Realizing we were all resource-constrained, I designed the separation of concerns between the UI Components (assigned to Idan/Roee) and the Guard Logic/Auth (assigned to Tamar), ensuring parallel development could happen without merge conflicts.

Scope Containment: Acting as the "Technical Gatekeeper," I defined the "Non-Goals" and Operational Constraints (e.g., Emulator support). I rigorously pruned complex features (like detailed RBAC) to ensure the team remained focused on a deliverable MVP.

Personal note: The severe lack of human resources in my unit meant I was disconnected for weeks at a time. My strategy was to front-load the "Thinking" phase—partnering with Roee to define the product, then pivoting to architect the technical constraints and pick-up work to help with whenever possible as i get breaks now and then from the military.

2. LLM Usage During the Work
I utilized LLMs as a "force multiplier" to condense the architectural definition phase from weeks into days.

Key Uses:

Drafting the Technical Specifications: I fed the LLM the high-level concepts Roee and I discussed, prompting it to convert them into formal RFC-style specifications. This ensured that "fuzzy" ideas became testable requirements (e.g., "The system SHALL redirect unauthenticated users...").

Scenario Simulation: I used the LLM to "stress test" our architecture. I ran simulations like "What happens if a user logs in but has no department set?" which revealed the need for a dedicated Onboarding State—a critical architectural decision that prevented routing loops.

Decoupling Strategy: I used the LLM to break down the monolithic requirements into isolated, testable scenarios (e.g., "Scenario: Teacher attempts to access student dashboard") that Idan and Tamar could later turn directly into Playwright tests.

3. How the LLM Worked and the Difficulties Discovered
Successes: The LLM was exceptional at converting abstract product intent into concrete logic. It helped bridge the gap between Roee's user-focused PRD and the actual code. For instance, it helped identify that we needed a distinct profileComplete flag in Firestore to manage the Onboarding flow securely.

Difficulties:

Context Loss: The biggest challenge was the disconnect. When I returned from duty, re-aligning the LLM with the team's actual progress (which sometimes deviated from my specs) was difficult.

Over-Engineering: The LLM initially suggested complex features like a "Compliance Verifier" engine. I had to intervene and manually move these to the "Non-Goals" section of the spec to ensure the project remained feasible for my teammates who were also juggling personal challenges.

4. Prompts I Used
Below are the main prompts I used to generate the specifications and execution strategy:

Specification & Requirements:
"I am collaborating with a PM on a PRD. He is handling the user stories. I need to handle the System Constraints. Take these features and convert them into a formal 'Current Truth' document using normative language (MUST/SHALL). Focus on Auth Gating and Role-Based Routing."

"Define the behavior for 'Neutral Entry Pages' (like /login). If an authenticated user lands there, where exactly should they be redirected based on their profile status? Write this as a 'Scenario' we can test against."

Strategic Planning:
"I have a team of 3 developers and I will be unavailable due to Miluim. Break this project down into independent modules (UI, Auth, Logic) that have minimal overlap. What are the interfaces they need to agree on first?"

"Identify the 'Non-Goals' for this MVP. What features should we explicitly cut to ensure we finish on time?"

5. What I Learned from the Process
I learned that specification is the ultimate tool for asynchronous collaboration. By co-authoring the product definition with Roee, we ensured alignment, but by writing the specifications.md, I provided the technical guardrails. I learned that LLMs are powerful tools for architecting constraints—helping me define the "box" the team worked inside, which was crucial given our collective constraints.

6. Actions Performed Manually
Defining the MVP Scope: Manually deciding to cut features and strictly defining the "Student vs. Teacher" binary role model to simplify development.

Architectural Handoff: conducting the initial breakdown of tasks based on the specs before deploying.

Final Spec Approval: Reviewing the LLM-generated scenarios and ensuring they matched the logic of the course's requirements before committing them to the repo.