---
name: emberadventures-story
description: Create, update, migrate, validate, or review normal EmberAdventures story-template JSON files. This is the authoritative base story skill and schema contract. Use it directly for original/source-free stories and always load it before Source EmberAdventures Story for source/canon work.
---

## Version and Update Check

Current skill version: `1.0.10`.

For ordinary story creation, review, repair, or migration, use the installed
skill text as the active instructions. Do not interrupt the creator workflow to
download, install, clone, replace, or update skills unless the user explicitly
asks to update or verify skill currency.

For maintenance only, the authoritative GitHub version file is:

https://raw.githubusercontent.com/andro951/ember-adventures-tools/main/skills/emberadventures-story-version.md

If the user explicitly asks to update skills and the retrieved version differs
from the local version, pull the current `emberadventures-story` skill folder
from GitHub, replace the local copy, and then continue with the user's job. Do
not silently use a stale local copy.

# EmberAdventures Story

This is the authoritative normal EmberAdventures story-template skill. Use it
directly for source-free stories, including invented premises, player options,
party members, NPCs, objective chains, future cast, maps, title cards, opening
messages, migrations, validation, and quality review.

For a story based on a game, anime, manga, book, movie, mythology, or another
existing source, load this skill first and then load `Source EmberAdventures
Story`. The source skill extends this contract with research, canon scope,
adaptation, milestone, and source-validation rules. It does not replace or
restate this schema.

This skill must work as a standalone public skill. Do not assume an EmberAdventures
maintainer or a separate main thread will repair the story after output. The
generated JSON may be imported directly, so major schema, premise, objective,
character-depth, visibility, or field-purpose issues must be fixed before final
export.

This file is the skill's complete schema contract. Do not require or inspect
external app source files, private local project paths, or existing story files
for new story creation. The only external skill
dependency this story skill may assume is access to the EmberAdventures character
skills for character definitions.

Sections explicitly titled or qualified as `Original` or `source-free` apply
only when this skill is used directly for an invented story. For source/canon
work, keep this skill active for the schema and general workflow while the
Source EmberAdventures Story extension supplies source-specific values and
rules.

This skill creates and updates normal EmberAdventures story-template files. The
filesystem-backed Codex version uses a separate campaign packet shape; when the
user asks for that format, use `original-emberadventures-codex-story` instead of
forcing one schema into the other. Normal story-template exports do not use a
`story_engine` or `schema_version` discriminator.

## Model Readiness Check

Before substantial story creation, verify the current model and
reasoning/intelligence/effort level with the creator when it is not already
known. The minimum recommended setup for this skill is a thinking model at
medium effort/intelligence or higher, such as ChatGPT/Codex 5.4 or higher at
Medium. The optimal setup is 5.6 Sol at High effort/intelligence.

If the current setup is below optimal but still at or above the minimum, stop
before story design and warn that lower model/intelligence settings may create
a weaker story, miss long-range structure, or produce an invalid JSON file.
Suggest increasing to 5.6 Sol High, then continue only if the creator chooses
to proceed.

If the current setup is below the minimum, stop before story design and say it
is extremely unlikely to create a valid EmberAdventures story JSON file. Tell
the creator they probably should not continue until they raise the
model/intelligence/effort to at least the minimum.

## Story File Storage Check

Before substantial story design, ask where the creator wants to keep the story
files while work is in progress. Explain the tradeoff clearly:

- ChatGPT local storage is the default and requires no setup, but the creator
  cannot directly browse or edit those files. Provide download links whenever
  the creator wants to inspect, save, or move the current design document,
  notes, or JSON file.
- Google Drive is usually best for nontechnical creators because the creator
  can directly view, edit, organize, and share the files.
- GitHub is best for creators who want version history or are comfortable with
  repos. Use one stories repo, not one repo per story.
- Another shared folder service is acceptable if the creator already uses it.

Ask: "Where would you like to keep the story files while we work? The default
is ChatGPT local storage, but those files are not directly viewable by you
unless I provide download links. Better options are Google Drive, GitHub, or
another shared folder. Would you like help setting up Google Drive or a GitHub
stories repo?"

If the creator chooses Google Drive, help create or use this structure:

```text
Ember Adventures Stories/
  Stories/
    Story Name.json
  Design/
    Story Name/
      Story Name - Design Document.md
      Story Name - Notes.md
```

If the creator chooses GitHub, help create or use one stories repository with
this structure:

```text
ember-adventures-stories/
  stories/
    Story Name.json
  design/
    Story Name/
      Story Name - Design Document.md
      Story Name - Notes.md
```

If the creator skips setup or says to continue, use ChatGPT local storage and
provide download links at major checkpoints: first design document draft,
objective/arc plan, and final playable JSON.

Do not use existing EmberAdventures story files on the user's computer as creation
references, quality references, structure references, style references, or
coverage references when creating a new story. This includes active stories,
archived stories, generated output folders, downloaded examples, and previous
drafts. Existing story files may only be opened when the task is explicitly to
inspect, review, migrate, compare, or update that exact file.

For new original-story creation, build quality from the schema docs, this
skill's reference docs, and the user's requested premise. Do not copy depth,
wording, objective shape, opening style, or
character structure from existing local story files.

## Required Reads

Before producing, reviewing, or migrating final story-template JSON:

1. Use this skill as the schema and authoring source. Do not inspect app source
   files for new story creation.
2. Inspect the target story JSON only if updating, migrating, reviewing, or
   comparing that exact story file. Do not inspect existing local story files
   as examples or references for new story creation.
   When updating an existing story, first read and preserve its
   `story_memory`, `story_rules`, `story_inventory`, `story_shops`,
   `future_cast`, current objectives, player options, hidden notes, and
   runtime-design constraints. Do not overwrite or simplify those systems
   unless the user explicitly asks to change them.
3. If the story creates, embeds, or updates player/party/NPC definitions, load
   `EmberAdventures Character`. Do not duplicate its full character process
   here.

The complete field contract, objective patterns, long-form patterns, world-map
patterns, and quality checklist are included below in this same file. Apply the
relevant sections; do not look for a separate `references` folder.

When character creation is needed, load `EmberAdventures Character`; do not
duplicate its full character-design process here.

## Creative Direction Workflow

Lead the creative process until the user's vision is clear. Then become an
expert creative partner that expands and improves that vision without changing
its core fantasy.

If this is a brand-new story-creation thread or the user has not made an
EmberAdventures story before, begin with a short orientation before asking for
story details:

- Explain that the user is designing a playable story framework, not writing
  every line of narration and dialogue like a book.
- Explain that objectives, choices, rules, cast, locations, rewards, shops,
  jobs, and state changes tell EmberAdventures what the story is and how it can
  progress; the live AI writes most moment-to-moment narration during play.
- Explain that the user may specify exact phrases or key dialogue for important
  moments, but they normally should not script full scenes unless they want a
  very tight story beat.
- Explain that EmberAdventures stories are more open-ended than books or
  traditional Choices-style games by default, but can become more Choices-like
  through explicit choice objectives, tight objective chains, locked scenes,
  branch consequences, and endings.
- Offer to recommend a structure after hearing the premise instead of forcing
  the user to choose from every story type up front.

When discussing story pacing, use these creator-facing names:

- Player-Paced Story: the player chooses when to pursue the main plot. Use
  `story_pacing.mode: "player_controlled"`.
- Time-Controlled Story: recommended for most guided main plots. Main-story
  events are scheduled or triggered by prior objectives, but the schedule
  deliberately includes gaps where the player can explore, shop, work jobs,
  romance, train, rest, or pursue side objectives. Use
  `story_pacing.mode: "time_controlled"`.
- Strict Time-Controlled Story: special-case pacing for urgent sequences where
  main objectives happen back-to-back and side objectives/jobs should not be
  available until the sequence ends. This is a restrictive subtype of
  `time_controlled`, not the default recommendation.

Do not call the recommended middle option "hybrid"; call it Time-Controlled
Story and explain that its downtime is intentional. Do not describe normal
time-controlled pacing as having no gaps. If the creator is unsure, recommend
Time-Controlled Story with meaningful downtime unless the premise is a pure
sandbox or a tightly scripted crisis.

Before drafting final JSON, decide which mode the task is in:

- Interviewer mode: the user gave only a loose idea, genre, kink, premise, or
  vibe. Ask targeted story-juice questions instead of only configuration
  questions. Discover the core player fantasy, emotional target, world hook,
  key relationship focus, progression/building axis, NSFW role if any, and the
  payoff or reversal the story should build toward.
- Creative-partner mode: the user gave enough to imagine the story, but several
  valid games could still be built from it. Propose 2-3 strong directions,
  recommend one, and ask for approval or changes.
- Director mode: the user has chosen a direction or delegated the design.
  Create the full playable story, making strong design choices yourself.

Use a confidence gate: if you can imagine several substantially different
games from the user's prompt, ask more or propose directions before writing the
story. If you know exactly what game the user wants, proceed.

Do not interview forever. After each round of questions, judge whether the
core playable story is clear enough to finish by making strong design choices.
The creator does not need to specify every character, objective, twist, shop,
job, scene, route, or ending before you can write the story. Once the premise,
player fantasy, emotional target, world hook, core cast/relationship direction,
pacing model, and likely payoff are clear enough, tell the creator:

> I feel that I have enough information to write the rest of the story. Would
> you like me to complete the story now, or continue asking questions?

If the creator asks to continue, respond:

> Okay, I'll keep asking questions. Let me know when you would like me to
> finish the story.

Then ask only the highest-value remaining questions. If the creator says to
finish, stop asking for more input, write the story design document or final
story file as appropriate, and make reasonable choices for unresolved details.

Do not stop at genre, NSFW status, player gender, or a list of character types.
Ask the questions that make the story unique:

- What fantasy is the player meant to live out?
- What should the player feel most often: danger, desire, power, vulnerability,
  discovery, belonging, guilt, temptation, triumph, dread, or something else?
- What makes this world or premise different from a generic version?
- Which relationship should the player care about most, and how should it
  change over time?
- What can the player build, restore, earn, lose, collect, lead, protect, or
  become?
- What moment should make the player reevaluate the situation?
- Should the story be sandbox, Telltale-style branching, linear/mostly-linear,
  or simple/short?
- Which genders should be available among the starting selectable player
  characters and intentionally represented in the starting cast? Suggest
  `male`, `female`, and `non-binary` as the general default. For an adult/NSFW
  story, also suggest `futanari` as an optional fourth default when it fits the
  intended audience and premise. Let the user replace, remove, or expand this
  list. Record the decision in planning and implement it through actual player
  and cast definitions; do not store a separate preference field in story JSON.
- If NSFW, is sexual content a central fantasy, an optional reward, a romantic
  payoff, a danger/temptation, or mostly background spice?

For substantial stories, the main work product during creation should be a
human-readable story design document, not immediate JSON. Build and revise that
document first, then convert it to JSON only at the end when the user approves
or delegates the final conversion. The design document should be organized so a
human can read it easily and an AI can convert it reliably:

- premise and player fantasy;
- intended story structure and pacing model;
- player options and starting state;
- main cast, future cast, important NPCs, and relationship arcs;
- world rules, common knowledge, hidden truths, currencies, shops, jobs, and
  important resources;
- locations and unlockable locations;
- arcs, arc steps, likely objectives, and expected freedom/tightness for each
  part;
- choice points, hidden outcome routing, durable consequences, endings, and
  failure states;
- image guidance and important visual moments;
- notes from the user and unresolved decisions.

Before writing objectives for a serious story, produce a compact plot outline
or story design document with the premise, player fantasy, emotional targets,
world hook, beginning, midpoint or reevaluation moment, climax, ending choices
or postgame, progression/building axis, key relationship arcs, intended story
structure mode, and objective/arc plan. Show the user what is known so far,
clearly list missing decisions, and ask focused questions. Always allow the
user to skip questions by saying something like "you decide"; then make strong
story choices yourself instead of blocking indefinitely.

Use approval checkpoints for major work: premise/structure, cast/player
options, plot outline, objective/arc breakdown, and final conversion. If the
user explicitly asks to skip approvals or delegates the design, continue without
stopping but still keep an internal design outline before JSON.

Treat the story template as the director and EmberAdventures's live AI as the scene
writer. The live AI is good at moment-to-moment prose but weak at long-term
anticipation, payoff, and pacing unless the story definition enforces them.
Use objectives, rewards, story rules, relationship changes, image rewards,
state changes, choices, and conditional routing to create anticipation and
payoff. Do not rely on the live AI to invent the intended arc unaided.

For relationship, romance, dark romance, harem, court, companion, or NSFW
payoff stories, include playable relationship-building objectives between major
plot beats. Examples include spending time together, learning something
personal, earning a voluntary disclosure, surviving a mission together, sharing
a quiet evening, celebrating, arguing and repairing the damage, defining a
boundary, refusing or accepting temptation, and choosing distance. NSFW scenes
should have context, anticipation, invitation, resistance, or aftermath unless
the user explicitly asks for an immediate-sex premise.

NPCs and the world should feel alive before the player touches them. Give major
NPCs goals, problems, loyalties, fears, and plans; use offscreen motion when it
fits the premise, such as rivals acting, deadlines approaching, jobs rotating,
opportunities closing, or consequences advancing. Include meaningful failure,
missed opportunities, rejection, arriving too late, death, or worse outcomes
when they would make the story stronger, especially in Telltale-style stories
with rollback and choice support.

## Core Workflow

1. Determine whether the story is source-free or source/canon.
   - Broad genre tropes, high-level inspiration, tone references, and requests
     for an original story with a similar kind of appeal do not make the story a
     source adaptation. Continue with this skill when the setting, cast, names,
     factions, conflicts, scenes, and objective structure are newly invented.
   - Also load `source-emberadventures-story` when the user wants to retell,
     adapt, continue, or directly use an existing work's recognizable world,
     cast, locations, factions, or storyline. Keep this base skill active for
     the normal story schema and general workflow.
   - If an allegedly original premise is so close that it appears to reproduce
     protected source expression rather than broad ideas, explain the concern
     and redesign it into distinct original material. When unsure, use a
     targeted web check before deciding.
   - Tell the user they may create source-based stories for private/local use,
     but those stories are not allowed to be published to EmberAdventures public
     hosting, then load `source-emberadventures-story` for that work.
   - Do not author an actual source adaptation from the base skill alone. Use
     the source extension for its research, scope, canon, and source-title
     decisions while continuing to use this base contract.
   - If the user confirms the story is truly original, continue with
     `source: "Original"`.
2. Run the model readiness check and stop or warn as described above before
   substantial story design.
3. Run the story file storage check and help with Google Drive or GitHub setup
   when the creator wants shared storage.
4. Build a premise with a clear playable starting situation, not just lore.
5. Draft or update the human-readable story design document. Recommend a story
   structure type after learning the premise if the user has not chosen one.
6. Ask for approval or missing information unless the user delegated the design.
7. Convert the approved design into final story JSON only after the outline,
   cast, arc plan, and objective strategy are coherent.
8. Create or verify required public metadata.
9. Create a focused starting state with one immediate active objective.
10. Build a hidden objective spine for the main story.
11. Add side objectives that fit the premise instead of filler errands.
12. Add future cast only when it improves play; keep locked future entries hidden.
13. Build a useful world map with starting locations and unlockable future areas.
14. Write a vivid opening message that preserves player agency.
15. Run the progression design pass before final JSON:
    - define the current starting state;
    - define the hidden future state the story can reach;
    - define which objective rewards update state, rules, map locations, scene
      lists, character fields, images, items, and future-cast availability;
    - define which `story_rules` are active at start and which objectives add,
      replace, or remove them.
16. Run the feature-utilization pass. For every serious story, explicitly
    decide whether the story should use `state.players`, `story_rules`,
    `future_cast`, map unlocks, branch/exclusive objectives, relationship/stat
    rewards, `set_state_field`, `add_story_rule`, `remove_story_rule`,
    `add_state_list_item`, `remove_state_list_item`, `kill_character`,
    direct choice objectives, conditional `next_objectives` routing, hidden
    AI-adjudicated `outcome_routes`, multiple
    endings, failure/death branches, `generate_profile_image`,
    `generate_solo_normal_image`, and `generate_story_image`. Use the feature
    when it materially improves play; do not leave a feature unused just because
    the simpler outline is easier to write. Do not force Telltale-style
    branching into a premise that is better as a focused linear story.
    Also decide whether the story should use `story_inventory`, character
    shops, job boards, story-authored one-time jobs, or generic EmberAdventures jobs.
    Story-authored jobs must be curated for this exact story, not randomized,
    and each should have genre labels, unlock requirements, rewards, and a
    clear start/turn-in loop.
    For romance, dark romance, harem, court, companion, or relationship-driven
    stories, count `completion_control: "choice"` objectives and
    `adjust_relationship` rewards before finalizing. If either count is zero,
    add appropriate mechanics or explicitly justify why the premise is better
    without them. If the user asks for multiple endings, many choice objectives,
    a Telltale-style story, or a story with frequent direct player control,
    target roughly 30-40% choice objectives as a general planning goal. Do not
    let choice objectives exceed half the objective count unless the user
    explicitly requests an unusually menu-heavy structure. Count visible
    narrative choice objectives separately from hidden/shop-triggered treatment
    hooks. Hidden post-purchase hooks, shop follow-up hooks, and engine
    one-option start/turn-in job choices do not count against visible story
    pacing density.
    Direct choice clusters must be playable by Auto mode. Unless every option
    is intentionally fatal or ending-only, include at least one currently
    selectable continuation option that keeps the story moving, put the safest
    or most neutral continuation first, or mark the preferred auto path with
    `auto_preferred: true`. Do not make the only available choice a hidden
    locked option, a dead end, or a game-over branch unless that is the intended
    ending moment.
    Use conditional `next_objectives` when consequences should route from
    hidden state thresholds after an objective completes, such as exposure,
    suspicion, public reputation, money, injury, or relationship state. Do not
    turn those into choice objectives unless the player is intentionally
    choosing between the outcomes.
    Use `route_control: "ai"` with hidden `outcome_routes` when the correct
    consequence depends on natural dialogue, tactics, treatment, secrecy,
    relationship behavior, or other scene context that cannot be represented
    reliably by stored-state comparisons. This is not a visible choice menu.
    Build objective structures so the visual Story Builder tree can display
    them cleanly: one visible objective node per playable beat, `choices[]`
    owned by the choice objective, `next_objectives` for conditional routing,
    `requires` for unlock dependencies, and `exclusive_group` only for true
    one-path-only branch locks.
    For stories with dozens or hundreds of purchasable/talkable shop
    characters, use large-shop-stock mode: major/fixed story companions still
    need full depth, while stock characters should be compact but playable and
    distinct. Each stock character still needs a real name, species/race, role,
    appearance, outfit, personality, speech style, durable facts, intended shop
    placement, unlock requirement when relevant, and a post-purchase or
    post-introduction hook. Do not make stock characters anonymous,
    interchangeable, or bloated with main-character-level prose.
12. Run a character-depth pass. Important playable companions, major NPCs, and
    major future-cast entries need enough durable facts to actually use in play,
    not just a name and archetype. Main party members usually need 6-10 concrete
    facts; major NPCs usually need 4-6. Minor one-scene utility NPCs may be
    shorter, but one generic fact is draft quality.
13. Run the field-purpose pass: for every field, ask what it is for, how
    EmberAdventures uses/displays it, whether the value serves that purpose, and
    whether it can be clearer, less spoilery, or less like process text.
14. Run the creator-instruction leakage pass: remove anything that was an
    instruction to Codex/the story creator rather than story data.
15. Validate schema, player-visible text, objective references, and embedded
    character definitions before final output.
16. Run the standalone release pass: assume no later maintainer cleanup exists.
    If objectives are shallow, future_cast is thin, character facts are generic,
    schema fields are questionable, the premise is underdeveloped, or visible
    text leaks future/private information, fix the JSON before final output
    instead of leaving notes for someone else.
17. Run the objective-quality pass: every objective must have authored,
    story-specific completion criteria and completion instructions. Reject and
    rewrite objectives whose criteria or instructions merely repeat the title,
    use boilerplate such as `Return yes only when the player completes: {title}`,
    use generic variants such as `Return yes only when the player clearly takes
    action toward this goal: {summary}`, or use boilerplate such as `Resolve the
    immediate outcome of {title} and move to the next objective`. This applies
    to sandbox, simple, compact, and test stories too; short stories still need
    concrete criteria tied to the actual scene and intended completion moment.
    Never silently truncate, discard, or omit objectives because of an arbitrary
    implementation count limit. Preserve the complete authored objective graph.
    If the target application cannot retain the full graph, stop and report the
    incompatibility instead of returning a story whose later content will vanish.
18. Run the pacing-and-relationship pass: serious stories should not place
    chapter-scale beats directly beside each other without bridge objectives.
    Add playable objectives for trust, suspicion, attraction, private
    conversations, world understanding, preparation, and consequences when those
    beats are part of the intended experience. If a single player message could
    complete multiple consecutive objectives, merge or rewrite those objectives.
    Use `adjust_relationship` rewards when an objective should deterministically
    change trust, attraction, affection, or arousal.
    For every major romantic lead, companion lead, recurring rival/temptation,
    or relationship-gated ally, include at least one objective that builds,
    tests, defines, or damages that relationship unless the character is not
    meant to matter emotionally. Relationship objectives are not only spicy
    scenes: boundaries, refusals, apologies, trust tests, protection,
    jealousy, vulnerability, private conversations, and chosen distance are all
    valid relationship beats.
    For romance, dark romance, romantasy, harem, and other relationship-first
    stories, relationship building is not optional pacing filler. Add multiple
    playable relationship objectives between major plot milestones so the story
    does not speed-run from event to event. Include private conversations,
    emotional aftermath, temptation, vulnerability, jealousy, recovery, chosen
    distance, and scenes where a romantic lead actively shows interest. If the
    intended player is submissive, shy, or unlikely to pursue intimacy, provide
    optional-with-skip choice objectives and narrator instructions that let love
    interests flirt, invite, tempt, court, or come onto the player while
    preserving explicit player choice.
    Match the romantic and social cast to the user's chosen audience, attraction
    targets, starting-gender list, and premise. Do not impose a universal gender
    balance or add a special gender/anatomy type that was not requested or
    accepted during intake. A deliberately single-gender or narrowly targeted
    cast is valid when it is part of the intended fantasy.
19. Run the publish-as-is pass: assume the user will import or publish the
    generated file immediately with no manual cherry-picking, no comparison
    against another draft, and no review from another thread/model. If two
    internal options look useful, merge them yourself before final output. Do
    not produce "base plus suggested improvements" as the final result.

## Required Output Wrapper

Story exports use this wrapper:

```json
{
  "app": "EmberAdventures",
  "exportType": "story-template",
  "storyTemplate": {
    "id": "story-id",
    "title": "Story Title",
    "description": "Short player-facing description",
    "createdAt": "<actual ISO 8601 creation timestamp>",
    "updatedAt": "<actual ISO 8601 update timestamp>",
    "state": {
      "meta": {
        "app": "EmberAdventures",
        "genres": ["fantasy", "adventure"],
        "kink_tags": [],
        "story_guidance": "",
        "story_source": {
          "mode": "original",
          "title": "Story Title",
          "description": "Short premise description",
          "modifications": ""
        }
      },
      "location": {
        "universe": "Story Title",
        "world": "World Name",
        "continent": "",
        "region": "Starting Region",
        "settlement_type": "",
        "settlement_name": "",
        "district": "",
        "specific_place": "Starting Place"
      },
      "world_map": {
        "current_location_id": "loc-start",
        "focus_location_id": "loc-start",
        "travel_history": [],
        "locations": {
          "loc-start": {
            "id": "loc-start",
            "name": "Starting Place",
            "type": "place",
            "scale": "site",
            "parent_id": "",
            "x": 50,
            "y": 50,
            "discovered": true,
            "travel_enabled": true,
            "summary": "The place where the story begins.",
            "detail": {},
            "connections": [],
            "npcs": []
          }
        }
      },
      "time": {
        "year": 1,
        "month": 1,
        "day": 1,
        "hour": 8,
        "minute": 0
      },
      "scene": {
        "summary": "The opening situation in one concise sentence.",
        "intimacy_level": 0,
        "spicy_mode": "off",
        "party_members_present": [],
        "image_characters": ["Player"],
        "npcs_present": [],
        "speak_targets": [],
        "image_action": "standing at the starting place",
        "sex_position": "",
        "ai_sex_position": "",
        "sex_acts": []
      },
      "player": {
        "version": 1,
        "id": "player-character",
        "name": "Player Character Name",
        "source": "Original",
        "creation_tool": "<actual tool/model> (<reasoning level>)",
        "genres": ["fantasy"],
        "kink_tags": [],
        "nsfw": false,
        "loli": false,
        "can_die": false,
        "gender": "female",
        "age": 25,
        "role": "Story protagonist",
        "personality_description": "Durable starting identity that preserves player agency.",
        "speech_style": "Natural dialogue suited to the character.",
        "boldness": 5,
        "starting_relationship_to_player": "self",
        "starting_trust": 0,
        "starting_attraction": 0,
        "starting_affection": 0,
        "starting_arousal": 0,
        "starting_state_of_mind": "neutral",
        "starting_physical_state": "healthy",
        "starting_pose": "standing at the starting place",
        "appearance": {
          "species": "human",
          "race": "",
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
              "undershirt": "plain cotton undershirt",
              "shirt": "plain everyday shirt",
              "underwear": "plain comfortable underwear",
              "pants": "plain everyday trousers",
              "socks": "plain socks",
              "feet": "practical shoes"
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
      },
      "characters": {},
      "npc_directory": {
        "locations": {}
      },
      "world_flags": {
        "tone": "Concise story-specific tone guidance."
      },
      "objectives": {
        "active_id": "opening-objective",
        "no_current": false,
        "items": [
          {
            "id": "opening-objective",
            "title": "<specific immediately actionable objective title>",
            "type": "story",
            "status": "active",
            "summary": "<specific player-facing description of the opening goal>",
            "requires": [],
            "exclusive_group": "",
            "unlock_mode": "manual",
            "selectable": false,
            "available_now": true,
            "blocked_reason": "",
            "notes": [],
            "rewards": [],
            "next_objectives": [],
            "route_control": "",
            "outcome_routes": [],
            "objective_mode": "",
            "timeline_event_id": "",
            "locked_until_complete": false,
            "choices": [],
            "completion_message": "",
            "completion_control": "player",
            "completion_criteria": "<specific observable condition that proves this exact opening goal is complete>",
            "completion_instruction": "<specific immediate result, consequence, reveal, or transition for completing this exact goal>",
            "auto_completed_from_prereqs": false,
            "travel_location_id": "",
            "travel_location_name": ""
          }
        ]
      },
      "future_cast": {
        "enabled": true,
        "items": {}
      },
      "story_clock": {
        "elapsed_minutes": 0,
        "label": "Day 1, 8:00 AM"
      },
      "story_pacing": {
        "mode": "player_controlled",
        "pending_event_id": "",
        "timeline": {}
      },
      "timed_events": {},
      "story_rules": [],
      "story_memory": {
        "world_notes": [],
        "unresolved_threads": [],
        "relationship_notes": [],
        "rules_and_constraints": [],
        "ai_private_notes": []
      },
      "recent_changes": []
    },
    "messages": [
      {
        "role": "assistant",
        "speaker": "Narrator",
        "text": "A concise, immediately playable opening that ends with a concrete situation the player can act on."
      }
    ],
    "source": "Original",
    "app": "EmberAdventures",
    "templateType": "story",
    "creation_tool": "<actual tool/model> (<reasoning level>)",
    "genres": ["fantasy", "adventure"],
    "kink_tags": [],
    "nsfw": false,
    "loli": false,
    "default_image_model": "",
    "editor_data": {
      "story_tree": {
        "positions": {},
        "viewport": {
          "x": 0,
          "y": 0,
          "zoom": 1
        }
      }
    },
    "title_card_subjects": [],
    "title_card_image": {
      "id": "",
      "title": "",
      "prompt": "",
      "negativePrompt": "",
      "seed": "",
      "model": "",
      "source": "none",
      "url": "",
      "hosted_url": "",
      "html": "",
      "favorite": false
    }
  },
  "exportedAt": "<actual ISO 8601 export timestamp>"
}
```

All timestamp and creation-tool strings in this example are documentation
placeholders. Replace them with factual values in final output. Preserve
`createdAt` and embedded character `created_at` when editing existing content;
update `updatedAt` and changed embedded character `updated_at` only when their
content changes. Set `exportedAt` to the actual export time.

The canonical skeleton is structural documentation, not ready-made story
content. Replace every generic title, description, location, objective,
completion criterion, completion instruction, character fact, and opening line
with concrete premise-specific content. Never emit the skeleton unchanged or
reuse its example names in a finished story.

Required state sections:

`meta`, `location`, `world_map`, `time`, `scene`, `player`, optional `players`,
`characters`, `npc_directory`, `world_flags`, `objectives`, `future_cast`,
`story_rules`, `story_memory`, `recent_changes`.

Optional top-level editor metadata:

`editor_data.story_tree` stores visual Story Builder layout only. It is not
runtime state and is not sent to narrator prompts. It may be omitted, but when
present it should use:

```json
{
  "positions": {
    "objective-id": { "x": 80, "y": 80 }
  },
  "viewport": { "x": 0, "y": 0, "zoom": 1 }
}
```

Use this only to make the manual visual tree editor nicer to open. Never put
story lore, hidden objectives, creator notes, or AI instructions in
`editor_data`. The visual tree editor reads normal objective fields:
`requires` for prerequisite/dashed links, `next_objectives` for post-completion
route/solid links, `completion_control: "choice"` plus `choices[]` for direct
choice nodes, `exclusive_group` for mutually exclusive path locks, and
`rewards` for deterministic effects. Do not create separate fake branch-node
objects just to make a diagram.

Optional hidden economy sections:

`story_inventory`, `story_shops`, `story_job_offers`,
`story_job_offer_history`, `active_generated_jobs`, and
`story_generated_npc_pool`.

Use these only when the story benefits from controlled resources, shops, job
boards, item selling, or purchasable/recruitable characters. They are hidden
engine state, not narrator lore. Normal AI prompts do not receive them whole,
so any shop/job/resource behavior that must happen reliably must be represented
through the UI, objective choices, or deterministic rewards.

`story_inventory` stores story-owned resources such as `coins`, `credits`,
`adventurer_xp`, `adventurer_rank`, repair parts, suspicion, reputation, and
items. Use it for resources that should not be freely granted by narrator prose.
Items may include `id`, `name`, `type`, `quantity`, `value`, `sellable`,
`quest_item`, `description`, `image_prompt`, and `image_id`. Quest items should
normally be non-sellable.

`story_shops` is an object keyed by shop id. A shop has `id`, `title`, internal
`type` (`"character"`, `"job"`, `"general"`, or `"clothing"`), display-only `subtype`, optional
`description`, `unlocked`, `currency`, `location`, optional `owner_npc_id`, and
`items`. `type` is hidden
engine behavior; `subtype` is just text shown to the player, such as `Slave
Shop`, `Companion Shop`, `Mercenary Guild`, `General Store`, `Outfitter`, or
`Job Board`.

Character-shop items should be minimal and reference `future_cast.items` by
`character_id`; do not duplicate full character definitions inside shop items.
Use `price`, `purchased`, `locked`, structured `requirements`, and optional
`unlock_reason` and `on_purchase_objective`. `purchase_story`,
`purchase_objective`, and `purchase_story_objective` are accepted aliases, but
`on_purchase_objective` is the normalized stored field. When the character is
purchased, EmberAdventures starts that objective and selects it unless a locked
urgent objective is currently active. Locked character-shop cards remain
visible but show only the character name, a generic locked image, and the visible
unlock requirement/reason; they do not show the real image, details, or price.
Requirements and affordability do not make an otherwise visible character
secret: the shop shows their details, price, and exact unmet status. Use explicit
`locked: true` only when the real image/details/price must remain hidden. A
character shop must set both `purchase_verb` and `purchase_completed_verb`.
These are arbitrary author-provided display strings, not enums. For example,
`purchase_verb: "Recruit"` and `purchase_completed_verb: "recruited"`, or
`purchase_verb: "Contract"` and `purchase_completed_verb: "contracted"`.
EmberAdventures never guesses either word from the shop title, subtype, or other
prose. It may set `post_purchase_presence` to
`"current_scene"` (the default) or `"roster"`; use `"roster"` only when the
character should be owned but should not physically enter the current scene.
The shop owner and purchasable/talkable characters must be real full
character/NPC definitions in `future_cast`, not labels like `shopkeeper` or
`worried baker`.

General item shops use `type: "general"`. Every listing contains a stable `id`,
optional finite `quantity` (`null` or omitted means unlimited), optional
requirements/lock fields, and an `item` using the normal story-inventory item
shape. The item's positive numeric `value` is its underlying value and the exact
amount a buying shop pays per unit. The shop's `markup` is a number of at least
`1`; EmberAdventures charges `ceil(item.value * shop.markup)` when selling the
item. Use a markup near `1` for inexpensive low-class merchants and a larger
markup for prestigious or exploitative merchants. Higher-class shops should
also carry appropriately valuable, rare, or high-quality stock. Do not author a
separate listing `price`; derive retail prices consistently from value and
markup. Use `buying: { "enabled": true, "quest_items_rejected": true }` when
the shop buys ordinary inventory. Quest items remain unsellable.

Clothing shops use `type: "clothing"`. Each listing contains `id`, `title`,
positive integer `price`, optional requirements/lock fields, and one complete `outfit` using the
normal character outfit schema. Purchasing copies that complete preset into the
selected player or owned party character's `outfits`; it does not equip it.
Catalog outfits may be purchased independently for multiple characters, but the
same character cannot purchase the same listing twice. Do not represent every
shirt, shoe, or accessory as a separate inventory item unless a future feature
explicitly adds mix-and-match clothing commerce.

Job boards use `type: "job"`, `visible_count`, and
`generic_jobs_enabled: true` when EmberAdventures should generate built-in rotating
jobs. Generated jobs are engine-authored, not AI-authored. Do not prefill
`story_job_offers`, `active_generated_jobs`, or `story_generated_npc_pool` in a
normal story template unless creating a deliberate starting active job. When a
generated job is accepted, EmberAdventures creates side objectives; the first is a
one-option choice to start the job, and the final is a one-option choice to
turn it in. Jobs never expire, can be abandoned, and completion clears generated
offers on all boards.

Story-specific jobs belong in `story_shops[board_id].items[]`. These are
curated authored jobs, not randomized jobs. Use this exact item schema unless a
newer bundled schema contract says otherwise:

- `id`: stable unique job item id;
- `title`: player-facing job title;
- `summary`: player-facing hook;
- `genres`: approved story genre labels required for the job to appear;
- `nsfw`: boolean; true only when the job itself is adult/NSFW and should be hidden in SFW mode;
- `rank`: nonnegative difficulty/rank number when useful;
- `requirements`: structured requirements array;
- `reward_coins`: number, or `0` when no money reward;
- `reward_xp`: number, or `0` when no XP/rank reward;
- `reward_items`: optional story-inventory item rewards;
- `client_npc_id`: optional future-cast id for the client/contact;
- `start_location`: optional location override object for the job start, using
  normal `state.location`-style keys such as `world`, `region`,
  `settlement_name`, `district`, and `specific_place`. Do not use a string
  location id here; omit `start_location` when the job should start at the job
  board's own location;
- `completion_criteria`: concrete completion check;
- `completion_instruction`: concrete narrator/objective guidance.

Do not use alternate fields such as `quest_id`, generic `reward`, `purchased`,
`on_accept_objective`, or free-text reward blobs for story jobs. The current
EmberAdventures job-board accept path does not consume `on_accept_objective`; it
creates its own generated side-objective flow from the job item's summary,
completion criteria, completion instruction, start location, optional client,
and rewards. Do not write a story job as if it will complete a separate
`linked` authored objective chain; the accepted job's own generated objective
is the playable job unless you model that content as a normal objective chain
outside the job board. If an authored objective chain must exist, make it a
normal objective chain unlocked by story progression, not a job-board item that
relies on `on_accept_objective` or text references to linked objectives.
A story job is listed only when every label in its `genres` array is present in
the story's `genres`; use this to keep genre-mixed stories precise. Story jobs
are one-time content: after acceptance/completion they should not rotate back
in like generic jobs. Use requirements such as
`story_inventory.adventurer_rank >= 1`, `story_inventory.credits >= 200`, or a
story-specific inventory flag to control when they unlock. Do not write job or
shop requirements as path/list scans against `story_rules`; use
`{ "type": "story_rule", "id": "rule-id" }` for rule gates, or mirror unlock
gates into `story_inventory` flags/lists with objective rewards when the UI
needs a resource/list requirement.

Generic jobs are EmberAdventures's fallback rotating jobs. They have genre labels on
the engine pool entries and are eligible only when all of those labels are
present in the active story. Use `generic_jobs_enabled: true` for boards that
should provide repeatable money/XP work beyond the curated story jobs, and
`false` for boards that should show only authored story jobs.

Structured requirements use:

```json
{ "path": "story_inventory.coins", "op": ">=", "value": 120 }
```

Supported operators are `>=`, `>`, `<=`, `<`, `==`, `!=`, `truthy`, `falsy`,
`includes`, and `not_includes`. Choice and shop UIs show requirements directly,
so write them as player-understandable resource/stat checks such as
`story_inventory.credits >= 500` or `Companion Name trust >= 6`.

## Field Purpose And Process-Leakage Rules

Use the authoritative `Field Purpose Standard`, `Creator Instructions Are Not
Story Data`, and `state.meta` sections below. They contain the complete rules
for player-visible fields, hidden runtime guidance, blank defaults, creator
instruction leakage, and `story_guidance`.

## Public Metadata

Use the authoritative `storyTemplate Fields`, `state.meta`, `Public Hosting
Metadata`, and `Story Image Rules` sections below. They contain the complete
source, creation-tool, genre, kink-tag, NSFW, loli, image-model, title-card,
creator-identity, and publishing contract.

## Original Story Rules

- Do not assume NSFW, romance, slavery, hypersexual tone, or kink premise unless
  the user requested it.
- Invent story-specific conflict and choices; avoid generic "chosen hero" shape
  unless requested.
- Keep the first session playable: the player should immediately understand
  where they are, who is present, what pressure exists, and what they can do.
- Use original named people. When the skill invents a new player, party member,
  NPC, or future-cast person, generate a first and last name by default. Preserve
  any user-specified/manual name exactly, including one-word or nonstandard
  names, unless the user asks to rename it.
- Do not make a story require a specific named player character unless the user
  explicitly asks for a fixed protagonist. EmberAdventures may allow the user to pick
  any character as the player. In objectives, verifier text, hidden rules,
  story rules, and player-facing prose, prefer role-neutral wording such as
  `the player`, `the protagonist`, or `the human scavenger` instead of a
  hardcoded fallback name. If the story includes a default/fallback `state.player`,
  that name is only the default option and must not be required by the story
  logic.
- Do not use titles, jobs, groups, or descriptions as generated names or speaker
  identities, such as `Guard`, `Guild Clerk`, `woman`, `traveler`, `bandits`, or
  `shopkeeper`.
- Use `EmberAdventures Character` for invented players, party members, NPCs,
  and future cast.
- Vary adult ages intentionally according to role, species, authority, and story
  position. Do not cluster everyone around one generic age.
- Keep clothing precise. Clothing slots are item slots; avoid ambiguous values
  like "adventuring clothes or maid outfit depending on scene." Create separate
  outfits when needed.
- Every outfit must describe the complete set of clothing the character normally
  wears in that look. Include applicable underwear, bra/support layer,
  undershirt, outer top, bottom, socks/hosiery, footwear, and other real layers.
  Do not provide only an outer garment when that would make partial undressing
  impossible without making the character immediately naked. Omit a layer only
  when the outfit intentionally does not include it.
- Default outfit depth for original story characters:
  - SFW story characters should usually have 3-5 tailored outfits each.
  - NSFW story characters should usually have 13-15 tailored outfits each, with
    at least 10 clearly NSFW/adult outfits when the character is an adult and
    not loli/underage.
  - Preserve the starting/default outfit as the first outfit when updating an
    existing story, then add story-specific alternatives suited to that
    character's role, species, body, personality, genre, and setting.
  - Do not add NSFW outfits to loli, underage, minor-coded, or non-adult
    characters even when the story itself is NSFW.
  - Avoid identical wardrobe dumps across the cast. A warrior, clerk, noble,
    monster, robot, ghost, student, shop owner, and love interest should not all
    receive the same outfit names or clothing text unless the uniformity is
    intentional in-world.
  - For one-piece garments that cover top and bottom, use both a top/body slot
    and a bottom coverage slot. Example: `shirt`: "one-piece black fishnet
    teddy bodysuit" and `underwear`: "same teddy covers her groin with a
    high-cut panty shape".
- Include optional side objectives and branches by default when they improve
  play, tone, character interaction, discovery, romance, comedy, combat,
  investigation, shopping, training, downtime, or problem solving.

## Spoiler And Visibility Rules

Do not expose future party members, NPCs, villains, locations, factions,
relationships, betrayals, bosses, twists, objective rewards, or planned story
events in the opening scene unless they are present, known, and actionable at
that moment.

Use hidden objectives and `future_cast` for full-story knowledge. Before
finalizing, run a hidden-future visibility pass over:

- opening messages;
- story description;
- visible objective titles/summaries;
- map summaries/details;
- current NPC fields;
- party member fields visible in library/editor UIs;
- story metadata visible in public/library cards.

Visible text should contain only what the protagonist/player could reasonably
know at the starting point. Future names, future party roles, locked locations,
hidden rewards, required relationship outcomes, future villains, and major twists
belong in hidden future cast/objectives/rewards until play reaches them.

If a present NPC has a real stored name that the player should not know yet,
store the real name in `npc_directory` for voice/state stability, but add
`player_known_name: false` and a concise `player_facing_label` such as
`damaged robot torso`, `masked prisoner`, or `unknown knight`. Until the reveal,
opening text, visible objective titles/summaries, and auto-player-facing
summaries should use the label/role/pronouns, not the hidden real name. Hidden
speaker tags may still use the stored name only to route voices, but the visible
prose must establish what the player actually knows.

## Opening Rules

The first assistant message should be vivid and immediately playable, not a lore
dump. It should normally introduce only:

- the immediate sensory situation;
- one present NPC max, unless a second person is essential and actionable;
- one visible problem;
- one concrete player action.

The opening may establish unavoidable starting circumstances, but it must
preserve player agency. Do not write the player as already having made a
meaningful choice, agreed to a relationship, submitted, attacked, flirted,
forgiven someone, accepted a job, or committed to a moral path unless that is
the explicit requested starting premise.

Use grounded, actionable details before abstract setting mechanics. Avoid
front-loading councils, prophecies, cosmic systems, charters, political
contracts, or hidden frameworks unless that concept is the single visible
problem the player can act on immediately.

End on an in-world situation or action opportunity, not a meta prompt. Never end
the opening with `What do you do?`, `How do you respond?`, `What happens next?`,
or another question that merely reminds the player that the game is interactive.

For comedy, build humor from character personalities, clumsiness,
misunderstandings, timing, social consequences, and concrete situations. Do not
make buildings, furniture, paperwork, the universe, or an unexplained game-like
system constantly watch, judge, chant at, or react to the player unless that is
the explicit premise. Do not let a throwaway joke become the world's dominant
mechanic or the AI's repeated fixation.

For surprise, danger, first-contact, or mystery openings, write the opening
objective and early completion instructions so an automatic player turn reacts
believably from limited knowledge. Do not encourage perfect diagnosis, instant
technical solutions, hidden-name usage, or optimal plot advancement unless the
player has already visibly earned that knowledge.

## Objective Rules

- Use one active opening objective.
- Before writing the chain, decide whether the story is Telltale-style
  branching or simpler linear/mostly-linear. Telltale-style stories should use
  multiple direct choice clusters, branch-specific rewards, hidden outcome
  logic, and distinct endings when the premise supports them. Linear
  stories should use bridge objectives and occasional real choices, not fake
  menu choices that do not matter. If the user asks for multiple endings, many
  choice objectives, or a Telltale-style structure, aim for roughly 30-40%
  `completion_control: "choice"` objectives. Not every objective should be a
  choice objective; more than half is usually too many unless explicitly
  requested.
- Hidden main objectives should form a coherent story milestone chain. Every
  non-terminal main objective must route somewhere intentionally: either a real
  dependent objective requires it, or it has `next_objectives` for conditional
  post-completion routing. If a main objective is an ending, death, or bad
  ending, make that terminal status explicit in the title/summary and use
  deterministic ending rewards such as `kill_character` with
  `ignore_can_die: true` when appropriate. Do not leave a non-final main
  objective with no dependent objective, no `next_objectives`, and no terminal
  reward; that makes EmberAdventures fall back to objective picking instead of
  authored pacing.
- Side objectives use `type: "side"`. Do not author `kind` solely to mark an
  objective as side content; current normalization preserves `type` and may
  discard `kind`.
- Objective `requires` values must reference valid objective ids.
- Objective rewards must reference valid future-cast ids when they introduce
  people.
- Objectives must not have step fields.
- Objectives need verifier criteria and safe completion instructions.
- Objective titles are the primary player-facing instruction. Read each title
  alone and make sure the player knows the intended direction.
- Use `completion_control: "player"` when the player's action completes the
  objective. Use `"ai"` when the title gives the player a goal but the
  narrator/world must decide success or outcome, such as `Defeat the Bandits`.
  Use `"choice"` for direct forced player choices that EmberAdventures should present
  in a choice menu and complete immediately without AI verification.
- Completion and hidden routing are separate. An objective may use player or AI
  completion plus `route_control: "ai"`; once completion is proven, the same
  verifier classifies the full scene into exactly one private authored outcome.
  Outcome-route `requirements` are hard eligibility filters. Only eligible
  routes are shown to the classifier. Always include exactly one
  `fallback: true` or `default: true` route with no requirements so completed
  objectives always have a valid ambiguous/neutral/default route.
- EmberAdventures checks one selected objective at a time. Do not design chains that
  expect one player message to complete multiple consecutive objectives. Use
  larger scene-scale objectives or bridge objectives instead.
- Player-controlled objectives are checked after player-authored turns.
  AI-controlled objectives are checked after the narrator reply has actually
  shown the outcome. Do not write AI-controlled criteria as if the verifier is
  deciding whether the next reply should do the event.
- Do not use generic completion text. Never write criteria like
  `Return yes only when the player completes: {title}` or instructions like
  `Resolve the immediate outcome of {title} and move to the next objective`.
  Also reject variants such as `Return yes only when the player completes or
  survives...`, `Return yes only when the player completes, submits, or
  receives...`, or `Return yes only when the player clearly takes action toward
  this goal...`. Criteria must name the actual scene result, acceptance,
  purchase, reveal, survival outcome, conversation result, or decision that
  completes the objective.
- Player-controlled objective criteria must name the specific player action,
  commitment, question, purchase, travel, inspection, choice, or conversation
  that completes the objective.
- AI-controlled objective criteria must name the specific narrator/world state
  that counts as resolved, such as enemies defeated/routed/captured, a duel
  decided, a trial concluded, a reveal delivered, or a danger ended. AI
  objective criteria must not say `player completes`.
- Completion instructions must describe the concrete immediate outcome,
  consequence, reveal, transition, or future-cast introduction for that exact
  story beat. They are hidden narrator guidance, not a duplicate of the title.
- When a named character is present but their identity is not yet player-known,
  player-facing objective titles/summaries and player-controlled criteria should
  use what the player can perceive, such as `the damaged machine`, `the masked
  stranger`, or `the sealed voice`. Put the real stored name only in hidden
  rewards/instructions that truly need it.
- Do not create passive external-event objectives such as `Hear the Alarm` when
  the event can be revealed in the previous objective's completion instruction.
- Never create meta objectives such as `Do Not Force a Fake Ending`.
- Player-facing objective titles/summaries must not spoil locked future cast,
  future locations, objective rewards, private AI notes, or required outcomes.
- Serious stories should include memorable side content unless the user asks for
  a minimal story.
- Side objectives should usually have real consequences, not only prose. Prefer
  giving them at least one appropriate reward such as an item, story rule,
  relationship/stat change, location unlock, hidden lead, image trigger, or
  scene/list update.
- For romance, dark romance, court intrigue, harem, companion, and relationship
  stories, include bridge objectives that build the relationship before major
  payoffs. Use `adjust_relationship` rewards for deterministic trust,
  attraction, affection, and arousal changes. `preset: "all"` changes trust,
  attraction, and affection; `preset: "all_and_arousal"` also changes arousal.
- For these story types, do not rely on romantic prose alone. Add objective
  rewards for relationship changes that must persist, and add direct choice
  clusters when the player is choosing trust, boundaries, desire, allegiance,
  a bargain, a partner, a betrayal, or an ending. If a serious romance/dark
  romance/harem/court story has zero `choice` objectives or zero
  `adjust_relationship` rewards, treat that as a failed quality pass unless
  the final notes explain a deliberate exception.
- Branch objectives should have actual branch effects. Use `exclusive_group` only for true mutually exclusive choice clusters where taking one path should lock the other path until the player rolls back to an older state snapshot. For forced menu choices, put `exclusive_group` on the one visible owner objective with `completion_control: "choice"` and internal `choices[]`; do not create one top-level objective per option. Later branch objectives should require the owner objective and rely on selected-choice story rules, state changes, or relationship changes to preserve which path was chosen. Do not use `exclusive_group` for optional content, hub tasks, parallel goals, or side branches/source milestones that can all be completed.
- For forced menu choices, create one visible owner objective with
  `completion_control: "choice"`, `selectable: true`, and a `choices` array.
  Each choice item should have `id`, `title`, `summary`, `rewards`, and
  optional `effects`. Use choice `summary` for consequence-neutral
  clarification when the option title alone may not be enough. Do not leave
  summaries blank for major or meaningful choices unless the title is truly
  self-explanatory. Keep `effects` empty unless they only show visible
  requirements, visible costs, or visible story-inventory changes. Do not reveal
  death, failure, romance, sale, betrayal, ending, route labels, unlock labels,
  hidden recommendations, or hidden branch outcomes in the choice UI. Bad
  visible `effects` include `Bad ending route`, `Hana affection route`,
  `Unlocks Mira treatment route`, `Fail-forward dark route`, and
  `Best with first law: Truth or Freedom`. Good visible `effects` include
  `credits -80`, `Companion Name trust >= 6`, `suspicion +1`, and `requires cellar
  key`. Do not create one top-level objective per option, and do not
  hide the options in one objective's summary or notes. Good uses include
  choosing a first law, choosing which ally to trust, choosing a bargain,
  choosing a route, or choosing an ending. The owner title should name the
  decision, such as `First Contact` or `Choose Your First Law`; each choice
  title should be the actual option text, such as `Stay Hidden`, `Trust
  the companion`, or `Accept the Stranger's Bargain`.
- Use a choice owner objective whenever the story is clearly passing control to
  the player for a meaningful decision: trust/refuse, accept/reject a bargain,
  set a boundary, escalate/avoid intimacy, choose a lover/rival/faction stance,
  knock on a character's door or go to bed, spare/punish, choose a route, or
  choose an ending.
- Use timed events when the world should keep moving while the player does
  other things. Timed events are checked from the additive game clock after
  turns and reward processing. They can show player-visible game messages,
  apply normal objective rewards, introduce or change characters, start urgent
  objectives, or record story rules when a deadline passes. Use them for rescue
  windows, background faction progress, shop/job deadlines, travel pressure,
  worsening injuries, rival plans, and other pressure that should not wait
  forever for the player.
- Use `locked_until_complete: true` only for time-sensitive objectives that
  must be played through immediately once active. While locked, the player
  should not be able to switch to side objectives or clear the current
  objective. Use this for battles for a city, urgent attacks, time-critical
  rescue, irreversible confrontation, arrest, collapse, deathbed repair, or
  other moments where walking away would break the story. Do not use it for
  ordinary main-story guidance, normal tight objective chains, relationship
  scenes, political dinners, exposition, or author convenience.
- For immediate-merge choices, record the consequence in the choice rewards and
  let the next shared objective require only the choice owner. Use this for
  short relationship stance, boundary, flirt/refuse, mercy/cruelty, or tone
  choices where the story continues through the same next scene.
- For optional-with-skip choices, make one choice owner objective whose options
  include the optional scene and a skip option. Example: `Knock on the Companion's
  Door` versus `Go to Bed`. Put visible requirements such as relationship
  thresholds in option text/effects only when the player can reasonably know
  them; keep hidden trust, attraction, arousal, scene, or rule consequences in
  rewards and completion instructions. This is the preferred pattern for
  optional romance/NSFW moments when the user does not want separate side
  objectives.
- For multi-route convergence, do not use `exclusive_group` when all routes are
  valid and can be completed before a later event. Create separate route
  objectives/chains, then make the convergence objective require all route
  terminals. Use this for structures like defeating several generals before a
  boss, resolving several courts before a coronation, gathering several repair
  parts before a rebuild, or completing several trials before a throne scene.
- For fail-forward branches, avoid dead-ending the story on a bad choice unless
  the user explicitly wants hard failure. Let poor choices continue with debt,
  injury, lost resources, distrust, a harder route, a different ally reaction, or
  a worse ending path.
- For delayed callback choices, record the early decision with a story rule,
  relationship reward, state field, or story-inventory marker, then let a later
  objective or ending check that recorded consequence.
- For visible relationship-threshold choices, include locked options in the
  choice list with visible requirements/effects such as `Companion Name trust >= 6` or
  `Companion Name attraction >= 8`. Do not hide or swap the option text based on
  hidden stat checks; the game should show unmet options as unavailable.
- For resource-gated route order, expose multiple route objectives or choice
  options while making some require visible resources such as money, supplies,
  reputation, evidence, repair parts, or party trust before they can start.
- In Telltale-style stories, important choice clusters should usually have 2-4
  options and later objectives must preserve the selected path through
  `requires`, story rules, relationship rewards, state-field changes, map
  changes, image rewards, or death/failure endings when appropriate. Re-merge
  branches only after the permanent consequences have been recorded.
- Use `story_inventory` for story-owned resources such as credits, parts,
  reputation, suspicion, evidence, or repair supplies when those resources
  should be modified only by objective rewards. Show only concrete resource
  effects or requirements in the choice UI, such as `credits +500` or
  `Companion Name trust >= 6`; keep hidden outcomes in rewards and completion
  instructions.
- Branch rewards should update state/rules/map/cast so the branches do not
  collapse back into identical play.
- Use deterministic rewards for permanent story changes. Examples include
  repairing or transforming a character with `set_state_field`, changing a hard
  constraint with `add_story_rule`/`remove_story_rule`, moving someone out of a
  scene with `remove_state_list_item`, introducing a pressure source with
  `introduce_future_character`, and queuing images with
  `generate_profile_image`, `generate_solo_normal_image`, or
  `generate_story_image`.
- Use `generate_profile_image` only when a change affects face, hair, arms,
  torso, chest, shoulders, or overall silhouette. Use
  `generate_solo_normal_image` for major visible changes that should appear in
  chat. Leg-only or lower-body-only changes should normally generate a solo
  normal image, not a profile image.
- Use `generate_story_image` for authored non-character images that strengthen
  the story: important objects, locked doors, clues, symbols, maps, memory
  objects, locations, horror reveals, jump scares, ritual scenes, and other
  one-time visual beats. Include a stable `id`, exact `prompt`, and optional
  `negative_prompt`. This is not a title-card image and does not need a
  character target.
- Use `story_rules` as runtime law, not lore notes. Good rules are active
  constraints such as locked romance gates, current danger rules, repair
  boundaries, active pursuit, or body-state restrictions. Add and remove them
  through objective rewards as the story changes.
  Never add story rules that describe future engine work, schema conversion,
  temporary compatibility, pending implementation, or what a later maintainer
  should do. Those are creator notes, not runtime story law.

## Character And Scene Rules

- `characters` is the saved-state schema key for party members. AI-facing and
  player-facing text should call them `party members`.
- `npc_directory` holds NPCs and must use the current nested runtime shape:
  `npc_directory.locations.<location label>.characters.<npc name>`. Do not use
  the old flat shape `npc_directory.<npc name>`. Runtime scene normalization
  only resolves NPCs from the nested `locations` shape, so a flat opening NPC
  can be removed from `scene.npcs_present` even if the opening text names them.
- `players` is optional and only for start-of-game playable character select.
  If used, `state.player` remains a fallback/default copy of the first option.
- Unselected player options are not present in the scene or party.
- Use `state.players` when the premise does not require one locked protagonist
  and player choice would improve the story. Every player option must support
  the same objective logic. Opening text, objectives, story rules, and hidden
  guidance must use role-neutral wording such as `the player`, `the repairer`,
  or `the protagonist` unless the story is intentionally locked to one named
  protagonist.
- Objectives and hidden story rules must be written to work with whichever
  player character the user selects. Do not require the fallback player's name,
  gender, anatomy, personality, voice, or backstory unless the user explicitly
  requested a locked protagonist story.
- Do not reuse names or surnames from examples, templates, skill references,
  local story files, or unrelated locations. No non-player character should share a
  surname with any player option unless the story intentionally makes them
  related and records that relationship. No unrelated characters should share a
  surname with each other. If two characters share a surname, make the
  family/household relationship explicit in their character facts or rename one
  of them.
- For characters embedded in a story, build them to serve play. Durable facts
  should include how the character affects objectives, what they can do in
  scenes, what relationship tensions matter, and what future rewards or gates
  may change about them. Do not put unlock timing or objective scheduling inside
  character prose.
- Opening people who are physically present but not party members belong in
  `npc_directory`, not `characters`.
- Starting templates must not include temporary speaker state. If someone can
  speak in the opening, create a real named NPC or party member.
- If opening text contains an inline voice tag such as `(First Last)`, then that
  name must resolve before play starts: put the NPC under
  `npc_directory.locations.<current location label>.characters.First Last` and
  include `First Last` in `scene.npcs_present`, or make them a party member and
  include them in `scene.party_members_present`.
- For a present speaker whose identity is intentionally hidden, create the real
  NPC entry, set `player_known_name: false`, and set `player_facing_label` to
  the visible description the player can use. Add a later objective reward that
  sets `player_known_name` to `true` only when the story actually reveals the
  name.
- The player must never be placed in `scene.party_members_present`,
  `scene.npcs_present`, or `scene.speak_targets`.
- `scene.speak_targets` should usually start empty; if used, every target must
  already be physically present in the matching scene presence list.
- `scene.image_characters` should normally be `["Player"]` for the opening
  normal image, even when NPCs or party members are present. Opening NPCs and
  party members can receive their own profile/solo images through the app's
  character-image paths or objective image rewards. Only include other names in
  `scene.image_characters` when the story deliberately needs a group opening
  image instead of a solo player opening image.

## Runtime-State Separation

Use the authoritative field contract and final `Schema` checklist below. They
contain the complete immutable-definition, live-state exclusion, profile/image,
progression, preference, and blocked-meta-field rules.

## Story Memory Rules

Use the authoritative `state.story_memory` section below. It defines the only
supported memory buckets and the boundary between memory, rules, objectives, and
creator/process notes.

## Validation Checklist

Before finishing:

- JSON parses.
- Wrapper keys are present.
- Required state sections exist.
- Public metadata is present and uses approved genres.
- `creation_tool` matches the actual tool/model/intelligence used for this run,
  not a stale example value.
- For source-free stories, `source` is `"Original"`. High-level inspiration
  remains original when the finished setting, cast, conflicts, and plot
  expression are distinct. For an actual retelling, adaptation, continuation,
  or direct use of recognizable source material, verify the source value under
  the Source EmberAdventures Story extension instead.
- `nsfw` and `loli` follow current rules.
- `title_card_image` exists and stores only one active/default reference.
- `title_card_subjects`, if present, is a short non-spoilery list of visible
  cover subjects, not printed text.
- The creative-direction pass is complete: the core player fantasy, emotional
  target, world hook, progression/building axis, main relationship focus when
  relevant, midpoint or reevaluation moment, climax, ending/postgame shape, and
  structure mode are clear before final JSON.
- If the initial prompt could become several different games, the skill asked
  story-juice questions or proposed 2-3 directions instead of blindly choosing
  a generic plot.
- The objective spine acts as the story director: it creates anticipation,
  payoff, world motion, relationship pacing, and intentional failure/branch
  outcomes instead of relying on the live AI to invent them later.
- `world_map.locations` exists and is an object.
- `future_cast.enabled` exists and `future_cast.items` is an object.
- Objectives are arrays and all references are valid.
- No objective uses boilerplate verifier text such as
  `Return yes only when the player completes: {title}`.
- No objective uses generic verifier text such as
  `Return yes only when the player clearly takes action toward this goal`.
- No objective uses boilerplate narrator text such as
  `Resolve the immediate outcome of {title} and move to the next objective`.
- AI-controlled objectives do not use `player completes` phrasing in
  `completion_criteria`.
- Every objective has concrete criteria and instructions that can be understood
  without reading the title as the only source of meaning.
- One opening objective is active unless requested otherwise.
- The progression design pass is complete: current state, future state,
  starting rules, reward-driven changes, map unlocks, branches, image triggers,
  and future-cast introductions have all been intentionally considered.
- The feature-utilization pass is complete: any omitted major feature is omitted
  because it does not serve this story, not because it was forgotten.
- For romance, dark romance, harem, court, companion, and relationship-driven
  stories, the final check reports or internally verifies the number of direct
  choice objectives, the number of `adjust_relationship` rewards, and at least
  one relationship-building/test objective for each major relationship lead.
- Serious stories use deterministic objective rewards for important permanent
  changes instead of relying only on narrator prose.
- Side objectives have useful story/game consequences where appropriate.
- Branches that are truly one-path-only use `exclusive_group`, branch-specific
  `requires`, and branch-specific rewards. Branches that can all be completed
  do not use `exclusive_group`.
- Conditional consequence routing uses `next_objectives` on the completed
  objective, not a fake visible choice or separate empty branch node. Every
  referenced next objective exists, requirements are structured and
  story-state-based, and any default fallback is last.
- Scene-adjudicated hidden routing uses `route_control: "ai"` and
  `outcome_routes`, never a fake visible choice. Route ids and criteria are
  private, route ids are unique, exactly one route is the no-requirements
  fallback/default, every route has a valid next objective or `terminal: true`,
  and the objective does not also contain `next_objectives`.
- Visual tree integrity is valid: every objective id is unique, every
  `requires` id exists, every `next_objectives[].objective_id` exists, direct
  choice objectives have owned `choices[]`, choice options have visible titles
  and deterministic rewards/effects, and non-final main objectives have either
  outgoing `next_objectives` or real dependent objectives. A main objective
  with no outgoing/dependent route must be an explicit terminal ending/death
  objective with deterministic ending rewards. Do not leave hidden or future
  objectives unreachable, and do not rely on EmberAdventures's fallback objective
  picker as normal story flow.
- Choice-heavy stories keep choice objectives meaningful but not constant:
  roughly 30-40% choice objectives for multiple-ending/Telltale-style requests,
  and normally never more than half unless explicitly requested.
  Hidden shop-triggered post-purchase hooks and one-option job start/turn-in
  objectives are counted separately and do not count as visible pacing choices.
- Optional romance/NSFW moments can be baked into the main flow with an
  optional-with-skip choice owner objective rather than a separate side
  objective.
- Multi-route convergence uses separate playable branches that all must be
  completed before the merge objective; reserve `exclusive_group` for true
  one-path-only decisions.
- Fail-forward branches keep the story playable after bad choices through debt,
  damage, distrust, worse routes, or altered endings instead of accidental
  dead-ends.
- Delayed callback choices persist early choices through explicit rewards/rules
  so later objectives or endings can react to them.
- Relationship-threshold choices show locked options and visible requirements in
  the choice UI; do not hide or rewrite options based on hidden thresholds.
- Choice option `effects` are player-facing UI text. They may show only
  currently visible requirements or concrete mechanical deltas such as
  `credits -80`, `trust >= 6`, `suspicion +1`, or `key required`. Do not put
  route labels, ending labels, unlock labels, hidden recommendations, or
  outcome spoilers in `effects`; store those consequences in rewards, story
  rules, and completion instructions instead.
- Resource-gated route order uses visible requirements for money, supplies,
  reputation, evidence, parts, or trust when a route is available but not yet
  startable.
- `state.players`, if present, contains full player definitions and only exists
  for real player select.
- For player-select stories, opening text, objective text, story rules,
  relationship memories, shop notes, future-cast notes, and hidden guidance use
  generic role/protagonist prose unless the field belongs to one specific
  player definition. No fallback player name, gender, pronoun, anatomy,
  backstory, or voice leaks into shared story text.
- No non-player character shares a surname with any player option unless they
  are intentionally related and that relationship is explicit in durable facts.
  No unrelated characters share surnames with each other. No example/template/
  reference names or surnames were reused accidentally.
- If duplicate surnames remain, every duplicate has an explicit family,
  household, clan, or source relationship in durable facts.
- Embedded characters use the current character schema.
- Embedded characters use `speech_style` for durable dialogue behavior and
  `personality_description` for identity/motivation. Do not put TTS voice names,
  current mood, or private story instructions in `speech_style`.
- `can_die`: Internal boolean plot-armor flag. Standalone character definitions default to `false`. Story-embedded important characters should usually be `false`; disposable/simple NPCs may be `true`. This field is hidden from AI prompts and should never be explained in player-facing prose. Objective rewards may change it with `set_state_field`, and `kill_character` can override it only with `ignore_can_die: true`.
- Embedded character definitions do not include `power`, active `known_facts`,
  active `clothing`, active `inventory`, active `image`, profile image history,
  story-image history, or other live/runtime fields.
- Important embedded characters pass the character-depth floor: concrete
  durable facts cover identity, role, personality under pressure, usefulness,
  relationship dynamics, quirks/preferences, and relevant story complications.
- Embedded character names are proper names, not titles/jobs/groups.
- Body/appearance fields are meaningful and current.
- `appearance.extra_description` is the general extra durable visual-detail field.
  Use it for unusual upper-body anatomy, scars, markings, species details, or
  visual facts that no specific appearance field can express. Do not repeat body
  size/shape/proportion already represented by `height`, `muscular`,
  `shoulders`, `chest`, `stomach`, `hips`, `waist`, `legs`, `arms`, hair, skin,
  or eyes. Bad examples: `thin adult body`, `large breasts`, `wide hips`,
  `defined abs`, or `long legs` when those are already encoded by numeric/body
  fields.
- Set `appearance.nonhuman_lower_body` to true only when normal humanoid hips
  and legs are replaced by a distinct nonhuman lower body. Then describe that
  replacement concretely in `appearance.extra_description_lower_body`; do not
  repeat numeric hips or legs there. Keep every clothing slot the character
  actually wears. Profile prompts omit this lower-body description, while
  lower-body-capable normal and group prompts include it.
- When `appearance.nonhuman_lower_body` is false,
  `appearance.extra_description_lower_body` may still contain a concrete visual
  detail that applies only below the waist; otherwise use `""`.
- Clothing and outfits use current clothing slots only.
- `voice` is always `null` in authored character definitions. Story-generation
  tools do not have the installed TTS/screen-reader voice data needed to assign
  it correctly. Do not infer a voice, use a character or actor name, or ask for
  voice metadata during normal story creation.
- Current scene fields exist: `intimacy_level`, `spicy_mode`,
  `party_members_present`, `image_characters`, `npcs_present`, `speak_targets`,
  `image_action`, `sex_position`, and `ai_sex_position`.
- The player is not in scene presence/speaker lists.
- Every starting `scene.npcs_present` entry resolves to an NPC under
  `npc_directory.locations.*.characters`, and every inline opening speaker tag
  resolves to a present NPC or party member. There are no flat
  `npc_directory.<npc name>` entries.
- Temporary speaker state is omitted.
- Locked future cast is not visible in map/current scene/opening/library text.
- Shop/future-cast integrity is valid: every character-shop `character_id`
  exists in `future_cast.items`, every future-cast item id matches its key,
  every `on_purchase_objective` exists or is intentionally pending with a note,
  every locked shop item has visible requirements or an unlock reason, full
  character data is not duplicated inside shop items, and purchasable characters
  are not present in the map/current scene before unlock.
- Story job-board item schema is consistent: story jobs use `id`, `title`,
  `summary`, `genres`, `nsfw`, `rank`, `requirements`, `reward_coins`,
  `reward_xp`, optional `reward_items`, optional `client_npc_id`, optional
  `start_location`, `completion_criteria`, and `completion_instruction`; no
  alternate `quest_id`, generic `reward`, `purchased`,
  `on_accept_objective`, or free-text reward blob fields are used for job
  items.
- Every story-job `start_location`, if present, is a location object rather
  than a string id. Every story job is self-contained for the runtime-generated
  job objective flow and does not refer to a separate linked authored objective
  chain in its criteria or instruction.
- Every `story_shops[type="job"].items[].genres[]` label exists in the
  story's public `genres[]`; otherwise the job may be hidden by genre
  filtering.
- Every `story_inventory.rule_flags includes X` requirement is reachable:
  either `X` is present in the starting `story_inventory.rule_flags` array or
  some objective reward can add `X` with `add_state_list_item`.
- Numeric story-inventory changes use `adjust_story_inventory` deltas for
  add/spend changes, `operation: "multiply"` or `"divide"` for percentage or
  ratio math, and `operation: "set"` only when a deliberate exact reset/set is
  intended. Do not accidentally overwrite `story_inventory.coins`, credits,
  XP, reputation, suspicion, or parts with `set_state_field` when the story
  meant to change a numeric amount.
- Before final export, search story text for known process/future-system
  phrases and remove or rewrite any hits as current in-world runtime
  constraints: `future engine`, `future shop`, `future quest`, `should later`,
  `convert these`, `until those systems exist`, `linked objective`,
  `authored objective`, and `objective chain`.
- Clean exports do not rely on `settings` or `meta.allow_spicy`.
- Public metadata uses `starting_party_member_count`, never
  `starting_character_count`.
- Story descriptions are player-facing pitches, not hidden outlines.
- Player-visible fields do not reveal future cast, future roles, locked
  locations, hidden rewards, private AI instructions, or implementation notes.
- `state.meta.story_source` has no old planner-summary or source-outline
  fields.
- `story_memory.ai_private_notes` contains only concise in-world continuity
  constraints when needed; it does not contain coverage-table text, omission
  reports, audit notes, or creator-process instructions.
- No removed genre tags such as `game`, `progression`, `survival`, or `litRPG`.
- No mojibake or accidental replacement characters in prose.
- Do not rely on a later main-thread cleanup pass. The final JSON must be the
  best complete version this skill can produce on its own.
- Do not rely on cherry-picking between drafts. The final JSON must already
  contain the best internally selected objective structure, cast coverage,
  character definitions, map, metadata, opening, and validation fixes.

## Durable Guidance Updates

If new reusable normal-story guidance appears, update this base skill or
propose the update before continuing. Guidance that applies only to
source/canon research or adaptation belongs in the source extension. Minor
process clarifications can be patched directly; substantive workflow changes
should be discussed with the user first.

# Objective Direction, Handoffs, And Iterative WIP Editing

## Choose Scene Mode Intentionally

Normal EmberAdventures stories may move in and out of two complementary modes.

- **Authored scene sequence:** Use a tight chain of linked objectives when the
  story needs deliberate pacing, a sequence of reveals, political procedure,
  investigation, training, negotiation, romance development, an emotional
  confrontation, a social ritual, a trial, a mission briefing, or any scene
  where each response should establish the next beat. A tight chain is not
  limited to the opening. Enter it whenever the author needs to tell a
  particular sequence of scenes, then return to broader player control when
  that sequence has delivered its purpose.
- **Open objective:** Use a larger objective when the player should control the
  method, order, tone, or amount of engagement: explore a city, earn access to
  a faction, investigate a mystery, prepare for a journey, pursue optional
  relationships, or solve a problem by any plausible approach. Do not create
  artificial micro-objectives merely to force the player through an otherwise
  open situation.

A strong story alternates deliberately. A broad objective can lead into a
political hearing; the hearing can use a tight sequence of authored objectives;
after the decision and consequences, the story can return to a broad objective.
Freeform relationship time can lead into a tightly authored confession,
argument, invitation, boundary, or shared crisis, then return to free play.

## Required Objective-Handoff Pass

For every objective in an authored scene sequence, validate this handoff:

`previous completion criteria -> previous completion instruction -> current
scene -> next title -> next summary`

Before writing or revising Objective N, inspect Objective N-1 and answer:

1. What exact player action or world result completes Objective N-1?
2. What does its one-time completion response show?
3. Where is the player after that response?
4. Who is physically present, and who is only known or expected elsewhere?
5. What does the player know, and what remains hidden?
6. What immediate action, choice, conversation, or freedom is now available?
7. Does Objective N's title clearly ask for that action?
8. Does Objective N's summary describe that exact live situation and why the
   action matters now?
9. Does Objective N-1's completion instruction stop before doing Objective N
   for the player?

Do this pass for each handoff in a tight sequence. For a broad/open objective,
validate only that its starting situation and completion criteria leave room for
multiple credible player approaches.

When the user builds objectives incrementally, begin the response by restating
the previous approved objective's completion criteria and completion instruction
before proposing the next objective. Do not jump ahead into unapproved future
content. Preserve stable ids and unrelated story data.

## Completion Instructions Are One-Time Handoffs

`completion_instruction` directs the immediate narrator response after that
objective completes. It is not permanent scene guidance, durable memory, a
replacement for deterministic rewards, or permission to complete the next
objective automatically.

Use it to do only the work needed to hand the story forward:

- show the immediate consequence;
- reveal one relevant fact;
- visibly introduce someone whose definition has been unlocked or made current;
- move the scene or advance time;
- establish the next actionable situation.

Then stop. A completion instruction should hand the scene to the next objective,
not consume the next objective's playable content. A travel objective normally
establishes the destination and the next interaction; it does not perform the
entire conversation, lesson, negotiation, or conflict waiting there.

## Objective Summaries Describe The Live Situation

An objective summary is player-facing. It describes the immediate situation and
why the requested action is relevant now. Include current pressure, useful
context, available freedom, and who or what is waiting when that information
helps the player decide what to do. If an objective has a `summary` field, do
not leave it blank. The player usually opens the summary because they want help,
so give a minor non-spoilery hint about how to approach or complete the
objective: likely person, place, action, resource, topic, or constraint. It must
add meaningful context beyond the title without exposing hidden future outcomes,
route labels, endings, betrayals, or unearned consequences.

## Reusable Objective Patterns

### Multi-Topic Conversation Or Teaching

Use one objective for a coherent lesson, interview, debrief, negotiation, or
conversation even when it has several related concepts. Do not split one
natural exchange into trivial "ask one question" objectives.

- Give the objective a title that identifies the person or subject.
- Use the summary to name the broad topics.
- List each required fact or concept in `completion_criteria`.
- Require that the NPC actually explain every required topic; do not require
  exact player wording.
- Use the completion instruction only for the practical next step.

Use separate objectives only when a topic naturally becomes its own scene,
choice, conflict, travel action, or relationship beat.

### Freeform Interlude

Use a broad or tightly bounded objective to provide freeform time before one
concrete advancement action: dinner before sleep, an inn evening before
departure, downtime before a briefing, exploration before leaving a building,
or companion conversation before a mission.

Make the eventual advancement action clear. Permit unrelated conversation,
exploration, visitors, or optional interaction first. Complete the objective
only when the player performs the actual advancement action. Do not assume
freeform dialogue creates durable facts or relationship changes; persist any
important result through supported state changes or rewards.

### Time Advancement

For sleep, rest, waiting until an event, or another time jump, make criteria
name the actual state-changing action and explicitly reject plausible
near-misses when useful. Entering a bedroom, lying down, or receiving a visitor
is not necessarily sleeping. The completion instruction may move the player,
advance the time fields, show the wake-up/event, and establish the next action.

### Bridge Objective

When location, time, social context, purpose, or the set of present characters
changes, ask whether that transition is itself a playable beat. Add a bridge
objective when the player needs to choose, travel, converse, prepare, or
otherwise take an action to enter the next scene. Do not jump from a reveal to
bedtime, from an introduction to training, or from an event to an unrelated
location without an authored handoff when the transition has playable value.

## Persistence And Knowledge

Anything later play must reliably know must be persisted in the correct
supported structure. Opening prose and completion instructions establish a
moment; they are not durable memory by themselves.

- Use a state field for an exact supported mechanical value.
- Use a story rule for a current hard runtime constraint or mechanic the
  narrator must obey, not ordinary lore or biography.
- Use story memory/world notes for durable continuity or lore when it does not
  need deterministic mechanical enforcement.
- Use a character/NPC field for identity, ability, durable facts, and other
  facts belonging to that person.
- Use an `adjust_relationship` reward for a persistent social change.
- Use location/map rewards and fields for discovery, availability, and travel.
- Use inventory fields and supported inventory rewards for controlled resources.

Do not invent undocumented nested state paths merely because a generic patch
could write them. Model a custom mechanic only in a documented supported
location. If the normal story schema lacks a suitable supported location,
identify that as an app/schema decision instead of silently inventing a new
persistent shape.

For every important reveal, maintain a knowledge partition: what the player
knows; what each present companion knows; what natives, officials, specialists,
and antagonists know; what is common knowledge; and who learns what during this
scene. Do not make all present characters react as though they share the same
information.

Narrate unfamiliar worlds through the player's knowledge lens. Distinguish what
the player directly perceives, what they can reasonably compare to familiar
media/history, what has been explicitly explained, and what remains unknown.
Do not turn author knowledge into player knowledge.

## Reveal Embargoes And Ensemble Scenes

For an important hidden class, identity, betrayal, secret power, appraisal,
relationship, or mystery, define the reveal objective and audit the embargoed
term/fact before it completes. Scan player-visible/current-context fields:

- title, description, public metadata, and `meta.story_source.description`;
- opening messages, current scene summary, current location text, and current
  NPC/character fields;
- visible objective titles and summaries;
- any current player fields shown in UI or included in ordinary prompts.

The hidden fact may appear in the revealing objective's completion instruction,
deterministic rewards, and later hidden objectives where appropriate. Do not
leak it through an early summary, metadata, current state, or image prompt.

Ensemble openings are valid when the premise requires a group event, summoning,
trial, team selection, family scene, crew introduction, or class ceremony. Keep
one immediate actionable focus, limit unnecessary speaking roles, avoid a cast
encyclopedia, and define every named speaker as a real current NPC or party
member before their voice tag appears. The player must never be placed in scene
speaker/presence lists.

For crowd reactions, do not write a crowd as one synchronized emotional organism
unless that unity is intentional. Differentiate nobles, officials, attendants,
servants, soldiers, and individuals through silence, alarm, whispers, pity,
disbelief, restrained ridicule, calculation, or conflicting reactions.

## Character Introduction And Map Timing

A visible introduction in `completion_instruction` is not a substitute for a
usable character definition. Predefine recurring or important later characters
in `future_cast` with full data. At the objective where they visibly arrive,
use the applicable introduction/promotion/state rewards so their identity,
availability, and scene presence persist. Do not store a character's identity
only as a story rule.

Distinguish map existence, discovery, travel availability, current location, and
focus location. A location may exist in the template but remain hidden or
unavailable. Unlock it no later than the first objective where the player may
reasonably visit or use it. For a travel handoff, validate applicable updates to
current location, focus location, location detail, discovery/travel availability,
travel history, and valid map connections. Prefer a meaningful hierarchy such
as world -> region -> settlement -> district/building -> room/site rather than
using an unrelated room as the parent of every room in a building.

## Incremental WIP And Final-Release Modes

Use **incremental WIP mode** when the user is intentionally approving a story
one objective, scene, character, or change at a time.

1. Read the exact latest target file.
2. Detect normal story-template versus filesystem-backed Codex story shape
   before authoring. A normal story uses the wrapper documented by this skill
   and `storyTemplate.state.objectives`. It has no `story_engine` or
   `schema_version` discriminator. Route filesystem-backed Codex stories to
   `original-emberadventures-codex-story`.
3. Identify the approved frontier and previous handoff.
4. Propose or patch only the requested fields.
5. Preserve unrelated fields and stable ids.
6. Keep unfinished future routing only at the explicit WIP frontier.
7. Keep WIP/incomplete status outside player-visible story prose and metadata.

Use **final-release mode** only when the user asks for a finished/import-ready or
publish-ready story. Run the complete schema, handoff, visibility, routing,
character, map, and quality passes. No non-terminal main objective may remain
without an intentional route in final-release mode.

## Local File Update Verification

When Codex is asked to modify a local story file:

1. Read the exact source file and identify the requested target/version.
2. Preserve a backup or write a new numbered version when overwrite reliability
   is uncertain or the user asks to preserve prior drafts.
3. Apply only approved targeted changes.
4. Write the output.
5. Reopen the written output and parse it as JSON.
6. Verify exact expected values: objective count and ids, edited titles,
   summaries, criteria, instructions, rewards, `requires`, `next_objectives`,
   location references, and any other requested values.
7. Report success only after that verification and give the exact output path.

Do not claim a write succeeded merely because an edit command was issued. This
procedure applies to Codex file edits; it does not assume a user working in an
external ChatGPT session has local filesystem access.

## Adjacent-Title Rhythm

Read objective titles in sequence as well as individually. Improve repetitive
adjacent title shapes when a clearer natural verb exists, but preserve clarity
and stable ids. Repetition is a soft quality concern, not a reason to replace
the clearest player-facing title.

# Integrated Reference Material

The following sections were formerly bundled reference files. They remain authoritative and are included here so this skill is fully self-contained.


---


# EmberAdventures Objective Patterns

Use objectives as the playable story engine.

## Objective Item

Recommended object:

```json
{
  "id": "stable-kebab-id",
  "title": "Short Action Title",
  "type": "story",
  "status": "hidden",
  "summary": "One sentence explaining why this beat matters.",
  "rewards": [],
  "requires": ["previous-objective-id"],
  "next_objectives": [],
  "travel_location_id": "",
  "travel_location_name": "",
  "unlock_mode": "manual",
  "exclusive_group": "",
  "selectable": false,
  "available_now": false,
  "blocked_reason": "",
  "notes": [],
  "completion_message": "",
  "completion_control": "player",
  "completion_criteria": "Return yes only when the player has asked the wounded courier who attacked them, inspected the sealed letter, or otherwise clearly committed to investigating the ambush.",
  "completion_instruction": "Let the courier reveal one urgent lead, show the immediate danger created by the letter, and point the scene toward the next concrete investigation objective.",
  "auto_completed_from_prereqs": false
}
```

Opening objective differences:

- `status`: `"active"`
- `requires`: `[]`
- `available_now`: `true`

## Chain Design

For long original stories, make a milestone list first, then convert milestones into objectives.

Good objective granularity:

- One scene-scale task.
- One decision, encounter, purchase, reveal, or travel beat.
- Avoid giant objectives like "complete the entire city arc."

Use hidden main objectives for story order. Use hidden side objectives for optional intimacy, downtime, investigations, training, shopping, extra character focus, premise-specific side content, mechanically useful detours, comedy beats, and other memorable play.

Default to including meaningful side content in full story templates. A good
story usually has a main spine plus optional branches, not only a straight
line. Do not omit major side stories or fun one-off side objectives unless the
user asks for a minimal/critical-path-only template.

Side content can be:

- A single one-off objective.
- A short side chain.
- A side tree with a decision or reward choice.
- A major optional arc unlocked by a hub, cast member, location, or main-story
  milestone.

Branching main structure is also normal. One objective may unlock multiple
paths; several paths may all be required before a major later objective; or
optional branches may open alongside the next main objective. Use this when it
matches the source/story instead of forcing every campaign into one linear
chain.

## Story Direction Before Objectives

Before drafting objectives for a serious story, define the player fantasy,
emotional target, world hook, progression/building axis, major relationship
arcs, midpoint or reevaluation moment, climax, ending/postgame shape, and
structure mode. If those pieces are vague, the objective chain will usually
become a list of chores or chapter titles instead of a playable story.

Use the objective spine to enforce anticipation and payoff. The live AI can
write individual scenes, but objectives must decide when relationships soften,
when information is revealed, when intimacy becomes available, when an NPC's
attitude changes, when failure matters, and when the world reacts.

For relationship-driven stories, place bridge objectives between major plot
beats. Good bridge objectives can ask the player to spend time with someone,
learn something personal, earn a voluntary disclosure, prepare together,
survive a small mission, share downtime, recover after conflict, define a
boundary, accept or refuse temptation, or deal with jealousy/consequences. Do
not jump directly from introduction to attraction to sex or loyalty unless the
user explicitly requested that pacing.

For NSFW stories, design sexual content as part of the story arc. Use
objectives to create invitation, tension, consent/refusal, anticipation,
ambiance, escalation, and aftermath. Optional-with-skip choices are useful when
the story should offer intimacy without forcing it.

Give the world and major NPCs motion outside the player's immediate action.
Objectives may represent rivals acting, deadlines moving closer, shop/job
opportunities changing, NPCs pursuing their own plans, or the player arriving
too late. Failure, rejection, death, loss, and missed opportunities are valid
story outcomes when they are intentional and supported by rollback/choice flow.

## Story Structure Mode

Before drafting objectives, ask whether the story should be one of these modes
unless the user already specified the structure:

- Open adventure: a clear main direction with significant freedom, broad side
  objectives, exploration, jobs, shops, and AI-adapted connective play.
- Guided story: a strong main objective chain with open interludes and optional
  side arcs between authored story beats.
- Time-controlled story: main events are scheduled, time-locked, and separated
  by downtime gaps where the player may explore or pursue side content.
- Choice-heavy / Choices-like: direct player choice menus, mutually exclusive
  routes, hidden outcome logic, branch consequences, and multiple endings.
- Sandbox: world setup, systems, recurring loops, locations, jobs, shops, and
  emergent objectives with little or optional fixed plot.
- Relationship-focused: objectives primarily develop trust, affection, desire,
  rivalry, dependency, loyalty, betrayal, repair, or other character arcs.
- Telltale-style branching: direct player choice menus, mutually exclusive
  routes, hidden outcome logic, failure/death branches when appropriate, and
  multiple endings.
- Linear/mostly-linear: one strong objective spine with bridge objectives,
  side arcs, and occasional real choices only when they materially change play.

If the user does not know which mode they want, do not dump every option as a
blocking questionnaire. Ask a few story-intent questions, then recommend one to
three suitable modes with a short reason. The user may choose one, blend them,
or say "you decide"; if they delegate, choose the structure that best serves the
premise and explain the practical result briefly. Once those few questions give
enough direction, explicitly offer to complete the story instead of continuing
to ask more questions.

If interaction is unavailable or the user explicitly asked for no questions,
infer from the premise. Moral dilemmas, dark romance agency choices, faction
routes, survival mistakes, player-defined laws, bargains, and ending decisions
usually benefit from Telltale-style structure. Guided adventures, focused
relationship arcs, slice-of-life loops, and simple original adventures often work
better as linear/mostly-linear stories.

Do not encode the structure mode as visible story content or a JSON field. It
is an authoring choice.

### Internal Story-Structure Lenses

Use story theory as an internal planning tool, not as homework for the user.
After understanding the premise, quietly check whether any of these lenses
would improve pacing, objective order, or relationship payoff. Use one, blend
several, or ignore them when they do not fit. Tell the user the practical story
shape, not the theory label, unless the label helps discussion.

- Hero's journey: ordinary situation, call/displacement, mentor/allies, trials,
  midpoint revelation, major test/loss, transformation, final ordeal, aftermath.
- Three-act structure: setup, confrontation/escalation, resolution.
- Five-act escalation: setup, rising complications, midpoint turn, crisis,
  climax, aftermath.
- Mystery/investigation: hook, clue chains, suspects, false leads, reveals,
  confrontation, truth/consequence.
- Romance/relationship arc: first impression, friction, shared task, trust,
  vulnerability, rupture/test, repair/commitment or changed distance.
- Faction/political arc: factions, leverage, public events, private bargains,
  betrayals, reputation shifts, power change.
- Open-world hub-and-spoke: hub, optional spokes, gated main milestones, world
  state changes, return-to-hub consequences.
- Countdown/crisis: visible pressure, limited windows, tradeoffs, missed-event
  consequences, decisive intervention or failure.
- Corruption/temptation: offer, compromise, benefit, consequence, point of no
  return or resistance.
- Redemption: harm/guilt, denial, consequence, restitution, sacrifice, earned
  trust.
- Tournament/trial ladder: repeated tests, rival development, rising stakes,
  rule changes, final trial.
- Survival/escalation: scarcity, danger, adaptation, loss, escape/conquest.

### Structure-Specific Objective Patterns

These are helper patterns, not rules the story must obey. Objective trees should
be structured to follow the story's intent and make the experience feel the way
the creator wants. Use, modify, combine, or ignore these patterns when a better
objective tree fits the story.

For open adventure:

- Start with one clear main objective that gives direction without locking the
  player into a narrow path.
- Add broad side objectives, rumors, shops, jobs, locations, and NPC goals.
- Use discovery, travel, investigation, relationship, and resource objectives
  to let the player choose how to engage.
- Avoid too many locked objectives; use state, memories, story rules, and
  hidden outcome routes to adapt to the player's direction.

For guided story:

- Build a main objective chain with meaningful bridge objectives between major
  beats.
- Use tight objective clusters for authored scenes such as meetings, dinners,
  political sessions, discoveries, fights, or relationship development.
- Insert freeform interludes after tight clusters so the player can talk,
  explore, shop, train, rest, or pursue side content.
- Unlock side objectives and relationship scenes from main milestones.

For time-controlled stories:

- Put main story events in `story_pacing.timeline`.
- Make every main story objective before final aftermath/freeplay
  `time_locked` and `locked_until_complete`.
- Create downtime by spacing scheduled events or objective-triggered future
  events. This is the normal recommended form of time-controlled pacing because
  it lets players explore, shop, do jobs, rest, and pursue side objectives
  between main story events.
- Use wait prompts when the next event is ready but the player has not started
  it.
- Author missed-event consequences when overlapping events intentionally force
  the player to miss one.
- Use strict time-controlled pacing only for urgent arcs where side content
  should be unavailable, such as battles, escapes, trials, disasters, or
  consecutive endgame set pieces.

For choice-heavy / Choices-like stories:

- Use explicit `completion_control: "choice"` owner objectives for moments
  where the player knowingly chooses.
- Keep option titles and summaries non-spoilery; hide route labels and hidden
  outcomes.
- Apply durable consequences through relationship rewards, story rules,
  inventory/resources, future-cast changes, map changes, deaths, endings, or
  state-field updates.
- Use branch-and-bottleneck structure to prevent impossible content explosion:
  choices change state and later scenes, but major milestones may reconverge.

For sandbox stories:

- Prioritize locations, systems, recurring jobs, shops, social loops, rumors,
  factions, and reusable objectives.
- Keep the main plot light, optional, or generated from player action unless
  the user asks for a stronger spine.
- Use broad hub objectives and rotating/renewable side content.
- Let player behavior create new objectives through state changes and story
  memory instead of relying on a fixed chapter chain.

For relationship-focused stories:

- Build objective chains around shared tasks, private conversations, trust
  tests, vulnerability, jealousy, boundaries, conflict, repair, intimacy, or
  loyalty.
- Track durable relationship changes with deterministic rewards; do not rely
  only on narrator prose.
- Use tight clusters for emotional scenes, then open space afterward for
  player reaction and follow-up.
- Store promises, fears, avoided topics, favorite memories, and changed
  boundaries in durable state when they matter later.

Useful objective purposes include discovery, travel, conversation/teaching,
trust-building, explicit choice, hidden AI route, training, shop/job/resource
loop, crisis, aftermath, hub/freeform interlude, faction move, relationship
repair, and ending/freeplay transition. Do not force these labels into JSON
unless the normal objective fields need them; they are planning aids.

For Telltale-style stories:

- Use several `completion_control: "choice"` clusters when the story scope
  supports them.
- If the user asks for multiple endings, many choice objectives, or a
  Telltale-style story, use roughly 30-40% choice objectives as a general target.
  Do not make more than half the objectives choices unless explicitly requested.
- Create one visible owner objective for each choice cluster. Set
  `completion_control: "choice"`, `selectable: true`, and use a `choices`
  array for the options.
- Give each branch deterministic consequences through story rules,
  relationship changes, state-field changes, map/location changes, image
  rewards, items, or death/failure endings.
- Keep major branch option UI non-spoilery. Choice titles should be the visible
  options; `summary` should clarify what the option means in the current scene
  when helpful, and `effects` should be empty unless it shows only visible
  requirements, visible costs, or story-inventory changes. Do not reveal
  death, failure, sale, romance, betrayal, ending, route labels, unlock labels,
  hidden recommendations, or hidden branch outcomes in player-facing choice
  text. Bad visible `effects` examples include `Bad ending route`, `Unlocks
  Mira treatment route`, `Hana affection route`, and `Best with first law:
  Truth or Freedom`. Good visible `effects` examples include `credits -80`,
  `trust >= 6`, `suspicion +1`, and `requires cellar key`.
- Make later branch objectives require the choice owner objective, and preserve
  the selected path through the chosen option's rewards: story rules,
  relationship changes, state changes, item/resource changes, or death/failure.
- Re-merge only after consequences are recorded, so the branches do not feel
  identical.

For romance, dark romance, harem, court-intrigue, companion, and
relationship-driven stories, audit choice mechanics even when the story is not
fully Telltale-style. Important choice clusters often include first trust,
first boundary, first bargain, choosing who to protect, defining a relationship,
choosing whether to escalate intimacy, choosing a faction/lover/rival stance,
and choosing an ending. If the story has none of these, verify that the premise
is intentionally linear and that player agency is still represented by bridge
objectives.

Use these branch shapes deliberately:

- Immediate merge: a choice records relationship/stat/rule consequences, then
  the next shared objective requires only the choice owner. Use for short
  boundary, stance, flirt/refuse, mercy/cruelty, or tone choices.
- Optional with skip: a choice offers an optional scene and a skip option, such
  as `Knock on the Companion's Door` versus `Go to Bed`. Use this for optional romance
  or NSFW moments inside the main objective flow when the user does not want side
  objectives. Put only visible requirements/effects in player-facing option text.
- Multi-route convergence: separate route objectives/chains can all be completed
  before a larger event. The merge objective requires every route terminal. Do
  not use `exclusive_group` for these, because the routes are swappable and all
  valid.
- Fail-forward: a bad choice continues the story with debt, damage, distrust,
  lost resources, harder routes, or worse endings rather than accidentally
  ending play.
- Delayed callback: an early choice stores a rule, relationship change,
  state-field value, or story-inventory marker, and a later objective or ending
  reacts to that stored consequence.
- Conditional next routing: a completed objective can choose which next
  objective becomes active based on current story state, without showing a
  player choice menu. Use `next_objectives` on the completed objective for
  hidden consequence routing such as exposure, suspicion, reputation, money,
  injuries, relationship thresholds, or public/private outcomes. Entries are
  evaluated in order; the first matching entry wins. Use a final entry with no
  requirements as the default path when appropriate.
- Visible relationship-threshold fork: keep all relevant options visible in the
  choice list and show requirements such as `trust >= 6`, `attraction >= 8`, or
  `affection >= 5`. The game should show unmet options as locked/red; do not
  hide or rewrite the options based on hidden thresholds.
- Resource-gated route order: expose several route objectives/options, but make
  some require visible resources such as money, supplies, reputation, evidence,
  repair parts, or party trust before they can start.

For linear/mostly-linear stories, do not add fake choice menus. Use bridge
objectives to make pacing, relationships, world understanding, and intimacy
build naturally between major story beats.

For NSFW stories, optional adult side objectives are appropriate when they fit
the story and all characters involved are valid adult characters. For SFW
stories, side objectives should remain SFW. Do not hardcode any specific adult
side objective pattern; choose content that fits the premise.

Do not add legacy duplicate body fields such as `objective`, `steps`, `current_step_id`, or `selected_step`. The current app uses `summary` for player-facing objective text and the completion fields for verifier/narrator behavior.

Do not use the old nested completion-object shape:

```json
{
  "completion": {
    "type": "player_reaches_location",
    "location": "place-id"
  }
}
```

Convert that intent into the current flat fields instead:
`completion_control`, `completion_criteria`, and `completion_instruction`.

Every objective needs:

- `completion_control`: `"player"` when the player must initiate/ask/travel/buy/inspect; `"ai"` when the narrator resolves a plot beat such as combat, aftermath, or a reveal; `"choice"` when EmberAdventures should show a forced player choice menu, complete the owner objective immediately, and apply the selected option's rewards without AI verification; `"reward_only"` only for a hidden deterministic transition node that immediately applies rewards and moves to its next objective when reached.
- `completion_criteria`: private verifier criteria for when the objective is complete and, where useful, what counts only as progress.
- `completion_instruction`: narrator instruction after completion, especially for introducing unlocked predefined future-cast characters.

`completion_criteria` and `completion_instruction` must be authored content,
not generated boilerplate. Never write:

- `Return yes only when the player completes: {title}.`
- `Return yes only when the player completes or survives...`
- `Return yes only when the player completes, submits, or receives...`
- `Return yes only when the player clearly takes action toward this goal...`
- `Resolve the immediate outcome of {title} and move to the next objective.`
- `Continue naturally from completing this objective.`

For player-controlled objectives, criteria must name the exact player action,
commitment, question, purchase, travel, inspection, choice, or conversation that
finishes the objective. For AI-controlled objectives, criteria must name the
resolved narrator/world state that must be shown in the narrator reply and must
not say `player completes`.

Every non-terminal main objective must route intentionally. Use a dependent
objective with `requires`, use `next_objectives` when the next route depends
on structured state, or use hidden `outcome_routes` when it depends on natural
scene context. A main objective with none of those routes must be an explicit
terminal ending/death objective with deterministic ending rewards. Do
not rely on EmberAdventures's fallback objective picker as normal story flow.

Do not design objectives so one player message should complete several
objectives at once. EmberAdventures checks one selected objective at a time. If one
message can reasonably finish multiple consecutive objectives, those objectives
are probably too small, duplicated, or poorly ordered. Merge them or rewrite the
chain so each objective represents one meaningful scene-scale beat.

For relationship, romance, court, trial, mystery, and slow-burn stories, use
bridge objectives between chapter-scale milestones. Bridge objectives should
build trust, suspicion, attraction, world understanding, private conversation,
or practical preparation before the next major event. Do not place large
chapter beats directly next to each other unless the story is deliberately fast.
For romance, dark romance, romantasy, harem, companion, and courtship-heavy
stories, use more relationship bridge objectives than ordinary adventure
stories. Major plot objectives should often be separated by chances to talk,
recover, flirt, refuse, test trust, define boundaries, or let a love interest
make a clear but optional advance. If the player/protagonist is submissive or
unlikely to initiate, build invitations and temptation into objective choices and
completion instructions so spicy/romantic content can happen without requiring
the player to chase it.

For each major romantic lead, companion lead, recurring temptation/rival, or
relationship-gated ally, include at least one objective that builds, tests,
defines, or damages that relationship. These objectives can be about boundaries,
refusal, trust, protection, apology, jealousy, vulnerability, privacy, distance,
or desire. Do not make relationship progression only implicit narrator prose
when the relationship affects future play.

For romance-first stories, audit the cast mix. Unless the user asks for a
single-gender cast, include potential love interests and recurring social
characters across men, women, and any requested special gender/anatomy types
such as futanari. Balance does not mean identical counts, but the story should
not feel accidentally limited to one gender.

## Player-Facing Title And Control Rules

The player usually sees the objective title first and may not read the summary.
The title must therefore be a short playable command or clear direction by
itself. The summary should then provide optional help and context for players
who want a hint, not carry the whole objective by itself.

Good title shapes:

- `Reach the Flooded Archive`
- `Recover the Missing Ledger`
- `Question the Harbor Witness`
- `Train With the Companion`
- `Repair the Signal Lantern`
- `Choose the Next Route`

Bad title shapes:

- `Hear the Village Alarm` when hearing it is automatic and the objective should
  instead direct the player to respond.
- `Do Not Force a Fake Ending` because it is creator guidance, not gameplay.
- `Continue the Current Frontier` because it is vague/meta.
- `Choose the Current Frontier`, `Current Frontier`, `Pick the Next Arc`, or
  `Keep Following Canon` because these are story-author process labels, not
  playable in-world objectives.
- `Survive the Companion's Duel Thread` because `thread` is planning language.

Choose `completion_control` by asking what completes the objective:

- Use `"player"` when the player action itself completes the objective:
  leaving, asking, inspecting, buying, travelling, accepting,
  refusing, preparing, training, talking, or starting an attempt.
- Use `"ai"` when the title gives the player a goal but the narrator/world must
  decide the outcome: defeating enemies, surviving a duel, winning an auction,
  resolving a trial, escaping a disaster, or seeing an external event finish.
- Use `"choice"` when the story must force one mutually exclusive player
  decision from a list: choosing a law, ally, route, bargain, faction, romantic
  commitment, moral stance, or ending. Each option belongs in the owner
  objective's `choices[]` array; do not create one top-level objective per
  option.
- Use `"reward_only"` only for hidden infrastructure nodes that immediately
  apply deterministic rewards and route forward when reached. These are useful
  for convergence/transition points in a graph, not for visible player goals.

Do not split every attempt/outcome into two objectives. If `Defeat the Bandits`
is the player-facing goal, one AI-controlled objective is often correct: the
player knows what to try, and the narrator decides whether the attempt succeeds.

If an external event merely sets up the next action, usually fold that event
into the previous objective's `completion_instruction` instead of making it a
separate passive objective. Example: after `Leave the Barn`, the completion
instruction can reveal smoke, screaming, and bandits; the next objective can be
`Defeat the Bandits`.

Never create meta/process objectives such as `Do Not Force a Fake Ending`,
`Keep Following Canon`, `Continue the Story`, `Choose the Current Frontier`,
`Current Frontier`, `Pick the Next Arc`, or `Maintain Source Fidelity`. Convert
those authoring instructions into concrete playable objectives or hidden
runtime constraints.

Visible `title` and `summary` must be written for the player and must not leak
future character names or imply a future character role before that character is
introduced by objective rewards. Avoid objectives like `Meet the Smith`, `Find a
Healer`, `Secure a Captain`, or `Hire a Guide` when a locked future-cast
character fills that role. Name the problem or situation instead, then use
`completion_instruction` plus rewards to introduce the predefined character.

`completion_instruction` is hidden narrator guidance for the specific objective.
Do not paste broad boilerplate into it. Apply spoiler rules while writing it,
but do not store the spoiler rule itself. Good instructions describe the actual
immediate outcome, consequence, reveal, or transition.

Examples:

```json
{
  "title": "Question the Courier",
  "completion_control": "player",
  "completion_criteria": "Return yes only when the player asks the courier what happened, checks the letter, or clearly chooses to investigate the ambush.",
  "completion_instruction": "Have the courier give one urgent lead, keep the ambush's deeper mastermind hidden, and make the next objective a concrete place, person, or clue to pursue."
}
```

```json
{
  "title": "Defeat the Gate Raiders",
  "completion_control": "ai",
  "completion_criteria": "Return yes only when the narrator has resolved the gate fight and the raiders are defeated, routed, captured, or no longer an immediate threat.",
  "completion_instruction": "Resolve the fight according to the player's approach and current allies, show the cost or consequence, and transition to the aftermath objective."
}
```

## Rewards

`rewards` must always be an array. Entries may be normal reward objects or
reward bundle references. A bundle reference may be a string bundle id such as
`"reward-pack-trust-earned"` or an object such as
`{ "type": "apply_reward_bundle", "bundle_id": "reward-pack-trust-earned" }`.
Do not use old reward bucket objects such as `rewards.unlock_locations`,
`rewards.introduce_future_characters`, or `rewards.story_rules`.

Use rewards as the deterministic story-progression layer. Important changes
should not rely only on narrator prose. When an objective changes what is true
about the world, the cast, the map, a relationship gate, a character's body, or
the scene, encode that change in rewards.

Use inline reward objects when the reward is unique to one objective, route, or
choice. Use `state.reward_bundles` when the same exact fixed reward or group of
rewards would otherwise appear in more than one place. Story trees generated by
this skill should have zero repeated reward definitions; repeated effects must
be factored into a named bundle and referenced from each location.

Use a hidden `completion_control: "reward_only"` objective when the graph needs
an explicit convergence or transition node that applies rewards and then moves
to the next objective. Use this for graph structure, shared transition points,
or readable visual-tree layout. Do not use reward-only objectives merely to
avoid repeated reward JSON; use `state.reward_bundles` for fixed deduplication
and `state.reward_templates` when the repeated behavior needs typed character-id
or path parameters.

Reward bundle ids must be stable, descriptive slugs. Good examples:
`reward-pack-rescue-earned-trust`, `reward-pack-failed-city-defense`,
`reward-pack-choose-forest-route`. Avoid vague ids such as `reward-1` or
`shared`.

Useful reward types include:

- `introduce_future_character`
- `make_future_character_recruitable`
- `promote_future_character_to_party`
- `unlock_location`
- `add_item` / `grant_item`
- `add_story_item`
- `adjust_story_inventory`
- `advance_time`
- `complete_generated_job`
- `start_objective`
- `complete_objective`
- `add_story_rule`
- `remove_story_rule`
- `set_state_field`
- `modify_integer`
- `adjust_relationship`
- `add_state_list_item`
- `remove_state_list_item`
- `kill_character`
- `generate_profile_image`
- `generate_solo_normal_image`
- `generate_story_image`
- `apply_reward_bundle`
- `modify_number`
- `apply_reward_template`

Time advancement:

```json
{
  "type": "advance_time",
  "hours": 3,
  "minutes": 30,
  "reason": "traveling through the ravine"
}
```

Use `advance_time` for jobs, travel, training, repairs, research, shopping,
resting, recovery, and chapter transitions. Do not use direct set-time rewards
in normal story content. EmberAdventures owns the actual clock and only story
content should request additive elapsed time.

Future-cast introduction:

```json
{
  "type": "introduce_future_character",
  "character_id": "future-cast-id",
  "scene_presence": "nearby",
  "reason": "Why this character appears now."
}
```

```json
{
  "type": "promote_future_character_to_party",
  "character_id": "future-cast-id"
}
```

Permanent state/body/relationship changes:

```json
{
  "type": "set_state_field",
  "target": "Character Name",
  "field_path": ["appearance", "arms"],
  "value": "left arm intact and strong; right arm rebuilt as a matching synthetic combat arm"
}
```

### Numeric Stats, Precision, And Reference Math

Character definitions may optionally include a `stats` object for authored,
game-specific numeric systems:

```json
"stats": {
  "strength": 7,
  "mana": 12,
  "capacity_cost": 5
}
```

Stat keys are arbitrary stable identifiers chosen by the story. Negative, zero,
and positive values are valid. Do not use numeric strings, null, booleans,
non-finite values, or values outside the safe numeric range. Do not add generic
stats unless the story actually uses them. Full information for a character
present in the scene includes `stats`; reduced context for an absent character
intentionally omits it.

Stats and top-level numeric `story_inventory` fields are integers by default.
When a story genuinely needs decimal values, declare the allowed final storage
precision in `state.numeric_precision`:

```json
"numeric_precision": {
  "story_inventory": {
    "pack_strength": 4,
    "pack_share_percent": 4
  },
  "character_stats": {
    "pack_share": 4,
    "growth_multiplier": 3
  }
}
```

Each map value is the allowed number of decimal places, from 1 through 6. A key
absent from the appropriate map is an integer. Declare only fields that really
need decimals. Authored initial values must already fit their declared
precision. Reusable character-library definitions should keep `stats` integer
valued because decimal precision belongs to the story that uses those stats.

Use `modify_integer` for deterministic integer arithmetic against existing
story state or character fields. It supports exactly `add`, `subtract`,
`multiply`, and integer `divide`. Division truncates toward zero. Rewards run in
listed order, so later rewards see earlier results.

Direct state target with a direct state operand:

```json
{
  "type": "modify_integer",
  "operation": "subtract",
  "field_path": ["story_inventory", "capacity_available"],
  "value_path": ["story_inventory", "capacity_reserved"]
}
```

Direct state target with a character-relative operand:

```json
{
  "type": "modify_integer",
  "operation": "subtract",
  "field_path": ["story_inventory", "capacity_available"],
  "value_character_id": "character-dessa",
  "value_path": ["stats", "capacity_cost"]
}
```

Character-relative target with a direct state operand:

```json
{
  "type": "modify_integer",
  "operation": "add",
  "character_id": "character-dessa",
  "field_path": ["stats", "strength"],
  "value_path": ["story_inventory", "training_bonus"]
}
```

Character-relative target and character-relative operand:

```json
{
  "type": "modify_integer",
  "operation": "add",
  "character_id": "character-dessa",
  "field_path": ["stats", "strength"],
  "value_character_id": "character-mara",
  "value_path": ["stats", "training_bonus"]
}
```

Literal operand:

```json
{
  "type": "modify_integer",
  "operation": "multiply",
  "character_id": "character-dessa",
  "field_path": ["stats", "strength"],
  "value": 2
}
```

`character_id` anchors `field_path` at the live character with that stable
definition id. Without it, `field_path` starts at story state.
`value_character_id` similarly anchors `value_path`; without it, `value_path`
starts at story state. The resolver covers players, party characters, inspected
NPCs, future cast, and story shop/job character containers while preferring the
current live entity when lifecycle mirrors exist.

Every `modify_integer` reward must obey all of these rules:

- Include exactly one of `value` or `value_path`.
- `value_character_id` is valid only with `value_path`.
- `field_path` and `value_path` must be non-empty arrays of non-empty strings.
- Every referenced character id must exist in the story definition.
- Every target and referenced path must already exist when the reward executes.
  Never depend on missing values becoming zero and never use this reward to
  create a path.
- Literal and referenced values, target values, and results are safe integers.
- A literal divide by zero is invalid and must be rejected during story import,
  story-builder validation, and publishing. A referenced divisor that resolves
  to zero produces `Number.MAX_SAFE_INTEGER` and logs a diagnostic warning.
- Overflow and underflow clamp to `Number.MAX_SAFE_INTEGER` and
  `Number.MIN_SAFE_INTEGER`. The runtime checks bounds before arithmetic so an
  unsafe intermediate result is never stored.
- Paths may never contain `__proto__`, `prototype`, or `constructor`.

Use ordinary unique inline rewards for one-off arithmetic. If the exact same
math reward is needed in multiple objectives/routes/choices, put it in one
named reward bundle and reference that bundle. Importing and publishing use the
same authoritative story validator, so do not rely on one path accepting math
that the other rejects.

Use `modify_number` when a reward needs decimals or chained calculations. Its
outer `operation` is still one of `add`, `subtract`, `multiply`, or `divide`.
It accepts exactly one of `value`, `value_path`, or `value_expression`.

```json
{
  "type": "modify_number",
  "operation": "add",
  "field_path": ["story_inventory", "pack_strength"],
  "value_expression": {
    "initial": {
      "character_id": "character-mara",
      "path": ["stats", "strength"]
    },
    "operations": [
      {
        "operation": "multiply",
        "operand": {
          "path": ["story_inventory", "pack_share_percent"]
        }
      }
    ]
  }
}
```

An expression `initial` value and each operation `operand` may be:

- A finite numeric literal.
- `{ "value": 1.25 }`.
- `{ "path": ["story_inventory", "field"] }` for direct state.
- `{ "character_id": "character-id", "path": ["stats", "field"] }`
  for a character-relative value.

Expression operations run in listed order using exact rational arithmetic.
There is no intermediate rounding, including after division. Only the final
assignment is rounded to the destination field's declared precision. Half
values round away from zero. An undeclared destination rounds to an integer.
Final values clamp before storage if their scaled integer would exceed the
JavaScript safe range. A hardcoded zero divisor anywhere in a reward is invalid.
A referenced divisor that resolves to zero clamps the result and records a
diagnostic warning.

Every target and source path must already exist when `modify_number` executes.
`modify_number` never creates missing state. It uses the same safe path rules,
character resolution, and import/publish validation as `modify_integer`.

### Parameterized Reward Templates

Use `state.reward_templates` only when repeated reward behavior needs different
structured character ids or paths. Use `state.reward_bundles` for fixed repeated
rewards. Keep one-off rewards inline. Never duplicate an identical reward in an
objective tree.

```json
"reward_templates": {
  "add-character-pack-share": {
    "parameters": {
      "character_id": { "type": "character_id" },
      "stat_path": { "type": "path" }
    },
    "rewards": [
      {
        "type": "modify_number",
        "operation": "add",
        "field_path": ["story_inventory", "pack_strength"],
        "value_expression": {
          "initial": {
            "character_id": { "parameter": "character_id" },
            "path": { "parameter": "stat_path" }
          },
          "operations": [
            {
              "operation": "multiply",
              "operand": {
                "path": ["story_inventory", "pack_share_percent"]
              }
            }
          ]
        }
      }
    ]
  }
}
```

Invoke it with concrete typed arguments:

```json
{
  "type": "apply_reward_template",
  "template_id": "add-character-pack-share",
  "arguments": {
    "character_id": "character-mara",
    "stat_path": ["stats", "strength"]
  }
}
```

Template parameters support only `character_id` and `path`. A placeholder must
be the entire structured value `{ "parameter": "parameter_name" }`. Never use
string interpolation, partial text replacement, or placeholders inside a path
segment. Every declared argument is required, unknown arguments are invalid,
character ids must exist in the story, paths must pass the normal safe-path
rules, and bundle/template recursion is invalid. Templates may contain normal
inline rewards, bundle references, or other non-recursive template references.

Relationship/stat changes:

```json
{
  "type": "adjust_relationship",
  "target": "Character Name",
  "stats": {
    "trust": 1,
    "affection": 1
  }
}
```

Count relationship rewards during review. If a romance/dark
romance/harem/court/companion story has no `adjust_relationship` rewards, add
them where the story needs persistent trust, attraction, affection, suspicion,
or arousal changes, or document why the relationship is intentionally not
tracked by objective rewards.

```json
{
  "type": "adjust_relationship",
  "target": "all_present",
  "preset": "all",
  "amount": 0.5
}
```

`preset: "all"` changes trust, attraction, and affection. It does not change
arousal. Use `preset: "all_and_arousal"` only when the story beat should also
raise temporary sexual readiness. Valid convenience targets include
`all_present`, `all_party_present`, and `all_npcs_present`.

```json
{
  "type": "set_state_field",
  "target": "Character Name",
  "field_path": ["trust"],
  "value": 3
}
```

Story-rule gates and current constraints:

```json
{
  "type": "add_story_rule",
  "rule_id": "companion-intimacy-locked",
  "text": "The companion cannot willingly begin romance or sexual intimacy until the stated relationship condition is met."
}
```

```json
{
  "type": "remove_story_rule",
  "rule_id": "companion-intimacy-locked"
}
```

Scene/list updates:

```json
{
  "type": "remove_state_list_item",
  "path": ["scene", "npcs_present"],
  "value": "Character Name"
}
```

```json
{
  "type": "add_state_list_item",
  "path": ["scene", "npcs_present"],
  "value": "NPC Name"
}
```

Image triggers for visible changes:

```json
{
  "type": "generate_profile_image",
  "target": "Character Name",
  "reason": "The character's repaired arm changes their upper-body silhouette"
}
```

```json
{
  "type": "generate_solo_normal_image",
  "target": "Character Name",
  "reason": "The character's restored legs are now visible in the scene"
}
```

```json
{
  "type": "generate_story_image",
  "id": "cellar-door-first-look",
  "title": "Cellar Door",
  "prompt": "old rural house utility hallway, heavy cellar door wrapped in chains, one brass key lock and one six-letter combination lock, cold shadow under the door, cinematic horror lighting",
  "negative_prompt": "text, watermark, logo, signature"
}
```

Use `generate_profile_image` only when a change affects face, hair, arms,
torso, chest, shoulders, or the overall silhouette. Use
`generate_solo_normal_image` for major visible changes that should appear in
chat. Leg-only or lower-body-only changes should normally generate a solo
normal image, not a profile image.

Use `generate_story_image` for authored non-character images: story objects,
locations, clues, maps, symbols, ritual scenes, horror reveals, jump scares, or
other one-time visual beats. Keep a stable `id` so EmberAdventures can dedupe and
debug the image. The reward does not need a character target.

Branch consequences:

```json
{
  "type": "add_story_rule",
  "rule_id": "market-sale-moral-cost",
  "text": "The sale branch carries a visible moral cost; the companion was treated as property after refusing."
}
```

For future-character rewards, `character_id` must exactly match an object key in
`state.future_cast.items`, and that future-cast entry's own `id` must be the
same string. Do not use numeric/index keys for future cast and a different slug
inside the entry; the runtime reward lookup uses the object key.

Use `travel_location_id` and `travel_location_name` when completing the objective should move or reveal a location.

Use `exclusive_group` only for mutually exclusive branch-choice objectives where
one selected/completed path should permanently lock the others until the player
rolls back to an older state snapshot. Put the `exclusive_group` on the visible
choice owner objective, and make each branch's later objectives `requires` that
branch's own chosen result so losing-branch descendants stay hidden.
Do not use `exclusive_group` for optional branches, parallel tasks, side content,
or hub goals that can all be completed. Each exclusive branch should carry real
reward differences; a branch that only changes prose is likely to collapse back
into the same play path.

If several routes must all be completed before a larger event, model them as
parallel route chains with a convergence objective that requires all route
terminals. Do not mark those route chains exclusive.

For threshold-gated choices, requirements should be visible player-facing
requirements, not secret alternate objective text. If the option exists, show it
and let the game mark it unavailable until the requirement is met.

Player choice options and AI hidden routes use the same structured requirement
contract, but they resolve differently:

- Direct player choices are visible. Do not hide an option just because its
  requirements are unmet; the UI should show the locked option and its visible
  requirements. Every direct choice objective must include at least one option
  with no requirements so the player is never trapped.
- Hidden AI routes are private. Requirements filter which route ids the
  classifier is allowed to see. Ineligible route ids, criteria, rewards, and
  requirements must not be shown to the player.

For direct forced choices, create one visible owner objective with internal
options:

```json
{
  "id": "choose-first-law",
  "title": "Choose Your First Law",
  "type": "story",
  "status": "hidden",
  "summary": "Choose the first boundary your violet briar magic will defend.",
  "requires": ["reach-first-law-choice"],
  "exclusive_group": "first-law-choice",
  "selectable": true,
  "completion_control": "choice",
  "completion_criteria": "Completed immediately by EmberAdventures when the player selects one option from the choice menu.",
  "completion_instruction": "Resolve only the selected law and show the court reacting to that choice.",
  "rewards": [],
  "choices": [
    {
      "id": "law-freedom",
      "title": "Defend Freedom",
      "summary": "",
      "effects": [],
      "rewards": [
        {
          "type": "add_story_rule",
          "rule_id": "first-law-freedom",
          "text": "The player's first law is freedom: the violet briars resist attempts to take away consent, agency, or choice."
        }
      ]
    },
    {
      "id": "law-vengeance",
      "title": "Answer Theft With Vengeance",
      "summary": "",
      "effects": [],
      "rewards": [
        {
          "type": "add_story_rule",
          "rule_id": "first-law-vengeance",
          "text": "The player's first law is vengeance: the violet briars punish those who take from the player."
        }
      ]
    }
  ]
}
```

Do not create one objective per option. Do not list choices only in summary
text. The owner objective names the decision; `choices[]` contains the options
and their rewards. Keep hidden outcomes in rewards and completion instructions,
not in player-facing `summary` or `effects`.

Use `story_inventory` for objective-owned resources that the AI should not
freely change, such as credits, parts, suspicion, reputation, evidence, or
repair supplies. For numeric resources such as coins, credits, XP, suspicion,
reputation, and parts, use `adjust_story_inventory` with a delta for rewards
and costs so the current value is not accidentally clobbered. When a story
needs percentage-style math, `adjust_story_inventory` may also use
`operation: "multiply"` or `operation: "divide"` with `amount`, or
`operation: "set"` for deliberate exact assignments. Reserve
`set_state_field` for deliberate absolute state assignments, such as setting a
mode, flag, location, body field, or exact story variable. Expose only concrete
visible requirements/effects such as `credits +500`, `credits >= 1200`, or
`Companion Name trust >= 6`.

For conditional hidden routing after an objective completes, use
`next_objectives` on that completed objective instead of a fake choice objective
or a separate branch node:

```json
{
  "id": "resolve-public-rescue",
  "title": "Help Without Being Seen",
  "completion_control": "ai",
  "rewards": [
    {
      "type": "adjust_story_inventory",
      "path": "public_exposure",
      "amount": 2
    },
    {
      "type": "adjust_story_inventory",
      "path": "story_inventory.pack_share",
      "operation": "multiply",
      "amount": 1.05
    }
  ],
  "next_objectives": [
    {
      "objective_id": "agency-opens-a-file",
      "requirements": [
        { "path": "story_inventory.public_exposure", "op": ">=", "value": 5 }
      ]
    },
    {
      "objective_id": "stay-below-the-radar"
    }
  ]
}
```

`requires` remains for objective-id prerequisites. `next_objectives` is for
choosing among already-authored next objectives after this objective completes.
Do not show these branches in a choice menu unless the player is intentionally
choosing between them.

### AI-adjudicated hidden-outcome objectives

Use this objective pattern when the story must branch according to what actually
happened in the scene, but presenting the possible outcomes to the player would
reveal hidden consequences or turn an organic result into an explicit choice.
This is not a fourth `completion_control` value. The objective uses
`completion_control: "ai"` to determine whether its scene is complete, then
`route_control: "ai"` to select exactly one hidden outcome.

The lifecycle is fixed:

1. The AI completion verifier decides whether the objective is complete.
2. If incomplete, it selects no outcome and the objective remains active.
3. If complete, it must select the single route that best matches the full
   scene, recent player behavior, narration, and relevant structured state.
4. The runtime applies the objective's base rewards once, applies the selected
   route's rewards once, records the selected route privately, and activates
   that route's next objective or terminal result.

Author the objective in this shape:

```json
{
  "id": "resolve-mara-treatment",
  "title": "Resolve the Treatment",
  "completion_control": "ai",
  "completion_criteria": "The injury and treatment interaction has reached a clear resolution.",
  "completion_instruction": "Resolve the immediate treatment without describing hidden relationship labels.",
  "route_control": "ai",
  "outcome_routes": [
    {
      "id": "showed-concern",
      "criteria": "The player sincerely noticed or considered the pain Mara experiences while healing them.",
      "requirements": [],
      "rewards": [],
      "next_objective_id": "mara-softens"
    },
    {
      "id": "used-without-consideration",
      "criteria": "The player treated Mara's pain as irrelevant or treated her only as a reusable tool.",
      "requirements": [],
      "rewards": [],
      "next_objective_id": "mara-withdraws"
    },
    {
      "id": "accepted-assistance",
      "criteria": "The player accepted help pragmatically without meaningful concern or cruelty.",
      "requirements": [],
      "rewards": [],
      "next_objective_id": "mara-neutral",
      "fallback": true
    }
  ]
}
```

Use this for ally/neutral/hostile judgments, clean/costly/failed combat results,
concealed/partial/open revelations, recruitment states, and relationship
consequences inferred from natural play.

Route requirements use the same structured requirement contract as visible
choice/shop/job requirements. Use hard requirements only for facts that make a
route truly possible or impossible:

```json
{ "path": "story_inventory.adventurer_rank", "op": ">=", "value": 2 }
{ "type": "story_rule", "id": "mara-is-bound-by-first-law" }
{ "type": "known_fact", "target": "Mara Venn", "id": "mara-trusts-player" }
{ "type": "party_member", "character": "Mara Venn" }
{ "type": "character_alive", "character": "Mara Venn" }
{ "type": "character_dead", "character": "Bandit Captain" }
{ "type": "currency", "id": "coins", "op": ">=", "value": 120 }
```

Rules:

- If the player is knowingly choosing from clearly presented options, use a
  `completion_control: "choice"` objective instead. Hidden routing is for the
  result of play, not for concealing a decision the player should make.
- A completed objective must always produce one outcome. There is no
  valid response that leaves routing undecided. Prevent zero-eligible-route
  designs by giving the fallback route no requirements. EmberAdventures keeps
  the fallback route available as the zero-eligible safety route, so do not put
  meaningful locks on it.
- Route `requirements` are hard filters. Use them only for objective-owned
  state that truly makes a route possible or impossible, such as
  `story_inventory.adventurer_rank >= 2`, a required flag, or a required item.
  Use `criteria` for softer context judgments such as kindness, cruelty,
  deception, romance, caution, or tactical style.
- `criteria` must describe observable differences in behavior or outcome. Do
  not write circular criteria such as `Choose this route when route A applies`.
- Provide exactly one `fallback: true` route. It represents the closest neutral
  or ambiguous result and is used when no more specific criterion is a better
  match or when model output is unusable. It does not prevent a non-fallback
  route from winning whenever that route better fits the scene.
- If the route should be hidden unless every specific route is ineligible, use
  `default: true` or `fallback: true` with
  `default_mode: "only_if_no_other_eligible"`. This is useful for true
  zero-specific-match defaults, not for ordinary ambiguity between eligible
  routes.
- Outcome ids, criteria, requirements, route labels, and unchosen outcomes are
  private. Never expose them in objective titles, summaries, choice menus,
  narration, completion messages, hints, or visible reward descriptions.
- Each route must have a unique stable `id`, a non-empty `criteria`, a `rewards`
  array (empty is valid), and either an existing `next_objective_id` or
  `terminal: true`.
- Do not combine `outcome_routes` with ordinary `next_objectives` on the same
  objective. Do not prefill runtime fields such as `selected_outcome_id`.
- Use `terminal: true` only when that specific route intentionally has no next
  objective. Failure is not automatically terminal; prefer fail-forward routes
  when the story can continue coherently.

## Validation

- `id` values are unique.
- Every `requires` id exists.
- Every `next_objectives[].objective_id` exists. Every conditional entry has
  structured requirements, and any needed default path is last.
- Every AI outcome route has a unique id, private criteria, deterministic reward
  objects, and an existing `next_objective_id` or `terminal: true`. Exactly one
  route is the no-requirements fallback/default. AI-routed objectives do not
  also use `next_objectives`.
- Every future-character reward references `future_cast.items[id]`, where
  `id` is the exact future-cast object key and the entry's own `id`.
- The active opening objective is actionable in the starting scene.
- Hidden objectives do not require facts the player cannot plausibly learn yet.
- Hidden objective titles/summaries do not expose locked future-character names
  or role labels that encourage the narrator to invent substitutes.
- Full story templates include major/fun side content unless the user requested
  a minimal main-spine-only version.
- Branching is used where it improves story flow: optional branches, parallel
  main branches, and multi-prerequisite gates are all valid.
- Optional NSFW/romance objectives remain gated behind adult characters and appropriate story state.
- Read every title alone and ask: would the player know the next intended
  action/direction?
- Check every objective for creator/process language masquerading as gameplay.
- Reject any objective whose `completion_criteria` is only the title repeated
  in a sentence.
- Reject any objective whose `completion_instruction` is only the title repeated
  in a sentence.
- Reject any AI-controlled objective whose criteria says `player completes`.
- Forced branch choices use one `completion_control: "choice"` owner objective
  with a `choices[]` array. Each option has branch-specific rewards or story
  rules that downstream objectives can depend on.
- Relationship-heavy stories report or internally verify `choice` objective
  count and `adjust_relationship` reward count. Zero is a quality failure unless
  the story deliberately does not need that mechanic and the final notes say why.


---

# EmberAdventures Story Definition Field Contract

Use this contract when creating, reviewing, or migrating EmberAdventures story-template JSON. This contract describes the immutable/default parts of the current story-template format. It does not introduce a new reference system. Use the current EmberAdventures story method: player is a player object, party members are keyed by character name in the saved `state.characters` object, NPCs/future cast use the current story-template structures, and scene/runtime lists use names after import.

## Field Purpose Standard

For every field you write, ask these four questions before final export:

1. What is this field for in EmberAdventures?
2. How does EmberAdventures use or display it?
3. Does the value actually accomplish that purpose?
4. Could the value be shorter, clearer, less spoilery, or less like process text?

Do not fill fields because they exist. Empty strings, empty arrays, empty
objects, or `null` are often better than invented filler when the app treats the
field as optional/default state.

## Creator Instructions Are Not Story Data

Instructions from the user to Codex/the story creator must guide construction
but must not be copied into the story definition as story prose, objective text,
world facts, character facts, player guidance, or metadata.

Examples of creator/process instructions that must not appear as story content:

- `source faithful`, `follow canon`, `hide future cast`, `do not spoil`;
- `do not force a fake ending`, `continue at the current frontier`;
- `make objectives player-facing`, `use objective rewards`;
- `current app compatibility`, `story template`, `clean export`;
- `adult-only when settings allow`, `SFW/NSFW policy`;
- `do not introduce future characters unless unlocked`.

Convert those instructions into the correct field behavior instead. For
example, "do not force a fake ending" means the objective chain should continue
with concrete unresolved goals; it does not mean the story should contain an
objective or completion message that says "Do Not Force a Fake Ending."

If a field is player-visible, it must read like story content. If a field is
hidden runtime guidance, it should still be concise and story-specific, not a
verbatim copy of Codex process instructions.

## Top-Level Export Wrapper

- `app`: Must be `"EmberAdventures"`. This identifies the export owner. Do not use a story title, source title, or creator name here.

- `exportType`: Must be `"story-template"`. This tells import that the file is a story template, not a save file, character file, or settings export.

- `storyTemplate`: Object containing the actual template. This is the immutable story package plus starting-state defaults.

- `exportedAt`: ISO timestamp for when the export file was created. This is metadata only. It is not story time.

## storyTemplate Fields

- `id`: Stable story-template id string. Use a lowercase slug based on the
  finished title, represented generically as `"story-title-slug"`. Do not copy
  an id from skill examples, use a database id, random timestamp, or array index.
  Hosted downloads are imported locally; gameplay should not point at a live
  public database.

- `title`: Player-facing story title. Use a real title, not a setup answer,
  development label, or setting flag. Do not copy names from this skill's
  structural examples into a new story. Avoid translating the premise literally
  into an on-the-nose title or revealing the central twist. Prefer a concise
  in-world place, institution, object, phrase, family name, or evocative idea
  that fits the story without summarizing its entire setup.

- `description`: Short player-facing library/UI description of the premise. Keep it concise. Write it as a sales pitch, not an outline: describe the kind of adventure, the starting fantasy/genre appeal, and the immediate premise. Do not include hidden future spoilers, locked cast lists, future objective lists, ending/villain twists, private implementation notes, or objective verifier instructions.

- Keep the genre combination coherent. Use only tags the story genuinely serves,
  and do not bolt together unrelated genres, powers, factions, or cosmic systems
  merely to make the premise sound larger or cover more categories. A focused
  story may use one genre or a small compatible cluster.

- `createdAt`: ISO timestamp for original template creation. Preserve the
  existing value when editing an existing template.

- `updatedAt`: ISO timestamp for the most recent actual template edit. Change it
  only when template content changes.

- `state`: Starting story state object. This contains immutable/default story setup that is copied into a mutable game state when starting a new game.

- `messages`: Array of prewritten opening messages. Include at least the opening narrator message. Opening messages are immutable starting content only: do not store live chat history, post-start messages, or save-game transcript data in a story definition. Opening messages are shown to the player and treated as already represented by the starting state; they are not reprocessed as new state changes.

  Opening messages should contain only clean exported message fields needed to
  start play: `role`, `speaker`, `text`, optionally `nsfwMode`, and optionally
  `at`. Do not author `id` or `entryId`; the normal story exporter does not
  preserve them. Do not include runtime-only fields such as `streaming`, `detail`,
  `stateSyncStatus`, `spicySyncStatus`, `voiceMeta`, `voiceSpeakers`, or
  `objectiveComplete`.

- `settings`: Legacy/import-tolerated starting settings/defaults for local templates only. Clean exported/public story definitions strip `settings`; do not rely on it for immutable story identity. Do not put story state here.

- `source`: Use `"Original"` for original/source-free stories. This is the
  creative source label, not the creator's name, player name, profile name, or
  author alias. Never use `"Player"` as a story source. For source/canon work,
  the Source EmberAdventures Story extension determines the exact source title
  while this base skill continues to own the field's schema.

- `app`: Must be `"EmberAdventures"` inside `storyTemplate` as well.

- `templateType`: Must be `"story"`.

- `creation_tool`: Factual tool/model label used to create or finalize the
  template. Use `"<tool> <model> (<reasoning/intelligence level>)"` when those
  parts are available. Never copy a model label from an example and never leave
  this null. If the current tool/model/intelligence cannot be determined, ask
  before final export.

- `genres`: Array of one or more approved EmberAdventures genre strings. Copy the same approved list into `state.meta.genres` so public library/import validation and runtime prompt projection agree.

  Approved genre tags are: `anime`, `fantasy`, `sci-fi`, `modern`, `historical`, `romance`, `adventure`, `action`, `comedy`, `drama`, `mystery`, `thriller`, `horror`, `dark`, `cozy`, `slice of life`, `superpower`, `isekai`, `school`, `workplace`, `political`, `war`, `crime`, `mythology`, `supernatural`, `post-apocalyptic`, `western`, `cyberpunk`, `steampunk`, `harem`.

- `kink_tags`: Searchable public-library kink/spicy tags. Use only concrete leaf-style phrases that help users find or avoid content, such as `"harem relationships"`, `"slime partners"`, `"magical clothing"`, or `"teasing partners"`. Do not put broad genres here and do not use this as prompt instructions. Keep SFW-safe descriptions free of explicit kink prose; kink tags are metadata for NSFW-capable filtering and adult-appropriate views.

- `nsfw`: Boolean declaring whether the story template itself is unsafe or
  inherently adult in SFW mode because its premise, opening state, required
  objectives, required characters, or required storylines contain NSFW/adult
  content. This is public metadata and must always be explicitly true or false.
  Do not set this true merely because EmberAdventures can switch any story into
  NSFW mode, because optional player behavior could become sexual, because the
  user's preferences allow adult content, or because a SFW story can later be
  converted into a NSFW playthrough. A story that can be played safely in SFW
  mode should use `nsfw: false` even if runtime profile/playthrough settings can
  permit spicy play later. For those stories, omit public-visible adult scene,
  NSFW, and kink-facing prose. SFW means "no inherent NSFW tag," not "NSFW is
  blocked forever."

- `loli`: Boolean declaring whether the story template contains one or more
  embedded character entries marked `loli: true`. This is public metadata and
  must always be explicitly true or false. Do not mark the story loli based on
  source age/school context alone when every embedded character is an
  adult/non-loli variant with `loli: false`.

- `title_card_subjects`: Optional array of 0-5 visible subjects for generated
  story title-card art. Use story-start-visible people, factions, locations,
  objects, or scene motifs. These guide the background/cover subject only; they
  are not extra printed text. Do not include spoilers or future cast that is not
  visible at the start.

- `title_card_image`: Optional default story title-card image slot. This is the active/default image reference for the story card, not story image history. Its clean normal-story shape uses `id`, `title`, `prompt`, `negativePrompt`, `seed`, `model`, `source`, `url`, `hosted_url`, `html`, and `favorite`. It does not use `negative_prompt` or `note`. Public story publishing requires a hosted/default image URL. Local title-card image history is stored outside the story definition and should survive story deletion/reimport. Generated title-card prompts should describe only the background/cover art and must not ask the image generator to print the story title, logo, lettering, typography, subtitles, taglines, author names, captions, menu text, UI text, random letters, or character names as text. EmberAdventures overlays the story title itself. Keep `negativePrompt` blank in normal story templates.

- `default_image_model`: Optional story-level default image style id for normal generated story images and AI-created characters/NPCs created inside games that use this story. Use `""` by default. Supported ids include app image-style preset ids such as `"fantasy-rpg"` for the default cinematic fantasy look and `"polished-animation"` for the newer polished high-budget animated fantasy look. Set this only when the story creator intentionally wants the whole story to default to that image style; otherwise leave it blank so the player's global image style is used. If nonblank, also copy the value to `state.meta.default_image_model`.

- `editor_data`: Optional top-level editor-only metadata. It is not runtime
  story state and is not sent to narrator prompts. The supported story-tree
  shape is `editor_data.story_tree.positions`, an object keyed by objective id
  with `{ "x": number, "y": number }`, and
  `editor_data.story_tree.viewport` with `{ "x": 0, "y": 0, "zoom": 1 }`.
  Use this only to help the manual visual Story Builder open with a readable
  layout. Never store lore, hidden plot, creator notes, objective instructions,
  or AI guidance here. The visual editor derives links from normal objective
  fields: `requires`, `next_objectives`, `choices`, `exclusive_group`, and
  `rewards`.

## state.meta

- `meta`: Story/game metadata. Include only fields the app uses or needs for prompt projection.

- `meta.story_guidance`: Player-specific runtime guidance. Leave blank by
  default. Do not put general story guidance, source policy, canon policy,
  tone guidance, hidden-future rules, objective design instructions, or Codex
  process notes here. Populate this only when the story creator explicitly asks
  to put text in player guidance or explicitly approves text for this exact
  field. If the creator says "make it source faithful," "hide future
  characters," or "do not force a fake ending," treat that as authoring
  guidance, not player guidance.

- `meta.default_image_model`: Mirror the top-level `default_image_model` when
  that story-level image style default is nonblank. Omit it or use `""` when
  the story should inherit the player's global image style.

- `meta.genres`: Array of general story-category tags. Use one or more approved genre tags from the app genre vocabulary. Do not use removed/invalid tags such as `"game"`, `"progression"`, `"survival"`, or `"litRPG"`. Do not use a single `genre` string and do not invent compound values like `"dark romance"`, `"dark fantasy"`, `"cozy adventure"`, or `"mystery thriller"`; combine simple tags instead.

- `meta.kink_tags`: Copy of public `kink_tags` for local story-builder/search use. These are searchable tags, not runtime player preferences.


- `meta.allow_spicy`: Legacy/local draft runtime setting. Clean exported/public story definitions strip `meta.allow_spicy`; do not use it as immutable story identity. Public `nsfw` should only be true when the template cannot honestly be treated as SFW-safe.

- Blocked `meta` fields: do not include `setup_complete`, `is_spicy`,
  `allow_spicy`, `adult_warning_accepted`, `nsfw_has_ever_been_enabled`,
  counters, player counts, upload/publication counts, save ids, warning
  acceptance flags, runtime status, or UI flags. These are live app/UI state,
  not story-template identity.

- `meta.story_source`: Optional object for source/original setup. It may
  identify the source title and approved modifications. Its visible
  `description` should be short source/premise metadata, not a route outline.
  Do not add hidden full-story summaries, route outlines, or old planner fields
  here.

- Do not put user-profile preference arrays in story state metadata. `meta.player_preferences`, `meta.kink_preferences`, `meta.ick_limits`, and genre/entertainment preference lists belong on user profiles or runtime settings only, not in `state.meta` or exported story templates.

## state.location

- `location`: Current starting location summary fields. These are copied into runtime as the initial location state.

- `location.universe`: Source universe or original story universe. Be careful with source titles in ordinary prompts; projection should hide irrelevant source knowledge.

- `location.world`, `continent`, `region`, `settlement_type`, `settlement_name`, `district`, `specific_place`: Starting location labels. Use player-known starting facts. Do not spoil future locations or locked cast.

## state.world_map

- `world_map`: Current map definition and starting map runtime defaults. Use the current app shape with `locations` as an object keyed by location id.

- `world_map.current_location_id`: Location id where the story starts. Must exist in `world_map.locations`.

- `world_map.focus_location_id`: Location id used as the current map focus. Usually same as the current location or its parent area.

- `world_map.travel_history`: Starting travel history array. Usually includes the starting location id or is empty if the app initializes it.

- `world_map.locations`: Object keyed by stable location id. Do not use old `visible_locations`.

- `world_map.locations[id].id`: Stable location id string. Must match the object key.

- `world_map.locations[id].name`: Player-facing location name.

- `world_map.locations[id].type`: Location type such as `"room"`, `"building"`, `"district"`, `"village"`, `"region"`, `"world"`, `"site"`.

- `world_map.locations[id].scale`: Hierarchy scale such as `"room"`, `"site"`, `"building"`, `"district"`, `"settlement"`, `"region"`, `"world"`.

- `world_map.locations[id].parent_id`: Parent location id or `""`/`null` for root.

- `world_map.locations[id].x`, `y`: Optional map coordinates. Use numbers if present.

- `world_map.locations[id].discovered`: Starting discovered boolean. Opening-known locations can be true; future/spoiler locations should usually be false.

- `world_map.locations[id].travel_enabled`: Starting travel-enabled boolean. Do not enable future locations before objectives reveal them unless the story starts with free travel.

- `world_map.locations[id].summary`: Short player-known location summary. Do not mention future cast or future plot events before they are unlocked.

- `world_map.locations[id].detail`: Optional object for extra location detail. Keep it player-known. Do not place hidden future planners, locked future cast, undiscovered source events, objective rewards, or private AI instructions here.

- `world_map.locations[id].connections`: Array of connected location ids. Every id should exist or be intentionally created later by objectives.

- `world_map.locations[id].npcs`: Array of NPC names already known/introduced at the start. Do not put locked future-cast names here. Future placement belongs in `future_cast.items[id].location_hint`, objective rewards, and `completion_instruction`. Public/map views may show these names, so this list must contain only visible, current, named people.

- Do not add location `tags`. The app does not use them and they add clutter.

## state.time

- `time`: Starting in-world time.

- `year`, `month`, `day`, `hour`, `minute`: Integers. Do not use prose dates inside these fields.

## state.scene

- `scene`: Starting scene runtime defaults. This is copied into mutable runtime and should represent the opening moment only.

- `scene.summary`: Current starting scene summary. Keep it concise and aligned with the opening message.

- `scene.intimacy_level`: Starting runtime intimacy number. Use `0` for normal story templates. Only use a nonzero value if the user explicitly requested that the story begin already inside an intimate/spicy scene.

- `scene.spicy_mode`: Starting runtime spicy-scene state, as the current engine string `"off"` or `"on"`. Use `"off"` for normal story templates. Only use `"on"` if the user explicitly requested that the story begin already inside a spicy scene.

  During play, intentional clothing removal starts a spicy scene when it is
  intended to be sexual or progress toward sex. The spicy runtime can remove
  all top clothing, all bottom clothing, all clothing, or exact individual
  structured clothing slots. Broad and individual removal commands are
  mutually exclusive for one participant in one update; never request both.
  Partial removal does not authorize invented slot-specific exposure prose in
  image prompts. Complete bare-top or bare-bottom wording is derived only when
  the corresponding structured clothing group is empty.

- `scene.party_members_present`: Array of known party-member names physically present right now. Do not include the player, `"Player"`, protagonist labels, unknown placeholders, generic groups/titles/jobs, or future cast that is not actually present. Entries must be proper character names backed by actual party-member data.

- `scene.image_characters`: Array of names to include in starting image composition. The opening normal image should usually be a solo player image, so this should normally be `["Player"]` even when NPCs or party members are present. Opening NPCs and party members can receive their own profile/solo images through character-image paths or objective image rewards. Include other names only when the story deliberately needs a group opening image. This is image/UI state and should not be shown to ordinary narrator/state/objective prompts except through image-specific flows.

- `scene.npcs_present`: Array of nearby known non-party NPC names close enough to interact. Do not use as long-term memory. Do not put generic labels such as `"guards"`, `"travelers"`, `"Guild Clerk"`, or `"cart drivers"` here; use proper named NPCs or leave it empty.

- `scene.speak_targets`: Array of names allowed/expected for speech targeting. Usually empty. Every entry must be a proper character name, not a title, job, group, or generic description. This is not an off-scene contact list; every entry must also be physically present in the matching scene list: party members in `scene.party_members_present`, non-party NPCs in `scene.npcs_present`.

- `scene.image_action`: Short visual phrase, usually 2-8 words, no comma and no full sentence.

- `scene.sex_position`, `scene.ai_sex_position`: Empty strings unless starting in a spicy scene. Blank values may exist in stored/exported JSON for schema consistency, but AI prompt projections should omit these keys entirely when blank.

- Do not add a separate scene boolean for player presence. The player is always present during normal play and is represented by `state.player`, not by scene presence lists.

## state.player

`player` is the protagonist/playable character. It uses current story method fields, with immutable/default fields copied from the common character definition where possible.

- `player.name`: Real character name. Do not use `"Player"`, `"Protagonist"`, `"Hero"`, `"Main Character"`, or placeholders.

- `player.age`: Integer age in years. If adult/spicy capable, must be 18 or older.

- `player.gender`: Player character gender/anatomy text.

- `player.role`: Durable player role/archetype.

- `player.personality_description`: Durable player identity. Keep player agency in mind: this is a starting description, not a script for future choices.

- `player.speech_style`: Durable player dialogue style for auto-player narration/speech when applicable. Keep it concise and do not script future choices.

- `player.starting_arousal`: Immutable/default starting arousal value. Usually
  `0`. Do not author active `arousal` in a clean reusable story definition.

- `player.starting_inventory`: Immutable/default starting inventory array. Do
  not author active `inventory` in a clean reusable story definition.

- `player.known_facts`: Legacy/runtime field. Do not include active
  `known_facts` in clean story definitions. Put durable player facts in
  `durable_known_facts`.

- Character-definition-style starting fields such as outfits, starting outfit,
  boldness, starting relationship meters, default image config, and default
  profile image are immutable/default fields. Clean story definitions use the
  current character-definition shape and do not add live runtime-only fields.

## state.players

- `players`: Optional array of full playable character definitions for stories that let the player choose a protagonist before the opening prompt. Omit this field or leave it empty for normal single-protagonist stories.

- When `players` contains more than one entry, the app opens a character-select screen before starting the first playable prompt. The chosen entry is copied into runtime `state.player`, and runtime play must not keep the full `players` array as mutable game state.

- `state.player` must still exist as a fallback/default playable character. For multi-player-select stories, make `state.player` a copy of the first/default option in `players`.

- Every `players[]` entry must use the same immutable/default character
  definition shape as `state.player`: real `name`, integer `age`, `gender`,
  `role`, durable `personality_description`, durable `speech_style`, appearance,
  outfits, `starting_inventory`, `durable_known_facts`, blank image defaults,
  and `voice: null`.

- Do not include `power` while progression is shelved. It is not part of clean
  current story definitions.

- Do not put unselected playable options in `state.characters`, `scene.party_members_present`, `scene.npcs_present`, `npc_directory`, or opening messages as present party members. They are not in the scene unless the story explicitly introduces them later.

- Opening messages for multi-player-select stories should be written so they work for any selected protagonist, or should refer to the selected character generically by role/title. Do not assume the fallback player name unless every option shares that name.

## state.characters

- `characters`: Object keyed by character display name. These are saved party-member/current-companion entries at the start of play. It can be empty. Treat `characters` as the stored JSON schema key; use `party members` in AI-facing text and explanatory guidance.

- Each value must use the immutable/default character-definition shape from
  `EmberAdventures Character`. Use `starting_*` fields and
  `durable_known_facts`; do not author current relationship meters, arousal,
  pose, clothing, inventory, known facts, or image history.

- Do not put opening handlers, registrars, merchants, quest givers, clerks, or future companions here unless they truly start as joined party/current companion characters.

- Do not duplicate the same person in both `characters` and active NPC containers unless the current app explicitly expects it.

## state.npc_directory

- `npc_directory`: Known local NPC directory for NPCs that exist now.

- `npc_directory.locations`: Object keyed by location label/name.

- `npc_directory.locations[location].label`: Player-facing location label.

- `npc_directory.locations[location].characters`: Object keyed by NPC display name.

- Do not use the old flat shape `npc_directory.<npc name>`. Runtime scene
  normalization resolves NPCs from `npc_directory.locations.*.characters`, so a
  flat NPC can be dropped from `scene.npcs_present` even when opening dialogue
  uses that NPC's inline voice tag.

- NPC entry fields such as `name`, `gender`, `age`, `role`, `relationship`,
  `note`, `current_appearance`, `inspected`, `voice`, and `full_character` follow
  the current app shape. Use `role` for job/title/role text.

- NPC death is structured state, never inferred from prose. A dead NPC must use
  exact `status: "dead"` and a non-empty `death_note`. If the player caused the
  death, also set `killed_by_player: true` and set `killed_by` to the exact player
  name; otherwise set `killed_by_player: false`. Do not encode death only in
  `relationship`, `physical_state`, `state_of_mind`, `pose`, `note`, or recent
  change prose.

- `current_appearance` contains only temporary or scene-current visible changes
  to the NPC's base appearance. It must not duplicate base appearance from
  `full_character.appearance` or the compact uninspected description. Leave it
  blank when there is no temporary difference.

- For an uninspected NPC without `full_character`, use `note` for one concise,
  player-visible summary of currently knowable appearance and personality. Do
  not invent a separate shell `appearance` or `personality` field; current NPC
  normalization stores that compact information in `note`.

- Authored NPC `voice` is `null` or omitted. Never infer a TTS/screen-reader
  voice, actor, or character name. Runtime voice assignment belongs to the app.

- Active/current NPC `role`, `relationship`, and `note` must be safe to show to
  the player unless the app explicitly stores them in a private hidden field. Do
  not put future plot facts, hidden allegiances, unrevealed twists, objective
  instructions, or private AI behavior notes in visible NPC fields. For
  uninspected NPCs, keep visible fields especially minimal and describe only what
  the player can currently know.

- `full_character`: Full character definition for inspected/opening important NPCs. Use the current app field names while preserving the immutable/default intent from the character definition contract. Do not make a separate "inspected NPC definition" type.

  Full character payloads must be rich enough for play. Main party members and
  important NPCs usually need multiple concrete durable facts, not one generic
  fact. Facts should cover identity, role, personality under pressure,
  usefulness, relationship dynamics, quirks/preferences, and story-specific
  complications when relevant.

- NPC keys and `name` values must be proper character names. Do not create NPCs
  named by title, job, group, or generic description such as `"Gate Guard"`,
  `"Guild Clerk"`, `"travelers"`, `"novice adventurers"`, `"cart drivers"`, or
  `"shopkeeper"`. For original stories, invent a full first-and-last name when
  an NPC needs to speak or exist in the starting state.

## state.future_cast

- `future_cast`: Important future characters not yet introduced or not yet available. This is the current story method for future character storage.

- `future_cast.enabled`: Boolean.

- `future_cast.items`: Object keyed by future-cast id slug. Do not use
  numeric/index object keys such as `"0"` or `"15"` for future cast unless that
  numeric string is truly the stable character id.

- Supported authored shell fields are `id`, `name`, `status`,
  `canonical_order`, `introduce_as`, `can_die`, `location_hint`,
  `scene_presence`, `role`, `relationship`, `note`, `personality_description`,
  `greeting`, `full_character`, `meet_condition`, `join_condition`, `on_unlock`,
  `unlocked_by`, and `last_triggered_reason`. Shell `profile_images` and `images`
  are legacy/import-tolerated only and should not be authored.

- Do not put `gender`, `age`, `adult`, `nsfw`, or `speech_style` on the
  future-cast shell. Current normalization discards those fields there. Put
  gender, age, NSFW metadata, and speech style in `full_character`.

- The story-wide future-cast check must include omissions. If an important
  planned companion, merchant, authority, antagonist, political/family figure,
  side-arc NPC, or future continuity figure is not included, document why in
  notes outside the final JSON or revise the cast.

- `future_cast.items[id].id`: Same slug as the object key. Use a stable
  lowercase id such as `"character-name"`. Objective rewards use
  `future_cast.items[character_id]`, so object key, entry `id`, and reward
  `character_id` must match exactly.

- `future_cast.items[id].name`: Character display name.

- `future_cast.items[id].canonical_order`: Integer ordering hint for future cast.

- `future_cast.items[id].introduce_as`: Use `"npc"`. Current runtime preserves
  this metadata but does not use `"party_character"` to join the party. Joining
  must happen through `promote_future_character_to_party`.

- `future_cast.items[id].can_die`: Optional boolean mirrored into the introduced
  NPC/full character when the story intentionally controls plot armor.

- `future_cast.items[id].location_hint`: Non-prompt placement hint for where the character is introduced. Do not expose locked future names in visible map `npcs`.

- `future_cast.items[id].scene_presence`: Use `"nearby"` for an introduced NPC.
  Do not use `"active"` as a shortcut for party membership. A character joins
  the party only through `promote_future_character_to_party`.

- `future_cast.items[id].status`: Use `"locked"` in immutable templates unless
  the character intentionally starts introduced. Runtime progression may move
  the entry through `"introduced"`, `"recruitable"`, and `"joined"`. Do not
  pre-author a later runtime status merely because the full payload exists.

- `future_cast.items[id].role`: Short job/title/role text. Avoid leaking this through objective text before unlock.

- `future_cast.items[id].relationship`: Starting relationship text, usually `"not yet met"`.

- `future_cast.items[id].note`: Future setup note. Hide from ordinary narrator prompts until relevant.

- `future_cast.items[id].personality_description`: Durable personality summary.

- Store durable dialogue behavior only in `full_character.speech_style`; the
  future-cast shell does not preserve a separate `speech_style` field.

- Future-cast notes, personality summaries, and full-character facts must not
  contain scheduling/process instructions such as `Should not appear before X`
  or `Introduce only after Y`. Put timing in `requires`, objective rewards,
  `meet_condition`, `join_condition`, or hidden future-cast notes, not in
  character `known_facts`/`durable_known_facts`.

- `future_cast.items[id].profile_images`, `images`: Legacy/import-tolerated image
  history arrays on the future-cast shell. Do not generate them in new clean
  templates. Inside `full_character`, use the canonical blank character image
  fields: blank `default_profile_image`, blank `profile_images`, and blank
  `images`. Generated image history stays local.

- `future_cast.items[id].meet_condition`, `join_condition`: Optional condition text or `null`.

- `future_cast.items[id].on_purchase_objective`: Optional objective id for the
  character's follow-up/purchase story. `purchase_story`,
  `purchase_objective`, and `purchase_story_objective` are accepted authoring
  aliases. When the character is introduced by objective reward or purchased
  from a character shop, EmberAdventures starts this objective and selects it
  unless a locked urgent objective is currently active.

- `future_cast.items[id].on_unlock`: Object controlling introduction behavior.

- `future_cast.items[id].on_unlock.greeting`: Optional narrator guidance used
  only when the character unlocks. The top-level `greeting` is also supported.
  Keep either form concise and scene-flexible. Do not use unsupported
  `ai_greeting` or `greeting_instruction` keys, and do not write boilerplate
  such as `has just been introduced by an objective reward`.

- `future_cast.items[id].on_unlock.image`: Optional image instruction object.

- `future_cast.items[id].unlocked_by`, `last_triggered_reason`: Empty strings in immutable templates; runtime may fill them.

- `future_cast.items[id].greeting`: Short setup/greeting text for unlock.

- `future_cast.items[id].full_character`: Full character data using the complete
  current `EmberAdventures Character` definition shape. This is embedded
  in the story file so hosted/local imports behave the same.

  Full character payloads must be rich enough for play. Main party members
  usually need 6-10 specific durable facts. Major NPCs usually need 4-6. Minor
  one-scene utility NPCs may be shorter, but one generic fact is draft quality.
  Do not include `power`, active `known_facts`, active `clothing`, active
  `inventory`, active `image`, populated profile/image history, or other
  live/runtime fields in `full_character`.

## state.objectives

- `objectives`: Objective state defaults and immutable objective definitions.

- Story structure mode is an authoring decision, not a JSON field. Before
  writing objectives, decide whether the story should be Telltale-style
  branching with direct choices and multiple endings, or simpler
  linear/mostly-linear. Do not write that process decision into story JSON.

- Stored/exported JSON keeps the `objectives` object, but normal narrator prompts should not include an `objectives` object inside the `STATE` JSON. If there is an active objective, show it as a plain text prompt section outside `STATE`. Completed-objective handling should use the dedicated completion/turn directive text, not hidden story-source policy metadata.

- `objectives.active_id`: Id of the active objective at game start, or `""` if no objective starts selected.

- `objectives.no_current`: Boolean indicating no selected/current objective. Usually false when `active_id` is set.

- `objectives.items`: Array of objective objects. Must be an array, not an object keyed by id.

- Objective `id`: Stable slug string.

- Objective `title`: Player-facing objective title. Do not name locked future characters or role spoilers before they are introduced.

- Objective `type`: `"story"` or `"side"`.

- Objective `kind`: Do not author this redundant editor field in clean normal
  story JSON. Use `type: "story"` or `type: "side"`; the visual editor may derive
  its own `kind` value while editing.

- Objective `status`: Starting status such as `"active"`, `"hidden"`, or `"completed"` only for template initial state. Runtime changes this after play.

- Objective `summary`: Player-facing objective text shown in UI. There is no separate `objective` field.

- Objective `rewards`: Array of reward objects or reward bundle references. Current reward examples include future-cast introduction, future-cast promotion to party, shared bundle references, and supported travel/location reveal behavior. Future-character rewards must use `character_id` equal to an existing `future_cast.items` object key. Do not use old reward bucket objects such as `rewards.unlock_locations`, `rewards.introduce_future_characters`, or `rewards.story_rules`; convert each bucket entry into a normal reward object. Do not use XP, level, rank, or progression-skill rewards while the progression system is shelved. Rewards should be hidden from ordinary narrator prompts unless reward handling needs them.

Supported deterministic objective rewards include: `introduce_future_character`, `make_future_character_recruitable`, `promote_future_character_to_party`, `unlock_location`, `add_item`, `grant_item`, `add_story_item`, `adjust_story_inventory`, `advance_time`, `complete_generated_job`, `start_objective`, `complete_objective`, `add_story_rule`, `remove_story_rule`, `set_state_field`, `modify_integer`, `modify_number`, `adjust_relationship`, `add_state_list_item`, `remove_state_list_item`, `kill_character`, `generate_profile_image`, `generate_solo_normal_image`, `generate_story_image`, `apply_reward_bundle`, and `apply_reward_template`. Do not invent reward types. Use `apply_reward_bundle` only as a reference to `state.reward_bundles`; do not put actual rewards inside the reference. Use `apply_reward_template` only as a typed invocation of `state.reward_templates`. Use `adjust_relationship` for objective-owned trust, attraction, affection, or arousal changes; `preset: "all"` means trust/attraction/affection and `preset: "all_and_arousal"` includes arousal. Use `add_story_item` and `adjust_story_inventory` for controlled story-owned resources/items. Use `advance_time` for additive game-clock pressure from travel, jobs, training, repairs, recovery, research, shopping, and chapter transitions. Use `complete_generated_job` only inside generated/story job turn-in objective choices. Use `generate_profile_image` only for changes that affect a character's face, hair, arms, torso, chest, shoulders, or overall silhouette. Use `generate_solo_normal_image` for major visible changes that should appear in chat. Leg-only changes should normally generate a solo normal image, not a profile image. Use `generate_story_image` for authored non-character story images such as important objects, locations, clues, ritual scenes, horror reveals, and jump scares. Its shape is `{ "type": "generate_story_image", "id": "stable-image-id", "title": "Optional Display Title", "prompt": "exact positive image prompt", "negative_prompt": "optional negative prompt" }`; it does not require a target character.

- Objective `requires`: Array of prerequisite objective ids. Use at least one example in templates where appropriate. Do not use step fields.

- Objective `next_objectives`: Optional ordered array on the objective that just
  completed. Use this when completing the current objective should
  automatically choose one next objective based on story state instead of
  showing a player choice menu. Each entry may be a string objective id or an
  object with `objective_id` and optional structured `requirements`. Entries
  are evaluated in order; the first entry whose requirements are met becomes
  the next active/focused objective. Put an unconditional/default entry last
  when the story needs a fallback. `requires` is still for prerequisite
  objective ids; `next_objectives` is only for after-completion routing among
  already-authored objectives.

- Objective `route_control`: `"ai"` only when hidden consequences must be
  classified from natural scene context. Omit or use `""` for normal routing.

- Objective `outcome_routes`: Hidden array used only with
  `route_control: "ai"`. Each route has a unique stable `id`, private
  `criteria`, optional structured `requirements` used as hard eligibility
  filters, deterministic `rewards`, and `next_objective_id`.
  Exactly one route has `fallback: true` or `default: true`, and that route
  must have no requirements. A route may omit its next objective only when it
  declares `terminal: true`. The runtime records
  `selected_outcome_id` privately and applies base plus selected-route rewards
  once. Authors must not prefill runtime selection fields.

- Objective `travel_location_id`, `travel_location_name`: Optional travel target metadata.

- Objective `unlock_mode`: Current app field. Usually `"manual"` unless the story intentionally uses another supported mode.

- Objective `exclusive_group`: String. Use `""` when not needed. Use a stable
  branch id on the visible owner objective for a mutually exclusive choice
  cluster. Do not put each option in the objective list. Later objectives in a
  branch should usually leave this blank and instead `requires` the owner
  objective while using selected-choice story rules/state changes for gating.

- Objective `selectable`: Boolean. Whether the player can manually select this objective.

- Objective `locked_until_complete`: Boolean. In `player_controlled` stories,
  use `true` only for urgent time-sensitive active objectives that must be
  finished before the player can switch to side objectives or clear the current
  objective. In `time_controlled` stories, every main story objective that can
  become active before final aftermath/freeplay should be `time_locked` and
  locked until complete. Timed events may start a locked objective when a
  deadline, attack, collapse, arrest, rescue window, battle for a city, scheduled
  meeting, political session, relationship set-piece, or other authored main
  event arrives.

- Objective `available_now`: Starting availability boolean. Runtime may change it.

- Objective `blocked_reason`: Starting blocked reason string. Use `""` when not blocked.

- Objective `notes`: Array of objective notes. Keep internal/AI notes out of player-facing fields.

- Objective `choices`: Array used only when `completion_control` is `"choice"`.
  Each choice item should have `id`, `title`, `summary`, `rewards`, and
  optional `effects` and `requirements`. These are the options shown in the forced choice UI; they
  are not top-level objectives and should not appear in the normal objective
  list. For major branch choices, use player-facing `summary` only for
  non-spoilery clarification of what the option means in the current scene, and
  keep `effects` empty unless they only show visible requirements, visible
  costs, or story-inventory changes.
  Do not reveal hidden outcomes such as death, failure, sale, romance,
  betrayal, ending, route labels, unlock labels, hidden recommendations, or
  unchosen branch consequences in the choice UI. Bad visible `effects` examples
  include `Bad ending route`, `Hana affection route`, `Unlocks Mira treatment
  route`, `Fail-forward dark route`, and `Best with first law: Truth or
  Freedom`. Good visible `effects` examples include `credits -80`, `trust >=
  6`, `suspicion +1`, and `requires cellar key`.
  Auto mode may complete choice objectives without opening the UI. Unless every
  option is intentionally fatal or ending-only, provide at least one selectable
  continuation option with no requirements that keeps the story moving. Put the safest/neutral
  continuation first, or add `auto_preferred: true` to the preferred auto path.

- Objective `completion_message`: Optional completion message string. Use `""` if not needed.

- Objective `completion_control`: `"player"`, `"ai"`, `"choice"`, or `"reward_only"`. `"player"` means the verifier checks one selected player-action objective after a player-authored turn and can record progress without completing. `"ai"` means EmberAdventures checks after the narrator reply and completes only if the reply actually showed the required outcome. `"choice"` means EmberAdventures presents this objective as a forced choice menu, completes the owner objective immediately when the player selects one option from `choices[]`, and applies that option's rewards without AI verification. `"reward_only"` means the objective is hidden infrastructure: when it becomes available, EmberAdventures immediately completes it, applies its rewards, and advances to `next_objectives` or dependent objectives without asking the player or AI.

Reward-only objective rules:

- Use `completion_control: "reward_only"` only for hidden deterministic transition nodes.
- A reward-only objective must have at least one reward or reward bundle reference.
- A reward-only objective must have `next_objectives`, `outcome_routes`, or at least one dependent objective that requires it.
- Do not make reward-only objectives visible story goals. They are graph tools.
- Do not use reward-only objectives to deduplicate repeated rewards; use `state.reward_bundles` for fixed rewards or `state.reward_templates` for parameterized behavior.

## state.reward_bundles

`state.reward_bundles` is optional. When present, it is a map of stable bundle
ids to arrays of normal rewards or other bundle references:

```json
"reward_bundles": {
  "reward-pack-rescue-earned-trust": [
    {
      "type": "add_story_rule",
      "rule_id": "rescued_lyra",
      "text": "Lyra believes the player risked themself to rescue her."
    },
    {
      "type": "adjust_relationship",
      "target": "Lyra",
      "trust": 2,
      "affection": 1
    }
  ]
}
```

Reference a bundle from an objective, direct choice, hidden outcome route,
timed event, or timeline event:

```json
"rewards": [
  "reward-pack-rescue-earned-trust"
]
```

or:

```json
"rewards": [
  {
    "type": "apply_reward_bundle",
    "bundle_id": "reward-pack-rescue-earned-trust"
  }
]
```

Use bundles when two or more places need the same exact deterministic effect.
Example: if three possible objectives can all prove the player protected a
companion, put the trust/fact rewards in one bundle and reference the bundle
from all three objectives. Do not paste the same `add_story_rule`,
`adjust_relationship`, `set_state_field`, or inventory reward into multiple
tree locations.

Use inline rewards when the effect is unique to one place. If only one route
gives an extra clue, keep that clue inline in that route. If two routes share a
base effect and one has an extra effect, reference the shared bundle plus an
inline extra reward on the route that needs it.

Use reward-only objectives when the objective graph itself needs a shared
transition point, such as several branches converging into one hidden node that
applies rewards and selects the next beat. Reward-only objectives and reward
bundles can be used together, but they solve different problems: bundles remove
duplicate reward definitions; reward-only nodes shape the graph.

  For Telltale-style stories, use `"choice"` owner objectives for direct menu
  choices. The owner objective is the only top-level visible objective; put the
  options in a `choices` array. Later objectives in that branch should require
  the owner objective and rely on the selected option's rewards, story rules,
  relationship changes, or state changes to preserve the chosen path. Failure
  or death choices may use `kill_character` with `ignore_can_die: true` when
  the story objective owns the death outcome. For simpler linear stories, do
  not add fake menu choices.

- `story_inventory`: Optional state object for resources controlled by the
  story/objective system, such as credits, parts, suspicion, reputation,
  evidence, or repair supplies. Use objective rewards with `field_path` values
  under `story_inventory` to change these resources; do not rely on narrator
  prose or the AI to freely edit them. Choice UI may show concrete visible
  resource requirements/effects such as `credits +500` or `credits >= 1200`.

- Objective route integrity: Every non-terminal main objective must have a
  planned route forward through a dependent objective with `requires` or through
  `next_objectives` or `outcome_routes`. A main objective with no dependent route,
  `next_objectives`, or `outcome_routes` must be an explicit terminal ending/death objective with
  deterministic ending rewards. Do not rely on EmberAdventures's fallback objective
  picker as normal story flow.

- `story_shops`: Optional hidden object for story shops and job boards. Keys are
  stable shop ids. Each shop has `id`, `title`, internal `type`
  (`"character"`, `"job"`, `"general"`, or `"clothing"`), display-only `subtype`, optional
  `description`, `unlocked`, `currency`, `location`, optional `owner_npc_id`, and
  `items`. `story_shops` is not sent
  wholesale to normal narrator prompts.

  Character shop items reference `future_cast.items[id]` with `character_id`
  and may include `price`, `purchased`, `locked`, structured `requirements`,
  `unlock_reason`, and `on_purchase_objective`. `purchase_story`,
  `purchase_objective`, and `purchase_story_objective` may be used by authors
  as clearer aliases, but imported data normalizes to `on_purchase_objective`.
  When a purchased or introduced future-cast character has one of these fields,
  EmberAdventures starts that objective and selects it unless a locked urgent
  objective is currently active. Do not duplicate full character definitions in
  shop items. Locked character-shop cards remain visible but show
  only the character name, a generic locked image, and the visible unlock
  requirement/reason; they do not show the real image, details, or price.
  Unmet requirements and insufficient funds keep non-secret character details
  visible. Character shops must define arbitrary non-empty `purchase_verb` and
  `purchase_completed_verb` strings; the first is used for the command and the
  second in completed-action text. The game never infers these words. They may
  also define
  `post_purchase_presence` (`"current_scene"` or `"roster"`).

  General shops use `markup` and optional `buying.enabled`. Their listings own a
  normal `item`; retail price is `ceil(item.value * markup)`, while merchants
  buy eligible inventory at exactly `item.value`. Clothing shops own complete
  outfit listings with explicit positive integer `price` and `outfit`; purchases add the preset
  to one selected owned character without equipping it.

  Job boards use `type: "job"`, `visible_count`, and optionally
  `generic_jobs_enabled: true`. Generated jobs are EmberAdventures-authored engine
  content, not AI-generated story prose. Templates should normally leave
  `story_job_offers`, `story_job_offer_history`, `active_generated_jobs`, and
  `story_generated_npc_pool` empty unless deliberately starting with an active
  generated job.

  Job-board `items[]` are story-authored one-time jobs, not randomized generic
  jobs. Each may include `id`, `title`, `summary`, `genres`, `rank`, `nsfw`,
  `requirements`, `reward_coins`, `reward_xp`, `reward_items`,
  `client_npc_id`, `start_location`, `completion_criteria`, and
  `completion_instruction`. `start_location`, when present, must be an object
  with normal location keys such as `world`, `region`, `settlement_name`,
  `district`, and `specific_place`; do not use a string location id. Do not
  include `on_accept_objective` on story job items; the job-board accept path
  creates its own generated side-objective flow from the job item fields and
  does not start authored objective ids. Do not write completion criteria or
  instructions that depend on a separate linked authored objective chain; if
  the story needs an authored chain, create it as normal objectives outside the
  job board. Write job instructions as playable runtime guidance, such as
  where the job starts, what problem the player must solve, what proof or
  result counts, and how payment is claimed. Do not store schema commentary
  such as `generated from the board`, `linked objective`, or `authored
  objective` in player/runtime job text.
  Every label in a job item's `genres` array must be present in the story's
  public `genres` for that job to appear. Use this for curated story-specific
  contracts with explicit unlock conditions. Generic rotating jobs are
  controlled by `generic_jobs_enabled` and the engine's genre-labeled job pool.

  Structured requirements use objects such as
  `{ "path": "story_inventory.coins", "op": ">=", "value": 120 }`.
  Supported operators are `>=`, `>`, `<=`, `<`, `==`, `!=`, `truthy`, `falsy`,
  `includes`, and `not_includes`. For common story conditions, prefer explicit
  typed requirements instead of fragile path/list checks:
  `{ "type": "story_rule", "id": "rule-id" }`,
  `{ "type": "known_fact", "target": "Character Name", "id": "fact-id" }`,
  `{ "type": "party_member", "character": "Character Name" }`,
  `{ "type": "character_alive", "character": "Character Name" }`,
  `{ "type": "character_dead", "character": "Character Name" }`, and
  `{ "type": "currency", "id": "coins", "op": ">=", "value": 120 }`.
  Use direct path requirements for concrete `story_inventory`, `world_flags`,
  player, character, NPC, or map fields when a typed shortcut does not exist.
  For numeric resource rewards or costs, use `adjust_story_inventory` with a
  positive or negative delta. Do not use `set_state_field` on
  `story_inventory.coins`, `story_inventory.credits`, XP, rank progress,
  reputation, suspicion, or parts unless the story intentionally needs an exact
  absolute assignment.

- Objective `completion_criteria`: Verifier-only criteria. The verifier returns exactly `yes` or `no`.

- Objective `completion_instruction`: Narrator-only instruction used after the verifier completes the objective. Use it to bridge consequences and introduce predefined future-cast characters when appropriate. Do not use it to decide player choices.

  Write this as a direct story instruction for this objective's immediate
  outcome. Do not paste broad boilerplate such as `Show the immediate story
  outcome without introducing future characters...`. Apply hidden-future rules
  while writing the instruction, but do not store the rule itself as the
  instruction. Good: `The player steps outside and sees smoke, fleeing
  villagers, and bandits attacking the road.` Bad: `Show the immediate story
  outcome without introducing future hooks unless rewards unlock them.`

- Objective `auto_completed_from_prereqs`: Boolean. Usually false in immutable templates.

- Forbidden objective fields: Do not use `objective`, `completion`, `steps`, `current_step_id`, `selected_step`, `selected_step_id`, or old step-based fields. The old nested `completion: { type, ... }` shape must be converted into the current flat `completion_control`, `completion_criteria`, and `completion_instruction` fields.

## state.world_flags

- `world_flags`: Concise durable facts about the starting world's tone or
  conditions. Every entry must describe the fictional world itself.

- Never author `world_flags.adult_content_rule`, content-mode policy, user
  preferences, creator/process notes, future-system notes, or future-cast
  scheduling. Put active behavioral constraints in `story_rules`, ordinary
  continuity in `story_memory`, and deterministic unlock timing in objectives
  and `future_cast`.

## state.story_rules

- `story_rules`: Array of durable story-rule objects used as hidden progression constraints. Each rule is `{ "id": "stable-rule-id", "text": "Current rule text." }`.
- Story rules are sent to most narrator/state/image-related AI prompts as text under STORY_RULES. They are not sent to the auto-player prompt.
- Use story rules for current hard constraints that must guide AI behavior, such as locked romance gates, hidden danger rules, repaired body state constraints, or source/story-specific world rules.
- Do not use `story_rules` as a generic notes dump. If a fact is ordinary lore, put it in `story_memory`; if it is a deterministic unlock/change, put it in objective rewards.
- Do not use `story_flags`. There is no current story flag system.

## state.story_memory

- `story_memory`: Memory buckets the app expects.

- `world_notes`: Durable notes that are genuinely useful and not better expressed as objectives/future cast.

- `unresolved_threads`: Starting unresolved threads. Usually empty.

- `relationship_notes`: Starting relationship notes. Usually empty.

- `rules_and_constraints`: Hard rules only. Avoid broad story planners.

- Story memory is for compact runtime continuity, not story-creation process.
  Do not write notes like `Use objectives as the only story progression system`
  unless the app literally needs that as hidden runtime guidance. Prefer
  concrete continuity facts and constraints.

- `ai_private_notes`: Private AI notes only when needed; hide from
  player-facing UI and ordinary irrelevant prompts. Use concise in-world
  continuity constraints, not story-creation process notes, coverage-table
  reports, omission reports, audit notes, or instructions such as avoiding a
  fake ending.

## state.story_clock, state.story_pacing, and state.timed_events

- `story_clock`: Additive runtime game clock. Immutable story templates should
  start with `{ "elapsed_minutes": 0, "label": "Day 1, 8:00 AM" }` unless the
  premise needs a different visible starting label. Story content should advance
  the clock with `advance_time` rewards, not by directly setting absolute time.

- `story_pacing`: Main-story pacing contract. Use this only when the story's
  main path is intended to be controlled by an authored timeline instead of
  entirely by player-selected objectives.

- `story_pacing.mode`:
  - `"player_controlled"`: creator-facing name Player-Paced Story. Main story
    objectives are available, selected, and completed through ordinary
    objective flow. Do not schedule main story milestones with time.
  - `"time_controlled"`: creator-facing name Time-Controlled Story. The main
    story has authored events that begin at story-clock times or after
    prerequisite objectives. The recommended form includes intentional downtime
    between main events so the player may spend time on side objectives, shops,
    jobs, travel, and exploration, then use the timeline prompt to wait for the
    next main event. In this mode, main story objectives are time-controlled
    commitments, not ordinary swappable guidance.

- Strict Time-Controlled Story is not a separate `story_pacing.mode`; implement
  it with `"time_controlled"` plus back-to-back timeline events and
  time-locked objectives where side objectives/jobs are unavailable until the
  urgent sequence ends. Use it sparingly for scenes that should feel
  intentionally restrictive.

- `story_pacing.timeline`: Object keyed by stable event id. Timeline entries
  are for main-story events that should happen at a meaningful time. They are
  not generic background timers.

- Timeline event fields:
  - `id`: stable event id matching the object key.
  - `title`: short event title shown in timeline prompts.
  - `status`: usually `"waiting"` at template start. Runtime may use
    `"ready"`, `"active"`, `"complete"`, `"missed"`, or `"declined"`.
  - `objective_id`: objective started by this event.
  - `trigger`: object with either `at_elapsed_minutes` for an absolute
    story-clock minute, or `objective_id` for "after this objective completes".
    A trigger may include both.
  - `prompt`: player-facing decision text when the event is ready. Include
    `message`, `accept_label`, and `decline_label`.
  - `accept`: usually `{ "objective_id": "<objective id>" }`. May also include
    normal deterministic `rewards` and `travel_to_location_id`.
  - `decline`: optional `message` and deterministic `rewards` if the player
    intentionally skips the event.
  - `missed_due_to_conflict`: optional `message` and deterministic `rewards`
    when this event starts while another time-locked objective is active.
  - `auto_start`: use sparingly. If true, the event starts as soon as the
    trigger is met instead of waiting for the player prompt.

- In `time_controlled` stories, every main story objective that can become
  active before the final aftermath/freeplay phase should use
  `"objective_mode": "time_locked"` and `"locked_until_complete": true`.
  A time-locked objective cannot be deselected or replaced by side content until
  it completes.

- Free time belongs between locked main objectives, not inside them. Create
  downtime by spacing timeline triggers, using objective-triggered future
  events, or prompting the player to wait for the next scheduled event. During
  those gaps, side objectives, shops, jobs, travel, and exploration can remain
  selectable.

- Do not leave a main story objective unlocked in a `time_controlled` story
  merely because the player has time before it begins. If the story is waiting
  for that beat, schedule it later and let the player spend the gap freely.

- The only normal exception is the end of a time-controlled story: after the
  final fight, final conflict, or last scheduled event, remaining aftermath,
  epilogue, romance wrap-up, freeplay, or player-paced cleanup may use ordinary
  unlocked objectives.

- If a locked main objective immediately starts another main-story crisis,
  meeting, battle, negotiation, or relationship set-piece, the follow-up main
  objective should also be time-locked unless it is deliberately part of the
  final player-paced aftermath.

- Use downtime between timeline events intentionally. If a later main event is
  scheduled in the future, EmberAdventures can ask whether the player wants to
  wait for it, with the tradeoff that the skipped time could have been spent on
  side objectives, shops, jobs, travel, or exploration.

- If two important timeline events are intentionally mutually exclusive, schedule
  them close enough that the first time-locked event can cause the second to be
  missed. Author `missed_due_to_conflict` consequences so the world changes
  coherently instead of silently ignoring the missed event.

- Use `time_controlled` pacing when the story benefits from pressure, downtime,
  and scheduled set-piece events. Prefer Time-Controlled Story with deliberate
  gaps over Strict Time-Controlled Story for most guided stories. If the player
  should decide when to pursue the main plot, keep the story
  `player_controlled`.

- Example:

```json
"story_pacing": {
  "mode": "time_controlled",
  "pending_event_id": "",
  "timeline": {
    "briar-moon-invasion": {
      "id": "briar-moon-invasion",
      "title": "Briar Moon invasion",
      "status": "waiting",
      "objective_id": "defend-briar-moon",
      "trigger": { "at_elapsed_minutes": 4320 },
      "prompt": {
        "message": "The Briar Moon invasion begins tonight. Wait for the attack and take part?",
        "accept_label": "Defend the city",
        "decline_label": "Do not go"
      },
      "accept": {
        "objective_id": "defend-briar-moon",
        "travel_to_location_id": "loc-briar-moon"
      },
      "decline": {
        "message": "You stay away. By dawn, the city has changed without you.",
        "rewards": [
          {
            "type": "add_story_rule",
            "rule_id": "briar_moon_not_defended",
            "text": "The player declined to take part in the Briar Moon invasion."
          }
        ]
      },
      "missed_due_to_conflict": {
        "message": "The Briar Moon invasion happened while another urgent event held you elsewhere.",
        "rewards": [
          {
            "type": "add_story_rule",
            "rule_id": "briar_moon_fell_unopposed",
            "text": "The Briar Moon invasion was missed because the player was locked into another urgent event."
          }
        ]
      }
    }
  }
}
```

- `timed_events`: Object keyed by stable event id. Use timed events when the
  story needs background consequences, private deadlines, warnings, or world
  changes that are not the main objective spine. Good uses include injuries
  that worsen after a window, enemies advancing in the background, missed
  meetings, shops/jobs rotating after time, rescue deadlines, rival plans, and
  world events that become visible if the player ignores them.

- Timed event fields:
  - `id`: stable event id matching the object key.
  - `title`: short private/authoring title.
  - `status`: usually `"waiting"` at template start. Runtime may use
    `"active"`, `"complete"`, or `"cancelled"`.
  - `visibility`: `"hidden"`, `"vague"`, or `"visible"`. Use `"hidden"` for
    private timers, `"vague"` for pressure the player should sense without exact
    mechanics, and `"visible"` for explicit deadlines.
  - `trigger`: object with `objective_id` or `immediately: true`. The timer
    starts when the trigger is met.
  - `time_limit`: object such as `{ "hours": 24 }` or
    `{ "days": 2, "hours": 6 }`.
  - `cancel_objective_id`: optional objective id that cancels the event if
    completed before the deadline.
  - `message`: optional player-visible game message when the deadline fires.
  - `stages`: optional warning/escalation array. Each stage has `id`, `after`,
    optional `visibility`, optional `message`, and optional `rewards`.
  - `rewards`: normal deterministic reward objects applied when the deadline
    fires.

- Do not use `timed_events` as the main-story scheduling system. Use
  `story_pacing.timeline` for scheduled main-story events and use
  `timed_events` for background consequences.

Example:

```json
"timed_events": {
  "litia-power-failure": {
    "id": "litia-power-failure",
    "title": "Litia power failure",
    "status": "waiting",
    "visibility": "vague",
    "trigger": { "objective_id": "find-litia" },
    "time_limit": { "hours": 24 },
    "cancel_objective_id": "repair-litia-core",
    "message": "Litia's damaged core has failed. The chance to save her has passed.",
    "stages": [
      {
        "id": "power-warning",
        "after": { "hours": 12 },
        "visibility": "vague",
        "message": "Litia's power is fading faster than expected."
      }
    ],
    "rewards": [
      {
        "type": "kill_character",
        "target": "Litia",
        "ignore_can_die": true
      },
      {
        "type": "add_story_rule",
        "rule_id": "litia-dead-from-delay",
        "text": "Litia died because her major damage was not repaired in time."
      }
    ]
  }
}
```

## Runtime Temporary Speaker State

- Do not include temporary speaker state in exported story templates. It is
  mutable runtime state only. If someone can speak in the opening/starting
  scene, create a real named NPC entry in `npc_directory` and reference that
  proper name from scene arrays/opening voice tags.

## state.recent_changes

- `recent_changes`: Must be an empty array for exported story templates. New game files should not start with stale change logs.

## Opening Messages

- Opening messages array should contain at least one assistant narrator message.

- Opening messages are not save messages. They must contain only the immutable starting narrator/setup messages needed before live play begins.

- If prewritten opening dialogue comes from a known opening character/NPC, put a hidden voice tag immediately before each quoted spoken line using `(Full Name) "spoken words"`. Do not include gender in the tag. The tag must be a real predefined character's proper name, not a title/job/group/generic description such as `(Gate Guard)` or `(Guild Clerk)`.

- Use plain ASCII quotes for spoken dialogue. Curly quotes can break tag stripping/voice assignment.

- The opening should start playable action immediately and end with a concrete action the player can take.

## AI Visibility Rule

The story template may store future cast, future objective instructions, rewards,
hidden locations, hidden original-story knowledge, and default image metadata.
Normal gameplay AI must not receive the raw full template. Build task-specific
projections so the narrator sees only current runtime state, known current
characters/NPCs, visible/current location, and the active objective projection.
Future-cast `full_character` data is hidden until an objective reward or current
context makes that character relevant.
Outcome route ids, criteria, requirements, unchosen routes, and selected route
metadata are private process data. They must never appear in objective banners,
completion messages, narration, choice menus, or player-visible effects.

## Player-Visible Field Rule

Before final export, audit every field that can appear in a library card,
story-definition UI, map, objective list, opening message, character card, or
read-only definition view. Player-visible fields must not reveal hidden future
cast, future party roles, future locations, unrevealed twists, objective rewards,
private AI instructions, locked relationship outcomes, or implementation notes.

At minimum, audit `storyTemplate.title`, `storyTemplate.description`, public metadata, `messages[]`, `state.location`, `world_map.locations[*].name`, `summary`, `detail`, `npcs`, `scene.summary`, objective `title` and `summary`, current NPC `role`, `relationship`, `note`, and any embedded character fields that the library/editor can display.

Public-library cards may show counts and tags, but not hidden future-cast names, hidden objective titles, future location names, or locked side-arc spoilers.

## Public Hosting Metadata

Public hosted stories need enough metadata for Supabase/library search before upload:

- required base metadata: `source`, `creation_tool`, approved `genres`, `nsfw`, and `loli`
- required default image: a real hosted/default `title_card_image.url`; never
  fabricate a URL when no hosted image exists
- derived library counts: player-select boolean/count, main objective count, side
  objective count, future character count, starting party member count, and
  starting NPC count

The application derives those counts from the story during publishing. Do not
author them as extra `storyTemplate` fields. In the public-library record the
current field is `starting_party_member_count`, not
`starting_character_count`. Public story definitions must not include
player-specific `last_played`, live save data, or local-only image ids.

## Story Image Rules

- `title_card_image` stores the active/default story image reference only.
- Story title-card image history is local data outside the story definition.
- Deleting a story definition must not delete local story images; reimporting the same story should be able to reuse existing local title-card images.
- Public story publishing requires a default hosted title-card image.
- `title_card_image.prompt` must describe only the cover/background image. Do
  not ask the image generator for title text, readable text, exact title text,
  logos, typography, subtitles, captions, UI text, or character-name lettering.
  EmberAdventures overlays the story title itself. Keep
  `title_card_image.negativePrompt` blank; the current normal exporter clears it.
- Authored `generate_story_image` objective rewards may
  include `negative_prompt` when it helps prevent wrong objects, extra people,
  text, logos, or unsafe content.


---

# Story Quality Checklist

Use this before finalizing a story template.

## Playability

- Opening message creates an immediate situation.
- First objective can be acted on immediately.
- The first scene does not explain the entire plot.
- The player has a clear place, body/identity, inventory, and immediate conflict.
- The player can understand what is happening in the first 30 seconds.
- The opening establishes pressure and context without deciding the player's
  meaningful choices for them. Do not make the player agree, submit, attack,
  flirt, forgive, accept a role, or commit to a path before the user acts.
- The first objective matches the opening's final actionable prompt.
- The story hides future spoilers without making the opening confusing.
- Long stories include enough hidden objective detail to keep play advancing
  after the first scene.

## Creative Direction

- The story's core player fantasy is identifiable in one sentence.
- The intended emotional target is clear: danger, desire, power,
  vulnerability, discovery, belonging, guilt, temptation, triumph, dread, or
  another deliberate feeling.
- The world hook makes the premise more specific than a generic genre setup.
- The main relationship focus is clear when the story depends on romance,
  companions, rivals, court intrigue, harem, or NSFW payoff.
- The progression/building axis is clear when the premise supports it: party,
  home, workshop, guild, kingdom, reputation, resources, family, body repair,
  power growth, or another concrete axis.
- Serious stories have a compact outline before objective writing: premise,
  player fantasy, emotional targets, world hook, beginning, midpoint or
  reevaluation moment, climax, ending/postgame shape, relationship arcs, and
  structure mode.
- If several substantially different games could be built from the user's
  prompt, the skill asked clarifying story-juice questions or proposed
  directions before final JSON.
- The skill did not keep asking questions after the core playable story was
  clear. It either offered to complete the story or proceeded when the creator
  delegated unresolved details.
- The story template acts as the director. Objectives, rewards, story rules,
  state changes, choices, and routing enforce anticipation/payoff instead of
  leaving the live AI to invent the whole arc.

## Full-Story Structure

- Major milestones cover beginning, middle, and current/end frontier.
- The story structure mode was chosen intentionally: Telltale-style branching
  for choice-heavy/multiple-ending stories, or linear/mostly-linear for focused
  stories where fake menu choices would hurt pacing.
- Objectives map cleanly to milestones.
- Every objective has story-specific `completion_criteria`; none use generic
  title-repeat boilerplate such as `Return yes only when the player completes:
  {title}`, `Return yes only when the player completes or survives...`, or
  `Return yes only when the player clearly takes action toward this goal...`.
- Every objective has story-specific `completion_instruction`; none use generic
  title-repeat boilerplate such as `Resolve the immediate outcome of {title}
  and move to the next objective`.
- Every objective with a `summary` field has a non-empty, story-specific,
  player-facing hint or context note that helps the player understand how to
  approach the objective without spoiling hidden outcomes.
- In `time_controlled` stories, every main story objective before final
  aftermath/freeplay is time-locked and locked until complete. Free time is
  represented as gaps between locked main objectives, not as unlocked main
  story objectives.
- AI-controlled objectives describe the resolved narrator/world state in
  `completion_criteria` and never say `player completes`.
- The template is not only a bare critical path unless the user explicitly
  requested that. It includes major/fun side stories, optional chains, or
  memorable one-off side objectives that fit the source/premise.
- Branching is used where it improves play: one unlock can open several paths,
  optional side objectives can branch from hubs/milestones, and multiple
  branches can be required before a later major milestone.
- Every non-terminal main objective has an authored route forward through a
  dependent objective, `next_objectives`, or hidden `outcome_routes`. Any main objective with no route is
  an explicit terminal ending/death objective with deterministic ending rewards.
  The story does not rely on fallback objective picking as normal flow.
- Telltale-style stories include direct `completion_control: "choice"` owner
  objectives with `choices[]`, non-spoilery option titles, branch-specific
  rewards, hidden outcome logic, and distinct endings/failure paths when
  appropriate.
- Choice option `effects` contain only visible requirements or concrete
  mechanical deltas such as `credits -80`, `trust >= 6`, or `suspicion +1`.
  They do not expose route labels, ending labels, unlock labels, hidden
  recommendations, or outcome spoilers.
- Choice-heavy stories, including multiple-ending or Telltale-style requests,
  usually target about 30-40% choice objectives and normally stay under half.
- Linear/mostly-linear stories do not use forced choice menus unless the choice
  materially changes the story.
- Character introductions happen through objective rewards.
- Important permanent changes happen through deterministic objective rewards,
  not only through narrator prose.
- Truly mutually exclusive branches have branch-specific rewards,
  `exclusive_group` on the visible choice owner objective, and branch
  descendants gated with `requires`; they do not collapse back into the same
  state.
- Optional branches, parallel goals, and side content that can all be completed
  do not use `exclusive_group`.
- Immediate-merge choices record consequences in rewards before returning to a
  shared next objective.
- Optional-with-skip choices are used for optional romance/NSFW moments inside
  the main flow when separate side objectives are not desired.
- Multi-route convergence uses separate branches that all must be completed
  before the merge objective, not `exclusive_group`.
- Fail-forward branches continue play with consequences instead of accidental
  dead-ends.
- Delayed callback choices store explicit rules/state/rewards that later
  objectives or endings can check.
- Repeated deterministic effects are factored into `state.reward_bundles` or typed `state.reward_templates` instead of duplicated.
  There are zero repeated reward definitions across the objective tree. Inline
  rewards are used only for effects unique to one objective, route, choice, or
  event.
- Hidden `completion_control: "reward_only"` nodes are used only when the graph
  needs an explicit shared transition/convergence point. They have rewards,
  have a valid route forward, and are not used as visible player objectives.
- Relationship-threshold choices show locked options and visible requirements;
  options are not hidden or rewritten based on secret thresholds.
- Resource-gated routes show visible requirements for resources, reputation, or
  relationship stats before the route can start.
- Side objectives usually have useful consequences such as items, story rules,
  relationship/stat changes, location unlocks, hidden leads, image triggers, or
  scene/list changes.
- Major NPCs have their own goals, fears, loyalties, problems, or plans where
  the story depends on them feeling alive.
- The world has offscreen motion when the premise benefits from it: rivals,
  deadlines, jobs, shops, opportunities, threats, or consequences can advance
  without waiting for the player.
- Intentional failure, rejection, death, missed opportunities, arriving too
  late, or worse outcomes are represented when they would strengthen the story,
  especially in Telltale-style structures.
- Relationship, romance, court, mystery, and slow-burn stories include bridge
  objectives between major beats instead of jumping from chapter event to
  chapter event.
- Romance, dark romance, romantasy, harem, and relationship-first stories
  include multiple relationship-building objectives between major plot
  milestones, not only one token conversation.
- NSFW stories build context, anticipation, invitation, consent/refusal,
  ambiance, escalation, and aftermath around sexual scenes unless the user
  explicitly requested an immediate-sex premise.
- If the intended player is submissive, shy, or unlikely to initiate, romantic
  leads have objective/completion-instruction support to flirt, invite, tempt,
  court, or come onto the player while preserving explicit choice.
- Romance-first casts include a deliberate gender/anatomy mix unless the user
  requested a narrow cast.
- No objective chain expects one player message to complete multiple
  consecutive objectives; EmberAdventures checks one selected objective at a time.
- Relationship progress that should be deterministic uses `adjust_relationship`
  rewards instead of relying only on narrator prose.
- Romance, dark romance, harem, court, companion, and relationship-driven
  stories have a counted relationship-mechanics pass: direct choice objective
  count, `adjust_relationship` reward count, and relationship bridge objective
  coverage for each major relationship lead. A zero count must be fixed or
  justified as a deliberate design exception.
- `story_rules` are used for active runtime constraints when the story needs
  hard gates such as locked intimacy, pursuit, repair boundaries, source/world
  rules, body-state restrictions, or temporary danger. They are not used as a
  lore dump.
- Future locations are present in map state when needed.
- Story memory gives durable guidance without bloating the prompt.
- `story_memory.ai_private_notes` contains only concise in-world continuity
  constraints if needed; it does not contain coverage tables, omission reports,
  self-critiques, audit notes, or story-creation instructions.
- Objective content has variety where the premise supports it: travel,
  conversation, investigation, combat, shopping, training, downtime, social or
  relationship scenes, discovery, problem solving, and character moments.
- Side objectives are memorable or useful, not just filler errands.

## Feature Utilization

For every serious story, explicitly consider these features before finalizing:

- `state.players` for real player select when the story does not require one
  locked protagonist.
- `future_cast` for important people who should exist before they are met.
- `world_map.locations` with hidden/unlocked future locations.
- `story_rules` for current runtime laws and gates.
- `exclusive_group` for true mutually exclusive branch choices only.
- `completion_control: "choice"` for direct menu decisions in Telltale-style or
  otherwise choice-driven stories.
- `set_state_field` for permanent character/world/relationship/body changes.
- `adjust_relationship` for trust, attraction, affection, and carefully chosen
  arousal changes from objective rewards.
- For relationship-driven stories, `adjust_relationship` is expected whenever
  trust, attraction, affection, suspicion, rivalry, or arousal should persist
  beyond one scene. Do not leave major relationship growth only in prose.
- `add_story_rule` and `remove_story_rule` for changing hard constraints.
- `story_inventory` for story-owned resources such as credits, parts,
  suspicion, reputation, evidence, or repair supplies that objective rewards
  control instead of the AI freely changing.
- `state.reward_bundles` or typed `state.reward_templates` for shared deterministic rewards that would otherwise
  be repeated in more than one branch, route, choice, or event.
- `completion_control: "reward_only"` for hidden graph transition nodes that
  apply rewards and advance immediately when reached.
- `add_state_list_item` and `remove_state_list_item` for scene/list changes.
- `kill_character` for deterministic death outcomes, with `can_die` respected
  unless an objective intentionally overrides it.
- `generate_profile_image` for face/hair/arms/torso/chest/shoulder/silhouette
  changes.
- `generate_solo_normal_image` for major visible scene/body/outfit changes.
- `generate_story_image` for authored non-character visual beats such as
  important objects, locations, clues, symbols, horror reveals, or jump scares.

If a feature is omitted, the omission should be because it does not serve the
story, not because the skill forgot the feature exists.

## Character Integration

- Invented characters come from `EmberAdventures Character`. If canon
  characters are required, keep this base story skill active and also load
  `Source EmberAdventures Story` plus `Source EmberAdventures Character`.
- Future cast entries have full payloads when they will become active later.
- Embedded player, party, NPC, and future-cast definitions are built to support
  play. Durable facts include how the character affects objectives, what they
  can do in scenes, what relationship tensions matter, and what future rewards
  or gates may change about them.
- Character relationships and personalities remain consistent with the
  original premise unless the user requests changes.
- Clothing slots are precise item slots, not ambiguous scene-dependent descriptions.
- Player-character definitions describe starting identity/tendencies without
  scripting future choices, consent, morality, dialogue, or relationship paths.
- Public/standalone character definitions do not expose story-specific spoilers
  unless the entry is intentionally spoiler-heavy and safe to publish that way.

## Player-Visible Field Audit

Before final export, scan every field the player may see in a library card,
story-definition UI, map, objective list, opening chat, character card, or
read-only definition view.

Visible fields must not reveal hidden future cast, future party roles, future
locations, source twists, objective rewards, private AI instructions, locked
relationship outcomes, or implementation notes.

Audit these fields at minimum:

- story title and description;
- public source/genre/kink/SFW/NSFW metadata;
- opening messages;
- location and world-map names, summaries, details, and NPC lists;
- scene summary;
- objective titles and summaries;
- current NPC names, roles, relationships, and notes;
- character roles, personality descriptions, appearance, outfits, and durable
  known facts whenever they can appear in library/editor UIs.

Public-library cards may show counts and tags, but not hidden future-cast names,
hidden objective titles, future location names, or locked side-arc spoilers.

SFW-safe browsing text should not include explicit kink prose. Kink tags are
metadata for NSFW-capable filtering and should only surface in adult-appropriate
contexts.

## Creator-Instruction Leakage Audit

Before final export, search the story text for creator/process language that was
intended for Codex, not for the story file. Remove or rewrite it.

Do not leave terms like these in player-visible fields, story memory, world
flags, objective titles/summaries, character facts, or completion messages:

- `source-faithful`, `current app compatibility`, `story template`;
- `fake ending`, `current frontier`, `follow canon`, `hide spoilers`;
- `future hooks`, `objective rewards`, `without introducing future characters`;
- `should not appear before`, `has just been introduced by an objective reward`;
- `future engine`, `future shop`, `future quest`, `should later`,
  `convert these`, `until those systems exist`;
- `linked objective`, `authored objective`, `objective chain` when used as
  schema/process commentary instead of natural story wording;
- any explanation of how EmberAdventures objectives, publishing, SFW/NSFW policy, or
  prompt projection works.

If the concept is still needed, put it into the correct behavior:

- hidden future cast/objectives for spoilers;
- concise hidden runtime constraints for continuity;
- concrete player-facing objective titles for goals;
- blank/default fields when no story content belongs there.

For every field that feels questionable, ask: what is this field for, how is it
used by EmberAdventures, does this value serve that use, and could it be improved?

`story_guidance` / player guidance must be blank unless the creator explicitly
asks to populate that exact field or approves exact text for it.

## Originality And Hidden-Information Pass

- For source-free work, confirm the result remains source-free. If it has
  drifted into a recognizable adaptation, pause original-story work and load
  `Source EmberAdventures Story` before continuing under an explicit source
  scope.
- Visible text contains only what the protagonist/player could know at the
  starting point.
- Future names appear only in hidden future cast, hidden objectives, or rewards
  until introduced.
- Visible objectives do not leak locked future role labels.
- Map summaries do not reveal undiscovered enemies, places, allies, twists, or
  future relationships.

## Schema

- JSON parses.
- `future_cast.items` is an object.
- Every `future_cast.items` object key matches that entry's own `id`; do not
  use numeric/index keys for future cast.
- `world_map.locations` is an object.
- `scene.speak_targets` exists.
- Objective references resolve.
- No authored objectives, story rules, memory entries, scene participants,
  choices, rewards, map references, or other story content were silently
  truncated to satisfy an arbitrary count limit. If the target application
  cannot retain the complete authored data, report the incompatibility instead
  of presenting the shortened result as complete.
- Objective verifier criteria are concrete and specific enough for EmberAdventures to
  decide yes/no without guessing from the title alone.
- Objective completion instructions describe the immediate result, reveal,
  consequence, transition, or future-cast introduction for that exact beat.
- Future-cast reward ids resolve by exact `future_cast.items[character_id]`
  object key.
- Export metadata is current.
- `state.meta.story_source` does not include old planner-summary or
  source-outline fields.
- `nsfw` is true only when the story template itself contains required
  adult/NSFW premise, starting content, required objectives, required
  characters, or required storylines. It is false when the story is safe to play
  in SFW mode even if runtime settings can later allow spicy play.
- SFW stories do not use public-visible adult scene / NSFW / kink-facing prose,
  but they also do not block later NSFW conversion through runtime settings.
- `loli` is true only when at least one embedded character is actually marked
  `loli: true`; otherwise it is false, including adult/non-loli character
  variants.
- No stale revision labels.
- No mojibake apostrophes.
- Opening messages do not include runtime-only fields such as `streaming`,
  `stateSyncStatus`, `spicySyncStatus`, `voiceMeta`, `voiceSpeakers`, or
  `objectiveComplete`.
- Opening messages do not include exporter-discarded `id` or `entryId` fields.


---

# EmberAdventures World Map Patterns

Use `world_map.locations`, not old `visible_locations`, for stored story templates.

## Shape

```json
{
  "current_location_id": "loc-current",
  "focus_location_id": "loc-current",
  "travel_history": [],
  "locations": {
    "loc-current": {
      "id": "loc-current",
      "name": "Current Place",
      "type": "place",
      "scale": "site",
      "parent_id": "loc-settlement",
      "x": 50,
      "y": 50,
      "discovered": true,
      "travel_enabled": true,
      "summary": "Short map summary.",
      "detail": {
        "universe": "Story Title",
        "world": "World Name",
        "region": "Region Name",
        "settlement_name": "Settlement",
        "district": "District",
        "specific_place": "Specific place"
      },
      "connections": ["loc-settlement"],
      "npcs": []
    }
  }
}
```

## Hierarchy

Prefer stable parent chains:

world -> region -> settlement -> district/site

Opening site should be discovered. Nearby future places can exist but should often be `discovered: false` or `travel_enabled: false`.

Connections should be valid ids. Add bidirectional links when practical.

## NPC Pointers

`locations[id].npcs` can list proper names associated with that place, but full known NPC data belongs in `npc_directory`; future important characters usually belong in `future_cast`.

Do not put titles, jobs, groups, or generic descriptions in `locations[id].npcs`.
Invalid examples: `Gate Guard`, `Guild Clerk`, `travelers`, `cart drivers`,
`shopkeeper`, `villagers`. If the location needs a speakable or inspectable NPC,
create a named NPC such as `First Last` in `npc_directory` and list that
proper name here. Otherwise leave `npcs` empty.
