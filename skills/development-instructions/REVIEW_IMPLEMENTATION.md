Review the implementation against the attached plan. Do not implement new changes unless explicitly asked.

Goal:
- Verify that the implementation matches the plan, fixes the root cause, and does not introduce obvious regressions.

Tasks:
1. Compare implementation against the plan step by step.
2. Check whether the root cause was actually addressed.
3. Check whether scope was exceeded.
4. Review tests for adequacy:
   - do they test the bug?
   - do they test the happy path?
   - do they test likely regressions?
5. Identify fragile assumptions, hidden risks, and uncovered edge cases.
6. Identify any mismatch between claimed success criteria and actual implementation/testing.
7. Check completeness of the iteration:
   - Was logic invalidated by this change (checks, branches, flags, assertions) actually removed, or was stale logic left behind?
   - Were any negative checks added that assert the absence of old/removed behavior? Flag them — current requirements must be asserted positively, and only where needed.
8. Check handling of existing checks and conditions:
   - Was any existing check removed or a condition generalized to all cases? If so, is this explicitly justified by the task/plan, backed by an investigation of who relied on it?
   - If the task targets one mode/path, verify the other modes/paths remain fully functional.
9. Check structure of changed code:
   - Is new or changed behavior extracted into well-named single-responsibility methods, rather than inlined into a multi-responsibility method?
   - Is the extraction scoped to the changed parts (no over-fragmentation, no restructuring of unchanged code)?
10. Check naming and descriptions:
   - Are all introduced names and descriptions (methods, variables, classes, parameters, test names, commit messages, comments) clear to any developer without the task context, not only to the author?
   - Flag names that only make sense next to the ticket/plan, and new synonyms for domain terms the codebase already has.
   - Flag description content that carries no useful payload for the reader: generic filler, spec/tooling trivia, self-justification of the change.
11. Report whether the change is:
   - safe to merge
   - needs revision
   - incomplete

Rules:
- Do not make code changes.
- Be skeptical.
- Prefer finding concrete risks over giving general praise.
- Distinguish critical issues from minor suggestions.

Output format:
1. Verdict
2. Plan compliance
3. Root-cause coverage
4. Test adequacy
5. Regression risks
6. Missing edge cases
7. Recommended follow-ups