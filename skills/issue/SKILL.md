---
name: issue
description:  File a GitHub Issue.
---
# How to File a GitHub Issue

Every issue must be closeable.  Someone reading it should immediately know how to
close it as "done" or "won't do."  If neither action is obvious, rewrite the issue
until one is.

## Title

The title is a triage instrument.  A maintainer scanning 50 issues must be able to
rank yours by importance without clicking into it.

Good: `cargo test --release panics in crate_foo: "index out of bounds" in bar::transform`
Bad: `Tests are broken`
Useless: `Bug report`

Encode the problem, not the solution.  Include the affected component, the symptom,
and enough specificity to distinguish this issue from every other issue.

## Body

### Problem Statement

Lead with the problem.  One to two sentences.  This is the most important paragraph
in the issue.  If the title is the triage line, the problem statement is the
confirmation.

Do not lead with a solution.  Do not propose a solution unless it is obvious.  When
a solution is not obvious, a premature proposal narrows the design space and biases
the discussion.

### Environment

Every bug report must include:

- OS and version (e.g., macOS 14.5, Ubuntu 24.04 with kernel 6.8.0-40)
- Rust toolchain version (`rustc --version --verbose`)
- Host toolchain where relevant (Xcode version, glibc version)
- Commitish of the code under test

Omit what is irrelevant.  Include what someone needs to reproduce your exact
situation.

### Reproduction

Minimal steps to trigger the bug.  Numbered list.  Strip away everything that is not
necessary.  If the reproduction requires specific data, provide the smallest input
that triggers the failure or describe how to generate it.

A reproduction that works on any machine is worth ten that only work on yours.

### Expected vs. Actual

State both.  Always.

"Expected" catches impossible expectations early—before anyone spends time debugging.
"Actual" records the observed behavior precisely, including the exact error message or
panic output.

### Stack Traces and Logs

One stack trace per issue.  If you have multiple distinct panics, file multiple
issues.  Duplicate stack traces on the same bug are noise—include the one that best
shows the failure and trim the rest.

Wrap traces in a `<details>` block so they don't dominate the page:

````markdown
<details>
<summary>Stack trace</summary>

```
paste here
```

</details>
````

## Length

Three to five paragraphs.  Not forty-seven.  No life stories.  If you need more than
five paragraphs, you are either filing multiple issues in one or including context
that doesn't help someone fix the bug.

## Scope

One issue, one concern.

If you find a crash, a typo, and a missing log message in the same session, file
three issues.  They will be triaged independently, fixed independently, and closed
independently.  Bundling them delays the easy fixes and clutters the hard ones.

## Feature Requests

State the problem you are experiencing, not the solution you want.  The problem goes
in the title.  The body explains the pain: what you tried, why it didn't work, what
you need.

If you must suggest an implementation, put it last and mark it as a suggestion.  The
maintainer may know a better way.

## Checklist Before Submitting

- [ ] The title states the problem specifically enough to triage without opening.
- [ ] The body leads with the problem, not a proposed solution.
- [ ] Environment and reproduction steps are present for bugs.
- [ ] Expected and actual behavior are both stated.
- [ ] The issue contains exactly one concern.
- [ ] The body is five paragraphs or fewer.
- [ ] A reader can close this as "done" or "won't do" without asking clarifying questions.

## Mechanics

To actually create an issue, engage the user with dialogue and questions until you know for certain
that the above checklist is completely satisfied.  Then, propose text to the user.  When the user
confirms your text as valid, use the `gh` command to create the issue.  If the repo context is not
obvious from talking to the user, ask the user which org and repo to use.
