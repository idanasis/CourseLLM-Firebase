# Project Report: AI-Assisted Development (File Management & Monitoring)
1. **Project Overview**
Objective: Develop a File Management UI module for the "CourseWise" platform, allowing for CRUD operations, file previews, and system health monitoring. Tech Stack: Next.js, Firebase (Auth/Firestore), Jest (Unit Testing), Playwright (E2E Testing), and systeminformation (Monitoring). AI Tools Used: Firebase Integrated AI (Project IDX/Gemini), Claude 3.5 Sonnet, Google Gemini Pro.

2. **AI Development Workflow**
The development process followed an iterative prompting strategy, starting with high-level context and moving toward specific feature implementation.

* Phase 1: Context & Scaffolding
Input: The AI was initially primed with the Product Requirements Document (PRD) and specific feature requirements for the UI (File Management CRUD).

Result: The AI successfully generated the initial boilerplate code and UI components.

* Phase 2: Feature Refinement
Prompt: "Make it so that clicking a file opens it in a new tab."

Action: The AI modified the onClick handlers and file routing to support browser-native file previews in a separate tab.

* Phase 3: Testing & Security
Unit Tests: Requested the AI to generate Jest unit tests using mocks to simulate Firebase responses, ensuring logic reliability without hitting the live database.

Authentication: Instructed the AI to wrap the module with the Firebase Authentication package to secure file access based on user roles (Student vs. Teacher).

E2E Tests: Prompted for End-to-End tests to verify the full user flow from login to file upload.

* Phase 4: System Monitoring
Requirement: Implement a "Health Dashboard" using the systeminformation library in Next.js.

Metrics Implemented:

Process verification (health check).

CPU usage (Load/User/System).

Memory allocation (Used vs. Free).

Network traffic stats.

Outcome: A dedicated dashboard page exposing these metrics for administrator review.

3. **Challenges & AI Limitations**
While the AI was helpful for initial scaffolding, significant friction was encountered during complex implementation phases.

A. **Context Loss & "Loops"**
The Firebase integrated AI struggled to maintain context over long development sessions. It frequently got "stuck in loops," suggesting code changes that reverted previous fixes or introduced circular dependencies (e.g., in ESLint configurations or import cycles).

B. **Platform Instability**
Performance: The internal AI environment proved unstable. Specifically, on Monday, January 12, the system became unresponsive ("stacked") multiple times, requiring hard resets of the workspace to continue working.

History Loss: The lack of persistent chat history in the Firebase AI interface made it difficult to reference previous prompts, forcing the re-explanation of context multiple times.

C. **Complexity Ceiling**
The integrated AI failed to handle the complexity of advanced E2E testing and specific Unit Test mocking scenarios. It often generated hallucinated APIs or deprecated syntax that caused build failures.

4. Mitigation Strategy (Hybrid AI Approach)
To overcome the limitations of the internal tool, the workflow was shifted to external, higher-reasoning LLMs (Claude and Gemini Pro).

Manual Intervention: We manually exported code snippets to these external models to fix broken test suites and resolve the configuration loops.

Refactoring: External models were used to clean up the "slop" (unused code/dependencies) left behind by the initial scaffolding.
5. what I learned:
A key lesson learned from this project is that integrating Large Language Models (LLMs) into the development workflow is not an automatic efficiency boost; without precise prompt engineering, it can actually lead to time-consuming loops and context loss. However, we discovered that when the AI is guided correctly—specifically by combining specialized agents (e.g., using different models for scaffolding versus complex logic), it transforms from a potential bottleneck into a powerful accelerator, capable of handling robust tasks like testing and system monitoring
6. Conclusion
The project successfully delivered a robust File Management and Monitoring system. However, the experience highlighted that while integrated IDE assistants are excellent for starters and boilerplate, they currently lack the stability and long-context reasoning required for complex debugging and system architecture. The move to specialized external LLMs was necessary to bring the project to a production-ready state.