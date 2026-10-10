# GenUI Bridge

Interactive answers inside **DeepSeek Harness Desktop**: charts, tables, forms, quizzes, diagrams, 3D scenes and session panels.

GenUI Bridge is Josee0617’s packaging fork of [omdsh-dev/dsh-genui](https://github.com/omdsh-dev/dsh-genui), based on upstream **0.11.4** (`5d0d63b8f542886db4910f4dd13a875b1e01803c`). The upstream MIT license, credits, renderer and model instructions are preserved. This release targets your **Harness Desktop 0.2.0-rc.2**.

[简体中文](README.zh-CN.md) · [Releases](https://github.com/Josee0617/dsh-genui-bridge/releases) · [Component reference](SKILL.md)

## Install in Desktop

1. Open **Plugins → Add plugin** and paste:

```text
https://github.com/Josee0617/dsh-genui-bridge/releases/download/v0.1.0/josee0617-dsh-genui-bridge-0.1.0.tgz
```

2. Install and enable the plugin, then **fully quit and reopen Harness** (macOS: ⌘Q).
3. Open a new chat with a configured model and ask:

> Use dsh-ui to make a sample sales dashboard with three stat cards, a sortable table, and a bar chart. Use fictional data.

The reply should show interactive components rather than only a code block. You do not need to download the `.tgz` first: Harness downloads this release URL directly. The GitHub source ZIP and repository homepage are not compiled installers. This fork is distributed through GitHub Releases, **not npm**.

If the upstream GenUI is already installed, disable it before enabling this fork. Both register the same UI language, model tools and panel commands; they are alternatives, not two plugins to run together.

## Same GenUI workflow

- Ask in normal language, adding **“use dsh-ui”** when needed. The bundled `genui` skill supplies the full component reference.
- Tables, charts, forms, plots, quizzes, Mermaid and 3D scenes retain their upstream behavior.
- Local controls update immediately. Actions that need the model send `[genui-action]` back into the conversation and can incur model usage.
- `/panel` opens a persistent session panel; `/panel <instruction>` asks the model to customize it; `/panel clear` clears it.
- Settled blocks offer **Export → HTML** or **GenUI JSON**. HTML preserves local controls, but model actions are disabled outside Harness. Remote media still needs a network connection.
- Both registry and DOM rendering channels, streaming, persisted interaction state, validation and fence repair are preserved.

The model must emit a supported `dsh-ui` specification; installing GenUI does not guarantee that every model follows the format. Never enter passwords or API keys into generated forms.

## What changed in this fork

Only package identity, matching client ModuleLoader identity, lazy-asset URLs, feedback identity, install fixtures and Desktop documentation were changed. The component protocol, rendering logic, interaction behavior and model instructions are retained from upstream. Skill providers use the fork identity; the user-facing skill remains `genui`.

The original feature reference and upstream demo material remain in [the upstream README](docs/upstream-README.md). Those npm commands install the original package, not this fork.

## Development and verification

```sh
pnpm install --frozen-lockfile
pnpm run check
pnpm run check:host-api dsh-v0.2.0-rc.2
node scripts/verify-pack.mjs --keep
```

Verified on 10 October 2026: **1,031 tests passed** (99 upstream tests skipped), **77 published-host API/lifecycle tests passed**, standalone bundle validation and the pack gate passed. A fresh Harness 0.2.0-rc.2 profile installed the tarball; its browser rendered ECharts and Mermaid, sorted numeric table values, and delivered a button action to a synthetic model which returned a new reply. This check used no provider credentials or paid model calls; the active Desktop profile was not modified.

The full test suite, published-host API check and pack gate cover the renamed package. Fixture tests do not establish live model quality. Retest before updating Harness. No personal Harness profile or provider credentials are needed for those checks.

## License and attribution

MIT. Copyright and credits in [LICENSE](LICENSE) belong to their original authors. Fork maintained by [Josee0617](https://github.com/Josee0617).
