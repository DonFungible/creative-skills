# creative-skills

Claude skills for creative work: the craft behind image, video, 3D and music, written so an agent can use it. Each category is a Claude Code plugin.

## Install

```
/plugin marketplace add DonFungible/creative-skills
/plugin install foundations@creative-skills
```

## Categories

| Category | What goes in it |
|---|---|
| `foundations` | Craft that applies to two or more media (composition, lighting, color, storytelling), plus critique: judging work against a brief. |
| `image`, `video`, `3d`, `music` | Craft tied to one medium. Each is created when its first skill lands. |
| `production` | Planned. Process skills that carry work through the production phases. |

Skills are tool-neutral, plain-text craft: the core guidance lives in `SKILL.md`, so it also works pasted as a system prompt (for example in ComfyUI's Claude node). See [GLOSSARY.md](GLOSSARY.md) for the terms used here and [docs/adr/](docs/adr/) for decisions.

## Layout

```
.claude-plugin/marketplace.json     # lists every category
skills/
└── <category>/
    ├── .claude-plugin/plugin.json  # category name, description, version
    └── skills/
        └── <skill-name>/
            ├── SKILL.md            # required: frontmatter (name, description) + instructions
            ├── references/         # optional: deeper material, loaded as needed
            ├── scripts/            # optional helpers; never required
            └── evals/              # test cases
notes/                              # study notes and research; never loaded by agents
```

## Adding a skill

1. Study the craft and write notes in `notes/<craft>.md`.
2. Draft `skills/<category>/skills/<skill>/SKILL.md`.
3. Write 2–3 test prompts and compare output with and without the skill.
4. Generate images from the strongest cases and compare them.
5. Fix the skill, then commit.

New category: create `skills/<category>/` with its own `.claude-plugin/plugin.json`, then add it to `.claude-plugin/marketplace.json`.
