---
name: emberadventures-story
description: Create, update, migrate, validate, or review normal EmberAdventures story-template JSON files. This is the authoritative base story skill and schema contract. Use it directly for original/source-free stories and always load it before Source EmberAdventures Story for source/canon work.
---

## Version and Update Check

Current skill version: `1.0.0`.

Before using this skill, retrieve the version number from the authoritative GitHub
version file and verify that it is exactly `1.0.0`:

https://raw.githubusercontent.com/andro951/ember-adventures/main/plugins/ember-adventures/skills/emberadventures-story-version.md

If the retrieved version differs from the local version, pull the current
`emberadventures-story` skill folder from GitHub, replace the local copy,
and then continue with the user's job. Do not silently use a stale local copy.

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

Before writing objectives for a serious story, produce a compact internal
outline with the premise, player fantasy, emotional targets, world hook,
beginning, midpoint or reevaluation moment, climax, ending choices or postgame,
progression/building axis, key relationship arcs, and intended story structure
mode. If the user is available and has not delegated the design, ask whether to
change the outline before final JSON.

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
2. Build a premise with a clear playable starting situation, not just lore.
   Ask whether this should be a Telltale-style branching story that focuses on
   direct choices and multiple endings, or a simpler linear/mostly-linear
   story, unless the user already specified the structure. If interaction is
   unavailable or the user explicitly asked for no questions, infer from the
   premise and note the chosen structure in your planning notes, not in the
   story JSON.
3. Create or verify required public metadata.
4. Create a focused starting state with one immediate active objective.
5. Build a hidden objective spine for the main story.
6. Add side objectives that fit the premise instead of filler errands.
7. Add future cast only when it improves play; keep locked future entries hidden.
8. Build a useful world map with starting locations and unlockable future areas.
9. Write a vivid opening message that preserves player agency.
10. Run the progression design pass before final JSON:
    - define the current starting state;
    - define the hidden future state the story can reach;
    - define which objective rewards update state, rules, map locations, scene
      lists, character fields, images, items, and future-cast availability;
    - define which `story_rules` are active at start and which objectives add,
      replace, or remove them.
11. Run the feature-utilization pass. For every serious story, explicitly
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
    playable relationship ob…44751 tokens truncated…ed `generate_story_image` objective rewards may
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
