Proceed to implementation of the attached plan.

Goal:
- Implement the approved plan exactly and safely.

Requirements:
1. Complete the development steps from the plan.
2. Write or update tests defined in the testing strategy.
3. If editing logic in an existing function, inspect its usages across the codebase and preserve existing behavior outside the scope of the plan.
4. Run relevant existing tests and ensure they pass.
5. If the plan is incomplete, inconsistent with the codebase, or unsafe to implement, stop and report the mismatch before proceeding.

Rules:
- Do not broaden scope beyond the plan.
- Do not make unrelated refactors, renames, formatting-only changes, or cleanup edits.
- Do not silently change behavior not covered by the plan.
- Prefer minimal edits.
- Preserve public interfaces unless the plan explicitly says otherwise.
- If implementation reveals the plan is wrong, stop and explain what changed.
- If a test fails outside the scope of the plan, report it separately instead of folding it into the same changes unless explicitly required.

Finish the work completely (obsolete vs. current logic):
- During iterative development, finish what your change makes obsolete: if the change invalidates an existing check, branch, flag, or assertion, remove it as part of the same change. Do not leave dead or stale logic behind.
- Never encode obsolete state as negation: do not add checks that assert the absence of old/removed behavior (negative checks against outdated conclusions). They heavily overload code comprehension, and future readers will falsely conclude the task required them, when in fact they were just an unnecessary leftover.
- Where the current solution needs protection, assert it directly with positive checks on the actual, current requirement — only in the places where it is genuinely needed.

Existing checks and conditions:
- Treat every existing check or condition as intentional until proven otherwise.
- Do not remove a check or generalize a condition to all cases unless this is explicitly justified by the task description. "This check looks redundant" is not a justification — it is a trigger to investigate first.
- If a check looks redundant, investigate who relies on it (modes, callers, configurations, integrations) before touching it, and ground the investigation in the task description.
- When the task targets one mode/path (e.g., app has modes A, B, C and the task adds an integration that works only with mode B), keep the change scoped to that mode. Do not remove the mode B check and make the condition common for all — modes A and C will likely break.
- Perform a cross-mode impact pass: not necessarily a deep audit, but enough to confirm that while changing B, modes A and C remain fully functional. Escalate to a deep check if anything is unclear.

Method extraction for changed code:
- When changing a sub-part of a method that mixes several responsibilities (e.g., a general init method with undelimited initialization of sub-parts), extract the changed sub-part into its own well-named method and call it from the original place.
- New functionality goes into new, well-named methods rather than being inlined into an existing multi-responsibility method.
- Do not over-fragment: extract by responsibility, not per line. The goal is code that reads like an open book — the orchestrating method shows what happens, the named methods show how.
- Extracting the part you changed is in scope; restructuring unchanged parts is an unrelated refactor and stays out of scope.

Naming and descriptions:
- Every name and description you introduce (methods, variables, classes, parameters, test names, commit messages, comments) must be clear to any developer on the team, not only to the person who implemented this task.
- Do not rely on task-specific context: a name that only makes sense next to the ticket or plan is a bad name. A reader without the task context must understand what the thing does from the name/description alone.
- Prefer domain terms already used in the codebase over new synonyms invented for this change.
- Verify the target files/functions from the plan exist.
- Verify the proposed changes still matches current code.
- Identify affected callers/usages of changed logic.
- Confirm which tests should fail before the changes and pass after the changes.

After coding:
- Summarize exact files changed.
- Summarize what was changed in each file.
- Summarize why the change is safe.
- Summarize tests added/updated.
- Report test results.
- Report any remaining risks or follow-up items.

Ask if something is not clear or ambiguous.