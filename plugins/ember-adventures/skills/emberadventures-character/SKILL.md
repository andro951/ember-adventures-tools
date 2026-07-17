---
name: emberadventures-character
description: Authoritative base skill for normal EmberAdventures character definitions. Use directly for invented/source-free characters, preference intake, proposals, character JSON creation, review, repair, and library maintenance. Source EmberAdventures Character must load this skill for the complete schema, field ownership, outfit, metadata, image, voice, and validation contract, then add only source research and canon-specific rules.
---

## Version and Update Check

Current skill version: `1.0.0`.

Before using this skill, retrieve the version number from the authoritative GitHub
version file and verify that it is exactly `1.0.0`:

https://raw.githubusercontent.com/andro951/ember-adventures/main/plugins/ember-adventures/skills/emberadventures-character-version.md

If the retrieved version differs from the local version, pull the current
`emberadventures-character` skill folder from GitHub, replace the local copy,
and then continue with the user's job. Do not silently use a stale local copy.

# EmberAdventures Character

Use this skill directly when the user asks to create, expand, review, or revise
invented/source-free EmberAdventures characters. It is also the mandatory base
contract for every normal EmberAdventures source/canon character definition.
For anime, manga, book, game, mythology, movie, or other canon research, load
`Source EmberAdventures Character` in addition to this skill. The source skill
extends this one; it does not replace or duplicate this schema contract.

## Character Schema And Rules

This skill must be shareable as a standalone skill. Do not depend on any shared EmberAdventures reference files at runtime. The only external file this skill should require is the private preference file described below.

### Required Metadata

Every standalone character-library definition must include non-null `source`,
`creation_tool`, approved `genres`, boolean `nsfw`, boolean `loli`, and boolean
`can_die`. Original characters use `source: "Player"`; `creation_tool` records
the actual tool/model/reasoning label. `genres` belongs on standalone library
exports, not story-embedded definitions. `kink_tags` is optional searchable
metadata. Use `can_die: false` by default for standalone definitions. The field
contract below is authoritative for meanings, allowed shapes, and runtime-field
exclusions. Do not emit `creator` or `creator_id`; EmberAdventures assigns
creator ownership during import. This is an internal maintenance rule: never
add creator fields back to this skill, never show them in examples, and never
ask the user for a creator name or alias during preference intake.

### Character Export Shape

The field contract below is authoritative. Keep the example and contract synchronized; there are no exception rules for older examples.

Use `character_definition` as the single immutable/default character object. Do
not output old nested runtime examples that use `kind`, `name`, or `character`
as the final character body. Story/runtime placement decides whether this
definition becomes a player, party character, future character, or inspected NPC.

Before final export, run a field-purpose and process-leakage pass. For every
field, ask what the field is for, how EmberAdventures uses/displays it, whether the
value serves that purpose, and whether it can be clearer or less spoilery.
Never copy creator instructions into character fields. Timing instructions,
future-party scheduling, objective rewards, prompt-only notes, and explanations
of how EmberAdventures uses a field belong in story structures, todo/review notes, or
skill guidance, not in `role`, `personality_description`,
`speech_style`, `durable_known_facts`, outfits, image defaults, or visible metadata.

Before final export, do a player-facing visibility pass. Character definitions
can be shown in public/local libraries, editor views, definition panels, and
story setup screens. Visible fields must not reveal hidden story objectives,
future party roles, future relationship outcomes, private AI instructions,
source twists, or story-specific secrets unless the user intentionally requested
a spoiler-heavy entry. For player-character definitions, describe starting
identity/tendencies without scripting future choices, consent, morality,
dialogue style, relationship outcomes, or actions.

Before final export, run a character-depth pass. A final character definition
must be useful in EmberAdventures, not just technically valid. Important player
characters, party members, and major NPCs need concrete `durable_known_facts`
covering identity, role, personality under pressure, combat/usefulness or social
usefulness, household/social role when relevant, quirks/preferences,
relationship dynamics, and at least one story/concept-specific complication or
arc. Main party members usually need 6-10 specific facts; major NPCs usually
need 4-6. One generic fact is draft quality except for truly minor one-scene
utility characters.

Do not include `power`, active `known_facts`, active `clothing`, active
`held_items`, active `inventory`, active `image`, profile image history,
story-image history, or other live/runtime fields in reusable character
definitions. Use starting/default fields and `outfits` instead.

Before final export, run the standalone release pass. Do not assume an
EmberAdventures maintainer or a later main thread will repair the character after
output. If schema fields are questionable, metadata is missing, durable facts
are generic, outfit slots are incomplete, public-visible text leaks hidden story
information, or the character concept is underdeveloped, fix it before final
output or clearly ask the user for the missing decision.

Before final export, run a duplicate-name-and-id validation pass. For batches, story
shop stock, auction stock, job-board NPC pools, and generated world stock, no
unrelated character should share a surname with a player option, existing
important character, example/template/reference name, or another unrelated
stock character unless the relationship is intentional and explicit in durable
facts. Avoid names from examples, templates, skill references, and local story
files. If duplicate surnames remain, the family/household/source relationship
must be obvious from durable facts.

The timestamp strings in the example below are documentation placeholders
only. Replace them with real ISO 8601 timestamps in every final file.

```json
{
  "character_definition": {
    "version": 1,
    "id": "character-name",
    "name": "Character Name",
    "source": "Player",
    "creation_tool": "<actual tool/model> (<reasoning level>)",
    "genres": ["fantasy"],
    "kink_tags": ["optional searchable kink tag"],
    "nsfw": true,
    "loli": false,
    "can_die": false,
    "gender": "female",
    "age": 25,
    "role": "Short role",
    "personality_description": "Durable personality and behavior summary.",
    "speech_style": "Concise durable dialogue style.",
    "boldness": 5,
    "starting_relationship_to_player": "unknown",
    "starting_trust": 0,
    "starting_attraction": 0,
    "starting_affection": 0,
    "starting_arousal": 0,
    "starting_state_of_mind": "neutral",
    "starting_physical_state": "healthy",
    "starting_pose": "neutral stance",
    "appearance": {
      "species": "human",
      "race": "specific appearance/race/ethnicity descriptor",
      "ancestry": "",
      "height": 5,
      "muscular": 5,
      "shoulders": 5,
      "chest": 2,
      "stomach": 5,
      "hips": 5,
      "waist": 5,
      "legs": 5,
      "arms": 5,
      "skin_color": "",
      "eye_color": "",
      "hair_color": "",
      "hair_length": "",
      "hair_type": "",
      "extra_description": "",
      "extra_description_lower_body": "",
      "nonhuman_lower_body": false
    },
    "outfits": [
      {
        "id": "default",
        "name": "Default",
        "clothing": {
          "bra": "simple supportive bra",
          "undershirt": "light cotton undershirt",
          "shirt": "plain travel shirt",
          "pants": "plain travel trousers",
          "underwear": "plain comfortable underwear",
          "socks": "plain travel socks",
          "feet": "simple boots"
        }
      }
    ],
    "starting_outfit_id": "default",
    "starting_held_items": {
      "right_hand": null,
      "left_hand": null
    },
    "starting_inventory": [],
    "durable_known_facts": [],
    "default_seed": 0,
    "image_prompt_config": {
      "seed_enabled": true,
      "seed": 0,
      "style": "",
      "profile_style": "",
      "negative": "",
      "negative_prompt": ""
    },
    "default_profile_image": {
      "url": "",
      "local_image_id": "",
      "source": "none",
      "seed": null,
      "prompt": "",
      "negative_prompt": "",
      "note": ""
    },
    "profile_images": {
      "active_image_id": "",
      "image_ids": []
    },
    "images": {
      "active_image_id": "",
      "image_ids": []
    },
    "voice": null,
    "created_at": "<actual ISO 8601 creation timestamp>",
    "updated_at": "<actual ISO 8601 update timestamp>"
  }
}
```

For batches, use `{ "characters": [ { "character_definition": { ... } } ] }` with no app/type/export marker fields.

Keep all image fields blank exactly as shown. The application supplies image
styles, generated image records, ownership ids, and active-image metadata after
import.

### Character Definition Field Contract

Use this contract when creating final EmberAdventures character definitions. The local, imported, exported, and public character definition is one shared shape. A player, party character, future character, and inspected NPC all use this same character definition. Do not add a `kind`, `entity_kind`, wrapper role, or name tag to distinguish them. Story/runtime placement decides how the character is used.

#### Top-Level Rule

The final character definition object is `character_definition`. It stores immutable/default character data only. Do not store current playthrough state here, including current location, current scene membership, current image inclusion, generated profile image history, post-play relationship changes, post-play arousal, death state, inspection state, invite state, or party/NPC/player placement.

Final local import/export files must wrap the reusable definition body as `character_definition`. Do not output or preserve old `character` wrapper files when updating checked-in content. If an old file is encountered, migrate the wrapper to `character_definition` and keep only clean immutable/default definition fields.

#### Field Purpose And Process-Leakage Standard

For every character field, ask:

1. What is this field for in EmberAdventures?
2. How does EmberAdventures use or display it?
3. Does this value serve that purpose?
4. Could it be shorter, clearer, less spoilery, or less like process text?

Do not copy instructions meant for Codex/the character creator into character
fields. Examples of forbidden process leakage:

- `source-faithful`, `current app compatible`, `clean export`;
- `should not appear before X`, `introduce after objective Y`;
- `future party member`, `will become romance partner`, `unlock reward`;
- `do not spoil`, `hide this from the player`, `use in prompt only`;
- field explanations such as `this is the active outfit` or `used by image gen`.

Apply those instructions through the story structure, future-cast conditions,
objective rewards, or hidden notes. Character fields themselves should describe
the character: identity, body, outfit presets, starting/default state, starting
inventory, and durable facts.

#### Field Rules

- `version`: Character definition schema version. Use `1` unless the app contract is explicitly updated.

- `id`: Stable character id string. Use a readable slug such as `"akane-fujimori"` or `"character-akane-fujimori"` according to the local file/library convention. Do not use random garbage when a readable stable id can be created from the character name.

- `name`: The character's exact proper name as shown to the player. For newly generated original characters, use a first and last name by default unless the user explicitly specified a one-word/nonstandard name or the setting strongly requires it. Preserve existing/manual names exactly. Do not append tags such as `(adult)`, `(loli)`, `(NPC)`, `(party)`, source names, roles, or version labels. Example valid: `"Lira Puddlewick"`. Example invalid: `"Lira Puddlewick (adult)"`.

- `source`: Source label for the character. For original characters, use `"Player"`. For source/canon characters, use the proper source title. Do not use this for creator attribution, species, role, or story placement.

- `creation_tool`: Tool/model label used to create or finalize the entry. Use a factual final readable string in the form `"<tool> <model> (<reasoning level>)"` when those parts are available. Do not copy a model label from an example. Do not leave null.

- `loli`: Boolean true or false. `true` means either the character is under 18 or the character is 18+ but looks under age. Create paired accurate/loli and adult-looking versions only when the user requests paired variants or the stored preferences explicitly require them. When paired, they share the exact same `name`; only `loli`, `age`, and age-appropriate physical description should differ. Do not add `(loli)`, `(adult)`, or similar tags to the name.

- `nsfw`: Boolean true or false. `true` means the character definition itself is
  inherently explicit/NSFW as a standalone public-library entry. Do not set true
  merely because the character is adult, attractive, romance-capable, or could be
  used in a later NSFW playthrough. SFW/non-NSFW characters should still be easy
  to use in NSFW playthroughs if runtime settings allow it; they simply do not
  carry an inherent NSFW tag.

- `can_die`: Boolean internal plot armor. Use `false` for standalone character-library definitions by default. Story templates may set `can_die` intentionally for embedded story characters. EmberAdventures hides this field from AI prompts; it is not a personality, lore, or player-facing field.

- `genres`: Approved broad genre/search tags for standalone character-library definitions. Do not store this on characters embedded inside story templates; embedded story characters inherit the story's `genres`. Approved values are `anime`, `fantasy`, `sci-fi`, `modern`, `historical`, `romance`, `adventure`, `action`, `comedy`, `drama`, `mystery`, `thriller`, `horror`, `dark`, `cozy`, `slice of life`, `superpower`, `isekai`, `school`, `workplace`, `political`, `war`, `crime`, `mythology`, `supernatural`, `post-apocalyptic`, `western`, `cyberpunk`, `steampunk`, and `harem`.

- `kink_tags`: Optional searchable public-library kink/spicy tags. Use concrete leaf-style phrases that help users find or avoid content, such as `"dominant partners"`, `"magical clothing"`, `"slime partners"`, or `"romantic intimacy"`. Leave empty when no specific kink/search content applies. Do not put broad genres here. Kink tags are metadata for NSFW-capable filtering and adult-appropriate views; do not write explicit kink prose into SFW-safe public descriptions.

- `age`: Age in number of years as an integer. Do not use ranges, words, unknown, approximate text, or decimals. If the character is intended for adult-content use, the non-loli adult version must be 18 or older.

- `gender`: Character gender/anatomy text. Use clear player-facing wording. Preferred default tags for consistency with the app editor are `"female"`, `"male"`, `"non-binary"`, `"trans female"`, `"trans male"`, `"trans non-binary"`, and `"futanari"`. Free text is allowed when those tags do not accurately describe the character. Anatomy-specific futanari wording belongs in sexual preference phrases, not default character gender tags. Do not use this for voice names or relationship roles.

- `role`: General durable description usable as a title, rank, position, profession, specialty, or group/story function. Examples: `"guild registrar"`, `"front-line bruiser"`, `"healer"`, `"merchant queen"`, `"runaway noble"`. Do not write current mood, current pose, or temporary scene action here.

- `personality_description`: Durable personality and behavior summary. Describe how the character tends to think, act, flirt, fight, negotiate, or handle pressure. Do not use only a list of kinks or current emotions. Avoid plot spoilers unless the character definition is allowed to contain them and they will be hidden from normal prompts until relevant. For player-character definitions, describe starting identity/tendencies without scripting future choices, consent, morality, relationship outcomes, or actions beyond the unavoidable starting premise.

- `speech_style`: Durable dialogue behavior. Write one concise sentence describing how the character usually speaks, such as terse, warm, formal, guarded, profane, poetic, blunt, clipped, rambling, teasing, flirtatious, evasive, or emotionally armored. Do not use this for current mood, TTS/voice metadata, visual traits, story instructions, relationship outcomes, or hidden future facts.

- `boldness`: Immutable 1-10 number describing how forward, assertive, sexually/directly expressive, or risk-taking the character tends to be. Numeric `0` and values outside `1-10` are invalid and normalize to the neutral default `5`. A custom string is also valid when the character needs nuance that the scale cannot express. If using a string, write only the behavior description, such as `"cautious flirt; uses compliments, lingering looks, and mild teasing when the scene supports it"`. Never include storage/system wording, effective-value summaries, numeric prefix summaries, or score annotations in the saved field. This is separate from the user's `characterBoldnessOffset` profile setting, which adjusts the maximum effective boldness at runtime.
  - `1`: very reserved; avoids romantic or sexual initiative unless trust and context are very strong.
  - `2`: reserved; shows warmth, shy interest, and subtle attraction before direct flirting.
  - `3`: cautious flirt; uses compliments, lingering looks, and mild teasing when the scene supports it.
  - `4`: friendly flirt; comfortable with banter, playful closeness, and light romantic pressure without pushing hard.
  - `5`: balanced; can openly flirt, tease, touch lightly, or show interest while still acting naturally for the setting.
  - `6`: confident; willingly initiates romantic tension, suggestive comments, and physical closeness when attraction supports it.
  - `7`: bold; frequent teasing, direct attraction, provocative posing, and confident escalation when the player responds positively.
  - `8`: very bold; openly suggestive, eager, and willing to reveal or touch themself if the player keeps watching.
  - `9`: aggressively bold exhibitionist; may expose intimate parts, escalate sexual teasing, and push toward risky displays when context allows and the player does not stop them.
  - `10`: unnaturally aggressive exhibitionist boldness; if the player watches and does not stop them, they will openly expose their chest, keep escalating into visible masturbation and full-body exposure, beg the player to fuck them, orgasm from the display, and eventually give up if rejected.

- `starting_relationship_to_player`: Starting relationship text copied into runtime when a new game/import begins. Examples: `"self"`, `"unknown"`, `"trusted companion"`, `"professional handler"`, `"rival"`, `"romantic partner"`. Do not update this after play; runtime relationship changes belong elsewhere.

- `starting_trust`: Starting trust from 0 to 10. Use a number. `0` means no trust or unknown trust; `10` means complete trust at start. Do not use legacy 0-100 va…13849 tokens truncated…nality phrasing
- inventory items
- known facts
- body language
- relationship wording
- names and name patterns
- jobs/concepts
- species/race mix
- outfits

## Names

Use preference-file naming guidance. In general, names should sound like names unless the user wants comedy or aggressive theme names.

For newly generated original characters, use a first and last name by default unless the user explicitly specifies a one-word/nonstandard name or the concept strongly requires a different naming convention.

Do not rename existing or user-specified characters unless the user asks for edits. Manual/pre-existing names are allowed to be one-word or nonstandard.

For batches, shop stock, auction stock, job-board NPCs, and story-world stock,
use unique surnames unless characters are intentionally related. Do not reuse
surnames from player options, examples, templates, skill references, or
unrelated existing characters. If two characters share a surname, record the
relationship clearly in durable known facts; otherwise rename one before final
export.

## Proposal Format

When proposing original character options before final JSON, follow
`proposal_preferences`. If it is unanswered, use this compact neutral fallback:

```text
Name (race)
Description.
```

Include the race/species parenthetical only when the saved preference requests it or when it materially helps compare concepts. For humans, obey `human_race_detail_preference` rather than always forcing an ethnicity into the proposal.

## Personality

Use preference-file personality and boldness guidance. Make personalities durable and specific, not just current mood or a list of sexual behaviors.

For spicy originals, combine sexuality with identity: job, flaws, humor, fears, habits, principles, contradictions, and social style.

Avoid repetitive boilerplate unless the user explicitly asks for a uniform batch.

## Practical Body And Appearance Guidance

The field contract above defines the schema. This section adds creation guidance
for producing clean image prompts and should not introduce alternate field shapes.

- Body slots describe body only. Do not put clothing, personality, mood, job,
  relationship, pose, or sexual behavior in physical slots.
- Prefer existing numeric 0-10 values for lookup-table body slots when a listed
  value fits. Numeric slots are easier for users to manually edit. Use a custom
  string only when the character has exceptional anatomy that no numeric mapping
  can represent. Calibration notes, stronger wording, concept flavor, and image
  prompting preferences do not justify replacing a usable numeric value.
- Use the embedded physical-attribute phrase list as image-generator-friendly vocabulary.
- `personality_description` owns personality, behavior, motivations,
  temperament, and durable social style only. Do not put body shape, clothing,
  hair, skin, tattoos, scars, horns, pose, or image-prompt visual text in it.
- `speech_style` owns how the character usually talks. Write one concise
  sentence covering rhythm, formality, bluntness, warmth, guardedness, profanity,
  humor, flirtation, or similar dialogue behavior. Do not put current emotions,
  story instructions, TTS/voice metadata, or visual traits in it.
- `species`, `race`, and `ancestry` own biological/source identity only.
- `skin_color`, `eye_color`, `hair_color`, `hair_length`, and `hair_type` own
  only those exact traits.
- `extra_description` owns concrete durable visual traits that do not fit another specific appearance field, including horns, claws, fangs, ordinary tails, wings, extra eyes, unusual ears, nonhuman hands, tattoos, scars, birthmarks, body paint, facial markings, body markings, or a concise species trait that cannot be expressed by one numeric field. Replacement nonhuman lower-body anatomy belongs in `extra_description_lower_body`, not here. It is a remainder field, not a second full-body description.
- Do not duplicate specific appearance fields inside `appearance.extra_description`. The game already converts numeric/string fields such as `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, `arms`, hair, eyes, and skin into image-prompt text. While drafting `extra_description`, compare every phrase against those fields and remove duplicated breast size, bust silhouette, abs/stomach definition, shoulder width, arm muscle, hip width, leg length, height, muscularity, hair, skin, and eyes. Bad examples: `thin adult body`, `large breasts`, `wide hips`, `defined abs`, or `long legs` when those are already in numeric/body fields. After the final character JSON is assembled, do one final appearance pass and clean `extra_description` again. If nothing unique remains, set it to `""`.
- Do not use filler `extra_description` prose such as `Attractive adult [race/species] with a distinctive silhouette`, `expressive face`, `design cues tied to her work as...`, or `[race/species] traits shaped around...`. Those phrases are not concrete visual traits and usually duplicate `race`, `role`, body fields, or personality. Write only specific durable visuals that the other fields cannot express, such as scars, tattoos, horns, tails, wings, markings, ports, unusual anatomy, or similar.
- Do not paste prose-first body-design notes into `extra_description`, mention the character by name, use narrative pronouns, describe posture or current state, or explain a visual trait through profession/history. Prefer a compact list of visible leftovers. Before export, preview the fully assembled image prompt and reject `extra_description` if it repeats structured prompt phrases or reads like a character-sheet paragraph.
- For exaggerated features, use direct graphic description language when needed for accurate image output.
- Manual characters may use the full valid 0-10 range when appropriate.
- When the preference file contains a numeric or calibrated body range, final character body fields must explicitly match that scale. Do not rely on vague words like "huge", "massive", or "defined" if the user has calibrated the scale with concrete anchors.
- For clothed characters, use the normal female chest phrase and append `fully covered by the described clothing` when structured upper-body clothing is present. Do not invent a separate clothed scale.
- If the user supplies a concrete anchor such as "8 equals full watermelon-sized per breast", use it to calibrate and select the numeric value `8`. Keep the final mapped body field numeric. Put genuinely additional unmapped anatomy in `extra_description`; do not repeat the mapped trait there.
- If the user prefers impossible anatomy, state it directly and visually, e.g. "more visible ab blocks than realistic human anatomy", rather than just "defined abs".
- Keep species/race anatomy consistent and visually useful.

### Image Prompt Projection Contract

Character files store facts; EmberAdventures decides what is visible for each image request. Authors must keep the structured facts complete rather than pre-composing a final image prompt.

- Profile portraits are framed from the top of the head through the waist. They include shoulders, chest, stomach, waist, arms, durable upper-body traits, and the visible upper clothing subset. They omit hips, legs, `extra_description_lower_body`, and genital-placement wording.
- Normal/full-body and group prompts include `extra_description_lower_body` whenever it is authored and the selected framing includes the lower body. It may describe lower-only markings or unusual humanoid details while `nonhuman_lower_body` is false, or the complete replacement anatomy while the flag is true.
- When `nonhuman_lower_body` is true, generic numeric hips and legs are omitted from image prompts. Other body fields and all authored clothing remain available.
- Adult NSFW prompts may describe anatomy at the humanoid-to-nonhuman body junction. Male and futa/futanari characters use penis wording; female non-futa characters use vulva/feminine-contour wording; unspecified characters use neutral anatomy/contour wording. Covered prompts describe only a covered contour. Genital placement never dictates softness, erection, or arousal state.
- Futa/futanari identity must be represented in structured `gender`, tags, kink tags, or sexual-preference metadata. Do not hide it only in role or free-form appearance prose.
- Age wording is deterministic: known ages 18 or older are described as `{age}-year-old adult`; known younger ages use the numeric age without `adult`; missing/invalid ages default to adult unless the definition is explicitly minor-marked, in which case image generation is forced SFW.
- Clothing prompt order is: `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `bra`, `undershirt`, `shirt`, `over_shirt`, `coat`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `underwear`, `pants`, `skirt`, `legwear`, `socks`, `feet`, `other_accessory`.

## Practical Clothing And Items Guidance

The field contract above defines the schema. This section adds workflow and
image-prompt guidance without adding alternate clothing fields.

- Clothing slots are precise item slots. Do not write ambiguous values like "adventuring outfit or maid clothes depending on scene."
- Create one or more precise outfit presets according to the request and saved wardrobe preferences. Never collapse multiple requested looks into one ambiguous outfit.
- Treat clothing like inventory/equipment slots.
  Characters created for Codex-version stories, story shops, auction stock, job
  boards, or generated NPC pools still use the same outfit system; do not move
  removable garments into prose fields just because the character is embedded
  inside a Codex story packet.
- During preference intake, ask what default outfit guidance should be saved for original characters. Offer options such as:
  - `0. You decide how many outfits based on the character`
  - `1. Make 1 normal outfit only unless I ask for more`
  - `2. Make 10 outfits for every character`
  - `3. Make a fixed wardrobe pattern, such as 1 normal, 1 formal, 1 casual, 1 sexy, 1 swimsuit, 1 cosplay, and variants`
  - `4. Free answer`
- Save the answer in `clothing_and_style.outfit_count_guidance`, `default_outfit_plan`, `normal_outfit_count`, `sexual_outfit_count`, `required_outfit_types`, `disallowed_outfit_types`, and `sexual_outfit_notes` as applicable. Use those saved preferences when the user asks for original characters unless the current request overrides them.
- Clothing slots are only for worn/removable items. Do not put tattoos, scars,
  birthmarks, body paint, facial markings, horns, claws, fangs, tails, wings,
  skin color, hair, eyes, body shape, anatomy, or other physical traits in any
  clothing slot, including `other_accessory`.
- If a physical feature is visible because of the outfit, keep the outfit in
  `clothing` and place the physical feature in `appearance.extra_description`.
- Fill every garment the character actually wears in each preset, including
  ordinary underlayers. A coat-only, dress-only, armor-only, or shirt-and-pants
  definition is incomplete when the intended character also wears underwear,
  a bra, undershirt, socks, or other removable layers. Omit a layer only when
  the character intentionally is not wearing it in that outfit.
- Use `starting_inventory`, `durable_known_facts`, and `starting_held_items` to make the character concrete and usable in game. Keep image metadata blank.
- Clothing slots strongly influence EmberAdventures image generation. Do not put lingerie-coded items in `bra`, `underwear`, `shirt`, `skirt`, or `back` unless the intended outfit is skimpy.
- If the user wants a dressed character, avoid values like `thong`, `bikini`, `bra top`, `skirt panels`, `plunging bodice`, or `cape over lingerie`. Use full garments such as tunic, robe, coat, dress, armor, pants, shorts, bodysuit, mantle, apron, or layered wraps.
- Negative image prompt wording cannot reliably overcome skimpy clothing slots. Fix the clothing slots first.
- For sexy-but-dressed characters, show appeal through fit, silhouette, material tension, posture, and selective exposure rather than defaulting to near-nudity.
- EmberAdventures's prompt builder checks top and bottom clothing coverage separately. If a one-piece garment covers the groin, hips, or legs, it must have a normal top/body slot entry and also a bottom-slot coverage entry. Otherwise the generated prompt may infer a naked bottom. Do not duplicate the whole garment description in both slots; put the main garment in the top/body slot, then use the bottom slot for concise lower-body coverage, length, or continuation information.
  - Fishnet teddy example: `shirt`: `"one-piece black fishnet teddy bodysuit"` and `underwear`: `"same teddy covers her groin with a high-cut panty shape"`.
  - Dress example: `shirt`: `"cute wine-red wrap dress with a soft neckline and short flutter sleeves"` and `skirt`: `"same wrap dress falls to mid-thigh"`.
  - Catsuit example: `shirt`: `"one-piece black latex catsuit with a front zipper"` and `pants`: `"same catsuit continues over her hips and legs to the ankles"`.

## Workflow Modes

Default workflow:

- Read preferences.
- Ask only missing or ambiguous preferences relevant to the request.
- Infer the rest from preferences and the prompt.
- Propose a few suitable options.
- Let the user review, select, request changes, or request more options.
- Create the final character after approval/selection.
- After user feedback, distinguish general preference updates from character-specific revisions.

Do not ask a standalone workflow-mode question during initial setup. Explain the default proposal-review-approval workflow in the main setup message and tell the user they can propose a different workflow if they dislike it. Save any user-provided override to preferences and obey it; direct creation is valid when the saved preference or current request asks for it.

If the user asks for proposed changes before editing, list exact planned changes with old value -> new value and wait for approval before editing.

## Final Deterministic Validation

Before returning any character file, validate every entry in the batch using
this checklist. Do not call an entry finished until all checks pass:

1. The export wrapper is correct: one definition uses `character_definition`; a
   batch uses `characters[]` containing those wrappers; no app/type/export
   marker fields are present.
2. Required metadata exists and is valid: `source` is non-null, original
   entries use `"Player"`, `creation_tool` is factual rather than copied from
   an example, `genres` is approved where required, and `nsfw`, `loli`, and
   `can_die` are booleans.
3. `version` is numeric, `id` is stable, `name` is a proper display name, and
   `age` is an integer. Paired loli/adult entries are created only when
   requested or required by saved preferences, and both keep the same plain
   name without variant suffixes.
4. `boldness` is either a number from 1 to 10 or a non-empty descriptive
   string. Numeric `0` and all other out-of-range numeric values are rejected.
   Text boldness contains behavior only and does not contain score annotations.
5. `voice` is exactly `null`; no inferred or invented TTS metadata is present.
6. `created_at` and `updated_at` are real ISO 8601 timestamps. Existing
   `created_at` is preserved; `updated_at` changes only when the definition
   changes.
7. `outfits` is a non-empty array, every outfit has a unique stable `id` and
   coherent clothing object, and `starting_outfit_id` matches an outfit id.
   Every outfit includes all intended visible and inner clothing layers.
   `active_outfit_id` and other runtime clothing fields are absent.
8. Body fields contain body information only, `extra_description` contains
   only additional durable visuals, and no appearance fact is duplicated across
   body, hair/skin/eye, extra-description, personality, or clothing fields. The
   final assembled image prompt has been reviewed, and `extra_description` is a
   concise remainder rather than copied body-design prose or narrative text.
   `nonhuman_lower_body` is a real boolean; when true,
   `extra_description_lower_body` contains a concise concrete replacement-body
   description and does not repeat numeric hips or legs. When false, the lower
   description is either blank or contains only a concrete humanoid lower-body
   detail that does not belong in another structured field.
9. All image metadata is blank exactly as shown in the canonical example:
   no image ids, URLs, prompts, styles, ownership, or invented image data is
   present; `default_profile_image.source` is `"none"`; `seed_enabled` is
   `true`; and both exported `negative` fields are present but empty.
10. Reusable definitions contain no current relationship/state/location,
   active outfit, current inventory, current known facts, scene membership,
   inspection, invite, death, or image-inclusion fields.
11. The entry contains no hidden process instructions, future unlock notes,
    story spoilers, or creator workflow text in player-visible character fields.
12. Batch names, ids, surnames, jobs, facts, personality wording, body language,
    inventory, and outfits are checked against the relevant existing library
    and against all entries in the current batch for accidental repetition.
13. Lookup-table body fields use numeric 0-10 values unless a documented
    exceptional anatomy cannot be represented by the scale. Waist progresses
    from impossibly tiny at 0 through average at 5 to massive at 10; chest is
    not treated differently from the other mapped body fields.
14. `creator`, `creator_id`, `short_description`, `creator_notes`,
    `character_version`, `consent_state`, and all other forbidden or obsolete
    fields are absent.

## Library Maintenance

When asked to maintain an original character library, support:

- metadata repair
- schema validation
- duplicate detection
- repetitive phrasing cleanup
- source/creation_tool/genres/nsfw/loli/can_die backfill
- style consistency
- race/species balance review
- relationship/default-state consistency
- moving rejected entries aside without deleting unless asked


## Story Shop / Job Board Characters

When this skill is used to create characters for an EmberAdventures story shop, job
board, slave market, companion shop, auction, guild counter, or generated-job
role pool, create full normal character definitions. Do not output placeholder
labels such as `shopkeeper`, `worried baker`, `guild clerk`, or `slave girl`.
Owners, clients, witnesses, rivals, purchasable characters, and talkable shop
characters need real names, roles, personalities, speech styles, outfits,
appearance, and durable facts. The story skill should reference these
definitions from `future_cast`/NPC placement instead of duplicating them inside
shop item records.

For large-shop-stock mode, distinguish depth tiers:

- major/fixed story companions and important shop owners need full character
  depth, usually 6-10 concrete durable facts;
- ordinary purchasable/talkable stock characters should be compact but
  playable, usually 3-5 concrete durable facts plus a specific role, species or
  race, appearance, outfit, personality, speech style, intended shop/stock
  category, unlock requirement when known, and a post-purchase or
  post-introduction hook;
- generated job-role NPCs such as recurring bakers, clerks, witnesses, or
  rivals can be shorter, but still need a proper name, real appearance, outfit,
  personality, speech style, and one reusable job-scene hook.

Do not make hundreds of stock characters main-character-length, but also do not
make them anonymous archetypes. They must be distinct enough that the player can
inspect, talk to, buy/recruit, remember, and use them in scenes.
