# EmberAdventures Skills

This folder contains the two skills used to create and validate EmberAdventures
characters and story templates:

- `emberadventures-character/`
- `emberadventures-story/`

## Which skill files to use

### EmberAdventures Character

Use `emberadventures-character/` when you want to create, revise, review,
repair, or validate an EmberAdventures character definition. In ChatGPT, copy,
paste, upload, or otherwise provide the skill files as ordinary instruction
documents. In Codex, install or load the skill folder as a Codex skill when it
is not already installed.

### EmberAdventures Story

Use `emberadventures-story/` when you want to create, revise, migrate, review,
or validate an EmberAdventures story template. The Story skill depends on the
Character skill for character definitions, so provide both skill folders when
working with stories. In ChatGPT, treat them as reference/instruction files. In
Codex, install or load them as Codex skills when they are not already installed.

### Quick guide

| Goal | Skill files to use |
| --- | --- |
| Create or review a character | `emberadventures-character` |
| Create or review a story | `emberadventures-character` and `emberadventures-story` |
| Create a story with characters, party members, or NPCs | `emberadventures-character` and `emberadventures-story` |
| Validate an existing story template | `emberadventures-character` and `emberadventures-story` |

## Using the skills

Use the Character skill for character definitions and the Story skill for story
templates. For source or canon work, also load the corresponding Source
EmberAdventures extension when available. The source extensions are separate
from this repository and add research and canon-specific guidance; they do not
replace the base skills.

Each skill has a sibling version file:

- `emberadventures-character-version.md`
- `emberadventures-story-version.md`

For ordinary story or character creation, do not start by checking versions or
replacing local files. Use the skill files already provided to the current AI
session. Version checks are for maintenance tasks where the user explicitly asks
to update or verify skill currency. The version files are deliberately plain
text so they are easy for a setup script or maintainer to retrieve.

## Keeping a local copy current

The authoritative files are maintained in the public repository:

https://github.com/andro951/ember-adventures-tools

When updating manually, compare the local version file with the matching raw
GitHub version file, then replace only the affected skill folder. Do not copy or
publish any private preference files. The Character skill may create its private
preference file in the user's local Codex private-data directory; that file does
not belong in this repository.
