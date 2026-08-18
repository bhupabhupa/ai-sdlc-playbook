---
name: write-tests
description: Write and run tests for implemented FRs, per the Test Plan in docs/SPEC.md. Argument optional, e.g. /write-tests FR-2
argument-hint: [FR-id or blank for all implemented]
---

Use the test-writer agent for this task.

Write tests for $ARGUMENTS (or all implemented-but-untested FRs if blank):

1. Implement the Test Plan cases from docs/SPEC.md first, then add edge
   cases you consider necessary.
2. Follow the project's test framework and layout (see CLAUDE.md).
3. Run the tests. If failures reveal implementation bugs, report precisely;
   fix implementation only if small and within the FR's scope.
4. Update IMPLEMENTATION_PLAN.md marking tested FRs.
