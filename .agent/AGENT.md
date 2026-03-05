# Agent Instruction Manual

Your baseline behavior must strictly adhere to this document. 

## Directory Structure
You are operating within a strict template structure. You must understand your environment:

- **`.agent/`** (Your Control Center)
  - `AGENT.md`: Your universal rules (Read-Only).
  - `PROJECT.md`: The specific context of the current project. (Read-Write)
  - `config/`: System configurations and prompt templates. (Read-Write)
  - `skills/`: Skills if you use (Read-Write)
  - `history/`: Your memory directory to save and read past task summaries. You should update it

All the other project-related files should be placed in the outside of `.agent/`.

## Operating Procedure
Whenever you receive a new user request, you MUST strictly follow this exact sequence. Do not skip any steps.

1. **Initialize Tracking:** 

   * Make a copy of `history_template.md` template and rename it to `[YYMMDD-HHMM]_TaskName.md` (e.g., `260305-1548_Setup_Auth.md`)  in `.agent/history/`.
   - Paste the exact user request into the `# User Request` section.

2. **Phase 1: Plan**

   - **Initial Plan:** Draft a step-by-step technical plan to fulfill the request BEFORE doing anything.
   - **Questions for User:** Identify any ambiguities, missing requirements, or unclear architectural decisions in the request. Write them down using `(Q)`.
   - **⚠️ CRITICAL STOP ⚠️:** If you have generated any questions, you MUST **IMMEDIATELY HALT EXECUTION AND PRESENT THE QUESTIONS TO THE USER AND WAIT FOR THE RESPONSE.**
     - **STRICTLY FORBIDDEN:** Do NOT write or guess the user's answer `(A)`.
     - **STRICTLY FORBIDDEN:** Do NOT proceed to `Phase 2`.
   - **Updated Plan:** ONLY AFTER the user provides the answers `(A)`, record them here and finalize your step-by-step plan.

3. **Phase 2: Do-Check**

   - Break down your `Updated Plan` into actionable checklist items `[ ]` in the `## Do-Check` section.
   - Mark an item as complete `[x]` ONLY after you have implemented the code, run necessary tests/linters, and verified it does not break existing logic.

4. **Phase 3: Report**

   - Once all Do-Check items are verified, commit the changes to the repository.
   - Fill out the `## Report` section and any closing remarks.
   - Send this section to user.