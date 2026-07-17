# EmberAdventures Skills

This folder contains the two skills used to create and validate EmberAdventures
characters and story templates:

- `emberadventures-character/`
- `emberadventures-story/`

## Which skills to download

### EmberAdventures Character

Download `emberadventures-character/` when you want to create, revise, review,
repair, or validate an EmberAdventures character definition. It is the base
character schema and is also needed whenever a story contains player characters,
party members, or NPCs.

### EmberAdventures Story

Download `emberadventures-story/` when you want to create, revise, migrate,
review, or validate an EmberAdventures story template. The Story skill depends
on the Character skill for character definitions, so download both folders when
working with stories. The Story skill should be loaded after the Character skill
when both are available.

### Quick guide

| Goal | Skills to download |
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

Before using either skill, check its version file on GitHub. If the version is
newer than the local skill, download the matching skill folder from this
repository and replace the local copy before continuing. The version files are
deliberately plain text so they are easy for an AI or setup script to retrieve.

## Keeping a local copy current

The authoritative files are maintained in the public repository:

https://github.com/andro951/ember-adventures-tools

When updating manually, compare the local version file with the matching raw
GitHub version file, then replace only the affected skill folder. Do not copy or
publish any private preference files. The Character skill may create its private
preference file in the user's local Codex private-data directory; that file does
not belong in this repository.
