# Conventional Commits: Simplified

[Русский](README.md) | **English**

## Introduction

Based on [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#specification)

This convention sets out the rules for writing commit messages.

Before adopting the convention, agree on the basic principles for maintaining the commit history:

1. **Commit granularity.**

   One commit should contain one logically complete change (for example, adding a new feature or fixing a bug).
   Strike a balance and avoid splitting changes into excessively small commits.

2. Each commit must leave the codebase in a working state that **compiles without errors**. If the component being changed is intended to run, it must also **start successfully** (for example, initialize the application context).

3. If the changes relate to a Jira issue, the branch name must exactly match the issue key.

---

## Commit Message Structure

Commit messages must have the following structure:

```text
[1] <type>[(<Jira issue key>)][!]: <description>

[2] [optional body]
```

Let us look at each block in detail:

### Header

`<type>[(<Jira issue key>)][!]: <description>`

The Jira issue key is optional. When included, it is placed in parentheses immediately after the type. For commits unrelated to an issue, omit both the key and the parentheses.

Commit types:

* `feat` - adding a new feature;
* `fix` - fixing a bug;
* `build` - changing the application build or updating dependencies;
* `refactor` - changing the code structure without adding or changing functionality;
* `ci` - adding or changing CI scripts, pipelines, etc.;
* `docs` - adding or changing documentation;
* `style` - changing code formatting;
* `test` - adding or changing tests;
* `chore` - other changes that do not fit any of the other types;
* `revert` - reverting changes.

The commit description must be meaningful and follow a consistent style. Where possible, it should start with a verb describing the action:
`feat: add ...`, `fix: fix ...`, `style: adjust indentation ...`, etc.

If the changes break backward compatibility (breaking changes), the `!` symbol is required. Place it immediately before the colon: after the issue key in parentheses, if present, or directly after the type.

### Body

`[2] [optional body]`

Separate the body from the header with one blank line.

---

## Commit Message Examples

```text
feat(JIRATASK-123): add assignment versioning
```

```text
fix(JIRATASK-123): fix NPE when creating a project stage
```

```text
build: add rsql-jpa-spring-boot-starter dependency
```

```text
feat(JIRATASK-123)!: introduce a new format without support for the previous one
```

```text
feat!: introduce a new format without support for the previous one
```

---

## Frequently Asked Questions

1. Q: *Doesn't this discourage rapid development and fast iteration?*

   A: It primarily discourages rapid, disorganized development. By introducing a standard, the convention helps teams move faster in the long run across multiple projects with different contributors.

2. Q: *What should I do if a commit fits more than one type?*

   A: Split independent changes into separate commits. If the changes are logically related and form a single whole, choose the commit type based on their main purpose.
   The convention makes the development history simple and easy to understand.

3. Q: *Should I use lowercase or uppercase letters?*

   A: Use lowercase in commit messages, except for names and identifiers.

4. Q: *How does reverting commits work?*

   A: There are no strict instructions, but using the `revert` commit type and listing the hashes of the reverted commits is recommended:

   ```text
   revert(JIRATASK-123): revert commits 676104e, a215868
   ```

5. Q: *What else does this convention offer besides an organized commit history?*

   A: Opportunities for automation, such as:

   - automatically generating a meaningful changelog;
   - automatically determining the semantic version bump (based on the commit _types_).
