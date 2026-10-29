# Moo Agent Kit

A growing collection of skills, agents, and package adaptations organized by their target AI coding environment. The first target is GitHub Copilot in VS Code, for use without Pi or other external agent runtimes.

## Copilot

```text
copilot/
  skills/
    moo-prompton/
      SKILL.md
```

| Skill | Invocation | Behavior |
| --- | --- | --- |
| [Moo Prompton](copilot/skills/moo-prompton/SKILL.md) | `/moo-prompton <draft>` | Rewrites a prompt, automatically choosing natural wording or a compact task contract. Empty input asks for a draft and waits. |

Moo Prompton returns only the rewritten prompt. It preserves explicit constraints and code blocks, and does not execute the task, inspect your workspace, or call external services. Like any instruction-based skill, behavior depends on the model; review its output before use.

## Install on another computer

Clone or download this repository using your organization's approved process:

```sh
git clone https://github.com/the-matt-moo/moo-agent-kit.git
cd moo-agent-kit
```

The `copilot/` folder is a distribution layout, not a Copilot discovery location. Choose one installation scope below; cloning alone does not install the skills.

### Personal: available across workspaces

Copy `copilot/skills/moo-prompton/` to `~/.copilot/skills/moo-prompton/`.

PowerShell, from the repository root:

```powershell
New-Item -ItemType Directory -Force "$HOME/.copilot/skills" | Out-Null
Copy-Item -Path "./copilot/skills/moo-prompton" -Destination "$HOME/.copilot/skills" -Recurse -Force
```

### Workspace: available in one project

Copy `copilot/skills/moo-prompton/` into the target project's `.github/skills/` directory. The resulting file must be:

```text
<your-project>/.github/skills/moo-prompton/SKILL.md
```

Keep any existing skills. Install this skill in one scope to avoid duplicate names. Review/back up local modifications before replacing an existing copy.

### Use

Open your target workspace in VS Code, select Copilot chat, and type:

```text
/moo-prompton fix the timeout issue without changing the public API
```

Or invoke `/moo-prompton` alone, then provide the draft when asked. The skill is explicitly invoked; it is not an automatic interceptor for other chat messages. Copy/reuse the result when you are ready to perform the task.

If the command does not appear, verify the installation path and enabled skill customizations in your VS Code build. See the [official skill documentation](https://code.visualstudio.com/docs/agent-customization/agent-skills).

### Update

Pull the latest approved revision, review the changes, then copy the desired skill folder to the same installation location again. Installed copies do not update automatically. For a controlled workplace rollout, use a reviewed commit rather than treating the moving `main` branch as approved.

## Workplace restrictions

Organization policies may block standalone skills or require an approved agent plugin. Public GitHub availability is not workplace approval; follow your organization's rules for importing customizations. See [VS Code enterprise AI settings](https://code.visualstudio.com/docs/enterprise/manage-ai-settings).

This repository does not bypass policy, install a runtime, or require API keys. Copilot itself still handles model requests and its normal enterprise data/retention policies apply.

## Adding more ports

Keep Copilot skills under `copilot/skills/<skill-name>/SKILL.md`. Add other Copilot assets under `copilot/` when needed, and list their installation paths and requirements here. Each port should work without its original agent runtime.

Moo Prompton adapts the rewrite behavior of [pi-prompton](https://github.com/the-matt-moo/pi-prompton); it is an instruction-based port, not the Pi extension or its editor shortcut.

## Verification

Skill metadata, packaging, and documented behavior rules have been checked locally. Live Copilot behavior and workplace policy compatibility have not been tested.

## License

[MIT](LICENSE).
