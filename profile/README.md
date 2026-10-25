<img src="https://raw.githubusercontent.com/step-review/step-review/main/packages/app/public/favicon.svg" alt="" width="64" height="64">

# Step Review

A better way to review PRs.

Your coding agent splits a PR into steps (by part of the system, by concern,
mechanical changes apart…) and writes notes on the changes: explainers for the
non-obvious parts, and issues to check. Step Review shows the review one step at
a time, with the notes beside the diff, and lets you mark files as viewed.

## How it works

1. Open [step-review.dev](https://step-review.dev) and paste the PR link (or a
   branch, or a commit range) into the prompt. The app copies the completed
   prompt for you.
2. Give the prompt to your coding agent. Following
   [SKILL.md](https://github.com/step-review/step-review/blob/main/packages/app/public/SKILL.md) (published at
   `step-review.dev/SKILL.md`), it writes a single review file, such as
   `pr-123.step-review`, in your repository. The file is never committed.
3. Drop the file into Step Review. Everything stays in your browser.
4. When the PR changes, ask the agent to review it again. Files whose changes
   are the same stay marked as viewed.

## Review files

A review file is a JSON section written by the agent (overview, steps, notes)
followed by the `git diff` of the PR, so the agent never writes diff content
itself. See [`@step-review/review-format`](https://github.com/step-review/step-review/blob/main/packages/review-format/README.md) for
the format, and `step-review.dev/schema/v3.json` for its JSON Schema.

## Development

pnpm monorepo:

- [`packages/app`](https://github.com/step-review/step-review/blob/main/packages/app): the web app (Vite, React, Primer).
- [`packages/review-format`](https://github.com/step-review/step-review/blob/main/packages/review-format): the review file format:
  schemas, parser and consistency checks.
- [`packages/tooling/oxlint-custom-rules`](https://github.com/step-review/step-review/blob/main/packages/tooling/oxlint-custom-rules):
  architecture lint rules.

See [Setup](https://github.com/step-review/step-review/blob/main/docs/setup.md) for requirements, commands and deployment.
Contributors and coding agents follow the principles in
[`AGENTS.md`](https://github.com/step-review/step-review/blob/main/AGENTS.md).

## License

[MIT](https://github.com/step-review/step-review/blob/main/LICENSE)
