---
name: emberadventures-character
description: Authoritative base skill for EmberAdventures character definitions. Use directly for characters, preference intake, proposals, character JSON creation, review, repair, and library maintenance.
---

# EmberAdventures Character

## Skill Maintenance

This section is for guidance on maintaining/updating this skill, and is not applicable when just using the skill.

This skill is only for character definitions. Do not add information that is not part of a character definition.

Never include information about image metadata or voice metadata anywhere outside this Skill Maintenance section.

This skill can use a separate preferences file. It is the only allowed file reference. The skill should otherwise be completely self-contained. Never include user preferences in the skill itself.

## Version and Update Check

Current skill version: `1.0.26`.

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
higher than High effort is unlikely to produce significantly better results, and is wasteful
for the user's paid usage. If higher than High effort, strongly suggest to reduce to High 
effort. This is a quality recommendation, not a hard gate; character creation should still 
work on lower models unless the output is visibly invalid.

## Private Preference File

Preference file default path:
`${CODEX_HOME}/private/emberadventures-character-preferences.json`, or
`~/.codex/private/emberadventures-character-preferences.json` when
`CODEX_HOME` is unset.

The first step for this skill is to locate and read that file.

If the file does not exist, enter preference-intake mode before anything else.

If the file exists, inspect intake state before using preferences:

- Use ask-missing mode by default. Ask only missing or ambiguous preference slots that are relevant to the current request, the next useful global calibration, or a user-requested preference audit.
- If a required safety/default slot is missing, ask the next missing required question before generating explicit/NSFW originals.
- Do not block character creation on broad optional setup. Infer optional preferences from the existing file and the current request unless the missing answer would materially change the character.
- Do not treat a preference file as complete just because it exists, but do not run a full questionnaire just because optional slots remain.
- For large batches meant to populate a setting, the requested premise and roles
  override private preferences unless the user explicitly says to apply those
  preferences. If the user gives a split such as "use my preferences for 25%
  only," obey that split exactly.
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

b. What target genders do you usually want for newly created characters?
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

- Ask character-role questions before relationship questions. The character creator can create player characters, companions, and NPCs, so do not assume every character needs a relationship to the player.
- Preferred relationship intake wording: "What type of character are you creating? Is it a player character, companion, or NPC? If it is a companion or NPC, what is the relationship to the player?"
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

Use the next letters after the first batch when listing unanswered follow-up questions. If the user still does not answer them, mark them skipped.

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

- `source`: `"Original"`
- `creation_tool`: the actual current tool/model/reasoning label, never a copied example label
- `genres`: `["fantasy"]` only when the concept is clearly broad fantasy and no more accurate approved set is known
- `nsfw`: `true` only when the character definition itself is inherently
  explicit/NSFW as stored or displayed; otherwise `false`
- `loli`: `false`
- `can_die`: `false`

Always use `source: "Original"`. Do not ask the user for another source label. Do not leave `source`, `creation_tool`, approved `genres`, `nsfw`, or `loli` null. `nsfw` and `loli` must be true or false. Do not emit or ask about `creator` or `creator_id`; EmberAdventures assigns both during import.

Before final export, verify that saved `creation_tool` metadata describes the current tool/session. If it is missing, stale, or unverifiable, ask for the actual tool name, model number, and intelligence/reasoning level, then format the label as `{tool} {model} ({intelligence})` when intelligence is present. Do not silently use the skill's example or a label saved by a different model/session.

## NSFW

- Spicy characters must be adults and physically adult.
- Never create sexualized minors or minor-coded characters.
- Characters can be extremely sexually forward when the user requests that style or preferences clearly set that as the default.

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

For newly generated characters, use a first and last name by default unless the user explicitly specifies a one-word/nonstandard name or the concept strongly requires a different naming convention.

Do not rename existing or user-specified characters unless the user asks for edits. Manual/pre-existing names are allowed to be one-word or nonstandard.

For batches and large character groups, use unique surnames unless characters
are intentionally related. Do not reuse
surnames from player options, examples, templates, skill references, or
unrelated existing characters. If two characters share a surname, record the
relationship clearly in durable known facts; otherwise rename one before final
export.

## Proposal Format

When proposing character options before final JSON, follow
`proposal_preferences`. If it is unanswered, use this compact neutral fallback:

```text
Name (race)
Description.
```

Include the race/species parenthetical only when the saved preference requests it or when it materially helps compare concepts. For humans, obey `human_race_detail_preference` rather than always forcing an ethnicity into the proposal.

## Personality

Use preference-file personality and boldness guidance. Make personalities durable and specific, not just current mood or a list of sexual behaviors. Boldness, aggression, and dominant/submissive dynamics are independent: a character may be extremely bold and submissive, quietly dominant, gentle and forward, or aggressive but romantically reserved.

For spicy characters, combine sexuality with identity: job, flaws, humor, fears, habits, principles, contradictions, and social style.

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
  runtime instructions, or visual traits in it.
- `species`, `race`, and `ancestry` own biological identity only.
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
- Clothing prompt order is: `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `undershirt`, `shirt`, `over_shirt`, `coat`, `bra`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `pants`, `skirt`, `legwear`, `underwear`, `socks`, `feet`, `other_accessory`.

## Practical Clothing And Items Guidance

The field contract above defines the schema. This section adds workflow and
image-prompt guidance without adding alternate clothing fields.

- Clothing slots are precise item slots. Do not write ambiguous values like "adventuring outfit or maid clothes depending on scene."
- Create one or more precise outfit presets according to the request and saved wardrobe preferences. Never collapse multiple requested looks into one ambiguous outfit.
- Treat clothing like inventory/equipment slots. Do not move removable garments into prose fields.
- During preference intake, ask what default outfit guidance should be saved for newly created characters. Offer options such as:
  - `0. You decide how many outfits based on the character`
  - `1. Make 1 normal outfit only unless I ask for more`
  - `2. Make 10 outfits for every character`
  - `3. Make a fixed wardrobe pattern, such as 1 normal, 1 formal, 1 casual, 1 sexy, 1 swimsuit, 1 cosplay, and variants`
  - `4. Free answer`
- Save the answer in `clothing_and_style.outfit_count_guidance`, `default_outfit_plan`, `normal_outfit_count`, `sexual_outfit_count`, `required_outfit_types`, `disallowed_outfit_types`, and `sexual_outfit_notes` as applicable. Use those saved preferences when creating characters unless the current request overrides them.
- Clothing slots are only for worn/removable items. Do not put tattoos, scars,
  birthmarks, body paint, facial markings, horns, claws, fangs, tails, wings,
  skin color, hair, eyes, body shape, anatomy, or other physical traits in any
  clothing slot, including `other_accessory`.
- If a physical feature is visible because of the outfit, keep the outfit in
  `clothing` and place the physical feature in `appearance.extra_description`.
- Fill every garment the character actually wears in each preset, including ordinary underlayers. Bras and underwear do not cause image-generation problems. Include them whenever the character wears them, and omit them only when the character intentionally is not wearing them in that outfit.
- Use `starting_inventory`, `starting_known_facts`, and `starting_held_items` to make the character concrete and usable in game.
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

## Character Schema And Rules

This skill must be shareable as a standalone skill. Do not depend on any shared EmberAdventures reference files at runtime. The only external file this skill should require is the optional private preference file described in this skill.

Follow the preference-file process near the top of this skill. Do not ask a second preference-file question here.

### Required Metadata

Every character-library definition must include `source: "Original"`, non-null
`creation_tool`, approved `genres`, boolean `nsfw`, boolean `loli`, and boolean
`can_die`. `creation_tool` records the actual tool/model/reasoning label.
`kink_tags` is optional searchable metadata.
Use `can_die: false` by default for standalone definitions. The field
contract below is authoritative for meanings, allowed shapes, and runtime-field
exclusions. Do not emit `creator` or `creator_id`; EmberAdventures assigns
creator ownership during import. This is an internal maintenance rule: never
add creator fields back to this skill, never show them in examples, and never
ask the user for a creator name or alias during preference intake.

### Character Export Shape

The field contract below is authoritative. Keep the example and contract synchronized; there are no exception rules for older examples.

Use `character_definition` as the single immutable/default character object. Do
not use other top level fields.
For creating batches of characters, use a characters array as shown below, or make a separate file for each character. Do not add any other top level fields to the export. Ask the user if they want separate files or 1 file with all characters in it when creating multiple at once. The game is capable of importing either, but for batches, it will import all of them, so a batch file should only be created if it's intended to import all of them into the game together.
```json
{
  "characters": [
    {
      "character_definition": {
        ...
      }
    }
  ]
}
```

Before final export, run a field-purpose and process-leakage pass. For every
field, ask what the field is for, how EmberAdventures uses/displays it, whether the
value serves that purpose, and whether it can be clearer or match the intended use better.
Character information should never mention how the character will be or how it will change in 
the future. Character definitions are meant to be a snapshot of a character in a specific 
point in time. You should describe them exactly as they are at that moment, and you can also 
include the backstory/history of that character. The only future related information
that is allowed is future aspirations, desires, and goals.

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
      "species": "human",
      "race": "specific appearance/race/ethnicity descriptor",
      "ancestry": "optional lineage/heritage descriptor",
      "height": 5,
      "muscular": 5,
      "shoulders": 5,
      "chest": 5,
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
    "created_at": "<actual ISO 8601 creation timestamp>",
    "updated_at": "<actual ISO 8601 update timestamp>"
  }
}
```

### Character Definition Field Contract

Use this contract when creating EmberAdventures character definitions. Do not add
any extra fields to the character file unless they are present in the example
above or explicitly described in the field rules below. Standalone library
characters and characters embedded in stories intentionally use different
subsets of this contract; follow the boundary below rather than copying every
standalone field into a story.

#### Standalone And Story-Embedded Fields

The complete export example is a standalone character-library definition.
Standalone definitions own their public discovery metadata and their optional
character-launcher experiences.

The following fields are standalone-only and must be omitted from every
story-embedded character definition, including players, party characters, NPC
shells and `full_character` definitions, and future-cast shells and
`full_character` definitions:

- `catalog_hook`
- `genres`
- `kink_tags`
- `chat_story`
- `chat_opening_message`
- `chat_starting_location`
- `chat_story_template`

Story-embedded characters inherit discovery and content classification from the
story. A story uses its own title, description, opening, state, and objectives;
it never carries a nested standalone Chat launcher on one of its characters.
This also prevents recursive stories inside stories.

All other approved authored character fields follow their normal field rules in
both contexts unless a later rule explicitly says otherwise. Runtime-only fields
remain forbidden in both contexts.

#### Field Purpose And Process-Leakage Standard

For every character field, ask:

1. What is this field for in EmberAdventures?
2. How does EmberAdventures use or display it?
3. Does this value serve that purpose?
4. Could it be shorter, clearer, or less like process text?

Do not copy instructions meant for Codex/the character creator into character
fields. Examples of forbidden process leakage:

- `current app compatible`, `clean export`;
- `should not appear before X`, `introduce later`;
- `will become a companion`, `will become romance partner`, `unlock later`;
- `do not spoil`, `hide this from the player`, `use in prompt only`;
- field explanations such as `this is the active outfit` or `used by image gen`.

Do not put those instructions in the character definition. Character fields
should describe the character: identity, body, outfit presets, starting/default
state, starting inventory, and durable facts.

#### Field Rules

- `version`: Character definition schema version. Set it to 1. Do not increment it when editing character content.

- `id`: Stable character id string. Use a readable slug such as `"akane-fujimori"` or `"character-akane-fujimori"` according to the local file/library convention. Do not use random garbage when a readable stable id can be created from the character name.

- `name`: The character's exact proper name as shown to the player. For newly generated characters, use a first and last name by default unless the user explicitly specified a one-word/nonstandard name or the setting strongly requires it. Preserve existing/manual names exactly. Do not append tags such as `(adult)`, `(loli)`, `(NPC)`, `(party)`, roles, or version labels. Example valid: `"Akane Fujimori"`. Example invalid: `"Akane Fujimori (adult)"`.

- `source`: Always use `"Original"`. Do not ask for or infer another source label.

- `creation_tool`: Tool/model label used to create or finalize the entry. Use a factual final readable string in the form `"<Tool> <Model Number> (<Reasoning or Intelligence Level>)"` when those parts are available. Do not copy a model label from an example. Do not leave null.

- `loli`: Boolean true or false. `true` means either the character is under 18 or the character is 18+ but looks under age. Create paired accurate/loli and adult-looking versions only when the user requests paired variants or the stored preferences explicitly require them. When paired, they share the exact same `name`; only `loli`, `age`, and age-appropriate physical description should differ. Do not add `(loli)`, `(adult)`, or similar tags to the name.

- `nsfw`: Boolean true or false. `true` should be used very sparingly. There are 2 definitions for nsfw in Ember Adventures. There is a visible definition and a descriptive definition. A character that meets either definition is considered nsfw. A character that meets neither definition is considered sfw.
Visible nsfw definition: Visible nipples on characters with breasts OR visible genitals OR visible anus. 
loli characters are never allowed to be nsfw, and are never allowed to have less than underwear, a top and a bottom piece of clothing to cover them well. Sexualizing loli characters is considered completely unacceptable by EmberAdventures and is not allowed in any way. Reject any request by a user to create a loli character that is sexualized or nsfw in any way.
Descriptive definition: Explicit, vulgar, sexual language such as dick, pussy, cock, cunt or similar used to describe a character other than in the body size description when the description is clearly just to describe size/shape accurately. For example, "Ridiculously massive, cartoonishly large boobs" is perfectly fine. It's just there to describe size for the image model. Mentioning nipple size or similar is considered nsfw. Penis size is also not considered nsfw as long as the description is clearly just to describe size. Similar descriptions for breasts and penises are fine and not inherently nsfw. The image prompt hides any description of genitals, breasts and similar unless in nsfw mode, so having them in the description will not create nsfw images.
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

Every newly authored outfit must include `nsfw: true` or `nsfw: false`. Mark an outfit NSFW when its purpose is sexual display, fetish presentation, or exposing as much as possible even if nipples, genitals, and anus remain narrowly covered. Ordinary attractive, fitted, fashionable, swimsuit, or revealing clothing can remain SFW when sexual display is not its primary purpose. A character with `nsfw: false` must have an SFW starting outfit and at least one SFW outfit in both canonical and fallback presentations. Missing legacy outfit flags inherit the character-level `nsfw` value.

Loli or under-18 characters must have `nsfw: false`, an empty `starting_nsfw_known_facts`, and only SFW outfits. Reject any request that violates this rule.

- `can_die`: Boolean internal plot armor. Always set this to false for standalone characters.

### Gender flexibility system
Every character is required to have 2 gender presentations. One male and one non-male (usually female). That means that each character has 2 sets of gender related fields. This is the full list of fields that have associated fallbacks for gender swapping:
name -> fallback_name
outfits -> fallback_outfits
starting_outfit_id -> fallback_starting_outfit_id
The character's gender is whatever default gender the character is supposed to be. The point being for someone who is attracted to all genders, the default genders will be shown. For someone who is only attracted to women, all characters will become women by women not changing and all others being gender swapped to female.
`romanceable` determines if the character's gender should match the player's preferred gender(s). There is also a setting that will force all characters to swap to the player's preferred gender(s) regardless of `romanceable`. That is why all characters must have both a male and non-male presentation. Non-binary genders are treated no different as female. trans-male is also considered male. All other genders are considered non-male. When choosing the default gender for a character, it is perfectly acceptable to use a non-binary gender, just make sure you understand what the fallback gender will be (male for all non-binary genders except trans-male). This means that if the character presents as male, it's generally best to use male or trans-male as the gender instead of something like non-binary to prevent confusion.

- `romanceable`: Required boolean. All standalone characters should have romanceable set to true.

- `fallback_name`, `fallback_outfits`, and `fallback_starting_outfit_id`: Required atomic opposite male/non-male presentation group for the same character. See "Gender flexibility system" above. Prefer a fallback name that retains at least the first letter, and preferably the first two letters, of the canonical name so the character remains recognizable. A natural, setting-appropriate authored name is more important than preserving letters when that would make the result strained. Fallback outfits must be nonempty and remain recognizable equivalents: preserve each outfit's purpose, colors, equipment, status, and general visual identity while changing only gendered construction, underwear, fit, and similar presentation details unless a larger change is specifically justified. `fallback_starting_outfit_id` must reference one of those outfits. Appearance, personality, facts, relationships, and all other identity fields remain unchanged. Local import and public publishing both reject the character until this group is complete.

- `fallback_gender`: Only required on futanari characters. Use exactly `"male"` or `"female"` to decide which presentation is used when the player's selected preferences include male and female but not futanari. Omit it for non-futanari characters. 

- `genres`: Approved broad genre/search tags for standalone character-library definitions. Approved values are `anime`, `fantasy`, `sci-fi`, `modern`, `historical`, `romance`, `adventure`, `action`, `comedy`, `drama`, `mystery`, `thriller`, `horror`, `dark`, `cozy`, `slice of life`, `superpower`, `isekai`, `school`, `workplace`, `political`, `war`, `crime`, `mythology`, `supernatural`, `post-apocalyptic`, `western`, `cyberpunk`, `steampunk`, and `harem`.

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

- `age`: Age in number of years as an integer. Do not use ranges, words, unknown, approximate text, or decimals. If the character is not marked as loli, it must be 18 or older, no exceptions. All characters under 18 must be marked as loli.

- `gender`: The default gender of the character. Some genders are recognized as exact strings. If the character is one of these recognized genders, write their gender exactly as it appears in this list: `"male"`, `"trans-male"`, `"trans male"`, `"futanari"`, `"futa"`, `"female"`. `"trans-male"` and `"trans male"` are treated identically. `"futanari"` and `"futa"` are treated identically. `"male"` and `"trans-male"` are the only male presenting genders. If the character is intended to be male presenting, you must use one of those two. If the character's gender falls outside the list, use any string that makes sense to describe the gender. It will be treated as female (non-male) by the game engine and it will use female-presenting language such as breasts. `"futa"` and `"futanari"` identify futanari characters; they use the female mechanics except that they have a penis. Every other value, including female, non-binary, trans female, trans non-binary, and free-text identities, uses the female mechanics bucket. Do not infer gender from `kink_tags`, `tags`, `sexual_preferences`, appearance prose, role, or any other field. Import and publish validation reject exact futa/futanari metadata on a character whose `gender` is not futa or futanari. Do not use this field for relationship roles.

- `appearance.penis_size`: Required integer value on all characters regardless of gender in case they are gender swapped to male or futanari. Do not set to 0 just because the default gender is not male. Choose this value from 0 to 10 based on what the character's penis size should be if they are male or gender swapped to male. Runtime ignores it unless the current presentation is male or futanari, but it must already exist because runtime gender adaptation can change a character's presentation. Below are the meanings of the numbers 0 through 10.
0.  micropenis, extremely tiny, 1 inch long and 0.6 inches wide
1.  tiny penis, 2 inches long and 0.8 inches wide
2.  very small penis, 3 inches long and 1 inch wide
3.  small penis, 4.5 inches long and 1.2 inches wide
4.  moderately sized penis, 6 inches long and 1.35 inches wide
5.  large, long penis with average thickness, 7 inches long and 1.5 inches wide
6.  very large, thick penis, 9 inches long and 1.75 inches wide
7.  massive fantasy-sized penis, 1 foot long and 2 inches wide
8.  gigantic fantasy-sized penis with exaggerated thickness, 1.5 feet long and 2.75 inches wide
9.  colossal fantasy-sized penis with extreme thickness, 2 feet long and 3.5 inches wide
10. absurdly enormous extreme-fantasy-scale penis, 3 feet long and 5 inches wide

- `role`: Extremely short role, specialty, title, or class description. This field is player-facing and more like a label than a description. It has very limited space to be displayed in game. General durable description usable as a title, rank, position, profession, specialty, or group function. Examples: `"Guild Registrar"`, `"healer"`, `"Queen"`, `"Noble"`, `"Duke"`, `"Assassin"`.

- `personality_description`: Durable personality and behavior summary. Describe how the character tends to think, act, flirt, fight, negotiate, or handle pressure. This is meant as permanent guidance for the player's personality, not temporary mood or state. This field is used by the ai to determine how this character acts and speaks.

- `speech_style`: Durable description of how the character speaks. Describe how the character usually speaks. This field is used by the ai to determine how this character speaks.

- `boldness`: Immutable 1-10 integer describing how readily and directly the character initiates romantic or sexual interest. Numeric `0` and values outside `1-10` are invalid and must be fixed before export. A custom string is also valid when the character's boldness does not match one of the provided boldness levels. However, in general, you should try to use the numbers to allow players to increment/decrement the boldness easily. If using a string, do not reference the numeric scale. The numbered values are converted to their associated strings. The AI is not aware of the number-to-string mappings. Use the same scale for every gender; gender adaptation never changes personality.
  - `1`: very reserved; almost never initiates romance or intimacy and waits for unmistakable mutual interest.
  - `2`: reserved; expresses interest subtly and waits for clear encouragement before initiating.
  - `3`: cautious; may initiate small compliments or mild flirting, then pauses to judge the response.
  - `4`: mildly forward; comfortably initiates light flirting or closeness when the context supports it.
  - `5`: balanced; can initiate direct interest, flirting, invitations, or welcomed physical closeness.
  - `6`: confident; readily initiates romantic tension, invitations, and physical closeness when attraction supports it.
  - `7`: very forward; states attraction directly and actively proposes escalation while watching for a clear response.
  - `8`: highly forward; readily initiates explicit flirting, intimate invitations, or consensual exposure when appropriate.
  - `9`: extremely forward; clearly proposes sexual escalation and communicates desire directly, while waiting for response before meaningful escalation.
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
- Player person term: `|[player_person_term]|`
- Player honorific: `|[player_honorific]|`
- Player formal address: `|[player_formal_address]|`
- Player monarch title: `|[player_monarch_title]|`
- Player royal-heir title: `|[player_royal_heir_title]|`
- Player noble title: `|[player_noble_title]|`
- Player spouse term: `|[player_spouse_term]|`
- Player parent term: `|[player_parent_term]|`
- Player child term: `|[player_child_term]|`
- Player sibling term: `|[player_sibling_term]|`
- Player uncle/aunt term: `|[player_uncle_aunt_term]|`
- Player nephew/niece term: `|[player_nephew_niece_term]|`

Player gendered terms resolve to the same male/non-male word pairs shown for the corresponding character references above.

Player pronoun and gendered-term references follow the same `_cap` rule. For example, `|[player_subject_pronoun_cap]|` becomes `He` or `She`.

- `starting_trust`: Starting trust from 0 to 10. Use a number. `0` means no trust; `10` means complete trust at start.

- `starting_attraction`: Starting attraction from 0 to 10. Use a number. This is initial attraction toward the player/protagonist. It is not an attractiveness score.

- `starting_affection`: Starting affection from 0 to 10. Use a number. This is initial emotional warmth/bond, not current romance progress after play.

- `starting_arousal`: Starting arousal from 0 to 10 when an arousal default is relevant. Use `null` or omit only for characters where arousal does not apply. Do not store post-play arousal here.

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

- `species`: Biological/species label. Examples: `"human"`, `"slime"`, `"elf"`, `"demon"`, `"arachne"`. Do not include gender information in `species`.

- `race`: Specific human race/ethnicity/visual ancestry when applicable, or a species subtype if useful. Follow `species_and_race.human_race_detail_preference`: specify, vary, infer, omit, or ask as recorded instead of forcing ethnicity into every human definition. Examples when specificity is wanted: `"Black"`, `"East Asian"`; `species` and `race` can feel a lot like the same thing. When uncertain, you can put either information into `species`, and `race` can be blank. Never have duplicate information between `species` and `race`.

- `ancestry`: Optional lineage/heritage detail distinct from race/species. Examples: `"half-demon bloodline"`, `"old noble family"`, `""`. Likely to be empty for most characters unless ancestry is a large part of the character's identity. Don't ever include information from `species` or `race` in `ancestry`.

- `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, `arms`: Body scale fields. Integer values make the editor behave like a predictable slider and let users increase or decrease a trait by one step. Use a custom string only for a specific exceptional anatomy or visual requirement that no mapped value can represent. When a string is necessary, make the intended scale position clear in the wording or nearby design context. `chest` follows the same rule as every other mapped body fields except it differs by gender.

- `skin_color`, `eye_color`, `hair_color`, `hair_length`, `hair_type`: Persistent visual details. Use concrete visual wording. Do not write personality or clothing.

- `extra_description`: Optional remainder field for concrete, durable visual traits that do not fit another appearance field. Examples include `"scar across left collarbone"`, `"transparent mint-green slime body"`, `"filed canines"`, or `"butterfly tattoo on right cheek"`. It is not a general physical-description field. Do not include temporary dirt, arousal, clothing damage, scene effects, personality, mood, pose, health, role, backstory, or explanations of how the character acquired a body type. Do not repeat details already represented by the other appearance fields. For details that are only on the lower body, do not include them here, such as `"tattoo on right ankle"`. All lower-body-specific descriptions belong in `extra_description_lower_body`. Use `""` when there is no distinct extra description needed.

- `nonhuman_lower_body`: Boolean. This field should only be set to true if the character does not have humanoid legs. Things like having hooves on humanoid legs are not a reason to set this to true. Use `true` only when the character's normal humanoid hips and legs are replaced by a distinct nonhuman lower body, such as a serpent tail, arachnid abdomen and legs, centaur body, merfolk tail, or similarly integrated anatomy. This does not mean merely having a tail, unusual feet, digitigrade legs, or ordinary humanoid legs with species traits. Setting `nonhuman_lower_body` to true causes the `waist` and `legs` slots to be completely ignored, meaning all lower body information about the `waist` and `legs` must be included in the `extra_description_lower_body`. For example, an arachnid character with humanoid legs and extra spider legs should not set `nonhuman_lower_body` to true, but a character with a complete arachnid lower body with no humanoid legs should set it to true and include all lower body information in `extra_description_lower_body`.

- `extra_description_lower_body`: The same rules for `extra_description` are applicable for `extra_description_lower_body` except only lower body specific information should be included. Do not duplicate information from `extra_description`. Concrete durable visual description limited to below the humanoid waist. It may hold lower-body-only markings or unusual details while `nonhuman_lower_body` is false. When `nonhuman_lower_body` is true, it owns the complete replacement lower-body structure and must include the information that would normally be included in the `waist` and `legs` fields. Do not mention numeric values from the `waist` or `legs` fields. This field is used in normal/full-body and group image prompts but omitted from profile portraits. Use `""` when there is no distinct lower-body-only detail needed.

When `nonhuman_lower_body` is true, still author every clothing slot the character actually wears. The game omits generic numeric `hips` and `legs` phrases from image prompts, but clothing remains independent and must not be deleted merely because the anatomy is nonhuman. Put clothing in the most reasonable existing slot for it. Do not delete clothing just because there isn't a slot that fits it perfectly. Put it in the best slot available.

##### Extra Description Deduplication

This section applies to information in both `extra_description` and `extra_description_lower_body`. Each time it talks about `extra_description`, it also applies to `extra_description_lower_body`.

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
- Keep genuinely additional integrated traits, species anatomy, scars/features not listed elsewhere, or unusual proportions that are not represented by one numeric field.
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

Outfits are immutable clothing presets stored on the character definition. When starting a game, the active outfit referenced by `starting_outfit_id` is copied into the character's runtime clothing.

- `outfits`: Array of outfit objects. Every character must have at least one outfit. A one-outfit character still needs `outfits: [{ "id": "default", "name": "Default", "clothing": { ... } }]` and `starting_outfit_id: "default"`. Do not replace `outfits` with a single `clothing` object. Do not leave it empty. Animal, monster, spirit, slime, natural-form, or otherwise unclothed characters still need at least one concrete outfit entry. If a character is intentionally naked, include only the underwear slots and have them empty strings, `""`. For non-human or demi-human characters, you can use natural clothing in slots such as a turtle shell for a turtle-human character if desired. Do not invent slots such as `full_body`; unsupported slots will throw an error. Never use `{}` as the clothing object.

- `outfits[]`: Each outfit object is a reusable preset. It should describe one coherent outfit the character can wear, such as travel clothes, a guild uniform, armor, sleepwear, formalwear, casual clothes, work clothes, battle gear, a disguise, or another kind of outfit. Do not create vague outfits like `"whatever fits the scene"` or `"armor or dress depending on mood"`. Do not use non-deterministic wording such as `"White or Black"` or `"could"` or `"roughly"` or `"maybe"`. If a character needs multiple looks, create separate concrete outfit entries. Outfits should include all layers that would actually be in the outfit, not just the outer layer. Underwear should be included unless the outfit is intended to not have underwear.

- `outfits[].id`: Stable short string id for the outfit inside this character definition. Valid examples: `"default"`, `"travel"`, `"formal"`, `"combat"`, `"guild_uniform"`, `"sleepwear"`, `"festival"`, `"disguise"`. Use lowercase snake_case or another stable simple string. Do not use a full sentence, display-only prose, user-facing description, random generated id, or the outfit's entire clothing list. This id is used by `starting_outfit_id` and runtime outfit switching.

- `outfits[].name`: Player-facing outfit name. Valid examples: `"Default"`, `"Travel Gear"`, `"Guild Uniform"`, `"Formal Dress"`, `"Combat Armor"`, `"Sleepwear"`. This should be readable in UI. Do not put mechanical notes, AI instructions, or conditional logic in the name.

- `outfits[].nsfw`: Required boolean on every newly authored outfit. Use the outfit-purpose test above. This flag controls SFW UI visibility, AI context, equipping, shops, rewards, and image generation; it does not replace character-level `nsfw`.

- `outfits[].clothing`: Object using EmberAdventures clothing slots. Values are item descriptions or `null`. This object should describe the full preset as clearly as possible. Use precise garments/equipment, not broad vibes. Good examples: `"linen travel shirt"`, `"black leather corset"`, `"steel breastplate"`, `"knee-high buckle boots"`, `"silver serpent hairpin"`. Bad examples: `"sexy clothes"`, `"normal outfit"`, `"varies"`, `"whatever she wants"`, `"revealing but tasteful"`, `"armor or maid dress"`.

- Clothing slots must come only from this supported list: `hat`, `hair_accessory`, `face`, `ears`, `neck`, `shoulders`, `bra`, `undershirt`, `shirt`, `over_shirt`, `coat`, `back`, `hands`, `right_wrist`, `left_wrist`, `right_fingers`, `left_fingers`, `waist`, `belt_accessory`, `underwear`, `pants`, `skirt`, `legwear`, `socks`, `feet`, and `other_accessory`. Do not make up or use any other clothing slots. If designing an outfit and none of the slots is clearly correct, use the one that makes the most sense. A missing slot or `null` means nothing is defined for that outfit slot.

- Every outfit must describe the complete set of clothing the character actually wears in that preset, including ordinary inner layers such as underwear, a bra, undershirt, socks, or other garments when appropriate. Do not define only the most visible outer garment. The runtime can remove clothing one piece at a time, so omitted inner layers can make a character become accidentally naked after removing one outer layer. Deliberately minimal, nude, or underwear-only outfits are valid when intended.

- Bras and underwear do not cause image-generation problems. Include them in every outfit where the character wears them. Omit them only when the character intentionally is not wearing them in that outfit.

- `null` means this outfit does not define an item in that clothing slot. However, this can and should be communicated by excluding the slot from the outfit instead to save space in the file.

- Do not create a nude outfit unless that is the intended default outfit of the character. Ember Adventures is capable of removing all clothing from a character to make them nude during play.

- `starting_outfit_id`: Outfit id that should be active when the character is first created/imported. It must exactly match one `outfits[].id`.

- `starting_held_items`: Object for hand slots at start. The only valid slots are `right_hand` and `left_hand`. Values are item descriptions or `null`. Do not put inventory lists here. Use these slots sparingly for items that are very important for a character to have in their hands in an image. Perchance is pretty bad at creating images with someone holding an item correctly. In general, weapons look better being worn instead of held in the hands and other items tend to clutter an image.

- `starting_inventory`: Array of starting inventory item strings or structured item objects if the item needs metadata. Use examples like `"Coin pouch"` or `{ "name": "Silver key", "note": "Opens the guild side door" }`.

- `starting_known_facts`: Array of facts about the character that are known when play starts. Use concise strings. This is definition data, not chat history, current scene memory, or a field that changes during play. Do not include future information or spoilers.

- `starting_nsfw_known_facts`: Optional array of adult-only facts known when play starts. Keep it separate from `starting_known_facts`; the runtime copies it to `nsfw_known_facts` and gates it by the active profile. Use `[]` when there are no adult-only facts.

- `catalog_hook`: Optional concise, spoiler-free player-facing pitch for the
  standalone character in catalog and discovery UI. Explain why someone would
  want to start a game with this character, usually in one or two sentences.
  Keep it accurate to the character's available experiences without revealing
  hidden routes, twists, transformations, or endings. It is display metadata,
  not personality guidance, AI instructions, chat context, or a substitute for
  `chat_story` or `chat_story_template.description`. Use `""` when no distinct
  hook is needed. A SFW character's hook must itself be SFW. Omit this field from
  every story-embedded character definition.

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
readable stable identifiers such as `strength`, `agility`, `mana`, or
`capacity_cost`; EmberAdventures does not prescribe a fixed
stat list. Every value must be a JavaScript safe integer. Negative, zero, and
positive integers are valid; decimals, numeric strings, booleans, null, and
values outside the safe-integer range are invalid. Omit `stats` when the
character does not participate in an authored numeric system. Do not add
generic RPG stats merely to fill the field. Stats are shown with full
character information and supplied to the AI for characters present in the
scene, but omitted from reduced absent-character context.

Characters should have concrete `starting_known_facts` covering identity, role, personality under pressure, combat/usefulness or social usefulness, household/social role when relevant, quirks/preferences, and relationship dynamics.

#### Player-Facing Visibility

The entire character definition is fully visible to the player if the player wants to inspect it. However, this isn't meant to be a normal part of play. They are allowed to view/edit to fix issues or make manual changes if desired.
Some fields are visible in the actual ui where the rest are only visible in the json editor.
Before exporting, audit fields that are visible in the ui: `name`, `genres`,
`kink_tags`, `gender`, `age`, `role`, appearance, and outfits.

Visible character fields must not reveal future roles, future relationship outcomes, twists, or secrets.

### Physical Attribute Phrase List

Use these embedded 0-10 descriptions when asking body-scale questions and when grounding final character body fields. For final JSON, almost always use numeric values from 0 to 10 instead of phrase strings. Lookup-table traits are `height`, `muscular`, `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, and `arms`. Use a custom string only when a specific exceptional physical detail cannot be represented by a table number, such as nonhuman anatomy or a concept-specific body structure. Chest has separate male and female presenting scales. The rest have a shared scale for all genders. The AI never sees the numeric values, only the phrases. The integers are for players to be able to increment/decrement the body traits to adjust size easily.

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

## Final Deterministic Validation

Before returning any character file, validate every entry in the batch using
this checklist. Do not call an entry finished until all checks pass:

1. The export wrapper is correct: one definition uses `character_definition`; a
   batch uses `characters[]` containing those wrappers; no app/type/export
   marker fields are present.
2. Required metadata exists and is valid: `source` is exactly `"Original"`,
   `creation_tool` is factual rather than copied from an example, `genres` is
   approved where required, and `nsfw`, `loli`, and `can_die` are booleans.
3. `version` is exactly 1, `id` is stable, `name` is a proper display name, and
   `age` is an integer. Paired loli/adult entries are created only when
   requested or required by saved preferences, and both keep the same plain
   name without variant suffixes.
4. `boldness` is either a number from 1 to 10 or a non-empty descriptive
   string. Numeric `0` and all other out-of-range numeric values are rejected.
   Text boldness contains behavior only and does not contain score annotations.
5. `created_at` and `updated_at` are real ISO 8601 timestamps. Existing
   `created_at` is preserved; `updated_at` changes only when the definition
   changes.
6. `outfits` is a non-empty array, every outfit has a unique stable `id` and
   coherent clothing object and explicit boolean `nsfw`, and
   `starting_outfit_id` matches an outfit id. SFW characters have SFW starting
   outfits and at least one SFW outfit in both presentations.
   Every outfit includes all intended visible and inner clothing layers.
   Animal or natural-form outfits use concrete body-covering slot values and
   never use `{}` as placeholder clothing.
7. Body fields contain body information only, `extra_description` contains
   only additional durable visuals, and no appearance fact is duplicated across
   body, hair/skin/eye, extra-description, personality, or clothing fields. The
   final assembled image prompt has been reviewed, and `extra_description` is a
   concise remainder rather than copied body-design prose or narrative text.
   `nonhuman_lower_body` is a real boolean; when true,
   `extra_description_lower_body` contains a concise concrete replacement-body
   description and does not repeat numeric hips or legs. When false, the lower
   description is either blank or contains only a concrete humanoid lower-body
   detail that does not belong in another structured field.
8. The entry contains no hidden process instructions, future unlock notes,
    spoilers, or creator workflow text in player-visible character fields.
9. Batch names, ids, surnames, jobs, facts, personality wording, body language,
    inventory, and outfits are checked against the relevant existing library
    and against all entries in the current batch for accidental repetition.
10. Lookup-table body fields use numeric 0-10 values unless a documented
    exceptional anatomy cannot be represented by the scale.
11. Gender adaptation is complete: `romanceable` is a boolean,
    `fallback_name` is non-empty, `fallback_outfits` is non-empty,
    `fallback_starting_outfit_id` matches a fallback outfit, and futanari
    characters have a valid male or female `fallback_gender`.
12. `appearance.penis_size` is an integer from 0 to 10 for every character.
13. `clothing` appears only inside outfit presets. No runtime-only fields such
    as a top-level `clothing`, `active_outfit_id`, current relationship values,
    current inventory, or current known facts are present.
14. `starting_trust`, `starting_attraction`, `starting_affection`, and any
    numeric `starting_arousal` are numbers from 0 to 10.
15. `starting_inventory`, `starting_known_facts`, and
    `starting_nsfw_known_facts` are arrays. Adult facts occur only in
    `starting_nsfw_known_facts` and are not duplicated in normal known facts.
    `starting_held_items` is an object containing only `right_hand` and
    `left_hand`, with item descriptions or `null` values.
16. `catalog_hook` is a string containing an accurate, spoiler-free standalone
    catalog pitch, or `""`. It is omitted from story-embedded characters.
17. Optional Chat scenario fields use their exact shapes: `chat_story` and
    `chat_opening_message` are strings; `chat_starting_location` contains only
    `label`, `place`, and `activity`, which are either all nonblank or all blank.
    The opening never controls the player, the scenario is safe for player inspection,
    and the three fields describe one coherent starting situation.
    `chat_story_template` is either `null` or only a complete inner `storyTemplate`
    object created and validated under the EmberAdventures Story skill. It may coexist
    with the lightweight fields because Full Story and Just Chat are separate launch
    choices.
18. When `stats` is present, it is an object with non-empty stable keys and
    JavaScript safe-integer values. It is omitted when the character does not
    need authored numeric stats.
19. Every character and player reference uses a supported token, resolves to a
    known stable character id where applicable, and appears only in a JSON
    value, never a JSON key.
20. Loli characters are never NSFW or sexualized, have no NSFW known facts or
    outfits, and have sufficient covering clothing. Every character under 18
    is marked as loli, and every character not marked as loli is at least 18.

## Library Maintenance

When asked to maintain a character library, support:

- metadata repair
- schema validation
- duplicate detection
- repetitive phrasing cleanup
- source/creation_tool/genres/nsfw/loli/can_die backfill
- style consistency
- race/species balance review
- relationship/default-state consistency
- moving rejected entries aside without deleting unless asked

