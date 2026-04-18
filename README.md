**English** | [简体中文](./README.zh-CN.md)

# Carl Jung.skill

A skill for exploring persona, shadow, projection, individuation, and symbolic patterns through a bounded Jungian lens. It supports reflection without claiming to recreate Jung's mind or discover hidden psychological facts.

[Examples](#examples) · [Installation](#installation) · [Routes](#routes) · [Sources](#sources) · [Maintenance](#maintenance) · [Credits](#credits-and-license)

Responses default to English. An explicit request for Chinese selects Simplified Chinese unless a different variant is specified. A conversation-wide language choice persists until changed; a request for one answer or artifact applies only there. Other explicitly requested languages are honored. A Chinese prompt or this README's language selector does not change the response language by itself.

## Examples

These are illustrative response outlines written for this project, not quotations, historical reconstructions, or clinical conclusions.

### Why am I so angry at a colleague who takes credit for my work?

Start with what happened: taking credit can be a real fairness problem. A Jungian question might explore why the incident feels especially charged, but projection is not assumed. The user can address credit and boundaries even if no inner association emerges.

### My reliable-person role is exhausting. Is it fake?

A chosen role can express real values. Separate reliability from always being available, then identify which demand is causing strain. If change is wanted, try a feasible boundary rather than assuming the whole role must be abandoned.

### Does my recurring dream mean something bad will happen?

A dream does not establish a prediction. Begin with the user's associations and recent context, compare symbolic and ordinary readings, and allow the meaning to remain uncertain. Do not infer hidden trauma or a diagnosis from imagery.

### Can I want both independence and closeness?

Use individuation as an invitation to acknowledge both needs. Explore their actual tradeoffs and the commitments the user wants to preserve. The answer can end with a clearer distinction rather than a mandatory exercise.

## Installation

```bash
npx skills add justinhuangai/carl-jung-skill
```

The Python maintenance tools are not required to use the skill. Ask for Carl Jung's perspective on a question or invoke `carl-jung-skill` explicitly. To select Chinese, say: `Please answer in Simplified Chinese for the rest of this conversation.`

## Routes

[SKILL.md](SKILL.md) defines language, evidence, and routing rules. Start with one operational reference and read research only as needed.

| Route | Purpose |
|---|---|
| [Shadow and projection](references/shadow-and-projection.md) | Strong reactions without assuming projection |
| [Persona and self](references/persona-and-self-split.md) | Role demands and identity strain |
| [Individuation](references/individuation-navigation.md) | Competing needs and integration |
| [Archetypes and symbols](references/archetypal-pattern-reading.md) | Optional readings of images and narratives |
| [Self-exploration boundaries](references/self-exploration-with-boundaries.md) | Uncertainty, consent, and useful stopping points |

## Sources

There are **3 unique source records**: one partial Britannica biography and two library catalogs. No primary Jung book prose is captured. The catalogs describe Psychological Types and The Archetypes and the Collective Unconscious; they support edition and contents-list facts, not quotations or detailed theory. Earlier records labeled IEP and Two Essays duplicated the same Britannica URL and have been removed.

The [six research notes](references/research/README.md) are editorial guides with explicit evidence gaps, not a comprehensive literature review. Inspect the [source inventory](references/sources/README.md) before citing a work. Verify exact quotations, disputed historical claims, and current scientific assertions against appropriate sources.

## Boundaries

- Treat psychological interpretations as possibilities, not facts about another person's hidden motives.
- Consider ordinary explanations and actual mistreatment before an inward interpretation.
- Respect the user's goals, constraints, consent, and correction; disagreement does not prove a theory.
- Do not diagnose, provide treatment, infer recovered memories, or replace appropriate professional support.
- Do not use symbolism, historical prestige, or untestable explanations to pressure or manipulate people.

## Repository layout

- [SKILL.md](SKILL.md): concise runtime instructions; version remains `1.0.0`.
- [references/](references/): five operational routes and an extraction framework.
- [references/research/](references/research/README.md): six thematic notes.
- [references/sources/](references/sources/README.md): preserved source content and provenance.
- [scripts/](scripts/) and [tests/](tests/): maintenance utilities and regression tests.
- [README.zh-CN.md](README.zh-CN.md): Simplified Chinese overview.

## Maintenance

Run from the repository root with Python 3.10 or later:

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

Core checks and tests use the standard library. Optional HTML capture tests run when Beautiful Soup is installed. Web/PDF capture optionally requires the packages in `requirements.txt` (requests, Beautiful Soup, pypdf); install them with `python3 -m pip install -r requirements.txt` when needed.

`capture_web_source.py` requires `--language` for the actual source language (`en`, `zh-CN`, another tag, or `und` if unknown). It preserves source text rather than translating it. `srt_to_transcript.py` converts SRT/VTT files. Subtitle download requires optional `yt-dlp`, defaults to English, and tries manual before automatic tracks. `--language zh-CN` selects only explicitly labeled Simplified Chinese tracks; neither selection falls back to another language. CLI messages remain English.

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

Checks validate links, metadata, repeated text, and script behavior; they do not prove historical truth, source completeness, rights clearance, or clinical efficacy. Keep both READMEs synchronized and use the [extraction framework](references/extraction-framework.md) when changing research.

## Credits and license

Maintained by Jackson Huang and assembled with [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill). Thanks to Nuwa's authors and contributors for the tooling.

Original project content is available under the [MIT License](LICENSE). Third-party texts, translations, and catalog records retain their own rights and terms; their inclusion does not relicense them under MIT.
