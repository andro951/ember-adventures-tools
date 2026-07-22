---
name: emberadventures-character
description: Authoritative base skill for normal EmberAdventures character definitions. Use directly for invented/source-free characters, preference intake, proposals, character JSON creation, review, repair, and library maintenance. Source EmberAdventures Character must load this skill for the complete schema, field ownership, outfit, metadata, image, voice, and validation contract, then add only source research and canon-specific rules.
---

## Version and Update Check

Current skill version: `1.0.13`.

For ordinary character creation, review, repair, or migration, use the installed
skill text as the active instructions. Do not interrupt the creator workflow to
download, install, clone, replace, or update skills unless the user explicitly
asks to update or verify skill currency.

For maintenance only, the authoritative GitHub version file is:

https://raw.githubusercontent.com/andro951/ember-adventures-tools/main/skills/emberadventures-character-version.md

If the user explicitly asks to update skills and the retrieved version differs
from the local version, pull the current `emberadventures-character` skill
folder from GitHub, replace the local copy, and then continue with the user's
job. Do not silently use a stale local copy.

# EmberAdventures Character

Use this skill directly when the user asks to create, expand, review, or revise
invented/source-free EmberAdventures characters. It is also the mandatory base
contract for every normal EmberAdventures source/canon character definition.
For anime, manga, book, game, mythology, movie, or other canon research, load
`Source EmberAdventures Character` in addition to this skill. The source skill
extends this one; it does not replace or duplicate this schema contract.

## Model Quality Recommendation

Before substantial character creation, if the current model and
reasoning/intelligence/effort level are known to be below 5.6 Sol High, tell the
creator that 5.6 Sol High is recommended and will likely produce a better
character. This is a quality recommendation, not a hard gate; character creation
should still work on lower models unless the output is visibly invalid.

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
`speech_style`, `starting_known_facts`, outfits, image defaults, or visible metadata.

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
characters, party members, and major NPCs need concrete `starting_known_facts`
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
    "romanceable": true,
    "gender": "female",
    "fallback_name": "Fallback Name",
    "fallback_outfits": [
      {
        "id": "default",
        "name": "Default",
        "clothing": {
          "undershirt": "light cotton undershirt",
          "shirt": "plain travel shirt",
          "pants": "plain travel trousers",
          "underwear": "plain comfortable underwear",
          "socks": "plain travel socks",
          "feet": "simple boots"
        }
      }
    ],
    "fallback_starting_outfit_id": "default",
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
      "penis_size": 5,
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
    "starting_known_facts": [],
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

- `romanceable`: Required boolean. Use `true` when the character is an intended potential romantic or sexual interest. Use `false` intentionally for plot-only officials, incidental contacts, antagonists, or other characters who should not normally adapt to the player's preferred romantic genders. Most recurring AI-created characters should be romanceable unless their story function gives a concrete reason not to be. Player characters are never gender-adapted from this field.

- `fallback_name`, `fallback_outfits`, and `fallback_starting_outfit_id`: Required atomic opposite male/non-male presentation group for the same character. The canonical `name`, `gender`, `outfits`, and `starting_outfit_id` remain the normal definition. Every reusable character must provide all three fields so local and public libraries can show only a presentation allowed by the active profile. Supply only one `fallback_name`; never create a name-alias list. A male canonical character uses the fallback for a non-male presentation, while a female or futanari canonical character uses it for a male presentation. Prefer a fallback name that retains at least the first letter, and preferably the first two letters, of the canonical name so the character remains recognizable. A natural, setting-appropriate authored name is more important than preserving letters when that would make the result strained. Fallback outfits must be nonempty and remain recognizable equivalents: preserve each outfit's purpose, colors, equipment, status, and general visual identity while changing only gendered construction, underwear, fit, and similar presentation details unless a larger change is specifically justified. `fallback_starting_outfit_id` must reference one of those outfits. Appearance, personality, facts, relationships, and all other identity fields remain unchanged. Local import may continue after an explicit warning when this group is missing; public publishing rejects the character until it is complete.

- `fallback_gender`: Optional only for a canonical futanari character. Use exactly `"male"` or `"female"` to decide which presentation is used when the player's selected preferences include male and female but not futanari. Omit it for non-futanari characters. Across a generated cast, split futanari fallback genders evenly so a 40% male / 40% female / 20% futanari base distribution becomes 50/50 when only male and female are preferred.

When migrating an existing cast into gender-flexible definitions, preserve identity instead of rewriting the character. If an existing female character becomes canonical male, move her original name to `fallback_name`, her original outfits to `fallback_outfits`, and her original starting outfit id to `fallback_starting_outfit_id`; then author a natural canonical male name and equivalent male outfits. If she remains canonical female, preserve her current name and outfits and add the male fallback. If she becomes canonical futanari, preserve the current non-male name and outfits as canonical, add a male fallback name and equivalent outfit set, and distribute `fallback_gender` evenly across the futanari cast. Never change appearance, personality, facts, role, stats, relationships, or inventory merely because the canonical gender presentation changed.

- `genres`: Approved broad genre/search tags for standalone character-library definitions. Do not store this on characters embedded inside story templates; embedded story characters inherit the story's `genres`. Approved values are `anime`, `fantasy`, `sci-fi`, `modern`, `historical`, `romance`, `adventure`, `action`, `comedy`, `drama`, `mystery`, `thriller`, `horror`, `dark`, `cozy`, `slice of life`, `superpower`, `isekai`, `school`, `workplace`, `political`, `war`, `crime`, `mythology`, `supernatural`, `post-apocalyptic`, `western`, `cyberpunk`, `steampunk`, and `harem`.

- `kink_tags`: Optional public-library discovery metadata. This is a closed vocabulary and is separate from player sexual preferences. Every value must exactly match one of the canonical lowercase strings below; these are the only valid options. Do not invent, combine, pluralize, reword, or add tags. Interpret every kink tag from the player's perspective: `dominance` means the player acts dominant, `submission` means the player acts submissive, `owning partners` means the player owns partners, and `being owned` means the player is owned. A character's behavior or preference alone does not justify the opposite player-perspective tag. Use only tags intrinsic to the interaction this standalone character definition supports, and use `[]` when none apply. Do not use vanilla kissing, oral sex, vaginal sex, ordinary romance, tone, body appearance, or broad genres as kink tags.
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

- `age`: Age in number of years as an integer. Do not use ranges, words, unknown, approximate text, or decimals. If the character is intended for adult-content use, the non-loli adult version must be 18 or older.

- `gender`: The sole source of character gender mechanics. Use clear player-facing wording. `"male"`, `"trans male"`, and `"trans-male"` use the male mechanics bucket and are normalized to male at runtime. `"futa"` and `"futanari"` identify futanari characters; they otherwise use the female mechanics bucket except for penis-specific behavior. Every other value, including female, non-binary, trans female, trans non-binary, and free-text identities, uses the female mechanics bucket. Do not infer gender from `kink_tags`, `tags`, `sexual_preferences`, appearance prose, role, or any other field. Import and publish validation reject exact futa/futanari metadata on a character whose `gender` is not futa or futanari. Do not use this field for voice names or relationship roles.

- `appearance.penis_size`: Required intentional integer from 0 to 10 on every character definition, including female, non-binary, futanari, male, `romanceable: false`, and other characters. Runtime ignores it unless the current presentation is male or futanari, but it must already exist because runtime gender adaptation can change a character's presentation. `0` is extremely small, `5` is average, and `10` is extreme fantasy scale.

- `role`: General durable description usable as a title, rank, position, profession, specialty, or group/story function. Examples: `"guild registrar"`, `"front-line bruiser"`, `"healer"`, `"merchant queen"`, `"runaway noble"`. Do not write current mood, current pose, or temporary scene action here.

- `personality_description`: Durable personality and behavior summary. Describe how the character tends to think, act, flirt, fight, negotiate, or handle pressure. Do not use only a list of kinks or current emotions. Avoid plot spoilers unless the character definition is allowed to contain them and they will be hidden from normal prompts until relevant. For player-character definitions, describe starting identity/tendencies without scripting future choices, consent, morality, relationship outcomes, or actions beyond the unavoidable starting premise.

- `speech_style`: Durable dialogue behavior. Write one concise sentence describing how the character usually speaks, such as terse, warm, formal, guarded, profane, poetic, blunt, clipped, rambling, teasing, flirtatious, evasive, or emotionally armored. Do not use this for current mood, TTS/voice metadata, visual traits, story instructions, relationship outcomes, or hidden future facts.

- `boldness`: Immutable 1-10 number describing how readily and directly the character initiates romantic or sexual interest. It measures initiative and directness, not aggression, dominance, submission, unrelated confidence, kink interests, or willingness to ignore consent. Numeric `0` and values outside `1-10` are invalid and normalize to the neutral default `5`. A custom string is also valid when the character needs nuance that the scale cannot express. If using a string, write only the behavior description, such as `"cautious; may initiate small compliments or mild flirting, then pauses to judge the response"`. Never include storage/system wording, effective-value summaries, numeric prefix summaries, or score annotations in the saved field. This is separate from the user's `characterBoldnessOffset` profile setting, which adjusts the maximum effective boldness at runtime. Use the same scale for every gender; gender adaptation never changes personality.
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

- `starting_relationship_to_player`: Starting relationship text copied into runtime when a new game/import begins. Examples: `"self"`, `"unknown"`, `"trusted companion"`, `"professional handler"`, `"rival"`, `"romantic partner"`. Do not update this after play; runtime relationship changes belong elsewhere.

- `starting_trust`: Starting trust from 0 to 10. Use a number. `0` means no trust or unknown trust; `10` means complete trust at start. Do not use legacy 0-100 values.

- `starting_attraction`: Starting attraction from 0 to 10. Use a number. This is initial attraction toward the player/protagonist when applicable, not attractiveness score.

- `starting_affection`: Starting affection from 0 to 10. Use a number. This is initial emotional warmth/bond, not current romance progress after play.

- `starting_arousal`: Starting arousal from 0 to 10 for characters/stories where arousal defaults are relevant. Use `null` or omit only for characters where arousal does not apply. Do not store post-play arousal here.

- `starting_state_of_mind`: Initial mood/mental state copied into runtime. Examples: `"neutral"`, `"curious"`, `"guarded"`, `"amused"`, `"panicked but focused"`. Do not write long story summaries.

- `starting_physical_state`: Initial physical condition copied into runtime. Examples: `"healthy"`, `"tired"`, `"wounded shoulder"`, `"covered in slime but unharmed"`. Do not use this for clothing or pose.

- `starting_pose`: Initial body posture or action pose copied into runtime. Examples: `"standing behind the counter"`, `"leaning against the bar"`, `"kneeling beside a broken crate"`. Keep it scene-useful and not too long.

#### Appearance

`appearance` describes the body and persistent visual traits only. Do not put clothing, current pose, current mood, relationship, inventory, or sexual behavior here.

- `species`: Biological/species label. Examples: `"human"`, `"slime woman"`, `"elf"`, `"demon"`, `"arachne"`.

- `race`: Specific human race/ethnicity/visual ancestry when applicable, or a species subtype if useful. Follow `species_and_race.human_race_detail_preference`: specify, vary, infer, omit, or ask as recorded instead of forcing ethnicity into every human definition. Examples when specificity is wanted: `"Black human"`, `"East Asian human"`, `"red slime"`; use `""` when the preference says to omit it or when the field is not applicable.

- `ancestry`: Optional lineage/heritage detail distinct from race/species. Examples: `"half-demon bloodline"`, `"old noble family"`, `""`.

- `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, `arms`: Body scale fields. Almost always use an integer from 0 to 10 from the mapped scales below. Numeric values make the editor behave like a predictable slider and let users increase or decrease a trait by one step. Use a custom string only for a specific exceptional anatomy or visual requirement that no mapped value can represent. When a string is necessary, make the intended scale position clear in the wording or nearby design context. `chest` follows the same rule as every other mapped body field and is not a special case.

- `skin_color`, `eye_color`, `hair_color`, `hair_length`, `hair_type`: Persistent visual details. Use concrete visual wording. Do not write personality or clothing.

- `extra_description`: Optional remainder field for concrete, durable visual traits that do not fit another appearance field. Examples include `"scar across left collarbone"`, `"transparent mint-green slime body"`, or `"filed canines"`. It is not a general physical-description field. Do not include temporary dirt, arousal, clothing damage, scene effects, personality, mood, pose, health, role, backstory, or explanations of how the character acquired a body type. Do not repeat details already represented by the other appearance fields.

- `nonhuman_lower_body`: Boolean. Use `true` only when the character's normal humanoid hips and legs are replaced by a distinct nonhuman lower body, such as a serpent tail, arachnid abdomen and legs, centaur body, merfolk tail, or similarly integrated anatomy. This does not mean merely having a tail, unusual feet, digitigrade legs, or ordinary humanoid legs with species traits.

- `extra_description_lower_body`: Concrete durable visual description limited to below the humanoid waist. It may hold lower-body-only markings or unusual details while `nonhuman_lower_body` is false. When `nonhuman_lower_body` is true, it owns the complete replacement lower-body structure and must not repeat numeric hips or legs. This field is used in normal/full-body and group image prompts but omitted from profile portraits. Use `""` when there is no distinct lower-body-only detail.

When `nonhuman_lower_body` is true, still author every clothing slot the character actually wears. The game omits generic numeric `hips` and `legs` phrases from image prompts, but clothing remains independent and must not be deleted merely because the anatomy is nonhuman.

##### Extra Description Deduplication

`extra_description` is only for visual traits that are not already captured elsewhere. Numeric body fields are converted into image-prompt phrases by the game, so repeating those same ideas in `extra_description` creates duplicated prompts and over-emphasized bodies.

When writing `extra_description`:

- First choose/fill the specific appearance fields.
- Then write `extra_description` only for leftover durable visual information that no other field can express.
- Never paste a prose-first body-design summary or complete silhouette description into `extra_description`. Planning prose must be translated into the dedicated fields and then discarded.
- Compare each `extra_description` phrase against every specific appearance field.
- Remove or rewrite phrases that duplicate numeric body fields, including breast size, bust silhouette, abs/stomach definition, shoulder width, arm muscle, hip width, leg length, height, and overall muscularity.
- Remove or rewrite phrases that duplicate skin, eye, hair, or notable-feature fields.
- Remove filler phrases such as `Attractive adult [race/species] with a distinctive silhouette`, `expressive face`, `design cues tied to her work as...`, or `[race/species] traits shaped around...`. These are not concrete visual traits and usually duplicate `race`, `role`, or personality.
- Do not write narrative prose using the character's name or pronouns. Do not explain traits with phrases such as `built from years of carrying armor`, `giving her an athletic silhouette`, or `showing the life of a veteran`. Record only the visible result when it is not represented elsewhere.
- Prefer a compact comma-separated list or one short sentence. Length is not a substitute for specificity.
- Keep genuinely additional integrated traits, species anatomy, scars/features not listed elsewhere, unusual proportions that are not represented by one numeric field, or source-faithful visual notes that cannot fit a specific field.
- At the end of character creation, perform a final pass over the whole appearance object and clean `extra_description` again after all numeric/string fields are final. Then assemble or mentally project the complete image prompt and remove any duplicated or prose-heavy fragment before export.

Bad `extra_description` when the specific fields already contain those traits:

```text
Athletic, rugged, and curvy with very broad shoulders, large breasts, deeply defined abs, wide hips, strong thighs, and powerful mechanic arms.
```

If `shoulders`, `chest`, `stomach`, `hips`, `legs`, and `arms` already encode those traits, keep only concrete unmapped traits, for example:

```text
Callused palms, old welding burns across both forearms, and a crescent scar below the left eye.
```

If nothing meaningful remains after deduplication, use `""` for `extra_description`.

#### Outfits And Starting Equipment

Outfits are immutable clothing presets stored on the character definition. They are not the same thing as the character's current runtime clothing. When a new game/import starts, the game copies the outfit referenced by `starting_outfit_id` into mutable runtime clothing. After that, the player, AI, spicy clothing removal system, location changes, outfit swaps, and manual edits should modify runtime clothing/outfit state, not the immutable outfit definitions. Never write post-play clothing changes back into `outfits`.

The spicy runtime may remove all top clothing, all bottom clothing, all clothing,
or exact individual clothing slots. Broad group removal and individual slot
removal are mutually exclusive for one participant in one update; never emit
both because the broad command already includes every slot in that group.
Individual removal uses exact structured clothing slot ids and never searches
garment descriptions for words. Image prompts add complete bare-top or
bare-bottom wording only when the corresponding structured covering group is
empty. Partial removal relies on the remaining structured clothing values and
must not add invented slot-specific exposure prose.

- `outfits`: Array of outfit objects. Every character must have at least one outfit, even if they only have a single outfit. A one-outfit character still needs `outfits: [{ "id": "default", "name": "Default", "clothing": { ... } }]` and `starting_outfit_id: "default"`. Do not replace `outfits` with a single `clothing` object. Do not leave it empty. Do not store active/current clothing here after play.

- `outfits[]`: Each outfit object is a reusable preset. It should describe one coherent outfit the character can wear, such as travel clothes, a guild uniform, armor, sleepwear, formalwear, casual clothes, work clothes, battle gear, a disguise, or a source-canon outfit. Do not create vague outfits like `"whatever fits the scene"` or `"armor or dress depending on mood"`. If a character needs multiple looks, create separate concrete outfit entries.

- `outfits[].id`: Stable short string id for the outfit inside this character definition. Valid examples: `"default"`, `"travel"`, `"formal"`, `"combat"`, `"guild_uniform"`, `"sleepwear"`, `"festival"`, `"disguise"`. Use lowercase snake_case or another stable simple string. Do not use a full sentence, display-only prose, user-facing description, random generated id, or the outfit's entire clothing list. This id is used by `starting_outfit_id` and runtime outfit switching.

- `outfits[].name`: Player-facing outfit name. Valid examples: `"Default"`, `"Travel Gear"`, `"Guild Uniform"`, `"Formal Dress"`, `"Combat Armor"`, `"Sleepwear"`. This should be readable in UI. Do not put mechanical notes, AI instructions, source spoilers, or conditional logic in the name.

- `outfits[].clothing`: Object using EmberAdventures clothing slots. Values are item descriptions or `null`. This object should describe the full preset as clearly as possible. Use precise garments/equipment, not broad vibes. Good examples: `"linen travel shirt"`, `"black leather corset"`, `"steel breastplate"`, `"knee-high buckle boots"`, `"silver serpent hairpin"`. Bad examples: `"sexy clothes"`, `"normal outfit"`, `"varies"`, `"whatever she wants"`, `"revealing but tasteful"`, `"armor or maid dress"`.

- Clothing slot keys should be stable equipment/body-wear slots. Canonical slots are `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `bra`, `undershirt`, `shirt`, `over_shirt`, `coat`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `underwear`, `pants`, `skirt`, `legwear`, `socks`, `feet`, and `other_accessory`. Use only slots that make sense. Do not author the legacy `hair` alias; use `hair_accessory`. A missing slot or `null` means nothing is defined for that outfit slot.

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

- `profile_image_presentations`: Application-managed pair of default profile-image slots named `male` and `non_male`. Each slot uses the same shape as `default_profile_image`; `male.male` must be `true` and `non_male.male` must be `false`. Character-creation AIs emit both blank slots exactly as shown and never invent URLs, local ids, prompts, or seeds. EmberAdventures fills them when images are generated or selected.

A character needs one real resolving hosted profile image for the male presentation and one for the non-male presentation before public publishing. Both `profile_image_presentations.male.url` and `profile_image_presentations.non_male.url` must resolve as images, and the character must also have the required alternate name/outfit group. Local import warns about missing presentation data and lets the player cancel or continue; public publishing is a hard rejection until every requirement is complete. `default_profile_image` remains the canonical/default presentation slot and should match one of the two presentation slots once the app has populated them. At runtime, a profile image is eligible only when its `male` value matches the character's active male/non-male presentation; never display the opposite bucket as a fallback. This metadata applies only to profile images. Normal/full-body, group, story, item, outfit, title-card, and other images must not receive a `male` field.

- `created_at`: Required ISO 8601 timestamp for when this definition was first created. Use the actual creation time for new entries; never leave it blank or use an empty placeholder. Preserve it unchanged when editing an existing definition.

- `updated_at`: Required ISO 8601 timestamp for the most recent definition change. Set it to the actual edit time for a new or modified entry. When reviewing without changing the definition, preserve the existing value.

- `profile_images`: Always emit `{ "active_image_id": "", "image_ids": [] }`.

- `images`: Always emit `{ "active_image_id": "", "image_ids": [] }`.

#### Voice

- `voice`: Always use `null`. Character-creation AIs do not have the installed TTS/screen-reader voice information needed to populate this correctly. Do not infer a voice bucket, assign a character name, use a voice actor, or ask the user for voice metadata during normal character creation.

#### Forbidden Definition Fields

Do not include these in `character_definition`: `kind`, `entity_kind`, duplicate name fields, `creator`, `creator_id`, `short_description`, `creator_notes`, `character_version`, `power`, `consent_state`, current `relationship_to_player`, current `trust`, current `attraction`, current `affection`, current `arousal`, current `state_of_mind`, current `physical_state`, current `pose`, `active_outfit_id`, active/current `clothing`, current `held_items`, current `inventory`, current `known_facts`, `profile_image_id`, `profile_images_list`, current location, scene lists, inspected status, invite status, party membership, NPC status, death state, or image inclusion state. `starting_outfit_id` is allowed because it identifies the immutable default preset; `active_outfit_id` is runtime state and is forbidden.


### Physical Attribute Phrase List

Use these embedded 0-10 descriptions when asking body-scale questions and when grounding final character body fields. For final JSON, almost always use numeric values from 0 to 10 instead of phrase strings. Lookup-table traits are `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, and `arms`. Use a custom string only when a specific exceptional physical detail cannot be represented by a table number, such as nonhuman anatomy or a concept-specific body structure. Chest is not special; it follows the same numeric-first rule as every other mapped trait.

Starting relationship stats `starting_trust`, `starting_attraction`, `starting_affection`, and `starting_arousal` are also base-10 values from 0 to 10. Do not use legacy 0-100 values for those fields.

`bodyStatKeys`: `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, `arms`.

`height`:

0. extremely short height
1. very short height
2. short height
3. slightly short height
4. a bit below average height
5. average height
6. a bit above average height
7. tall height
8. very tall height
9. towering height
10. super tall height

`muscular`:

0. no visible muscle definition
1. very soft build with almost no muscle definition
2. soft build with minimal muscle tone
3. lightly toned build
4. mildly athletic build
5. average muscle tone
6. athletic build with clear muscle tone
7. muscular build with defined arms and legs
8. very muscular build with strong visible definition
9. heavily muscled physique with prominent definition
10. extremely muscular bodybuilder physique

`shoulders`:

0. extremely narrow shoulders
1. very narrow shoulders
2. narrow shoulders
3. slightly narrow shoulders
4. a bit below average shoulder width
5. average shoulder width
6. moderately broad shoulders
7. broad shoulders
8. very broad shoulders
9. powerfully broad shoulders
10. extremely broad shoulders

`maleChestPhrases`:

0. flat narrow pectorals
1. slight pectoral definition
2. lean defined chest
3. athletic pectorals
4. firm muscular chest
5. broad muscular chest
6. large powerful pectorals
7. very large muscular pectorals
8. huge bodybuilder pectorals
9. massive heavily defined pectoral muscles
10. absurdly massive hyper-muscular pectorals

`femaleChestPhrases`:

0. full large B-cup breasts, naturally rounded with modest projection
1. full C-cup breasts, rounded and moderately prominent
2. full D-cup breasts, prominently rounded and clearly busty
3. full DD/E-cup breasts, very full with substantial projection
4. F/G-cup breasts, large, full, and heavy-looking
5. H/I-cup breasts, very large and noticeably top-heavy
6. J/K-cup breasts, huge and extremely full, each approaching the size of her head
7. L/M-cup breasts, enormous and heavily rounded, each approximately the size of her head
8. N/O-cup breasts, massive and oversized, each visibly larger than her head, dominating her upper-torso silhouette
9. R/S-cup breasts, impossibly huge and overwhelmingly top-heavy, each approaching the visible size of her upper torso
10. Z-cup breasts, absurdly oversized with impossible fantasy proportions, each approximately the visible size of an entire torso, extreme impossible bust-to-waist proportions, overwhelmingly top-heavy

When structured clothing covers the chest, append `fully covered by the described clothing` to the selected base phrase. Do not maintain or author a second clothed chest scale. SFW and NSFW image modes preserve the same authored chest number.

`stomach`:

0. very sunken stomach
1. flat soft stomach
2. soft stomach
3. slightly soft stomach
4. natural average stomach
5. average stomach
6. firm stomach
7. toned abs
8. defined abs
9. deeply defined muscular abs
10. extremely ripped abdominal muscles

`hips`:

0. extremely narrow hips
1. very narrow hips
2. narrow hips
3. slightly narrow hips
4. a bit below average hips
5. average hips
6. curvy hips
7. wide hips
8. very wide hips
9. extremely wide curvy hips
10. dramatically exaggerated wide hips

`waist`:

0. impossibly tiny nonhuman waist
1. extremely tiny waist
2. very thin waist
3. thin waist
4. slightly thin waist
5. average waist
6. slightly wide waist
7. wide waist
8. very wide waist
9. extremely wide waist
10. massive waist

`legs`:

0. extremely short legs
1. very short legs
2. short legs
3. slightly short legs
4. a bit below average leg length
5. average leg length
6. slightly long legs
7. long legs
8. very long legs
9. extremely long legs
10. dramatically long legs

`arms`:

0. extremely thin arms
1. very thin arms
2. thin arms
3. slightly thin arms
4. a bit below average arms
5. average arms
6. toned arms
7. muscular arms
8. very muscular arms
9. heavily muscled arms
10. extremely muscular arms

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

Do not ask for preference slots that do not map to EmberAdventures character fields unless the answer clearly informs existing fields. Waist is a mapped 0-10 body field, so collect a numeric waist range when body-scale preferences are being configured. Keep broader body-shape notes in `body_preferences.stomach_and_body_shape_notes` only when they add information not represented by the numeric stomach, hips, and waist scales.

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

For body scales, list the relevant embedded 0-10 descriptions and ask for either a range, a single number, or a natural-language answer. Use the embedded physical-attribute phrase list for wording. Do not use joke descriptions.

Example:

```text
d. What chest-size range do you usually like for adult female characters?
   Answer with a range like 2-6, a single number like 5, or words.
   0. roughly B-cup breasts
   1. full B-cup breasts
   ...
   10. absurdly oversized breasts, impossibly huge breasts, extreme hyper-voluptuous bust
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

looks_and_body (10)
looks.height -> body_preferences.height_range -> preferred height range
looks.muscular -> body_preferences.muscular_range -> preferred muscularity range
looks.shoulders -> body_preferences.shoulders_range -> preferred shoulder range
looks.chest -> body_preferences.chest_range -> preferred chest range
looks.stomach -> body_preferences.stomach_range -> preferred stomach range
looks.hips -> body_preferences.hips_range -> preferred hip range
looks.waist -> body_preferences.waist_range -> preferred waist range
looks.legs -> body_preferences.legs_range -> preferred leg range
looks.arms -> body_preferences.arms_range -> preferred arm range
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
    "default_source": "Player",
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
    "muscular_range": null,
    "shoulders_range": null,
    "chest_range": null,
    "stomach_range": null,
    "stomach_and_body_shape_notes": "",
    "hips_range": null,
    "waist_range": null,
    "legs_range": null,
    "arms_range": null,
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

- `source`: `"Player"`
- `creation_tool`: the actual current tool/model/reasoning label, never a copied example label
- `genres`: `["fantasy"]` only when the concept is clearly broad fantasy and no more accurate approved set is known
- `nsfw`: `true` only when the character definition itself is inherently
  explicit/NSFW as stored or displayed; otherwise `false`
- `loli`: `false`
- `can_die`: `false`
- `voice`: `null`

For original characters, always use `source: "Player"`. Do not ask the user for a default original-character source label. Do not leave `source`, `creation_tool`, approved `genres`, `nsfw`, or `loli` null. `nsfw` and `loli` must be true or false. Do not emit or ask about `creator` or `creator_id`; EmberAdventures assigns both during import.

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
- Make batches diverse in race/species, profession, personality, boldness, silhouette, outfit, and tone unless preferences request a narrower set.
- Include mismatch/subversion only when preferences or the prompt support it.
- Avoid making every character a generic archetype.
- Avoid making every character overpowered unless preferences or the current request support it.
- Use the user's job/concept preferences from the preference file.
- Follow `jobs_and_concepts.role_style_preference` and the current request when deciding whether a role should be ordinary, fantastical, setting-grounded, origin-driven, or varied. Do not hardcode one style for all users.
- If the user rejects a role or concept, use their explanation to revise the relevant preference instead of assuming every rejection means the role was too ordinary or job-like.
- Follow `species_and_race.human_race_detail_preference`. Use a specific race/ethnicity/visual ancestry when that preference requests it; otherwise infer, vary, omit, or ask as recorded.

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

Use preference-file personality and boldness guidance. Make personalities durable and specific, not just current mood or a list of sexual behaviors. Boldness, aggression, and dominant/submissive dynamics are independent: a character may be extremely bold and submissive, quietly dominant, gentle and forward, or aggressive but romantically reserved.

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
