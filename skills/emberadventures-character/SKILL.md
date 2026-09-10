---
name: emberadventures-character
description: Authoritative base skill for EmberAdventures character definitions. Use directly for characters, preference intake, proposals, character JSON creation, review, repair, and library maintenance.
---

## Skill Maintenance

This section is for guidance on maintaining/updating this skill, and is not applicable when just using the skill.

This skill is for only character information. Do not mention anything that is only related to character definitions when they are in story files. All differences between this skill (standalone characters) and story-embedded characters must be described in the story file.  Do not talk about it at all in this skill. This skill is for creating standalone characters. Story embeded characters are created with this skill as well, but then need to be modified to fit into the story.  The story file is the authoritative source for story-embedded characters, and this skill is the authoritative source for standalone characters.

## Version and Update Check

Current skill version: `1.0.33`.

Before using this skill, compare the installed version with the authoritative
GitHub version file. If the installed version is older, ask for permission to
download the new version. Only continue with the current version if the user
says to use the current version. Not updating will very likely cause the created
character to be invalid and fail to import, so always recommend updating to the
latest version before creating or editing characters.

The authoritative GitHub version file is:

https://raw.githubusercontent.com/andro951/ember-adventures-tools/main/skills/emberadventures-character-version.md

The GitHub skill file is:
https://raw.githubusercontent.com/andro951/ember-adventures-tools/main/skills/emberadventures-character/SKILL.md

## Model Quality Recommendation

Before working on the character json file, if the current model and
reasoning/intelligence/effort level are known to be below 5.6 Terra Medium, tell the
creator that 5.6 Terra Medium or higher is recommended and will likely produce a better
character. 5.6 Sol High is likely the best option for the highest quality results. Going
higher than High effort is unlikely to produce significantly better results, and is waistful
for the user's paid usage. If higher than High effort, strongly suggest to reduce to High
effort. This is a quality recommendation, not a hard gate; character creation should still
work on lower models unless the output is visibly invalid.

## Character Schema And Rules

This skill must be shareable as a standalone skill. Do not depend on any shared EmberAdventures reference files at runtime. The only external file this skill should require is the optional private preference file described in this skill.

If you are not aware of the user's preference file, and the user has not explicitly told you they don't want one, the first step of using this skill is asking the user if they want to create a private preference file to use when creating characters so that created characters will match their prefernces.

### Required Metadata

Every standalone character-library definition must include non-null `source`,
`creation_tool`, approved `genres`, boolean `nsfw`, boolean `loli`, and boolean
`can_die`. Original characters use `source: "Original"`; `creation_tool` records
the actual tool/model/reasoning label. `genres` belongs on standalone library
exports, not story-embedded definitions. `kink_tags` is optional searchable
metadata only for standalone library definitions; story-embedded definitions,
future-cast shells, and future-cast `full_character` definitions must omit it.
Use `can_die: false` by default for standalone definitions. The field
contract below is authoritative for meanings, allowed shapes, and runtime-field
exclusions. Do not emit `creator` or `creator_id`; EmberAdventures assigns
creator ownership during import. This is an internal maintenance rule: never
add creator fields back to this skill, never show them in examples, and never
ask the user for a creator name or alias during preference intake.

### Character Export Shape

The field contract below is authoritative. Keep the example and contract synchronized; there are no exception rules for older examples.

Use `character_definition` as the single immutable/default character object. Do
not use other top level fields. Story/runtime placement decides whether this
definition becomes a player, party character, future character, or inspected NPC.
For creating batches of characters, use a characters array as shown below, or make a separate file for each character. Do not add any other top level fields to the export. Ask the user if they want seperate files or 1 file with all characters in it when creating multiple at once. The game is capable of importing either, but for batches, it will import all of them, so a batch file should only be created if it's intended to import all of them into the game together.
```json
{
  "characters": [
    {
      "character_definition": {
        ...
      }
    }
  ]
}```

Before final export, run a field-purpose and process-leakage pass. For every
field, ask what the field is for, how EmberAdventures uses/displays it, whether the
value serves that purpose, and whether it can be clearer or or match the intended use better.
Character information should never mention how the character will be or how it will change in
the future. Character definitions are meant to be a snapshot of a character in a specific
point in time. You should describe them exactly as they are at that moment, and you can also
include include the backstory/history of that character. The only future related information
that is allowed is future asperations, desires, and goals.

Before final export, run a character-depth pass. A final character definition
must be useful in EmberAdventures, not just technically valid. Characters should have
concrete `starting_known_facts` covering identity, role, personality under pressure,
combat/usefulness or social usefulness, household/social role when relevant, quirks/preferences,
and relationship dynamics.

Before final export, run the standalone release pass. Do not assume an
EmberAdventures maintainer or a later main thread will repair the character after
output. If schema fields are questionable, metadata is missing, durable facts
are generic, outfit slots are incomplete, or the character concept is underdeveloped,
fix it before final output or clearly ask the user for the missing decision.

If creating a batch of characters, or if there is a known library of existing characters, run a duplicate-name-and-id validation pass where you make sure that there are no exact matches for character names. If there is an exact name match, or if the newly created character has only a first name and it matches an existing first name, a new name should be chosen. If a last name matches an existing character, it should be changed unless the two characters sharing a last name (being related) is intended.

The timestamp strings in the example below are documentation placeholders
only. Replace them with real ISO 8601 timestamps in every final file.

```json
{
  "character_definition": {
    "version": 1,
    "id": "character-name",
    "name": "Character Name",
    "source": "Original",
    "creation_tool": "<Tool> <Model Number> (<Reasoning or Intelligence Level>)",
    "catalog_hook": "A concise, spoiler-free reason to start a game with this character.",
    "default_image_background": "a candlelit apothecary lined with dried herbs and glass bottles",
    "genres": ["fantasy"],
    "kink_tags": ["optional searchable kink tag"],
    "nsfw": false,
    "loli": false,
    "can_die": false,
    "romanceable": true,
    "gender": "female",
    "fallback_name": "Fallback Name",
    "fallback_outfits": [
      {
        "id": "default",
        "name": "Default",
        "nsfw": false,
        "clothing": {
          "hat": "hat",
          "hair_accessory": "hair accessory",
          "face": "face",
          "ears": "ears",
          "neck": "neck",
          "shoulders": "shoulders",
          "bra": "bra",
          "undershirt": "undershirt",
          "shirt": "shirt",
          "over_shirt": "over shirt",
          "coat": "coat",
          "back": "back",
          "hands": "hands",
          "right_wrist": "right wrist",
          "left_wrist": "left wrist",
          "right_fingers": "right fingers",
          "left_fingers": "left fingers",
          "waist": "waist",
          "belt_accessory": "belt accessory",
          "underwear": "underwear",
          "pants": "pants",
          "skirt": "skirt",
          "legwear": "legwear",
          "socks": "socks",
          "feet": "feet",
          "other_accessory": "other accessory"
        }
      }
    ],
    "fallback_starting_outfit_id": "default",
    "age": 25,
    "role": "Short role",
    "personality_description": "Durable personality and behavior summary.",
    "speech_style": "Concise durable dialogue style.",
    "boldness": 5,
    "starting_relationship_to_player": "none",
    "starting_trust": 0,
    "starting_attraction": 0,
    "starting_affection": 0,
    "starting_arousal": 0,
    "starting_state_of_mind": "",
    "starting_physical_state": "",
    "starting_pose": "",
    "appearance": {
      "species": "complete species identity, including meaningful subtype or qualifier",
      "height": 10,
      "shoulder_width": 10,
      "chest": 13,
      "upper_body_build": 8,
      "midsection_build": 8,
      "hip_width": 10,
      "butt_build": 8,
      "lower_body_build": 8,
      "arm_length": 10,
      "leg_length": 10,
      "penis_size": 10,
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
        "nsfw": false,
        "clothing": {
          "hat": "hat",
          "hair_accessory": "hair accessory",
          "face": "face",
          "ears": "ears",
          "neck": "neck",
          "shoulders": "shoulders",
          "bra": "bra",
          "undershirt": "undershirt",
          "shirt": "shirt",
          "over_shirt": "over shirt",
          "coat": "coat",
          "back": "back",
          "hands": "hands",
          "right_wrist": "right wrist",
          "left_wrist": "left wrist",
          "right_fingers": "right fingers",
          "left_fingers": "left fingers",
          "waist": "waist",
          "belt_accessory": "belt accessory",
          "underwear": "underwear",
          "pants": "pants",
          "skirt": "skirt",
          "legwear": "legwear",
          "socks": "socks",
          "feet": "feet",
          "other_accessory": "other accessory"
        }
      }
    ],
    "starting_outfit_id": "default",
    "starting_held_items": {
      "right_hand": null,
      "left_hand": null
    },
    "starting_inventory": [],
    "starting_known_facts": [],
    "starting_nsfw_known_facts": [],
    "chat_story": "",
    "chat_opening_message": "",
    "chat_starting_location": {
      "label": "",
      "place": "",
      "activity": ""
    },
    "chat_story_template": null,
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
      "note": "",
      "male": false
    },
    "profile_image_presentations": {
      "male": {
        "url": "",
        "local_image_id": "",
        "source": "none",
        "seed": null,
        "prompt": "",
        "negative_prompt": "",
        "note": "",
        "male": true
      },
      "non_male": {
        "url": "",
        "local_image_id": "",
        "source": "none",
        "seed": null,
        "prompt": "",
        "negative_prompt": "",
        "note": "",
        "male": false
      }
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

Keep all image and voice fields blank exactly as shown. The application supplies image
styles, generated image records, ownership ids, voices, and active-image metadata after
import. All of these top level fields should be exactly the same as the example above:
"default_seed",
"image_prompt_config",
"default_profile_image",
"profile_image_presentations",
"profile_images",
"images",
"voice"

### Character Definition Field Contract

Use this contract when creating EmberAdventures character definitions. Do not add
fields that are absent from the example and field rules. Standalone library
characters and characters embedded in stories intentionally use different
subsets of this contract.

#### Standalone And Story-Embedded Fields

The complete export example is a standalone character-library definition.
Standalone definitions own their public discovery metadata and optional
character-launcher experiences.

The following fields are standalone-only and must be omitted from every
story-embedded character definition, including players, party characters, NPC
shells and `full_character` definitions, and future-cast shells and
`full_character` definitions:

- `catalog_hook`
- `default_image_background`
- `genres`
- `kink_tags`
- `chat_story`
- `chat_opening_message`
- `chat_starting_location`
- `chat_story_template`

Story-embedded characters inherit discovery and classification from the story.
A story uses its own title, description, opening, state, and objectives; it
never carries a nested standalone Chat launcher on one of its characters. This
also prevents recursive stories inside stories. All other approved authored
character fields follow their normal rules in both contexts unless a later rule
explicitly says otherwise. Runtime-only fields remain forbidden in both.

#### Field Purpose And Process-Leakage Standard

For every character field, ask:

1. What is this field for in EmberAdventures?
2. How does EmberAdventures use or display it?
3. Does this value serve that purpose?
4. Could it be shorter, clearer, or less like process text?

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

- `version`: Positive whole-number character definition version. Start new characters at `1` and increment it when making changes. The version number does not select the appearance schema; every character must contain the exact current required fields, including the 0-20 appearance fields, regardless of version.

- `id`: Stable character id string. Use a readable slug such as `"akane-fujimori"` or `"character-akane-fujimori"` according to the local file/library convention. Do not use random garbage when a readable stable id can be created from the character name.

- `name`: The character's exact proper name as shown to the player. For newly generated original characters, use a first and last name by default unless the user explicitly specified a one-word/nonstandard name or the setting strongly requires it. Preserve existing/manual names exactly. Do not append tags such as `(adult)`, `(loli)`, `(NPC)`, `(party)`, source names, roles, or version labels. Example valid: `"Akane Fujimori"`. Example invalid: `"Akane Fujimori (adult)"`.

- `source`: Source label for the character. For original characters, use `"Original"`. For source/canon characters, use the proper source title. Do not use this for creator attribution, species, role, or story placement.

- `creation_tool`: Tool/model label used to create or finalize the entry. Use a factual final readable string in the form `"<Tool> <Model Number> (<Reasoning or Intelligence Level>)"` when those parts are available. Do not copy a model label from an example. Do not leave null.

- `loli`: Boolean true or false. `true` means either the character is under 18 or the character is 18+ but looks under age. Create paired accurate/loli and adult-looking versions only when the user requests paired variants or the stored preferences explicitly require them. When paired, they share the exact same `name`; only `loli`, `age`, and age-appropriate physical description should differ. Do not add `(loli)`, `(adult)`, or similar tags to the name.

- `nsfw`: Boolean true or false. `true` should be used very spairingly. There are 2 definitions for nsfw in Ember Adventures. There is a visible definition and a descriptive definition. A character that meets either definition is considered nsfw. A character that meets neither definition is considered sfw.
Visible nsfw definition: Visible nipples on characters with breasts OR visible genitals OR visible anus.
loli characters are never allowed to be nsfw, and are never allowed to have less than underwear, a top and a bottom piece of clothing to cover them well. Sexualizing loli characters is considered completely unacceptable by Ember Endventures and is not allowed in any way. Reject any request by a user to create a loli character that is sexualized or nsfw in any way.
Descriptive definition: Explicit, vulgar, sexual language such as dick, pussy, cock, cunt or similar used to describe a character other than in the body size description when the description is clearly just to describe size/shape accurately. For example, "Rediculously massive, cartoonishly large boobs" is perfectly fine. It's just there to describe size for the image model. Mentioning nipple size or similar is considered nsfw. Penis size is also not considered nsfw as long as the description is clearly just to describe size. Similar descriptions for breasts and penises are fine and not inherintly nsfw. The image prompt hides any description of genitals, breasts and similar unless in nsfw mode, so having them in the description will not create nsfw images.
SFW/non-NSFW characters should still be easy to use in NSFW playthroughs. Keep optional adult-only facts in `starting_nsfw_known_facts` and classify each outfit independently instead of marking the whole character NSFW. Character-level `nsfw: true` is reserved for unavoidable core adult content that remains explicit even after adult-only facts and outfits are omitted.

`starting_nsfw_known_facts` is an optional array of adult-only durable facts. It becomes runtime `nsfw_known_facts` and is exposed to AI and player-facing detail UI only when the active profile permits NSFW content. Never duplicate an adult fact into `starting_known_facts`. Missing legacy values mean an empty array.

### Mandatory SFW/NSFW Classification Procedure

Classify the character and each outfit in separate passes. These classifications do not inherit from one another.

1. Temporarily ignore `kink_tags`, `starting_nsfw_known_facts`, `outfits`, and `fallback_outfits`. Examine only the character's public/core identity fields, including name, role, personality, speech, ordinary facts, appearance, inventory, and default state.
2. Move optional adult-only durable information into `starting_nsfw_known_facts`. An adult fact being moved is evidence that the separation works; it is not evidence that the character is NSFW.
3. Set character-level `nsfw: true` only when explicit adult content remains unavoidable in the core fields after that separation. Record the exact remaining field and phrase that requires `true`. If no exact evidence remains, set `nsfw: false`.
4. Classify every canonical and fallback outfit independently from its own complete clothing and intended presentation. Ignore the character-level flag, adult facts, kink tags, and the classifications of other outfits.
5. Check each starting outfit after classification. A SFW character needs a genuinely SFW starting outfit and at least one SFW outfit in each presentation. Change the starting selection or revise an outfit when necessary; never make the whole character NSFW merely to satisfy this invariant.

The following facts never make a character NSFW by themselves:

- the character has one or many NSFW outfits;
- the character has `starting_nsfw_known_facts` or sexual `kink_tags`;
- the character is flirtatious, seductive, sensual, romantic, attractive, confident, dominant, submissive, a succubus/incubus, or an adult romance option;
- the character has large breasts, a penis-size value, exaggerated body proportions, or other neutral body-shape data;
- the character can participate in NSFW play when an adult profile is active.

Character-level SFW examples include a flirtatious ember demon with optional adult power-dynamic facts, a seductive vampire with lingerie presets, a werewolf whose adult arousal response is isolated in `starting_nsfw_known_facts`, and a shapeshifter with optional voyeurism facts. Character-level NSFW examples include a character whose unavoidable public role or personality explicitly describes sex acts, whose ordinary public facts contain explicit genital or sex-act prose that cannot be separated without changing the concept, or whose core concept requires visible nipples, genitals, or anus outside an optional outfit. When a coherent SFW core remains after adult facts and outfits are hidden, the character is SFW.

Do not manufacture an adult fact merely to populate `starting_nsfw_known_facts`. An empty array is valid. Do not copy one generic adult fact across unrelated characters during a batch.

### Outfit Purpose Test And Borderline Examples

Judge the complete outfit, not isolated keywords. Ask: "Is this primarily clothing for travel, work, combat, ceremony, fashion, swimming, lounging, or sleeping, or is its primary purpose sexual display/fetish presentation?" Attractive styling does not change an ordinary outfit's purpose.

Normally SFW:

- fitted suits, uniforms, armor, workwear, travel clothes, formal gowns, fitted dresses, and fashionable fantasy clothing;
- an open-collar or partially open shirt, including a male bare upper chest;
- ordinary crop tops, miniskirts, high slits, low necklines, corset tops, thigh-high stockings, or garters when the complete outfit is fashion rather than sexual display;
- ordinary opaque bikinis, one-piece swimsuits, swim briefs, sports bras, gym clothing, pajamas, robes, and normal sleepwear;
- sheer sleeves, lace trim, mesh panels, or isolated cutouts that do not expose nipples, genitals, or anus and do not make sexual display the outfit's purpose;
- practical chest/body harnesses used as armor, climbing equipment, weapon support, ritual equipment, or fantasy adventuring gear.

Normally NSFW:

- lingerie intended as erotic display, fishnet teddies, fetishwear, bondage gear, rope harness sets, and sexual latex outfits;
- g-strings, c-strings, minimal chain sets, strategically placed ribbons, or garments designed to cover only nipples/genitals;
- transparent or sheer torso/lower-body garments that expose nipples, genitals, or anus;
- open garments with no meaningful underlayer when the presentation is designed around exposing breasts or genitals;
- hypersexualized cosplay, extreme sling dresses, micro garments, or cutout outfits whose primary purpose is showing as much body as possible;
- a decorative strap harness presented as intimate/fetishwear rather than functional equipment.

Borderline decisions:

- `bikini` is SFW by default; `micro bikini designed to expose as much as possible` is NSFW.
- `black corset dress with a low neckline` can be SFW; `open-cup corset exposing nipples` is NSFW.
- `sheer sleeves over an opaque bodice` is SFW; `transparent bodice exposing breasts` is NSFW.
- `leather battle harness supporting armor` is SFW; `minimal leather fetish harness with garters and no ordinary coverage` is NSFW.
- `nightshirt`, `pajamas`, or an ordinary opaque nightgown is SFW; an erotic negligée or lingerie sleep set is NSFW.
- A bra and underwear listed underneath ordinary outer clothing never make the outfit NSFW. An underwear-only outfit may be SFW when it is ordinary nonsexual changing-room, medical, athletic, or similar presentation; erotic lingerie presentation is NSFW.

Words such as `open`, `fitted`, `short`, `slit`, `sheer`, `corset`, `harness`, `bikini`, `stockings`, `garter`, `lounge`, `sleepwear`, `formal`, `armor`, and `battle` are not automatic classifications. Use the full clothing composition and purpose.

For equivalent canonical/fallback outfits, classifications should normally match because presentation gender does not change purpose. A mismatch requires a concrete clothing difference, such as one version being opaque and the other exposing anatomy. Never classify one presentation as NSFW merely because it contains a bra, skirt, breasts, or feminine construction.

For batch creation, migration, or review, inspect every character and outfit individually. Before finalizing, audit every `nsfw: true` value:

- Character `true`: identify the exact unavoidable core field and phrase.
- Outfit `true`: identify the exact clothing combination or presentation purpose.
- If the explanation is only "the character has adult content," "the outfit is revealing," or a single keyword, the classification is unsupported and must be reconsidered.
- If ordinary formalwear, armor, workwear, travel clothes, swimwear, or sleepwear are broadly becoming NSFW across the batch, stop and redo the outfit-purpose review instead of accepting the pattern.

Every outfit must include `nsfw: true` or `nsfw: false`. Mark an outfit NSFW when its purpose is sexual display, fetish presentation, or exposing as much as possible even if nipples, genitals, and anus remain narrowly covered. Ordinary attractive, fitted, fashionable, swimsuit, or revealing clothing can remain SFW when sexual display is not its primary purpose. A character with `nsfw: false` must have an SFW starting outfit and at least one SFW outfit in both canonical and fallback presentations. Missing outfit classification is a hard import error; never infer it from the character or another outfit.

Loli or under-18 characters must have `nsfw: false`, an empty `starting_nsfw_known_facts`, and only SFW outfits. Reject any request that violates this rule.

- `can_die`: Boolean internal plot armor. Always set this to false for standalone characters.

### Gender flexibility system
Every character is required to have 2 gender presentations. One male and one non-male (usually female). That means that each character has 2 sets of gender related fields. This is the full list of fields that have associated fallbacks for gender swapping:
name -> fallback_name
outfits -> fallback_outfits
starting_outfit_id -> fallback_starting_outfit_id
The character's gender is whatever default gender the character is supposed to be. The point being for someone who is attracted to all genders, the default genders will be shown. For someone who is only attracted to women, all characters will become women by women not changing and all others being gender swapped to female.
`romanceable` determines if the character's gender should match the player's preferred gender(s). There is also a setting that will force all characters to swap to the player's preferred gender(s) regardless of `romanceable`. That is why all characters must have both a male and non-male presentation. Non-binary genders are treated no different as female. trans-male is also considered male. All other genders are considered non-male. When choosing the default gender for a character, it is perfectly acceptable to use a non-binary gender, just make sure you understand what the fallback gender will be (male for all non-binary genders except trans-male). This means that if the character presents as male, it's generally best to use male or trans-male as the gender instead of something like non-binary to prevent confusion.

//TODO: Move to story skill
The goal is for there to be a 40% male, 40% female, 20% futanari split between the DEFAULT genders. This does not mean that you need to designed characters as the default gender. For instance, you can designed 100% of the cast as female, then at the end, swap the default gender and swapping the name, outfits, and starting outfit id with the fallback ones of 60% of the characters to match the desired split without changing anything else about the characters. The point of this is to allow gender flexibility for everyone and to give a good spread of genders for people that are attracted to multiple genders. Futanari characters have an extra field for fallback gender so that they swap to male or female if someone likes male and female but not futanari. To accomplish an even split of 50% male and 50% female when this happens, half of the futanari default gender characters should have a fallback gender of male and the other half female. When making a story, it is probably best to first ignore the 40/40/20 split and apply the split at the very end of story creation only as a gender swap, not modifying the character's identity, personality, appearance, or anything else. It is also perfectly acceptable to have a story ignore the split. Ask the story creator which they want, and explain what they are actually being asked to decide. They are deciding if the genders should be split evenly for people that like multiple genders to have a good balance without affecting the character's identity, personality, appearance, or anything else. The split is only for the default gender and any player who excludes genders would have the character's genders swapped. It is especially important to do this for games that have all 1 gender so that players who like multiple genders can have a spread of genders, not all just one. The default gender should never be swapped for standalone characters (including if the player has story characters duplicated as standalone characters) because the default gender is the character's identity. The split is only for stories, not individual characters. If you were to make a story with 100% women, then do the 40/40/20 split at the end and have all characters as standalone characters, all of the standalone characters should be women.

- `romanceable`: Required boolean. All standalone characters should have romanceable set to true.

//TODO: Move this part of the description to the story skill.
This field's name is slightly less descriptive than what it is used for. Ember Adventures requires all characters to be able to swap genders to whatever gender the player wants. This only affects the character's name, images, and outfits. Everything else stays the same. Male characters us the male presentation. All other genders use the female presentation. `romanceable` is used to determine if this character's gender should be swapped to a gender the player is attracted to. The reason all characters must have both a male and female presentation is that there is a setting to force all characters to swap to a perfered gender, not just the romanceable characters. So `romanceable` is which ones should always swap even if that setting is off. In general, if the character is intended to be a potential romantic/intimate/sexual partner, `romanceable` should be true. But you should probably have at least a few that aren't so that there are some of the other gender in the game so not every single character is one gender. It is used to determine if this character  Use `true` when the character is an intended potential romantic or sexual interest. Use `false` intentionally for plot-only officials, incidental contacts, antagonists, or other characters who should not normally adapt to the player's preferred romantic genders. Most recurring AI-created characters should be romanceable unless their story function gives a concrete reason not to be. Player characters are never gender-adapted from this field.

- `fallback_name`, `fallback_outfits`, and `fallback_starting_outfit_id`: Required atomic opposite male/non-male presentation group for the same character. See "Gender flexibility system" above. Prefer a fallback name that retains at least the first letter, and preferably the first two letters, of the canonical name so the character remains recognizable. A natural, setting-appropriate authored name is more important than preserving letters when that would make the result strained. Fallback outfits must be nonempty and remain recognizable equivalents: preserve each outfit's purpose, colors, equipment, status, and general visual identity while changing only gendered construction, underwear, fit, and similar presentation details unless a larger change is specifically justified. `fallback_starting_outfit_id` must reference one of those outfits. Appearance, personality, facts, relationships, and all other identity fields remain unchanged. Local import and public publishing both reject the character until this group is complete.

- `fallback_gender`: Only required on futanari characters. Use exactly `"male"` or `"female"` to decide which presentation is used when the player's selected preferences include male and female but not futanari. Omit it for non-futanari characters.

//TODO: Move this to story skill
Across a generated cast, split futanari fallback genders evenly so a 40% male / 40% female / 20% futanari base distribution becomes 50/50 when only male and female are preferred.

//TODO: Move this to story skill
When migrating an existing cast into gender-flexible definitions, preserve identity instead of rewriting the character. If an existing female character becomes canonical male, move her original name to `fallback_name`, her original outfits to `fallback_outfits`, and her original starting outfit id to `fallback_starting_outfit_id`; then author a natural canonical male name and equivalent male outfits. If she remains canonical female, preserve her current name and outfits and add the male fallback. If she becomes canonical futanari, preserve the current non-male name and outfits as canonical, add a male fallback name and equivalent outfit set, and distribute `fallback_gender` evenly across the futanari cast. Never change appearance, personality, facts, role, stats, relationships, or inventory merely because the canonical gender presentation changed.

- `genres`: Approved broad genre/search tags for standalone character-library definitions. Approved values are `anime`, `fantasy`, `sci-fi`, `modern`, `historical`, `romance`, `adventure`, `action`, `comedy`, `drama`, `mystery`, `thriller`, `horror`, `dark`, `cozy`, `slice of life`, `superpower`, `isekai`, `school`, `workplace`, `political`, `war`, `crime`, `mythology`, `supernatural`, `post-apocalyptic`, `western`, `cyberpunk`, `steampunk`, and `harem`.

//TODO: Move this to story skill
Do not store `genres` on characters embedded inside story templates; embedded story characters inherit the story's `genres`.

- `kink_tags`: Required for nsfw characters. Optional for SFW characters. Some tags are not appropriate for SFW characters. Use the nsfw descriptions in the nsfw section. This is a closed vocabulary and is separate from player sexual preferences. Every value must exactly match one of the canonical lowercase strings below; these are the only valid options. Do not invent, combine, pluralize, reword, or add tags. Interpret every kink tag from the player's perspective: `dominance` means the player acts dominant, `submission` means the player acts submissive, `owning partners` means the player owns partners, and `being owned` means the player is owned. A character's behavior or preference alone does not justify the opposite player-perspective tag. Use only tags intrinsic to the interaction this standalone character definition supports, and use `[]` when none apply. Do not use vanilla kissing, oral sex, vaginal sex, ordinary romance, tone, body appearance, or broad genres as kink tags.
  - **Power Exchange:** `dominance`, `submission`, `switching`, `owning partners`, `being owned`, `serving partners`, `being served`, `disciplining partners`, `being disciplined`, `punishing partners`, `being punished`, `training partners`, `being trained`, `brat taming`, `being a brat`, `using partners freely`, `being freely used`, `taking control in cnc`, `being overpowered in cnc`, `hypnotizing partners`, `being hypnotized`, `mind controlling partners`, `being mind controlled`, `corrupting partners`, `being corrupted`, `financial domination`, `financial submission`.
  - **Bondage And Restraint:** `bondage`, `binding partners`, `being bound`, `collaring partners`, `wearing a collar`, `leashing partners`, `being leashed`, `gagging partners`, `being gagged`, `blindfolding partners`, `being blindfolded`, `sensory depriving partners`, `being sensory deprived`, `enforcing chastity`, `wearing chastity`, `denying partners orgasms`, `being denied orgasm`, `forcing partners to orgasm`, `being forced to orgasm`.
  - **Impact And Pain:** `spanking partners`, `being spanked`, `slapping partners`, `being slapped`, `whipping partners`, `being whipped`, `flogging partners`, `being flogged`, `paddling partners`, `being paddled`, `caning partners`, `being caned`, `pulling hair`, `having hair pulled`, `biting partners`, `being bitten`, `scratching partners`, `being scratched`, `choking partners`, `being choked`, `sadism`, `masochism`.
  - **Sensation And Edge Play:** `wax play`, `temperature play`, `electrostimulation`, `tickling`, `needle play`, `knife play`, `blood play`.
  - **Psychological And Verbal:** `humiliating partners`, `being humiliated`, `degrading partners`, `being degraded`, `objectifying partners`, `being objectified`, `writing on partners`, `being written on`, `feminizing partners`, `being feminized`, `bimbofying partners`, `being bimbofied`, `praising partners`, `being praised`, `making partners beg`, `being made to beg`, `worshipping partners`, `being worshipped`, `dirty talk`.
  - **Roleplay:** `authority figure roleplay`, `subordinate roleplay`, `medical roleplay`, `pet owner`, `being a pet`, `primal predator`, `primal prey`, `uniforms`, `crossdressing`.
  - **Exposure And Multiple Participants:** `exhibitionism`, `voyeurism`, `public sex`, `group sex`, `participating in gangbangs`, `being gangbanged`, `sharing partners`, `being shared`, `watching partners with others`, `being watched with others`, `cuckolding partners`, `being cuckolded`, `swinging`, `double penetration`.
  - **Sexual Activities:** `penetrating partners anally`, `receiving anal`, `masturbation`, `using toys on partners`, `partners using toys`, `fisting partners`, `being fisted`, `pegging partners`, `being pegged`, `rimming partners`, `being rimmed`, `sitting on partners' faces`, `being facesat`, `giving titjobs`, `receiving titjobs`, `giving thighjobs`, `receiving thighjobs`, `giving creampies`, `receiving creampies`, `cum play`, `squirting`, `lactation`, `breeding partners`, `being bred`, `impregnating partners`, `being impregnated`, `being rough with partners`, `partners being rough`, `clothed sex`.
  - **Fantasy:** `using tentacles`, `receiving tentacles`, `futanari`, `transforming partners`, `being transformed`, `oviposition giving`, `oviposition receiving`.
  - **Fantasy Partners:** `angels`, `demons`, `succubi and incubi`, `vampires`, `werewolves`, `demi-humans`, `anthropomorphic characters`, `monsters`, `aliens`, `androids`, `robots`, `elves`, `dark elves`, `orcs`, `goblins`, `dragons`, `fairies`, `merfolk`, `centaurs`, `minotaurs`, `lamias`, `harpies`, `arachne`, `ghosts`, `undead`, `shapeshifters`, `living dolls`, `golems`, `elementals`, `deities`.
  - **Materials And Clothing:** `latex`, `leather`, `lingerie`.
  - **Fluids And Functions:** `watersports`, `scat`, `spit`, `sweat`, `food play`.

//TODO: Move this to story skill
Do not store `kink_tags` on characters inside story files; embedded story characters inherit the story's `kink_tags`.

- `age`: Age in number of years as an integer. Do not use ranges, words, unknown, approximate text, or decimals. If the character is not marked as loli, it must be 18 or older, no exceptions. All characters under 18 must be marked as loli.

- `gender`: The default gender of the character. Some genders are recognized as exact strings. If the character is one of these recognized genders, write their gender exactly as it appears in this list: `"male"`, `"trans-male"`, `"trans male"`, `"futanari"`, `"futa"`, `"female"`. `"trans-male"` and `"trans male"` are treated identically. `"futanari"` and `"futa"` are treated identically. `"male"` and `"trans-male"` are the only male presenting genders. If the character is intended to be male presenting, you must use one of those two. If the character's gender falls outside the list, use any string that makes sense to describe the gender. It will be treated as female (non-male) by the game engine and it will use gemale presenting language such as breasts. `"futa"` and `"futanari"` identify futanari characters; they use the female mechanics except that they have a penis. Every other value, including female, non-binary, trans female, trans non-binary, and free-text identities, uses the female mechanics bucket. Do not infer gender from `kink_tags`, `tags`, `sexual_preferences`, appearance prose, role, or any other field. Import and publish validation reject exact futa/futanari metadata on a character whose `gender` is not futa or futanari. Do not use this field for voice names or relationship roles.

- `appearance.penis_size`: Required integer from 0 to 20 on every character regardless of gender in case runtime adaptation changes the presentation to male or futanari. Do not set it to 0 merely because the canonical presentation is non-male. Runtime ignores it unless the active presentation is male or futanari. Use the locked mapping in [references/body-scales-0-20.md](references/body-scales-0-20.md).

- `role`: Required short occupational/social label, title, rank, or specialty. Maximum 40 characters, including spaces and punctuation. Do not put responsibilities or background here; put those in `starting_known_facts`. Examples: `"Guild Registrar"`, `"Healer"`, `"Queen"`, `"Assassin"`.

- `personality_description`: Durable personality and behavior summary. Describe how the character tends to think, act, flirt, fight, negotiate, or handle pressure. This is meant as permanent guidance for the player's personality, not temporary mood or state. This field is used by the ai to determine how this character acts and speaks.

- `speech_style`: Durable description of how the character speaks. Describe how the character usually speaks. Do not use this for TTS/voice metadata. This field is used by the ai to determine how this character speaks.

- `boldness`: Required integer from 1 through 10 or a nonempty custom behavioral description. Numeric values must be whole numbers in range; invalid authored values are rejected, not defaulted. Prefer the numeric scale when it fits: profile boldness adjustments apply to numbers. Custom descriptions are used directly and remain unchanged by profile adjustments. Do not include numeric score annotations in custom text or encode a number as a string. Use the same scale for every gender; gender adaptation never changes personality.
  - `1`: very reserved; almost never initiates romance or intimacy and waits for unmistakable mutual interest.
  - `2`: reserved; expresses interest subtly and waits for clear encouragement before initiating.
  - `3`: cautious; may initiate small compliments or mild flirting, then pauses to judge the response.
  - `4`: mildly forward; comfortably initiates light flirting or closeness when the context supports it.
  - `5`: balanced; can initiate direct interest, flirting, invitations, or welcomed physical closeness.
  - `6`: confident; readily initiates romantic tension, invitations, and physical closeness when attraction supports it.
  - `7`: very forward; states attraction directly and actively proposes escalation while watching for a clear response.
  - `8`: highly forward; readily initiates explicit flirting, intimate invitations, or consensual exposure when appropriate.
  - `9`: extremely forward; clearly proposes sexual escalation and communicates desire directly, while waiting for consent before meaningful escalation.
  - `10`: maximum initiative; openly states exactly what they want and proactively creates clear opportunities for consensual escalation, immediately respecting refusal or hesitation.

- `starting_relationship_to_player`: Starting relationship text copied into runtime when a new game/import begins. Examples: `"self"`, `"none"`, `"trusted companion"`, `"professional handler"`, `"rival"`, `"romantic partner"`.

Character, common title and pronoun references: When any text field needs to mention the character definition's own name, pronouns, or the gender specific titles listed below, use the ID-less references below instead of hardcoding the resulting word(s). The enclosing character definition supplies the identity, finalized name, and gender presentation. References may appear only in JSON values, never in JSON keys.

Reference types:

Names:
- Full name: `|[character]|`
  - Example result: `Akane Fujimori`
- First name: `|[character_first]|`
  - Example result: `Akane`

Pronouns:
- Subject pronoun: `|[character_subject_pronoun]|`
  - Male: `he`
  - Non-male: `she`
- Subject-pronoun shorthand: `|[character_pronoun]|`
  - Male: `he`
  - Non-male: `she`
- Object pronoun: `|[character_object_pronoun]|`
  - Male: `him`
  - Non-male: `her`
- Possessive determiner: `|[character_possessive_pronoun]|`
  - Male: `his`
  - Non-male: `her`
  - Use this before a noun, such as `his sword` or `her sword`.
- Independent possessive pronoun: `|[character_independent_possessive_pronoun]|`
  - Male: `his`
  - Non-male: `hers`
  - Use this without a following noun, such as `The sword is his` or `The sword is hers`.
- Reflexive pronoun: `|[character_reflexive_pronoun]|`
  - Male: `himself`
  - Non-male: `herself`

Gendered nouns and titles:
- Person term: `|[character_person_term]|`
  - Male: `man`
  - Non-male: `woman`
- Honorific: `|[character_honorific]|`
  - Male: `Mr.`
  - Non-male: `Ms.`
- Formal address: `|[character_formal_address]|`
  - Male: `sir`
  - Non-male: `ma'am`
- Monarch title: `|[character_monarch_title]|`
  - Male: `king`
  - Non-male: `queen`
- Royal-heir title: `|[character_royal_heir_title]|`
  - Male: `prince`
  - Non-male: `princess`
- Noble title: `|[character_noble_title]|`
  - Male: `lord`
  - Non-male: `lady`
- Spouse term: `|[character_spouse_term]|`
  - Male: `husband`
  - Non-male: `wife`
- Parent term: `|[character_parent_term]|`
  - Male: `father`
  - Non-male: `mother`
- Child term: `|[character_child_term]|`
  - Male: `son`
  - Non-male: `daughter`
- Sibling term: `|[character_sibling_term]|`
  - Male: `brother`
  - Non-male: `sister`
- Uncle/aunt term: `|[character_uncle_aunt_term]|`
  - Male: `uncle`
  - Non-male: `aunt`
- Nephew/niece term: `|[character_nephew_niece_term]|`
  - Male: `nephew`
  - Non-male: `niece`

Capitalization:
- References do not infer capitalization from their position in a sentence.
- Pronouns and gendered terms return lowercase text by default.
- Add `_cap` to the reference name when the resolved word must begin with a capital letter.
- Examples:
  - `|[character_subject_pronoun]|` becomes `he` or `she`.
  - `|[character_subject_pronoun_cap]|` becomes `He` or `She`.
  - `|[character_monarch_title]|` becomes `king` or `queen`.
  - `|[character_monarch_title_cap]|` becomes `King` or `Queen`.
- Full-name and first-name references already preserve the character name's proper capitalization and do not need `_cap`.
- Honorific references already return conventionally capitalized forms such as `Mr.` and `Ms.`.

Presentation-dependent text about another character must be self-contained. Use
`|[M|male text|female text]|`, where `M` or `F` is the default presentation,
the second part is the exact male text, and the third part is the exact
female/non-male text. Example:
`|[M|her brother Aurek Emberlash|her sister Aurelia Emberlash]|`.
If the player's preferences allow only one presentation, use that branch. If
both or neither are selected, use the declared default. The token must contain
exactly two internal `|` separators; both text branches must be non-empty and
must not contain `|`, `|[`, or `]|`.

Player references:
- Player full name: `|[player_name]|`
- Player first name: `|[player_first_name]|`
- Player subject pronoun: `|[player_subject_pronoun]|`
- Player subject-pronoun shorthand: `|[player_pronoun]|`
- Player object pronoun: `|[player_object_pronoun]|`
- Player possessive determiner: `|[player_possessive_pronoun]|`
- Player independent possessive pronoun: `|[player_independent_possessive_pronoun]|`
- Player reflexive pronoun: `|[player_reflexive_pronoun]|`

Player pronoun and gendered-term references follow the same `_cap` rule. For example, `|[player_subject_pronoun_cap]|` becomes `He` or `She`.

- `starting_trust`: Starting trust from 0 to 10. Use a number. `0` means no trust; `10` means complete trust at start.

- `starting_attraction`: Starting attraction from 0 to 10. Use a number. This is initial attraction toward the player/protagonist. It is not an attractiveness score.

- `starting_affection`: Starting affection from 0 to 10. Use a number. This is initial emotional warmth/bond, not current romance progress after play.

- `starting_arousal`: Starting arousal from 0 to 10 for characters/stories where arousal defaults are relevant. Use `null` or omit only for characters where arousal does not apply. Do not store post-play arousal here.

- `starting_state_of_mind`: Initial mood/mental state copied into runtime. Examples: `""`, `"curious"`, `"guarded"`, `"amused"`, `"panicked but focused"`. Used only for text generation.

- `starting_physical_state`: Initial physical condition copied into runtime. Examples: `""`, `"tired"`, `"wounded shoulder"`, `"covered in slime but unharmed"`. Do not use this for clothing or pose. Used for both image and text generation.

- `starting_pose`: Initial body posture or position. Examples: `"standing behind the counter"`, `"leaning against the bar"`, `"kneeling beside a broken crate"`, `"wrists bound together"`. Used for both image and text generation.

#### Appearance

Appearance and outfit fields primarily build image prompts. Describe each body
trait and garment precisely enough to help image generation, including concise
fit, coverage, or worn-appearance details when useful. Keep those descriptions
short, and do not duplicate the same visual information across appearance
fields, outfit slots, pose, or location. Leave a field blank rather than repeat
information that the prompt builder will already include elsewhere.

`appearance` describes the body and persistent visual traits only. Do not put clothing, current pose, current mood, relationship, inventory, or sexual behavior here.

- `species`: The complete concise species identity. Include the base species and every meaningful subtype, subgroup, visual qualifier, or heritage descriptor needed to identify the character, in one field. Examples: `"human"`, `"Black human"`, `"High Elf"`, `"Iron Coast Dwarf"`, and `"Cosmic Ghost"`. Character definitions have no separate race or ancestry fields; do not split one identity across multiple fields. Do not include gender in `species`.

- The body-scale portion of `appearance` contains exactly `height`, `shoulder_width`, `chest`, `upper_body_build`, `midsection_build`, `hip_width`, `butt_build`, `lower_body_build`, `arm_length`, `leg_length`, and `penis_size`. Every field is required and every value is an integer from 0 to 20. Do not author body-scale strings. `chest` uses the presentation-specific male or non-male mapping; the other ten fields use one mapping for every presentation. Read [references/body-scales-0-20.md](references/body-scales-0-20.md) before selecting or validating body values.

- Legacy appearance fields `muscular`, `shoulders`, `stomach`, `hips`, `waist`, `legs`, and `arms` are invalid. Clothing slots with names such as `shoulders` and `waist` are separate garment keys and remain valid.

- `skin_color`, `eye_color`, `hair_color`, `hair_length`, `hair_type`: Permanent, unconditional visual traits only. `hair_type` describes inherent hair type/texture (such as straight, wavy, curly, or tightly coiled), never styling. Keep hair color and length in their own fields. Braids, ponytails, buns, updos, partings, and other styling belong in the outfit's `hair_accessory` slot, not in permanent appearance or `extra_description`. Do not use conditional appearance wording such as "usually," "while working," or "when traveling"; define the relevant outfit instead.
- `skin_color`: Bare color phrase only, for example `"warm medium-deep brown"`. Do not include the word "skin," sentences, cultural context, conditional wording, or unrelated appearance details.

- `extra_description`: Optional remainder field for concrete, durable visual traits that do not fit another appearance field. Examples include `"scar across left collarbone"`, `"transparent mint-green slime body"`, or `"filed canines"`, `"butterfly tatoo on right cheek"`. It is not a general physical-description field. Do not include temporary dirt, arousal, clothing damage, scene effects, personality, mood, pose, health, role, backstory, or explanations of how the character acquired a body type. Do not repeat details already represented by the other appearance fields. For details that are only on the lower body, do not include them here such as `"tatoo on right ancle"`. All lower body specific descriptions belong in `extra_description_lower_body`. Use `""` when there is no distinct extra description needed.

- `male_only_extra_description` and `non_male_only_extra_description`: Optional, narrow appearance-only fields. Missing or `null` means no additional prompt text. Use them only for an important visual feature that genuinely differs between male and non-male presentations and is not represented by another field, primarily optional facial hair for male presentation. Do not use them for a general character description; most appearance belongs in shared fields. Breasts, pecs/chest, genitals, and any other anatomy owned by structured fields are forbidden here. Do not put clothing, pose, scene state, personality, sexual behavior, or instructions in these fields. The engine selects only the field matching the active presentation.

- `nonhuman_lower_body`: Boolean. Use `true` only when ordinary humanoid hips, buttocks, thighs/calves, and legs are replaced by an integrated lower body such as a serpent tail, arachnid body, centaur body, or merfolk tail. Hooves, digitigrade humanoid legs, unusual feet, an ordinary tail, or extra limbs alongside otherwise humanoid legs do not qualify. All eleven numeric body fields remain required for structural validity, but prompt projection suppresses `hip_width`, `butt_build`, `lower_body_build`, and `leg_length` when those traits do not apply. Never invent ordinary legs or glutes to justify the stored numbers.

- `extra_description_lower_body`: Follow the same remainder-field rules as `extra_description`, but include only durable lower-body-specific information. Do not duplicate `extra_description`. When `nonhuman_lower_body` is false, use it only for lower-body markings or unusual details not represented elsewhere. When `nonhuman_lower_body` is true, it owns the complete replacement anatomy and must describe the integrated lower-body structure without referring to suppressed numeric fields. It appears in normal/full-body and group prompts but not profile portraits. Use `""` when no distinct lower-body detail is needed.

When `nonhuman_lower_body` is true, still author every garment the character actually wears. Clothing is independent from body-scale applicability and must not be deleted merely because the anatomy is nonhuman. Put each garment in the most reasonable existing clothing slot.

##### Extra Description Deduplication

This section aplies to infromation in both `extra_description` and `extra_description_lower_body`. Each time it talks about `extra_description`, it also applies to `extra_description_lower_body`.

`extra_description` is only for visual traits that are not already captured elsewhere. Numeric body fields are converted into image-prompt phrases by the game, so repeating those same ideas in `extra_description` creates duplicated prompts and over-emphasized bodies.

When writing `extra_description`:

- First choose/fill the specific appearance fields.
- Then write `extra_description` only for leftover durable visual information that no other field can express.
- Never paste a prose-first body-design summary or complete silhouette description into `extra_description`. Planning prose must be translated into the dedicated fields and then discarded.
- Compare each `extra_description` phrase against every specific appearance field.
- Remove or rewrite phrases that duplicate numeric body fields, including breast size, bust silhouette, abs/stomach definition, shoulder width, arm muscle, hip width, leg length, height, and overall muscularity.
- Remove or rewrite phrases that duplicate skin, eye, hair, or notable-feature fields.
- Remove filler phrases such as `Attractive adult [species] with a distinctive silhouette`, `expressive face`, `design cues tied to her work as...`, or `[species] traits shaped around...`. These are not concrete visual traits and usually duplicate `species`, `role`, or personality.
- Do not write narrative prose using the character's name or pronouns. Do not explain traits with phrases such as `built from years of carrying armor`, `giving her an athletic silhouette`, or `showing the life of a veteran`. Record only the visible result when it is not represented elsewhere.
- Prefer a compact comma-separated list or one short sentence. Length is not a substitute for specificity.
- Keep genuinely additional integrated traits, species anatomy, scars/features not listed elsewhere, unusual proportions that are not represented by one numeric field, or source-faithful visual notes that cannot fit a specific field.
- At the end of character creation, perform a final pass over the whole appearance object and clean `extra_description` again after all numeric/string fields are final. Then assemble or mentally project the complete image prompt and remove any duplicated or prose-heavy fragment before export.

Bad `extra_description` when the specific fields already contain those traits:

```text
Athletic, rugged, and curvy with very broad shoulders, large breasts, deeply defined abs, wide hips, strong thighs, and powerful mechanic arms.
```

If `shoulder_width`, `chest`, `upper_body_build`, `midsection_build`, `hip_width`, `butt_build`, `lower_body_build`, `arm_length`, and `leg_length` already encode those traits, keep only concrete unmapped traits, for example:

```text
Callused palms, old welding burns across both forearms, and a crescent scar below the left eye.
```

If nothing meaningful remains after deduplication, use `""` for `extra_description`.

#### Outfits And Starting Equipment

Outfits are immutable clothing presets stored on the character definition. When starting a game, the active outfit referenced by `starting_outfit_id` is copied into the character's runtime clothing.

- `outfits`: Array of outfit objects. Every character must have at least one outfit. A one-outfit character still needs `outfits: [{ "id": "default", "name": "Default", "clothing": { ... } }]` and `starting_outfit_id: "default"`. Do not replace `outfits` with a single `clothing` object. Do not leave it empty. Animal, monster, spirit, slime, natural-form, or otherwise unclothed characters still need at least one concrete outfit entry. If a character is intentionally naked, include only the underwear slots and have them empty strings, `""`. For non-human or demi-human characters, you can use natural clothing in slots such as a turtle shell for a turtle-human character if desired. Do not invent slots such as `full_body`; unsupported slots will throw an error. Never use `{}` as the clothing object.

- `outfits[]`: Each outfit object is a reusable preset. It should describe one coherent outfit the character can wear, such as travel clothes, a guild uniform, armor, sleepwear, formalwear, casual clothes, work clothes, battle gear, a disguise, or another kind of outfit. Do not create vague outfits like `"whatever fits the scene"` or `"armor or dress depending on mood"`. Do not use non-deterministic wording such as `"White or Black"` or `"could"` or `"roughly"` or `"maybe"`. If a character needs multiple looks, create separate concrete outfit entries. Outfits should include all layers that would actually be in the outfit, not just the outer layer. Underwear shuold be included unless the outfit is intended to not have underwear.

//---Left Off Here---//

- `outfits[].id`: Stable short string id for the outfit inside this character definition. Valid examples: `"default"`, `"travel"`, `"formal"`, `"combat"`, `"guild_uniform"`, `"sleepwear"`, `"festival"`, `"disguise"`. Use lowercase snake_case or another stable simple string. Do not use a full sentence, display-only prose, user-facing description, random generated id, or the outfit's entire clothing list. This id is used by `starting_outfit_id` and runtime outfit switching.

- `outfits[].name`: Player-facing outfit name. Valid examples: `"Default"`, `"Travel Gear"`, `"Guild Uniform"`, `"Formal Dress"`, `"Combat Armor"`, `"Sleepwear"`. This should be readable in UI. Do not put mechanical notes, AI instructions, source spoilers, or conditional logic in the name.

- `outfits[].nsfw`: Required boolean on every newly authored outfit. Use the outfit-purpose test above. This flag controls SFW UI visibility, AI context, equipping, shops, rewards, and image generation; it does not replace character-level `nsfw`.

- Character profile images cannot be uploaded by users. EmberAdventures generates them from the structured definition. Generation is NSFW for an inherently NSFW character; otherwise it follows the exact selected outfit's `nsfw` value. Generated image classification is immutable, and NSFW profile images are unavailable behind a local placeholder in SFW mode.

- `outfits[].clothing`: Object using EmberAdventures clothing slots. Values are item descriptions or `null`. This object should describe the full preset as clearly as possible. Use precise garments/equipment, not broad vibes. Good examples: `"linen travel shirt"`, `"black leather corset"`, `"steel breastplate"`, `"knee-high buckle boots"`, `"silver serpent hairpin"`. Bad examples: `"sexy clothes"`, `"normal outfit"`, `"varies"`, `"whatever she wants"`, `"revealing but tasteful"`, `"armor or maid dress"`.

- Clothing slot keys should be stable equipment/body-wear slots. Canonical slots are `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `bra`, `undershirt`, `shirt`, `over_shirt`, `coat`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `underwear`, `pants`, `skirt`, `legwear`, `socks`, `feet`, and `other_accessory`. Use only slots that make sense. Do not author the legacy `hair` alias; use `hair_accessory`. A missing slot or `null` means nothing is defined for that outfit slot.
- `hair_accessory` is the head/hair presentation slot for hairstyles as well as hair accessories. It does not have to describe a clothing item or physical accessory: `"hair gathered into a loose braid"` is valid. Describe the hairstyle for this outfit unconditionally. Use `hat` for headwear; do not invent a `head`, `hair`, or `hairstyle` field.

- Every outfit must describe the complete set of clothing the character actually wears in that preset, including ordinary inner layers such as underwear, a bra, undershirt, socks, or other garments when appropriate. Do not define only the most visible outer garment. The runtime can remove clothing one piece at a time, so omitted inner layers can make a character become accidentally naked after removing one outer layer. Deliberately minimal, nude, or underwear-only outfits are valid only when that is the actual intended preset.

- Authored `bra` and `underwear` values are intentionally included in image prompts even beneath outer clothing. Do not omit them because they are mostly covered; models can correctly show realistic partial visibility such as a bra strap or waistband. When torso or lower outerwear exists, EmberAdventures lists the outer garments first and describes the corresponding bra or underwear as underneath. When no covering garment exists, the bra or underwear is described as visible clothing. SFW image generation may project a basic opaque bra or underwear only when the corresponding authored slot is empty, and that fallback never changes the saved outfit.

- Use `null` intentionally. `null` means this outfit does not define an item in that clothing slot. It does not mean a character permanently lost that item during play. Temporary removal during spicy scenes belongs to runtime clothing/inventory restore logic, not the outfit definition.

- Do not use outfit definitions to represent nudity caused by current scene action. If a character has an intentionally nude/default nude outfit, that can be a real outfit only when it is a deliberate reusable preset. Otherwise, clothing removed during a scene should be runtime state and should be restorable.

- Keep each outfit internally coherent. If the shirt is formal, the shoes, accessories, and lower-body clothing should usually match. Do not mix unrelated pieces unless the character concept intentionally calls for mismatched clothing and the description makes that clear.

- Keep outfits visually useful for image generation. Clothing fields strongly affect profile and scene images. Put the actual visible garments in the correct slots. Negative prompts cannot reliably fix bad clothing-slot values. If the character should be dressed, avoid accidentally lingerie-coded slots like `"thong"`, `"micro bikini"`, `"bra top"`, `"skirt panels"`, or `"cape over lingerie"` unless that is truly the intended outfit.

- For sexy-but-dressed characters, show appeal through fit, silhouette, material, tailoring, selective exposure, and posture-compatible clothing rather than defaulting to near-nudity. Example valid: `"fitted crimson corset over a white off-shoulder blouse"` plus `"high-waisted black leather breeches"`. Example invalid for a dressed tavern owner: `"black lace bra"` as the visible main top with no shirt unless intentionally dressed that way.

- Multiple outfits should be easy for the player or AI to swap between. If a character has multiple common contexts, add clear outfit presets such as `"default"`, `"combat"`, `"casual"`, `"formal"`, and `"sleepwear"`. Do not create many barely different outfits unless the differences matter. Do not create an outfit that depends on hidden future story knowledge unless the story prompt projection will keep it hidden until relevant.

- `starting_outfit_id`: Outfit id that should be active when the character is first created/imported. It must exactly match one `outfits[].id`. Do not use an outfit name here unless the name and id are identical. Do not leave it blank when `outfits` has entries. If there is only one outfit, `starting_outfit_id` should usually be `"default"`.

- Outfit definitions can be used by AI/runtime outfit swapping later, but the AI should change the active runtime outfit id or runtime clothing, not rewrite the immutable definition. If the AI invents a temporary outfit change in play, that belongs to runtime state unless the player explicitly saves it as a new reusable outfit.

- `starting_held_items`: Object for hand slots at start. Use at least `right_hand` and `left_hand`. Values are item descriptions or `null`. Do not put inventory lists here.

- `starting_inventory`: Array of starting inventory item strings or structured item objects if the item needs metadata. Use examples like `"Coin pouch"` or `{ "name": "Silver key", "note": "Opens the guild side door" }`. Do not store items gained during play here.

- `starting_known_facts`: Array of facts copied into mutable runtime `known_facts` when a new playthrough starts. Use concise strings. This is definition data, not chat history, current scene memory, or a field that changes during play. Avoid future spoilers unless the prompt projection system will hide them until relevant. For public/standalone character definitions, prefer facts safe for library/editor display; put story-only secrets in hidden story objectives, future cast notes, or private prompt projections instead.

- `starting_nsfw_known_facts`: Optional array of adult-only facts copied into runtime `nsfw_known_facts`. Keep it separate from `starting_known_facts`; EmberAdventures exposes it only when the active profile permits NSFW content. Use `[]` when there are no adult-only facts.

- `catalog_hook`: Optional concise, spoiler-free player-facing pitch for the
  standalone character in catalog and discovery UI. Explain why someone would
  want to start a game with this character, usually in one or two sentences.
  Keep it accurate without revealing hidden routes, twists, transformations, or
  endings. It is display metadata, not personality guidance, AI instructions,
  chat context, or a substitute for `chat_story` or
  `chat_story_template.description`. Use `""` when no distinct hook is needed.
  A SFW character's hook must itself be SFW. Omit it from every story-embedded
  character definition.

- `default_image_background`: Optional standalone-character image-setting
  guidance. When present, use a trimmed, nonempty string describing only the
  environment or background that normally suits this character, such as
  `"a candlelit apothecary lined with dried herbs and glass bottles"`. Do not
  put pose, camera, action, anatomy, clothing, or character-description prose
  in this field. EmberAdventures may use it for profile images and other solo
  standalone-character images when no story, scene, location, or explicit user
  setting is authoritative. It never overrides an explicit setting and does
  not apply to multi-character scene images. Omit the field when the normal
  genre-derived/default background is preferable; do not emit a blank string.
  Omit it from every story-embedded character definition.

#### Standalone Character Chat Scenario

Standalone characters may include a lightweight authored starting scenario for the
character library's Chat action. These fields are optional. Use blank strings and a
blank location object when no authored scenario is needed. They do not create
objectives, branches, rewards, shops, or other full-story systems.

- `chat_story`: Inspectable setup context for a new game started through this
  character's Chat action. Describe the immediate premise, relevant history, current
  situation, and durable constraints that the AI needs to continue the interaction.
  Keep it self-contained and focused on this character and the player. The player can
  inspect this text before starting and may replace it with their own opening guidance,
  so do not store secrets that must remain hidden from the player. This field is not a
  transcript and must not prescribe the player's dialogue, thoughts, feelings, or
  important decisions.
- `chat_opening_message`: Exact first visible message for the authored Chat scenario.
  Write finished in-game prose and dialogue rather than an instruction to generate a
  message. Establish an actionable moment and leave control of the player to the
  player. Use supported runtime tokens such as `|[player_name]|` when the text needs
  the selected player's identity. Leave this blank when the AI should generate the
  opening from `chat_story` instead.
- `chat_starting_location`: Exact object with only `label`, `place`, and `activity`.
  `label` is a short player-facing location name. `place` concretely describes where
  the scene occurs. `activity` describes what the character and player are presently
  doing and should work as scene/image context. Either provide all three nonblank
  strings or leave all three blank. Do not add coordinates, world-map topology, NPC
  lists, objectives, or runtime location ids.

Authored Chat fields are defaults, not commands the player must accept. The game tells
the player when authored content exists, lets them inspect it, and lets them override
the location or opening guidance before creating the save. Author these fields so the
scenario still makes sense when the player chooses a different valid location or
direction. Once a Chat game begins, the chosen authored or overridden setup is copied
into that save; later edits to the library character must not retroactively change an
existing game. Importing this character into a normal story does not start or inject
the Chat scenario.

- `chat_story_template`: Optional complete EmberAdventures `storyTemplate` object for
  players who want a full authored story with this character instead of an open-ended
  chat. Use `null` when no full story is included. Never hand-author, summarize,
  partially copy, or invent fields inside this object using the Character skill. Load
  and follow the EmberAdventures Story skill, create the story there, and place only
  its complete inner `storyTemplate` object in this field, never the outer export
  wrapper or any non-story data. The lightweight Chat fields may remain filled when a
  full story exists: they define the separately selectable Just Chat opening and do
  not override, merge into, or replace the full story. The inner story must set
  `allow_any_player: true`. Do not duplicate the surrounding standalone character
  in `state.player`, `state.players`, `state.characters`, NPC entries, or
  `future_cast`. The engine automatically registers the authoritative surrounding
  character under its stable standalone id before validating and launching the
  attached story. The story may reference that stable id in supported character
  references; a second embedded definition with the same id is invalid.

- `stats`: Optional object of game-specific integer stats. Keys are authored,
  readable stable identifiers such as `strength`, `agility`, `mana`,
  `capacity_cost`, or `pack_share`; EmberAdventures does not prescribe a fixed
  stat list. Every value must be a JavaScript safe integer. Negative, zero, and
  positive integers are valid; decimals, numeric strings, booleans, null, and
  values outside the safe-integer range are invalid. Omit `stats` when the
  character does not participate in an authored numeric system. Do not add
  generic RPG stats merely to fill the field. Stats are shown with full
  character information and supplied to the AI for characters present in the
  scene, but omitted from reduced absent-character context.

  Story-embedded copies may use decimal stat values only when the containing
  story declares that stat key and its allowed 1-6 decimal places in
  `state.numeric_precision.character_stats`. Decimal precision is story-owned,
  so standalone reusable character-library definitions remain integer-only.

  Do not put unlock timing, objective requirements, creator instructions, or
  scheduling notes here. Bad: `Should not appear before Harz politics become
  relevant.` Good: `Serves House Harz as a cautious noble contact.`

  Important characters need enough facts to be useful in play. Main party
  members usually need 6-10 specific facts. Major NPCs usually need 4-6. Cover
  identity, role, personality under pressure, combat/usefulness or social
  usefulness, household/social role when relevant, quirks/preferences,
  relationship dynamics, and story/concept-specific complications or arcs. One
  generic fact is draft quality except for truly minor one-scene utility
  characters.

#### Player-Facing Visibility

Character definitions may be shown in public libraries, local libraries, editor
views, character definition panels, and story setup screens. Before exporting,
audit fields that can be visible to players: `name`, `source`, `genres`,
`kink_tags`, `nsfw`, `loli`, `gender`, `age`, `role`,
`personality_description`, `speech_style`, appearance, outfits, starting state, inventory,
durable known facts, voice metadata, and default image metadata.

Visible character fields must not reveal hidden story objectives, future party
roles, future relationship outcomes, private AI instructions, source twists, or
story-specific secrets unless the character entry is intentionally published as
spoiler-heavy and appropriate for that context.

If the character is intended to be used as a player character, visible fields
should establish who they are at the start while preserving the user's future
agency.

#### Image Defaults

- Character-creation AIs do not have the application-owned image records needed to assign image metadata correctly. Always emit blank image defaults. Do not invent, infer, copy, promote, or attach image ids, URLs, prompts, styles, seeds from generated images, or ownership history. The application manages real image metadata after import.

- `default_seed`: Use `0`.

- `image_prompt_config`: Emit the blank object shape from the canonical example.

- `image_prompt_config.seed_enabled`: Use `true` in the blank authored shape.

- `image_prompt_config.seed`: Use `0`.

- `image_prompt_config.style`: Use `""`.

- `image_prompt_config.profile_style`: Use `""`.

- `image_prompt_config`: Use exactly the blank fields shown in the canonical example. The current EmberAdventures exporter emits `negative` and `negative_prompt`, so include both as `""` for round-trip schema consistency. Never put generated or inferred image guidance in them.

- `default_profile_image`: Emit the complete blank object shown in the canonical example, including blank `local_image_id`.

- `default_profile_image.url`: Use `""`.

- `default_profile_image.local_image_id`: Use `""`.

- `default_profile_image.source`: Use `"none"`.

- `default_profile_image.seed`: Use `null`.

- `default_profile_image.prompt`: Use `""`.

- `default_profile_image.negative_prompt`: Use `""`.

- `default_profile_image.note`: Use `""`.

- `default_profile_image.male`: Required boolean profile-presentation metadata. Use `true` only for a male or trans-male presentation. Use `false` for female, futanari, non-binary, and every other non-male presentation. Female and futanari profile images intentionally share the non-male bucket. For a blank authored slot, initialize this from the canonical character presentation. For a configured image, describe the presentation actually shown by that image, even when it is the character's fallback rather than canonical presentation. Never infer this value later from the character's current gender.

- `profile_image_presentations`: Application-managed pair of default profile-image slots named `male` and `non_male`. Each slot uses the same shape as `default_profile_image`; `male.male` must be `true` and `non_male.male` must be `false` when a real image slot is populated. Character-creation AIs emit both keys with blank/null image values and never invent real URLs, local ids, prompts, seeds, data URLs, transparent images, or placeholder image objects. Leave image values blank for EmberAdventures to fill when real images are generated or selected.

A character may be locally drafted or imported with empty profile-image slots, but public publishing requires one real resolving hosted profile image for the male presentation and one real resolving hosted profile image for the female/futanari presentation. Both `profile_image_presentations.male.url` and `profile_image_presentations.non_male.url` must resolve as real images before public upload, and the character must also have the required alternate name/outfit group. Do not use fake image data to satisfy this requirement. `default_profile_image` remains the canonical/default presentation slot and should be null/blank until it can match one of the two real presentation slots. At runtime, a profile image is eligible only when its `male` value matches the character's active male/female presentation; never display the opposite bucket as a fallback. This metadata applies only to profile images. Normal/full-body, group, story, item, outfit, title-card, and other images must not receive a `male` field.

- `created_at`: Required ISO 8601 timestamp for when this definition was first created. Use the actual creation time for new entries; never leave it blank or use an empty placeholder. Preserve it unchanged when editing an existing definition.

- `updated_at`: Required ISO 8601 timestamp for the most recent definition change. Set it to the actual edit time for a new or modified entry. When reviewing without changing the definition, preserve the existing value.

- `profile_images`: Always emit `{ "active_image_id": "", "image_ids": [] }`.

- `images`: Always emit `{ "active_image_id": "", "image_ids": [] }`.

#### Voice

- `voice`: Always use `null`. Character-creation AIs do not have the installed TTS/screen-reader voice information needed to populate this correctly. Do not infer a voice bucket, assign a character name, use a voice actor, or ask the user for voice metadata during normal character creation.

#### Forbidden Definition Fields

Do not include these in `character_definition`: `kind`, `entity_kind`, duplicate name fields, `creator`, `creator_id`, `short_description`, `creator_notes`, `character_version`, `power`, `consent_state`, current `relationship_to_player`, current `trust`, current `attraction`, current `affection`, current `arousal`, current `state_of_mind`, current `physical_state`, current `pose`, `active_outfit_id`, active/current `clothing`, current `held_items`, current `inventory`, current `known_facts`, `profile_image_id`, `profile_images_list`, current location, scene lists, inspected status, invite status, party membership, NPC status, death state, or image inclusion state. `starting_outfit_id` is allowed because it identifies the immutable default preset; `active_outfit_id` is runtime state and is forbidden.


### Physical Attribute Phrase List

The locked mappings, ownership boundaries, combination tests, and deterministic legacy-migration rules are in [references/body-scales-0-20.md](references/body-scales-0-20.md). Read that reference whenever creating, editing, reviewing, validating, or migrating character appearance.

Starting relationship stats `starting_trust`, `starting_attraction`, `starting_affection`, and `starting_arousal` are also base-10 values from 0 to 10. Do not use legacy 0-100 values for those fields.

`bodyStatKeys`: `height`, `shoulder_width`, `chest`, `upper_body_build`, `midsection_build`, `hip_width`, `butt_build`, `lower_body_build`, `arm_length`, `leg_length`, `penis_size`.

All eleven keys must exist exactly once and contain integers from 0 through 20. The old appearance keys `muscular`, `shoulders`, `stomach`, `hips`, `waist`, `legs`, and `arms` must not appear. Do not double old values during migration; use the field-specific conversion tables and precedence rules in the reference.

## Private Preference File

Preference file path:

`${CODEX_HOME}/private/emberadventures-character-preferences.json`, or
`~/.codex/private/emberadventures-character-preferences.json` when
`CODEX_HOME` is unset.

The first step for this skill is to locate and read that file. Do not store private preferences inside the shareable skill folder.

If the file does not exist, enter preference-intake mode before doing substantial character generation.

If the file exists, inspect intake state before using preferences:

- Use ask-missing mode by default. Ask only missing or ambiguous preference slots that are relevant to the current request, the next useful global calibration, or a user-requested preference audit.
- If a required safety/default slot is missing, ask the next missing required question before generating explicit/NSFW originals.
- Do not block character creation on broad optional setup. Infer optional preferences from the existing file and the current request unless the missing answer would materially change the character.
- Do not treat a preference file as complete just because it exists, but do not run a full questionnaire just because optional slots remain.
- For story shop stock, auction stock, job-board NPC pools, generic world stock,
  and large batches meant to populate a setting, the story premise and requested
  stock role override private preferences unless the user explicitly says to
  apply those preferences. If the user gives a split such as "use my
  preferences for 25% only," obey that split exactly and explicitly ignore or
  de-emphasize private preferences for the remaining stock instead of merely
  complementing them.
- If minimum setup is complete but optional setup is incomplete, do not show all optional groups by default. Mention only the few relevant missing fields, or offer an audit if the user asks what remains.
- Apply workflow preferences once required safety/default slots are known, but keep the current character request moving.

## Preference Intake Mode

Preference intake is opportunistic. It supports the requested character; it should not take over the whole turn unless the user explicitly asks to configure preferences first.

Ask missing preferences in small, relevant batches. Prefer generic answer options over highly tailored options unless the user asks for a character-specific brainstorm. Do not repeatedly ask the same preference in different words.

If the user asks for an audit, list:

- missing preference slots that genuinely remain
- preference slots you can infer from existing answers
- any conflicts or weak calibrations worth confirming

When the user confirms a correction is general, save it to the preference file. When the correction is only about the current character, keep it character-specific.

### Initial NSFW Question

The first message should only ask exactly: "Before we start, do you want to be able to make NSFW characters?"

After the user answers, create/update the private JSON preference file immediately with `allow_nsfw`, metadata defaults, setup tracking fields, and the filtered question plan.

### Main Setup Message

After the NSFW answer is saved, send one well-formatted setup message that explains how the skill works and asks only the first relevant missing batch.

Explain:

- The default creation workflow is: ask missing preferences, infer the rest, propose a few suitable options, let the user review/pick/request more options or changes, then create the final character.
- If the user dislikes that flow, they can describe another workflow, such as direct creation without proposals, one proposal at a time, or a full preference setup first.
- Setup asks up to 10 questions at a time by default, but most turns should ask fewer.
- Questions are labeled with letters: `a`, `b`, `c`, etc.
- Multiple-choice answers use numbers: `0`, `1`, `2`, etc.
- The user can answer like a quiz (`a: 1, b: 2-6, c: free answer`) or just write naturally.
- The user can skip any question or stop setup and return to character creation at any time.

Then ask up to 10 highest-priority relevant missing questions in the same message. If only 1-3 questions matter for the current character, ask only those.

Always include this metadata question early when missing or when the stored answer may not describe the current tool/session:

- Model number and intelligence/reasoning level for the creation tool: ask for the actual tool, model number, and reasoning/intelligence label, then store the factual final label. Treat this as session-sensitive metadata rather than a permanent taste preference. Before each final export, verify that a saved label still matches the current tool/session; when it cannot be verified, ask instead of silently reusing it.

Do not ask for preference slots that do not map to EmberAdventures character fields unless the answer clearly informs existing fields. Collect preferences against the eleven current body fields. Keep broader body-shape notes only when they add information not represented by `upper_body_build`, `midsection_build`, `hip_width`, `butt_build`, and `lower_body_build`.

### Question Formatting

Use letter labels for questions and numeric labels for answer options.

Format every multiple-choice question as a nested list:

- The question line starts at the left margin.
- Every answer option is indented under that question by three spaces.
- Every answer option must have its own numeric label.
- Do not put option `0` at the same indentation level as the question.
- Do not omit numeric labels from later options.
- Do not insert blank lines between options.
- If using Markdown, prefer a fenced `text` block for setup batches so indentation is preserved exactly.

Example:

```text
a. What default spice mode should I use?
   0. Normal/SFW by default
   1. Sexy by default
   2. Ask or infer each time
   3. Free answer

b. What target genders do you usually want for original characters?
   0. Adult women/female characters
   1. Adult men/male characters
   2. Adult nonbinary/androgynous characters
   3. Mix of genders
   4. Ask or infer each time
   5. Free answer
```

For body scales, list the relevant 0-20 descriptions from [references/body-scales-0-20.md](references/body-scales-0-20.md) and ask for either a range, a single number, or a natural-language answer. Do not use joke descriptions.

Example:

```text
d. What chest-size range do you usually like for adult female characters?
   Answer with a range like 8-14, a single number like 12, or words.
   0. completely flat chest with no breast projection
   1. nearly flat chest with slight soft breast contour
   ...
   20. absurd extreme-fantasy breast size with impossible torso-dominating projection
```

For broad catch-all body/anatomy questions, include concrete examples and, when there is an active requested character concept, include 6-10 optional uniqueness hooks tailored to that character. Make clear that the user can pick, combine, rewrite, or ignore the hooks. Store recurring preferences in `body_preferences.custom_body_notes` or the relevant specific preference slot. Store character-specific picks as guidance for that character only, not as a universal preference.

Example:

```text
j. Any recurring body/anatomy preferences I should remember for adult female or monster-girl characters?
   Examples: elegant monster anatomy, visible fangs, extra eyes, glossy chitin, soft fantasy anatomy, horror-leaning anatomy, powerful lower bodies, delicate human torsos, avoid insectoid faces, avoid too many limbs on the upper body.

   For this arachne character specifically, here are optional uniqueness hooks you can pick from or ignore:
   0. Silk-weaver artisan who makes beautiful restraints, clothing, and traps
   1. Venom alchemist who creates medicines from carefully diluted venom
   2. Dungeon ambusher with a cozy web-nest full of trophies and handmade gifts
   3. Gothic widow aesthetic with lace veils, mourning jewelry, and courtly manners
   4. Socially awkward monster girl who is terrifying in combat but shy in conversation
   5. Predatory noblewoman who treats every room like a chessboard
   6. Gentle caretaker who uses webs for comfort, safety, and healing
   7. Horror-leaning arachne with beautiful human features and unsettling spider instincts
   8. Traveling silk merchant who hides spy networks in trade routes
   9. Shrine guardian spider spirit with old rituals, taboos, and sacred thread
```

### SFW/NSFW Branching

Relationship-role options and question sets must branch by SFW/NSFW:

- Ask character-role questions before relationship questions. The character creator can create player characters, main story protagonists, party members, and NPCs, so do not assume every character needs a relationship to the player.
- Preferred relationship intake wording: "What type of character are you creating? Is it the main character of a story, a party member of the main character, or an NPC? If it is a party member or NPC, what is the relationship to the player?"
- Always include a no-relationship option for player characters, main characters, or standalone protagonists.
- For a compact setup batch, combine character type and relationship in one question unless the user's answer needs follow-up. Example options:
  - `0. Player character/main character; no relationship to player`
  - `1. Party member; ally/friend relationship`
  - `2. Party member; romantic or erotic companion`
  - `3. Party member; dominant consensual fantasy partner`
  - `4. NPC; neutral or powerful standalone NPC`
  - `5. NPC; rival or antagonist`
  - `6. NPC; mentor, client, quest-giver, or patron`
  - `7. Ask or infer each time`
  - `8. Free answer`
- If `allow_nsfw` is false, do not offer NSFW relationship roles such as consensual slave-by-choice, erotic companion, or dominant sexual partner. Use SFW options such as player/main character with no relationship, neutral NPC, friend/ally, romantic-but-SFW companion, rival/antagonist, party member, mentor, client, quest-giver, patron, or ask each time.
- If `allow_nsfw` is false, omit NSFW-only question groups and answer options.
- If `allow_nsfw` is true, include NSFW-capable options only when relevant, such as consensual slave-by-choice, erotic companion, or ask each time.
- Keep SFW-safe public descriptions free of explicit kink prose. `kink_tags` are
  metadata for NSFW-capable filtering and adult-appropriate views, not text to
  paste into SFW browsing descriptions.
- In final character JSON, `starting_relationship_to_player` may be `"none"` or a natural-language no-relationship value for player characters, main characters, or standalone protagonists. Do not force an NPC relationship when the character type makes that inappropriate.

### Batching And Follow-Up

Ask up to 10 questions at a time by default. If fewer than 10 relevant unanswered questions remain, ask fewer. In normal character-creation turns, prefer 1-5 highly relevant missing questions.

After each user response:

- Extract answers by matching question letters, option numbers, ranges, and natural-language statements.
- Update the preference file.
- Mark answered questions in `answered_questions`.
- Mark explicitly skipped questions in `skipped_questions`.
- Track unanswered questions from the batch.
- If any batch questions were not answered or skipped, give one follow-up opportunity at the bottom of the next response:

```text
It looks like you did not answer these questions. If you want to leave them blank, that is fine; this is just a last chance before I mark them skipped.

k. [unanswered question]
l. [unanswered question]
```

Use the next letters after the original batch when listing unanswered follow-up questions. If the user still does not answer them, mark them skipped.

When the user says "you pick", "priority order", or "I'll do all of them", choose the highest-priority relevant missing questions. Do not ask stale, already answered, or only loosely relevant optional questions.

### Optional Groups

Maintain optional groups as internal coverage tracking, not as a mandatory questionnaire. When presenting optional setup, include group counts only if the user asks what remains or explicitly wants setup/audit mode. In normal character creation, ask only the missing optional questions that matter for the requested character.

Suggested groups:

- Looks and body
- Genders and attraction
- Species/races
- Personality and boldness
- Jobs/concepts
- Relationship dynamics
- Clothing/style
- Names
- Sexual/NSFW preferences if allowed
- Limits and icks
- Batch uniqueness and similarity to existing characters

### Stable Question Bank

Use the stable ids below for `answered_questions`, `skipped_questions`, batch
tracking, and remaining counts. The ids are internal; continue labeling the
questions shown to the user with letters. Ask only relevant unanswered ids and
generate concise multiple-choice options plus a free-answer option. Filter all
`nsfw.*` questions when `allow_nsfw` is false. Compute remaining group counts
from unanswered applicable ids instead of copying hardcoded totals.

```text
required_setup (not included in optional group counts)
setup.allow_nsfw -> general.allow_nsfw -> whether NSFW character creation is allowed
setup.creation_tool -> general.default_creation_tool and default_creation_tool_parts -> current tool, model, and reasoning/intelligence label
setup.spice_mode -> general.default_spice_mode -> normal, sexy, explicit, or ask/infer default when NSFW is allowed

looks_and_body (12)
looks.height -> body_preferences.height_range -> preferred height range
looks.shoulder_width -> body_preferences.shoulder_width_range -> preferred shoulder-width range
looks.chest -> body_preferences.chest_range -> preferred chest range
looks.upper_body_build -> body_preferences.upper_body_build_range -> preferred upper-body build range
looks.midsection_build -> body_preferences.midsection_build_range -> preferred midsection build range
looks.hip_width -> body_preferences.hip_width_range -> preferred hip-width range
looks.butt_build -> body_preferences.butt_build_range -> preferred butt/glute build range
looks.lower_body_build -> body_preferences.lower_body_build_range -> preferred lower-body build range
looks.arm_length -> body_preferences.arm_length_range -> preferred arm-length range
looks.leg_length -> body_preferences.leg_length_range -> preferred leg-length range
looks.penis_size -> body_preferences.penis_size_range -> preferred penis-size range when relevant
looks.custom_anatomy -> body_preferences.custom_body_notes -> recurring anatomy or body details not covered by scales

genders_and_attraction (4)
gender.targets -> genders_and_attraction.target_genders -> genders the user wants created
gender.focus -> genders_and_attraction.gender_focus -> default gender focus or ask/infer behavior
gender.body_by_gender -> genders_and_attraction.body_type_focus_by_gender -> body preferences that differ by gender
gender.variation -> genders_and_attraction.variation_preference -> desired gender variation across batches

species_and_races (6)
species.likes -> species_and_race.liked_species -> liked species/races
species.dislikes -> species_and_race.disliked_species -> disliked species/races
species.human_detail -> species_and_race.human_race_detail_preference -> whether human ethnicity/visual ancestry should be specific, varied, inferred, or omitted
species.diversity -> species_and_race.diversity_expectation -> desired species/race diversity in batches
species.anatomy -> species_and_race.nonhuman_anatomy_preferences -> recurring nonhuman anatomy preferences
species.horror -> species_and_race.horror_appearance_tolerance -> tolerance for genuinely disturbing or horror-like designs

personality_and_boldness (7)
personality.boldness -> personality.boldness_range -> preferred numeric 1-10 boldness range or text guidance
personality.likes -> personality.liked_traits -> liked personality traits
personality.dislikes -> personality.disliked_traits -> disliked personality traits
personality.subversion -> personality.mismatch_or_subversion_preference -> preference for archetype subversion or mismatched traits
personality.aggression -> personality.aggression_preference -> aggression preference independent of boldness
personality.power_dynamic -> personality.power_dynamic_preference -> dominant, submissive, switch, neutral, varied, or ask/infer behavior
personality.tone -> personality.humor_and_tone_preference -> preferred humor, seriousness, warmth, darkness, or tonal mix

jobs_and_concepts (5)
concept.likes -> jobs_and_concepts.liked_jobs -> liked jobs, roles, and concepts
concept.dislikes -> jobs_and_concepts.disliked_jobs -> disliked jobs, roles, and concepts
concept.priority -> jobs_and_concepts.concept_priority -> whether job, archetype, appearance, personality, or another hook should lead design
concept.power -> jobs_and_concepts.overpowered_preference -> desired power level
concept.role_style -> jobs_and_concepts.role_style_preference -> ordinary, fantastical, setting-grounded, origin-driven, or varied role style

relationship_dynamics (5)
relationship.character_type -> relationship_defaults.default_character_type -> player character, party member, NPC, or ask/infer
relationship.default -> relationship_defaults.default_relationship_to_player -> default relationship to player
relationship.allowed -> relationship_defaults.allowed_relationship_types -> allowed relationship types
relationship.none -> relationship_defaults.allow_no_relationship -> whether no player relationship must remain available
relationship.special -> relationship_defaults.special_relationship_dynamics -> optional romance, ownership, oath, rival, family, erotic, or other special dynamics; omit NSFW options when NSFW is disabled

clothing_style (5)
clothing.likes -> clothing_and_style.liked_styles -> liked clothing styles
clothing.dislikes -> clothing_and_style.disliked_styles -> disliked clothing styles
clothing.count -> clothing_and_style.outfit_count_guidance -> how many outfits to create
clothing.plan -> clothing_and_style.default_outfit_plan -> recurring wardrobe composition
clothing.special -> clothing_and_style.special_outfit_notes -> special outfit requirements, including sexual outfit guidance only when NSFW is enabled

names (4)
names.likes -> names.name_style_likes -> liked naming styles
names.dislikes -> names.name_style_dislikes -> disliked naming styles
names.theming -> names.over_themed_name_tolerance -> tolerance for concept-themed names
names.length -> names.word_count_preference -> preferred name length and structure

sexual_nsfw_preferences (8; NSFW only)
nsfw.level -> nsfw_preferences.spice_level -> desired explicitness
nsfw.frequency -> nsfw_preferences.spice_frequency -> desired frequency of sexual characterization
nsfw.kinks -> nsfw_preferences.liked_kinks -> liked kinks and dynamics
nsfw.limits -> nsfw_preferences.limits -> sexual hard limits
nsfw.forwardness -> nsfw_preferences.default_sexual_forwardness -> default sexual forwardness
nsfw.anatomy -> nsfw_preferences.anatomy_preferences -> sexual anatomy preferences
nsfw.role -> nsfw_preferences.role_preferences -> preferred sexual roles or power dynamics
nsfw.clothing -> nsfw_preferences.clothing_preferences -> explicit clothing and exposure preferences

limits_and_icks (3)
limits.hard -> limits_and_icks.hard_limits -> content or traits never to create
limits.soft -> limits_and_icks.soft_avoids -> content or traits generally to avoid
limits.context -> limits_and_icks.contextual_limits -> content allowed only in specific contexts or when explicitly requested

batch_uniqueness (3)
batch.priority -> batch_uniqueness.uniqueness_priority -> desired uniqueness level
batch.compare -> batch_uniqueness.compare_against_existing_characters -> whether to compare against existing libraries
batch.similarity -> batch_uniqueness.similarity_to_existing_characters -> whether new characters should fit with or differ from existing characters
```

Most questions should be multiple choice with an explicit free-answer option. The user can skip any question or stop setup at any time.

When the user says they are done, happy enough, wants to stop questions, wants to skip setup, or wants to return to the character request, record that state in the preference file and proceed using the answered preferences plus reasonable defaults.

If optional counters or `answered_questions` disagree with populated preference fields, trust the populated fields, repair the counters, and avoid re-asking the same topic.

Use a shape like:

"Setup is saved.

There are 11 preference groups with unanswered questions:
- Looks and body: 10 questions
- Genders and attraction: 4 questions
- Species/races: 6 questions
- Personality and boldness: 7 questions
- Jobs/concepts: 5 questions
- Relationship dynamics: 5 questions
- Clothing/style: 5 questions
- Names: 4 questions
- Sexual/NSFW preferences: 8 questions
- Limits and icks: 3 questions
- Batch uniqueness and similarity: 3 questions

Do you want to answer the next 10 questions in highest-priority order, pick a group, skip a group, or stop setup and return to the character request?"

If NSFW is disabled, omit NSFW-only groups/questions from the count and prompt.

## Preference Schema

Use a structured JSON preference file with one general section and otherwise specific question/answer slots.

Suggested shape:

```json
{
  "schema": "emberadventures-character-preferences-v1",
  "updated_at": "<actual ISO 8601 update timestamp>",
  "general": {
    "setup_complete": false,
    "minimum_setup_complete": false,
    "optional_setup_complete": false,
    "user_stopped_setup": false,
    "user_stopped_optional_setup": false,
    "intake_status": "in_progress",
    "allow_nsfw": null,
    "default_spice_mode": "ask_or_infer",
    "default_source": "Original",
    "default_creation_tool": "<actual tool/model> (<reasoning level>)",
    "default_creation_tool_parts": {
      "tool": "",
      "model": "",
      "intelligence": ""
    },
    "preferred_workflow": "ask_missing_propose_review_approve_make",
    "workflow_notes": "Default: ask only relevant missing preferences, infer the rest, propose a few options, let the user review/pick/request changes, then create. User may override with direct creation or another flow.",
    "compare_existing_library": "ask",
    "existing_library_paths": [],
    "last_question_batch": [],
    "unanswered_from_last_batch": [],
    "answered_questions": [],
    "skipped_questions": [],
    "question_plan": {
      "question_label_style": "letters",
      "answer_option_label_style": "numbers",
      "batch_size": 10,
      "stable_question_bank_version": 1,
      "priority_order": []
    },
    "remaining_required_questions": [
      "setup.allow_nsfw",
      "setup.creation_tool",
      "setup.spice_mode"
    ],
    "remaining_optional_groups": {
      "looks_and_body": 10,
      "genders_and_attraction": 4,
      "species_and_races": 6,
      "personality_and_boldness": 7,
      "jobs_and_concepts": 5,
      "relationship_dynamics": 5,
      "clothing_style": 5,
      "names": 4,
      "sexual_nsfw_preferences": 8,
      "limits_and_icks": 3,
      "batch_uniqueness": 3
    }
  },
  "genders_and_attraction": {
    "target_genders": [],
    "gender_focus": "ask",
    "body_type_focus_by_gender": {},
    "variation_preference": "ask"
  },
  "body_preferences": {
    "height_range": null,
    "shoulder_width_range": null,
    "chest_range": null,
    "upper_body_build_range": null,
    "midsection_build_range": null,
    "hip_width_range": null,
    "butt_build_range": null,
    "lower_body_build_range": null,
    "arm_length_range": null,
    "leg_length_range": null,
    "penis_size_range": null,
    "custom_body_notes": ""
  },
  "species_and_race": {
    "liked_species": [],
    "disliked_species": [],
    "human_race_detail_preference": "ask",
    "diversity_expectation": "ask",
    "nonhuman_anatomy_preferences": [],
    "horror_appearance_tolerance": "ask"
  },
  "personality": {
    "boldness_range": null,
    "liked_traits": [],
    "disliked_traits": [],
    "mismatch_or_subversion_preference": "ask",
    "aggression_preference": "ask",
    "power_dynamic_preference": "ask",
    "humor_and_tone_preference": "ask"
  },
  "jobs_and_concepts": {
    "liked_jobs": [],
    "disliked_jobs": [],
    "concept_priority": "ask",
    "overpowered_preference": "ask",
    "role_style_preference": "ask"
  },
  "relationship_defaults": {
    "default_character_type": "ask",
    "default_relationship_to_player": "ask",
    "allow_no_relationship": true,
    "allowed_relationship_types": [],
    "slave_by_choice_default": "ask",
    "special_relationship_dynamics": []
  },
  "clothing_and_style": {
    "liked_styles": [],
    "disliked_styles": [],
    "ambiguity_rule": "pick_one_precise_outfit",
    "outfit_count_guidance": "ask",
    "default_outfit_plan": "ask",
    "normal_outfit_count": null,
    "sexual_outfit_count": null,
    "required_outfit_types": [],
    "disallowed_outfit_types": [],
    "sexual_outfit_notes": "",
    "special_outfit_notes": ""
  },
  "names": {
    "name_style_likes": [],
    "name_style_dislikes": [],
    "over_themed_name_tolerance": "ask",
    "word_count_preference": "ask"
  },
  "proposal_preferences": {
    "format": "ask",
    "detail_level": "ask",
    "include_race_parenthetical": "ask"
  },
  "nsfw_preferences": {
    "spice_level": null,
    "spice_frequency": null,
    "liked_kinks": [],
    "limits": [],
    "default_sexual_forwardness": "ask",
    "anatomy_preferences": [],
    "role_preferences": [],
    "clothing_preferences": []
  },
  "limits_and_icks": {
    "hard_limits": [],
    "soft_avoids": [],
    "contextual_limits": []
  },
  "batch_uniqueness": {
    "uniqueness_priority": "ask",
    "compare_against_existing_characters": "ask",
    "similarity_to_existing_characters": "ask"
  },
  "observed_acceptance_patterns": [],
  "preference_mismatches_to_discuss": []
}
```

If the user accepts/rejects characters in a way that conflicts with recorded preferences, tell them the mismatch you observe and work with them to update preferences or explain why your inference was wrong.

When feedback includes a calibration correction, ask or infer whether it is general or character-specific. Save general calibrations in the relevant preference slot. Examples:

- "This image is a 6, not an 8" -> save as body-scale calibration.
- "Spider women should have spider legs from the back, not a realistic abdomen" -> save as monster-girl anatomy guidance if general.
- "This outfit reads like lingerie" -> save clothing-slot and prompt guidance if general.

## Metadata Fallbacks

Use the preference file and user answers first. If a required value is still
missing, ask before final export whenever practical. For an immediate export,
use only these safe fallbacks:

- `source`: `"Original"`
- `creation_tool`: the actual current tool/model/reasoning label, never a copied example label
- `genres`: `["fantasy"]` only when the concept is clearly broad fantasy and no more accurate approved set is known
- `nsfw`: `true` only when the character definition itself is inherently
  explicit/NSFW as stored or displayed; otherwise `false`
- `loli`: `false`
- `can_die`: `false`
- `voice`: `null`

For original characters, always use `source: "Original"`. Do not ask the user for a default original-character source label. Do not leave `source`, `creation_tool`, approved `genres`, `nsfw`, or `loli` null. `nsfw` and `loli` must be true or false. Do not emit or ask about `creator` or `creator_id`; EmberAdventures assigns both during import.

Set `voice` to `null`. Do not ask for or infer voice information.

Before final export, verify that saved `creation_tool` metadata describes the current tool/session. If it is missing, stale, or unverifiable, ask for the actual tool name, model number, and intelligence/reasoning level, then format the label as `{tool} {model} ({intelligence})` when intelligence is present. Do not silently use the skill's example or a label saved by a different model/session.

## NSFW And Consent

- Original spicy characters must be adults and physically adult.
- Never create sexualized minors or minor-coded characters.
- Original characters can be extremely sexually forward only when the user requests that style or preferences clearly set that as the default.
- If the user asks for submissive/slave-by-choice dynamics, write them as adult consensual fantasy dynamics.
- Do not assume every original character is a willing slave by choice unless preferences or the current request say so.

## Character Design Goals

- Make characters interesting, distinct, and suited to the user's current request.
- Make batches diverse in species/variant, profession, personality, boldness, silhouette, outfit, and tone unless preferences request a narrower set.
- Include mismatch/subversion only when preferences or the prompt support it.
- Avoid making every character a generic archetype.
- Avoid making every character overpowered unless preferences or the current request support it.
- Use the user's job/concept preferences from the preference file.
- Follow `jobs_and_concepts.role_style_preference` and the current request when deciding whether a role should be ordinary, fantastical, setting-grounded, origin-driven, or varied. Do not hardcode one style for all users.
- If the user rejects a role or concept, use their explanation to revise the relevant preference instead of assuming every rejection means the role was too ordinary or job-like.
- Follow `species_and_race.human_race_detail_preference`. When that preference requests human ethnicity/visual ancestry, include the resulting qualifier in the single `species` value; otherwise infer, vary, omit, or ask as recorded.

## Existing Characters

Default to not touching existing characters unless the user asks to edit existing ones.

When creating unique characters, check whether an existing character library file is available or mentioned. If it exists, ask whether the user wants it reviewed so new characters are somewhat similar and fit in, or more distinct from the existing cast.

For uniqueness checks, scan current and relevant existing characters for repeated:

- personality phrasing
- inventory items
- known facts
- body language
- relationship wording
- names and name patterns
- jobs/concepts
- species/variant mix
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
Name (species/variant)
Description.
```

Include the species/variant parenthetical only when the saved preference requests it or when it materially helps compare concepts. For humans, obey `human_race_detail_preference` rather than always forcing an ethnicity into the proposal.

## Personality

Use preference-file personality and boldness guidance. Make personalities durable and specific, not just current mood or a list of sexual behaviors. Boldness, aggression, and dominant/submissive dynamics are independent: a character may be extremely bold and submissive, quietly dominant, gentle and forward, or aggressive but romantically reserved.

For spicy originals, combine sexuality with identity: job, flaws, humor, fears, habits, principles, contradictions, and social style.

Avoid repetitive boilerplate unless the user explicitly asks for a uniform batch.

## Practical Body And Appearance Guidance

The field contract above defines the schema. This section adds creation guidance
for producing clean image prompts and should not introduce alternate field shapes.

- Body slots describe body only. Do not put clothing, personality, mood, job,
  relationship, pose, or sexual behavior in physical slots.
- Use integer 0-20 values for all eleven body-scale fields. Body-scale strings
  are invalid. Use the locked reference mappings as image-generator-friendly
  vocabulary and put genuinely exceptional anatomy in the appropriate remainder
  field instead of replacing a numeric body field.
- `personality_description` owns personality, behavior, motivations,
  temperament, and durable social style only. Do not put body shape, clothing,
  hair, skin, tattoos, scars, horns, pose, or image-prompt visual text in it.
- `speech_style` owns how the character usually talks. Write one concise
  sentence covering rhythm, formality, bluntness, warmth, guardedness, profanity,
  humor, flirtation, or similar dialogue behavior. Do not put current emotions,
  story instructions, TTS/voice metadata, or visual traits in it.
- `species` owns the complete biological/source identity, including meaningful subtype, subgroup, ethnicity, or lineage qualifiers. Do not create `race` or `ancestry` fields.
- `skin_color`, `eye_color`, `hair_color`, `hair_length`, and `hair_type` own
  only those exact traits.
- `extra_description` owns concrete durable visual traits that do not fit another specific appearance field, including horns, claws, fangs, ordinary tails, wings, extra eyes, unusual ears, nonhuman hands, tattoos, scars, birthmarks, body paint, facial markings, body markings, or a concise species trait that cannot be expressed by one numeric field. Replacement nonhuman lower-body anatomy belongs in `extra_description_lower_body`, not here. It is a remainder field, not a second full-body description.
- Do not duplicate specific appearance fields inside `appearance.extra_description`. The game converts the eleven numeric body fields plus hair, eyes, and skin into image-prompt text. Remove duplicated height, shoulder width, chest size, upper-body build, abdominal build, hip width, butt/glute build, thigh/calf build, arm length, leg length, penis size, hair, skin, and eyes. After final assembly, clean both remainder fields again; if nothing unique remains, use `""`.
- Do not use filler `extra_description` prose such as `Attractive adult [species] with a distinctive silhouette`, `expressive face`, `design cues tied to her work as...`, or `[species] traits shaped around...`. Those phrases are not concrete visual traits and usually duplicate `species`, `role`, body fields, or personality. Write only specific durable visuals that the other fields cannot express, such as scars, tattoos, horns, tails, wings, markings, ports, unusual anatomy, or similar.
- Do not paste prose-first body-design notes into `extra_description`, mention the character by name, use narrative pronouns, describe posture or current state, or explain a visual trait through profession/history. Prefer a compact list of visible leftovers. Before export, preview the fully assembled image prompt and reject `extra_description` if it repeats structured prompt phrases or reads like a character-sheet paragraph.
- For exaggerated features, use direct graphic description language when needed for accurate image output.
- Manual characters may use the full valid 0-20 range when appropriate.
- When the preference file contains a numeric or calibrated body range, final character body fields must explicitly match that scale. Do not rely on vague words like "huge", "massive", or "defined" if the user has calibrated the scale with concrete anchors.
- For clothed characters, use the normal female chest phrase and append `fully covered by the described clothing` when structured upper-body clothing is present. Do not invent a separate clothed scale.
- If the user supplies a concrete anchor such as "8 equals full watermelon-sized per breast", use it to calibrate and select the numeric value `8`. Keep the final mapped body field numeric. Put genuinely additional unmapped anatomy in `extra_description`; do not repeat the mapped trait there.
- If the user prefers impossible anatomy, state it directly and visually, e.g. "more visible ab blocks than realistic human anatomy", rather than just "defined abs".
- Keep species/variant anatomy consistent and visually useful.

### Image Prompt Projection Contract

Character files store facts; EmberAdventures decides what is visible for each image request. Authors must keep the structured facts complete rather than pre-composing a final image prompt.

- Profile portraits are framed from the top of the head through the waist. They include `shoulder_width`, `chest`, `upper_body_build`, `midsection_build`, `arm_length`, durable upper-body traits, and the visible upper clothing subset. They omit `hip_width`, `butt_build`, `lower_body_build`, `leg_length`, `extra_description_lower_body`, and genital-placement wording.
- Normal/full-body and group prompts include `extra_description_lower_body` whenever it is authored and the selected framing includes the lower body. It may describe lower-only markings or unusual humanoid details while `nonhuman_lower_body` is false, or the complete replacement anatomy while the flag is true.
- When `nonhuman_lower_body` is true and ordinary humanoid lower-body traits do not apply, image prompts suppress `hip_width`, `butt_build`, `lower_body_build`, and `leg_length`. Other body fields and all authored clothing remain available.
- Adult NSFW prompts may describe anatomy at the humanoid-to-nonhuman body junction. Male and futa/futanari characters use penis wording; every other character uses vulva/feminine-contour wording. Covered prompts describe only a covered contour. Genital placement never dictates softness, erection, or arousal state.
- Futa/futanari identity must be represented by `gender: "futa"` or `gender: "futanari"`. Tags, kink tags, sexual preferences, role, and appearance prose never establish or override gender. Do not place exact futa/futanari metadata on a non-futanari definition because import and publish validation reject that contradiction.
- Age wording is deterministic: known ages 18 or older are described as `{age}-year-old adult`; known younger ages use the numeric age without `adult`; missing/invalid ages default to adult unless the definition is explicitly minor-marked, in which case image generation is forced SFW.
- Clothing prompt order is: `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `undershirt`, `shirt`, `over_shirt`, `coat`, `bra`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `pants`, `skirt`, `legwear`, `underwear`, `socks`, `feet`, `other_accessory`. A bra is rendered as `with {bra} underneath` when an `undershirt`, `shirt`, `over_shirt`, or `coat` exists. Underwear is rendered the same way when `pants`, `skirt`, or `legwear` exists. These decisions use structured slot occupancy only, never clothing-word searches.

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
- Use `starting_inventory`, `starting_known_facts`, and `starting_held_items` to make the character concrete and usable in game. Keep image metadata blank.
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
   entries use `"Original"`, `creation_tool` is factual rather than copied from
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
   coherent clothing object and explicit boolean `nsfw`, and
   `starting_outfit_id` matches an outfit id. SFW characters have SFW starting
   outfits and at least one SFW outfit in both presentations.
   Every outfit includes all intended visible and inner clothing layers.
   Animal or natural-form outfits use concrete body-covering slot values and
   never use `{}` as placeholder clothing.
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
13. The body-scale portion of `appearance` contains exactly the eleven current
    keys, each as an integer from 0 through 20. The seven legacy appearance keys
    are absent. Chest uses the correct canonical presentation table. Replacement
    nonhuman lower bodies retain all required numbers but suppress only the four
    inapplicable lower-body traits during prompt projection.
14. `creator`, `creator_id`, `short_description`, `creator_notes`,
    `character_version`, `consent_state`, and all other forbidden or obsolete
    fields are absent.
15. `starting_nsfw_known_facts` is an array, contains only adult-only durable
    facts, and duplicates none of `starting_known_facts`. Loli and under-18
    characters have no NSFW facts or outfits.
16. `catalog_hook` is a string containing an accurate, spoiler-free standalone
    catalog pitch, or `""`. It is omitted from story-embedded characters.
17. `default_image_background`, when present, is a trimmed nonempty string that
    describes only a suitable environment for solo standalone-character images.
    It is omitted rather than blank when unused, never overrides an explicit
    story/scene/location/user setting, and is omitted from story-embedded characters.
18. Optional Chat scenario fields use their exact shapes: `chat_story` and
    `chat_opening_message` are strings; `chat_starting_location` contains only
    `label`, `place`, and `activity`, which are either all nonblank or all blank.
    The opening never controls the player, the scenario is safe for player inspection,
    and the three fields describe one coherent starting situation.
    `chat_story_template` is either `null` or only a complete inner `storyTemplate`
    object created and validated under the EmberAdventures Story skill. It may coexist
    with the lightweight fields because Full Story and Just Chat are separate launch
    choices.

## Library Maintenance

When asked to maintain an original character library, support:

- metadata repair
- schema validation
- duplicate detection
- repetitive phrasing cleanup
- source/creation_tool/genres/nsfw/loli/can_die backfill
- style consistency
- species/variant balance review
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
  species/variant, appearance, outfit, personality, speech style, intended shop/stock
  category, unlock requirement when known, and a post-purchase or
  post-introduction hook;
- generated job-role NPCs such as recurring bakers, clerks, witnesses, or
  rivals can be shorter, but still need a proper name, real appearance, outfit,
  personality, speech style, and one reusable job-scene hook.

Do not make hundreds of stock characters main-character-length, but also do not
make them anonymous archetypes. They must be distinct enough that the player can
inspect, talk to, buy/recruit, remember, and use them in scenes.
