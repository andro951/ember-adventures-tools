# EmberAdventures 0–20 Body Scales — Image-Model Sequential Review

Status: **USER-LOCKED BODY-SCALE DESIGN + COMPLETE LEGACY MIGRATION SPEC FOR CODEX**

Purpose: these mappings exist only to produce image-model prompt phrases. The review therefore prioritizes sequential visual change, concrete size anchors, and non-overlapping slider ownership over elegant prose.

## Global rules used in this pass

- Every numeric value is a discrete image-prompt preset.
- Neighboring values must change at least one concrete measurable or body-relative anchor.
- Prefer ratios, body landmarks, cup/measurement anchors, or absolute dimensions over adjective-only progressions.
- Keep body-scale wording species-neutral; use terms such as adult proportions, realistic anatomy, ordinary proportions, and fantasy anatomy.
- Do not let one slider describe geometry or composition owned by another slider.
- Relative measurements are preferred over absolute measurements when absolute dimensions would conflict with the independent Height slider.
- `0` and `20` remain deliberately excessive endpoints where appropriate.
- V-shaped build scales intentionally change *type* of mass at the center: fat/soft mass decreases toward 10, then muscle mass increases away from 10.

## Height

Absolute standing height is the primary anchor; no leg/torso proportion language is allowed here.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurdly tiny adult figure, about **2'6" / 76 cm** tall |
| 1 | extraordinarily tiny adult figure, about **3'0" / 91 cm** tall |
| 2 | exceptionally tiny adult figure, about **3'6" / 107 cm** tall |
| 3 | extremely short adult figure, about **4'0" / 122 cm** tall |
| 4 | unusually short adult figure, about **4'4" / 132 cm** tall |
| 5 | very short adult figure, about **4'8" / 142 cm** tall |
| 6 | short adult figure, about **5'0" / 152 cm** tall |
| 7 | moderately short adult figure, about **5'2" / 157 cm** tall |
| 8 | slightly short adult figure, about **5'4" / 163 cm** tall |
| 9 | a little below average height, about **5'6" / 168 cm** tall |
| 10 | average adult height, about **5'8" / 173 cm** tall |
| 11 | a little above average height, about **5'10" / 178 cm** tall |
| 12 | moderately tall adult figure, about **6'0" / 183 cm** tall |
| 13 | tall adult figure, about **6'3" / 191 cm** tall |
| 14 | very tall adult figure, about **6'6" / 198 cm** tall |
| 15 | exceptionally tall adult figure, about **7'0" / 213 cm** tall |
| 16 | giant-scale adult figure, about **7'6" / 229 cm** tall |
| 17 | extremely tall fantasy figure, about **8'0" / 244 cm** tall |
| 18 | enormous fantasy figure, about **9'0" / 274 cm** tall |
| 19 | colossal fantasy figure, about **10'6" / 320 cm** tall |
| 20 | absurd extreme-fantasy height, about **12'0" / 366 cm** tall |

## Shoulder Width

Uses head-widths because shoulder span must remain independent of character height and upper-body musculature.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy narrow shoulder span, outer-shoulder to outer-shoulder width about **0.75 head-widths** |
| 1 | extraordinarily narrow shoulder span, outer-shoulder to outer-shoulder width about **1 head-width** |
| 2 | exceptionally narrow shoulder span, outer-shoulder to outer-shoulder width about **1.25 head-widths** |
| 3 | extremely narrow shoulder span, outer-shoulder to outer-shoulder width about **1.5 head-widths** |
| 4 | unusually narrow shoulder span, outer-shoulder to outer-shoulder width about **1.75 head-widths** |
| 5 | very narrow shoulder span, outer-shoulder to outer-shoulder width about **1.9 head-widths** |
| 6 | narrow shoulder span, outer-shoulder to outer-shoulder width about **2.05 head-widths** |
| 7 | narrow shoulder span, outer-shoulder to outer-shoulder width about **2.15 head-widths** |
| 8 | slightly narrow shoulder span, outer-shoulder to outer-shoulder width about **2.25 head-widths** |
| 9 | slightly narrow shoulder span, outer-shoulder to outer-shoulder width about **2.35 head-widths** |
| 10 | average shoulder span, outer-shoulder to outer-shoulder width about **2.5 head-widths** |
| 11 | slightly wide shoulder span, outer-shoulder to outer-shoulder width about **2.65 head-widths** |
| 12 | slightly wide shoulder span, outer-shoulder to outer-shoulder width about **2.85 head-widths** |
| 13 | wide shoulder span, outer-shoulder to outer-shoulder width about **3.05 head-widths** |
| 14 | wide shoulder span, outer-shoulder to outer-shoulder width about **3.3 head-widths** |
| 15 | very wide shoulder span, outer-shoulder to outer-shoulder width about **3.6 head-widths** |
| 16 | very wide shoulder span, outer-shoulder to outer-shoulder width about **4 head-widths** |
| 17 | extreme fantasy-wide shoulder span, outer-shoulder to outer-shoulder width about **4.5 head-widths** |
| 18 | extreme fantasy-wide shoulder span, outer-shoulder to outer-shoulder width about **5.1 head-widths** |
| 19 | colossal fantasy shoulder span, outer-shoulder to outer-shoulder width about **6 head-widths** |
| 20 | absurd extreme-fantasy shoulder span, outer-shoulder to outer-shoulder width about **7 head-widths** |

## Hip Width

Uses lateral hip span in head-widths; no butt, thigh, softness, or muscularity wording.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy narrow hip span, lateral outer-hip width about **0.75 head-widths** |
| 1 | extraordinarily narrow hip span, lateral outer-hip width about **1 head-width** |
| 2 | exceptionally narrow hip span, lateral outer-hip width about **1.2 head-widths** |
| 3 | extremely narrow hip span, lateral outer-hip width about **1.4 head-widths** |
| 4 | unusually narrow hip span, lateral outer-hip width about **1.6 head-widths** |
| 5 | very narrow hip span, lateral outer-hip width about **1.75 head-widths** |
| 6 | narrow hip span, lateral outer-hip width about **1.85 head-widths** |
| 7 | narrow hip span, lateral outer-hip width about **1.95 head-widths** |
| 8 | slightly narrow hip span, lateral outer-hip width about **2.05 head-widths** |
| 9 | slightly narrow hip span, lateral outer-hip width about **2.15 head-widths** |
| 10 | average hip span, lateral outer-hip width about **2.25 head-widths** |
| 11 | slightly wide hip span, lateral outer-hip width about **2.4 head-widths** |
| 12 | slightly wide hip span, lateral outer-hip width about **2.6 head-widths** |
| 13 | wide hip span, lateral outer-hip width about **2.8 head-widths** |
| 14 | wide hip span, lateral outer-hip width about **3.05 head-widths** |
| 15 | very wide hip span, lateral outer-hip width about **3.35 head-widths** |
| 16 | very wide hip span, lateral outer-hip width about **3.7 head-widths** |
| 17 | extreme fantasy-wide hip span, lateral outer-hip width about **4.1 head-widths** |
| 18 | extreme fantasy-wide hip span, lateral outer-hip width about **4.6 head-widths** |
| 19 | colossal fantasy hip span, lateral outer-hip width about **5.2 head-widths** |
| 20 | absurd extreme-fantasy hip span, lateral outer-hip width about **6 head-widths** |

## Arm Length

Uses shoulder-to-fingertip length as a percentage of standing height. Body landmarks are avoided through most of the scale because independent Leg Length can move the hips, thighs, knees, and ankles. The two deliberately absurd endpoints retain the user's requested hand/arm and elbow/ground relationships.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy short arms: shoulder-to-fingertip length about **15% of standing height**; each hand is visibly longer than the entire shortened shoulder-to-wrist arm |
| 1 | impossibly short arms: shoulder-to-fingertip length about **18% of standing height**; each hand is about as long as the shortened shoulder-to-wrist arm |
| 2 | extraordinarily short arms: shoulder-to-fingertip length about **22% of standing height** |
| 3 | extremely short arms: shoulder-to-fingertip length about **26% of standing height** |
| 4 | exceptionally short arms: shoulder-to-fingertip length about **29% of standing height** |
| 5 | very short arms: shoulder-to-fingertip length about **32% of standing height** |
| 6 | short arms: shoulder-to-fingertip length about **34% of standing height** |
| 7 | moderately short arms: shoulder-to-fingertip length about **36% of standing height** |
| 8 | slightly short arms: shoulder-to-fingertip length about **37% of standing height** |
| 9 | a little below-average arm length: shoulder-to-fingertip length about **39% of standing height** |
| 10 | average proportional arm length: shoulder-to-fingertip length about **41% of standing height** |
| 11 | a little above-average arm length: shoulder-to-fingertip length about **43% of standing height** |
| 12 | slightly long arms: shoulder-to-fingertip length about **45% of standing height** |
| 13 | long arms: shoulder-to-fingertip length about **48% of standing height** |
| 14 | noticeably long arms: shoulder-to-fingertip length about **52% of standing height** |
| 15 | very long arms: shoulder-to-fingertip length about **57% of standing height** |
| 16 | exceptionally long arms: shoulder-to-fingertip length about **63% of standing height** |
| 17 | extremely long arms: shoulder-to-fingertip length about **70% of standing height** |
| 18 | exaggerated fantasy-long arms: shoulder-to-fingertip length about **80% of standing height** |
| 19 | extreme fantasy-long arms: shoulder-to-fingertip length about **115% of standing height**; the upper-arm segment itself is long enough that the elbows hang close to the lower shins when standing upright |
| 20 | absurd extreme-fantasy arm length: shoulder-to-fingertip length about **160% of standing height**; the upper-arm segment alone is about **85% of standing height**, allowing the elbows to touch the ground while standing upright, with forearms and hands extending far beyond them |

## Leg Length

Uses hip-to-ground length as a percentage of total standing height; no lower-body mass wording.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy short legs; hip-to-ground leg length about **18% of total standing height**, with the hips only a short distance above the ankles |
| 1 | impossibly short legs; hip-to-ground leg length about **22% of total standing height** |
| 2 | extraordinarily short legs; hip-to-ground leg length about **27% of total standing height** |
| 3 | extremely short legs; hip-to-ground leg length about **32% of total standing height** |
| 4 | exceptionally short legs; hip-to-ground leg length about **36% of total standing height** |
| 5 | very short legs; hip-to-ground leg length about **40% of total standing height** |
| 6 | short legs; hip-to-ground leg length about **43% of total standing height** |
| 7 | short legs; hip-to-ground leg length about **46% of total standing height** |
| 8 | slightly short legs; hip-to-ground leg length about **48% of total standing height** |
| 9 | slightly short legs; hip-to-ground leg length about **50% of total standing height** |
| 10 | average proportional leg length; hip-to-ground leg length about **52% of total standing height** |
| 11 | slightly long legs; hip-to-ground leg length about **54% of total standing height** |
| 12 | slightly long legs; hip-to-ground leg length about **56% of total standing height** |
| 13 | long legs; hip-to-ground leg length about **59% of total standing height** |
| 14 | long legs; hip-to-ground leg length about **62% of total standing height** |
| 15 | very long legs; hip-to-ground leg length about **66% of total standing height** |
| 16 | very long legs; hip-to-ground leg length about **70% of total standing height** |
| 17 | extreme fantasy-long legs; hip-to-ground leg length about **75% of total standing height** |
| 18 | extreme fantasy-long legs; hip-to-ground leg length about **82% of total standing height**, with leg length overwhelmingly dominating torso length |
| 19 | colossal fantasy-long legs; hip-to-ground leg length about **88% of total standing height**, leaving only a very small upper-body portion above the hips |
| 20 | absurd extreme-fantasy leg length; hip-to-ground leg length about **94% of total standing height**, leaving a proportionally tiny torso above the extremely high-set hips |

## Upper-body Build

V-shaped composition scale: 0 fat-volume extreme → 10 emaciated extreme → 20 muscular extreme. Upper-arm diameter supplies the sequential size anchor. The wording is limited to upper arms, upper back, side torso, deltoids, and traps so this slider does not independently change breast/pectoral size or structural shoulder span.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd fat-volume extreme: enormously thick soft upper arms plus overwhelming soft tissue across the upper back and side torso with deep folds; upper-arm diameter about **2.2 head-widths** |
| 1 | extreme fat-volume upper body: massive soft upper arms plus very heavy softness across the upper back and side torso; upper-arm diameter about **1.9 head-widths** |
| 2 | severe fat-volume upper body: very thick soft upper arms plus substantial soft tissue across the upper back and side torso; upper-arm diameter about **1.6 head-widths** |
| 3 | very heavy soft upper body with large soft upper arms and pronounced upper-back/side-torso fullness; upper-arm diameter about **1.4 head-widths** |
| 4 | heavy soft upper body with thick upper arms and clearly substantial upper-back/side-torso soft-tissue volume; upper-arm diameter about **1.2 head-widths** |
| 5 | clearly overweight upper-body build with full soft arms and noticeable extra upper-back/side-torso mass; upper-arm diameter about **1 head-width** |
| 6 | mildly overweight upper-body build with soft upper arms and modest extra upper-back/side-torso fullness; upper-arm diameter about **0.85 head-widths** |
| 7 | naturally soft upper-body build with moderate arm softness and ordinary upper-back/side-torso fullness; upper-arm diameter about **0.7 head-widths** |
| 8 | average-soft upper-body build with ordinary arm mass and normal upper-back/side-torso soft-tissue volume; upper-arm diameter about **0.58 head-widths** |
| 9 | very thin upper-body build with slender arms, very little fat, and very little muscle bulk through the upper arms/back; upper-arm diameter about **0.38 head-widths** |
| 10 | absurd emaciated extreme: stick-thin arms with virtually no visible fat or muscle mass through the upper arms/back and sharply visible collarbone structure; upper-arm diameter about **0.22 head-widths** |
| 11 | extremely thin upper-body build with very slim arms and only trace visible upper-arm/back muscle tone; upper-arm diameter about **0.3 head-widths** |
| 12 | lean upper-body build with slim lightly toned arms and subtle upper-back definition; upper-arm diameter about **0.4 head-widths** |
| 13 | fit upper-body build with clearly toned arms and upper-back definition but modest muscle bulk; upper-arm diameter about **0.52 head-widths** |
| 14 | athletic upper-body build with visibly developed biceps, triceps, deltoids, traps, and upper-back muscles; upper-arm diameter about **0.65 head-widths** |
| 15 | muscular upper-body build with substantial arm muscles and strongly developed deltoids, traps, and upper back; upper-arm diameter about **0.8 head-widths** |
| 16 | very muscular upper-body build with large biceps/triceps and thick, strongly developed deltoids, traps, and upper-back musculature; upper-arm diameter about **1 head-width** |
| 17 | bodybuilder upper-body build with very large deeply defined arms, deltoids, traps, and upper-back muscles; upper-arm diameter about **1.25 head-widths** |
| 18 | extreme bodybuilder upper-body build with enormous rounded arm muscles and heavily hypertrophied deltoids, traps, and upper back; upper-arm diameter about **1.55 head-widths** |
| 19 | hyper-muscular fantasy upper-body build with colossal bulging arm, deltoid, trap, and upper-back muscle mass; upper-arm diameter about **1.9 head-widths** |
| 20 | absurd extreme-fantasy muscular upper-body build with gigantic impossible arm, deltoid, trap, and upper-back muscle mass; upper-arm diameter about **2.3 head-widths** |

## Midsection Build

V-shaped composition scale. Fat side uses belly projection and overhang landmarks; muscular side uses ab-count and measured relief.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd fat-volume extreme: front abdominal projection about **3 head-lengths** beyond the ribcage line; deep overhang reaching roughly knee level |
| 1 | fat/soft midsection: front abdominal projection about **2.5 head-lengths** beyond the ribcage line; heavy overhang reaching around mid-thigh |
| 2 | fat/soft midsection: front abdominal projection about **2.1 head-lengths** beyond the ribcage line; substantial overhang reaching the upper-mid thigh |
| 3 | fat/soft midsection: front abdominal projection about **1.7 head-lengths** beyond the ribcage line; large overhang reaching the upper thigh |
| 4 | fat/soft midsection: front abdominal projection about **1.4 head-lengths** beyond the ribcage line; pronounced overhang reaching around the groin/hip crease |
| 5 | fat/soft midsection: front abdominal projection about **1.1 head-lengths** beyond the ribcage line; full rounded belly hanging several inches below the waistline |
| 6 | fat/soft midsection: front abdominal projection about **0.8 head-lengths** beyond the ribcage line; soft belly with a modest overhang over the waistline |
| 7 | fat/soft midsection: front abdominal projection about **0.55 head-lengths** beyond the ribcage line; rounded soft belly without a heavy overhang |
| 8 | fat/soft midsection: front abdominal projection about **0.3 head-lengths** beyond the ribcage line; average-soft abdomen with mild natural fullness |
| 9 | fat/soft midsection: front abdominal projection about **0.12 head-lengths** beyond the ribcage line; very thin nearly flat abdomen with very little body fat |
| 10 | absurd emaciated extreme: deeply sunken abdomen with virtually no fat or abdominal muscle, recessed about **0.15 head-length** inside the ribcage/hip line |
| 11 | extremely lean flat abdomen with only faint natural abdominal lines and essentially no raised muscle blocks; abdominal muscle relief projects about **0 head-lengths** forward from the abdominal plane |
| 12 | lean flat abdomen with a faint **2-pack** and only slight upper-ab relief; abdominal muscle relief projects about **0.05 head-lengths** forward from the abdominal plane |
| 13 | fit abdomen with a clear **2-pack** and light oblique definition; abdominal muscle relief projects about **0.1 head-lengths** forward from the abdominal plane |
| 14 | athletic abdomen with a clear **4-pack** and visible obliques; abdominal muscle relief projects about **0.15 head-lengths** forward from the abdominal plane |
| 15 | muscular abdomen with a distinct **6-pack** and strong oblique definition; abdominal muscle relief projects about **0.2 head-lengths** forward from the abdominal plane |
| 16 | very muscular abdomen with a deep raised **6-pack**, thick blocks, and pronounced grooves; abdominal muscle relief projects about **0.3 head-lengths** forward from the abdominal plane |
| 17 | bodybuilder abdomen with a highly visible **8-pack**, deeply separated blocks, and prominent obliques; abdominal muscle relief projects about **0.4 head-lengths** forward from the abdominal plane |
| 18 | extreme bodybuilder abdomen with a thick raised **8-pack** and heavily hypertrophied blocks; abdominal muscle relief projects about **0.55 head-lengths** forward from the abdominal plane |
| 19 | hyper-muscular fantasy abdomen with oversized multi-row abdominal blocks and massive obliques; abdominal muscle relief projects about **0.8 head-lengths** forward from the abdominal plane |
| 20 | absurd extreme-fantasy abdomen with gigantic protruding multi-row abdominal blocks and impossible segmentation; abdominal muscle relief projects about **1.1 head-lengths** forward from the abdominal plane |

## Lower-body Build

V-shaped composition scale for thighs/calves only. Butt/glute volume is explicitly excluded and handled by Butt/Glute Build.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd fat-volume extreme with enormously thick soft thighs and calves, deep soft folds, and overwhelming lower-leg mass; thigh diameter about **3 head-widths** and calf diameter about **2 head-widths** |
| 1 | extreme fat-volume lower body with massive soft thighs and very thick soft calves; thigh diameter about **2.6 head-widths** and calf diameter about **1.75 head-widths** |
| 2 | severe fat-volume lower body with very large soft thighs and substantially thickened calves; thigh diameter about **2.3 head-widths** and calf diameter about **1.55 head-widths** |
| 3 | very heavy soft lower body with large thighs and noticeably heavy calves; thigh diameter about **2 head-widths** and calf diameter about **1.35 head-widths** |
| 4 | heavy soft lower body with clearly thick thighs and substantial calf softness; thigh diameter about **1.7 head-widths** and calf diameter about **1.15 head-widths** |
| 5 | clearly overweight lower body with full thighs and calves but still reasonably proportional; thigh diameter about **1.45 head-widths** and calf diameter about **1 head-width** |
| 6 | mildly overweight lower body with soft full thighs and modestly thick calves; thigh diameter about **1.25 head-widths** and calf diameter about **0.85 head-widths** |
| 7 | naturally soft lower body with moderate thigh/calf fullness; thigh diameter about **1.1 head-widths** and calf diameter about **0.72 head-widths** |
| 8 | average-soft lower body with ordinary thigh and calf mass; thigh diameter about **0.95 head-widths** and calf diameter about **0.6 head-widths** |
| 9 | very thin lower body with slender thighs/calves and very little fat or muscle; thigh diameter about **0.6 head-widths** and calf diameter about **0.4 head-widths** |
| 10 | absurd emaciated extreme with stick-thin thighs/calves and virtually no visible fat or muscle mass; thigh diameter about **0.35 head-widths** and calf diameter about **0.25 head-widths** |
| 11 | extremely thin lower body with very slim thighs/calves and only trace muscle tone; thigh diameter about **0.45 head-widths** and calf diameter about **0.3 head-widths** |
| 12 | lean lower body with slim lightly toned thighs/calves; thigh diameter about **0.6 head-widths** and calf diameter about **0.4 head-widths** |
| 13 | fit lower body with clearly toned thighs/calves but modest muscle bulk; thigh diameter about **0.8 head-widths** and calf diameter about **0.5 head-widths** |
| 14 | athletic lower body with visibly developed quadriceps, hamstrings, and calves; thigh diameter about **1 head-width** and calf diameter about **0.65 head-widths** |
| 15 | muscular lower body with substantial quadriceps, hamstrings, and calf development; thigh diameter about **1.25 head-widths** and calf diameter about **0.8 head-widths** |
| 16 | very muscular lower body with large thighs and heavily developed calves; thigh diameter about **1.5 head-widths** and calf diameter about **1 head-width** |
| 17 | bodybuilder lower body with very large deeply defined quadriceps, hamstrings, and calves; thigh diameter about **1.8 head-widths** and calf diameter about **1.2 head-widths** |
| 18 | extreme bodybuilder lower body with enormous rounded quadriceps/hamstrings and heavily hypertrophied calves; thigh diameter about **2.15 head-widths** and calf diameter about **1.45 head-widths** |
| 19 | hyper-muscular fantasy lower body with colossal bulging thigh and calf muscles; thigh diameter about **2.55 head-widths** and calf diameter about **1.7 head-widths** |
| 20 | absurd extreme-fantasy muscular lower body with gigantic impossible quadriceps, hamstrings, and calves; thigh diameter about **3 head-widths** and calf diameter about **2 head-widths** |

## Butt / Glute Build

V-shaped glute-only scale: 0 huge soft/fat volume → 10 completely flat → 20 huge muscular volume. Rear projection is the sequential anchor.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy soft/fat butt with enormously oversized plush glute volume, extreme roundness, and overwhelming glute projection; glute depth outward from the pelvis line about **3 head-lengths** |
| 1 | extremely huge soft fat butt with massive plush glute volume and enormous rounded projection; glute depth outward from the pelvis line about **2.6 head-lengths** |
| 2 | gigantic soft fat butt with very large plush glute volume and substantial rounded projection; glute depth outward from the pelvis line about **2.3 head-lengths** |
| 3 | enormous soft fat butt with large rounded cheeks and pronounced glute volume; glute depth outward from the pelvis line about **2 head-lengths** |
| 4 | very large soft fat butt with thick plush volume, strong roundness, and substantial projection; glute depth outward from the pelvis line about **1.7 head-lengths** |
| 5 | large soft fat butt with noticeably full rounded cheeks and generous projection; glute depth outward from the pelvis line about **1.4 head-lengths** |
| 6 | full soft butt with abundant natural fat volume and clear rounded projection; glute depth outward from the pelvis line about **1.15 head-lengths** |
| 7 | nicely full soft butt with noticeable plush volume and natural roundness; glute depth outward from the pelvis line about **0.9 head-lengths** |
| 8 | moderately full soft butt with gentle roundness and natural projection; glute depth outward from the pelvis line about **0.65 head-lengths** |
| 9 | small lean butt with little soft volume and limited glute projection; glute depth outward from the pelvis line about **0.3 head-lengths** |
| 10 | completely and totally flat butt with virtually no visible glute volume or outward projection; glute depth outward from the pelvis line is effectively **0 head-lengths** |
| 11 | extremely small lean glutes with only slight muscular shape and minimal projection; glute depth outward from the pelvis line about **0.2 head-lengths** |
| 12 | lean lightly toned glutes with modest muscular shape and little projection; glute depth outward from the pelvis line about **0.35 head-lengths** |
| 13 | fit glutes with clear muscular shape and moderate projection; glute depth outward from the pelvis line about **0.5 head-lengths** |
| 14 | athletic glutes with visibly developed muscle and firm rounded projection; glute depth outward from the pelvis line about **0.7 head-lengths** |
| 15 | muscular glutes with substantial muscle volume, strong roundness, and pronounced projection; glute depth outward from the pelvis line about **0.9 head-lengths** |
| 16 | very muscular glutes with large thick muscle mass and powerful rounded projection; glute depth outward from the pelvis line about **1.15 head-lengths** |
| 17 | bodybuilder glutes with very large deeply developed muscular volume and strong separation; glute depth outward from the pelvis line about **1.45 head-lengths** |
| 18 | extreme bodybuilder glutes with enormous hypertrophied muscle mass and exaggerated muscular projection; glute depth outward from the pelvis line about **1.8 head-lengths** |
| 19 | hyper-muscular fantasy glutes with colossal bulging muscle volume and extreme projection; glute depth outward from the pelvis line about **2.3 head-lengths** |
| 20 | absurd extreme-fantasy muscular glutes with gigantic impossible muscle volume and overwhelming glute projection; glute depth outward from the pelvis line about **3 head-lengths** |

## Chest — Female / Non-Male Presentation

Presentation-specific V-shaped chest scale: 0 huge extremely sagging/flattened soft breasts → 10 AA minimum → 20 huge rounded high-set/perky breasts. Relative head/torso volume and vertical landmarks drive sequence. Values 0–9 intentionally emphasize abnormal, pancake-like sagging even when breast volume becomes small.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme-fantasy soft breasts, each **more than 3 torso-volumes** in visible mass; extremely abnormally sagging, severely flattened/pancake-like, with broad lower masses resting heavily on the **ground** |
| 1 | extraordinarily huge soft breasts, each about **2.5 torso-volumes**; extreme abnormal sagging and flattened pendulous shape, with the lower third of the breast mass resting on the **ground** |
| 2 | gigantic soft breasts, each about **2 torso-volumes**; extremely sagging and pancake-like, with the lowermost curves hanging to roughly **ankle level** |
| 3 | extremely huge soft breasts, each about **1.5 torso-volumes**; severely sagging and flattened downward, with the lowermost curves hanging to roughly **mid-shin** |
| 4 | massively oversized soft breasts, each about **1 torso-volume**; extreme abnormal sagging and long pancake-like hang, with lowermost curves around **knee level** |
| 5 | enormous soft heavy breasts, each about **0.75 torso-volume**; severely pendulous and flattened, with lowermost curves around **mid-thigh** |
| 6 | very large soft breasts, each about **0.5 torso-volume / roughly 2 head-volumes**; extremely pronounced abnormal sagging, with lowermost curves around the **upper thighs** |
| 7 | large soft breasts, each about **1.25 head-volumes**; severe exaggerated sagging despite the smaller size, strongly flattened/pancake-like, with lowermost curves hanging to roughly the **hip-crease / top-of-pelvis level** |
| 8 | moderately sized soft breasts, each about **0.75 head-volume**; extreme abnormal sagging for their size, visibly stretched and pancake-like, with lowermost curves hanging to the **lower abdomen below the navel** |
| 9 | small soft breasts, roughly **A-cup / about 0.25 head-volume each**; extreme abnormal sagging despite very little volume, unusually elongated downward and distinctly pancake-like, with the lowermost curves hanging into the **upper abdomen several inches below the breast root** |
| 10 | minimum-volume point: extremely small **AA-cup** breasts with minimal projection, each well under **0.1 head-volume** |
| 11 | small **A-cup** breasts, about **0.2 head-volume each**, rounded, high-set, and modestly projected |
| 12 | full **B-cup** breasts, about **0.35 head-volume each**, rounded with clear forward projection |
| 13 | full **C-cup** breasts, about **0.55 head-volume each**, rounded, full, and high-set |
| 14 | full **D/DD-cup** breasts, about **0.8 head-volume each**, large, rounded, and prominently projected |
| 15 | **F/G-cup** breasts, about **1.1 head-volumes each**, very large, full, rounded, and high-set |
| 16 | **H/I/J-cup** breasts, about **1.5 head-volumes each**, huge, very full, rounded, and strongly projected |
| 17 | enormous fantasy breasts, about **2 head-volumes each**, strongly rounded and high-set, with the lowermost curves extending below the waist because of sheer size |
| 18 | massive fantasy breasts, each about **1 torso-volume**, extremely rounded and high-set, with the lowermost curves reaching roughly **mid-thigh** |
| 19 | colossal extreme-fantasy breasts, each about **1.75 torso-volumes**, massively rounded and high-set, with the lowermost curves reaching roughly **ankle level** because of sheer size |
| 20 | absurd extreme-fantasy breasts, each **more than 2.5 torso-volumes**, extremely full, rounded, high-set/perky in overall shape, and so enormous that their lowermost curves physically **touch the ground** while standing |

## Chest — Male Presentation

Presentation-specific V-shaped chest scale: 0 huge flattened adipose pectoral-region fullness → 10 flat minimum → 20 huge muscular pectorals. Low side avoids breast-shaped wording.

| Value | Image-prompt phrase |
|---:|---|
| 0 | absurd extreme fat-dominant chest with enormous soft adipose pectoral pads spread broadly across the chest wall and hanging as wide flattened folds rather than rounded breast-shaped mounds; soft pectoral-region projection about **2 head-lengths** forward from the chest wall |
| 1 | extremely fat-dominant chest with massive soft adipose pectoral pads, very heavy downward chest-fat volume, and broad flattened folds; soft pectoral-region projection about **1.7 head-lengths** forward from the chest wall |
| 2 | severely fat-dominant chest with very thick soft pectoral-region adipose pads and pronounced flattened chest-wall fullness; soft pectoral-region projection about **1.4 head-lengths** forward from the chest wall |
| 3 | very fat-dominant chest with large soft adipose pads across the pectoral region and clearly heavy flattened chest volume; soft pectoral-region projection about **1.15 head-lengths** forward from the chest wall |
| 4 | fat-dominant chest with thick soft adipose pectoral fullness, broad and flattened rather than breast-shaped; soft pectoral-region projection about **0.9 head-lengths** forward from the chest wall |
| 5 | clearly soft/heavy chest with substantial adipose padding across the pectoral region and modest downward fold; soft pectoral-region projection about **0.7 head-lengths** forward from the chest wall |
| 6 | mildly soft chest with noticeable adipose pectoral padding and limited visible pectoral definition; soft pectoral-region projection about **0.5 head-lengths** forward from the chest wall |
| 7 | soft pectoral area with moderate chest-fat fullness; soft pectoral-region projection about **0.35 head-lengths** forward from the chest wall |
| 8 | slightly soft pectoral area with a small amount of chest-fat padding; soft pectoral-region projection about **0.2 head-lengths** forward from the chest wall |
| 9 | very lean nearly flat pectoral area with only trace soft tissue and almost no projection; soft pectoral-region projection about **0.1 head-lengths** forward from the chest wall |
| 10 | minimum-volume point: completely flat chest with essentially no adipose padding and almost no pectoral projection, about **0 head-lengths** beyond the chest wall |
| 11 | extremely lean chest with slight pectoral definition; pectoral muscle projects about **0.08 head-lengths** forward from the chest wall |
| 12 | lean chest with modest pectoral shape; pectoral muscle projects about **0.12 head-lengths** forward from the chest wall |
| 13 | fit chest with clear pectoral definition; pectoral muscle projects about **0.18 head-lengths** forward from the chest wall |
| 14 | athletic pectorals with visible thickness and firm projection; pectoral muscle projects about **0.26 head-lengths** forward from the chest wall |
| 15 | muscular pectorals with substantial thickness and forward projection; pectoral muscle projects about **0.36 head-lengths** forward from the chest wall |
| 16 | very muscular pectorals with large thick muscle mass and strong projection; pectoral muscle projects about **0.5 head-lengths** forward from the chest wall |
| 17 | bodybuilder pectorals with very large deeply defined muscle volume; pectoral muscle projects about **0.7 head-lengths** forward from the chest wall |
| 18 | extreme bodybuilder pectorals with enormous hypertrophied thickness and rounded muscular projection; pectoral muscle projects about **0.95 head-lengths** forward from the chest wall |
| 19 | hyper-muscular fantasy pectorals with colossal forward-projecting muscle mass; pectoral muscle projects about **1.35 head-lengths** forward from the chest wall |
| 20 | absurd extreme-fantasy pectorals with gigantic impossible muscular projection and volume; pectoral muscle projects about **2 head-lengths** forward from the chest wall |

## Penis Size

Absolute length and width are the only size anchors. Body-relative landmarks are intentionally excluded because Height, Arm Length, and Leg Length are independent sliders and could otherwise contradict this field.

| Value | Image-prompt phrase |
|---:|---|
| 0 | almost no external projection penis, about **0.25 in / 0.6 cm long** and about **0.25 in / 0.6 cm wide** |
| 1 | extremely tiny penis, about **0.5 in / 1.3 cm long** and about **0.35 in / 0.9 cm wide** |
| 2 | extraordinarily tiny penis, about **0.75 in / 1.9 cm long** and about **0.45 in / 1.1 cm wide** |
| 3 | micropenis-scale penis, about **1 in / 2.5 cm long** and about **0.6 in / 1.5 cm wide** |
| 4 | exceptionally tiny penis, about **1.5 in / 3.8 cm long** and about **0.7 in / 1.8 cm wide** |
| 5 | tiny penis, about **2 in / 5.1 cm long** and about **0.8 in / 2.0 cm wide** |
| 6 | very small penis, about **2.5 in / 6.4 cm long** and about **0.9 in / 2.3 cm wide** |
| 7 | very small penis, about **3 in / 7.6 cm long** and about **1 in / 2.5 cm wide** |
| 8 | small penis, about **4.5 in / 11.4 cm long** and about **1.2 in / 3.0 cm wide** |
| 9 | moderately small penis, about **5.25 in / 13.3 cm long** and about **1.3 in / 3.3 cm wide** |
| 10 | average-sized penis, about **6 in / 15.2 cm long** and about **1.35 in / 3.4 cm wide** |
| 11 | large penis, about **7 in / 17.8 cm long** and about **1.5 in / 3.8 cm wide** |
| 12 | very large penis, about **8 in / 20.3 cm long** and about **1.6 in / 4.1 cm wide** |
| 13 | extremely large and thick penis, about **9 in / 22.9 cm long** and about **1.75 in / 4.4 cm wide** |
| 14 | massive fantasy-sized penis, about **12 in / 30.5 cm long** and about **2 in / 5.1 cm wide** |
| 15 | enormous fantasy-sized penis, about **15 in / 38.1 cm long** and about **2.4 in / 6.1 cm wide** |
| 16 | gigantic fantasy-sized penis, about **18 in / 45.7 cm long** and about **2.75 in / 7.0 cm wide** |
| 17 | colossal fantasy-sized penis, about **24 in / 61.0 cm long** and about **3.5 in / 8.9 cm wide** |
| 18 | absurd extreme-fantasy-scale penis, about **36 in / 91.4 cm long** and about **5 in / 12.7 cm wide** |
| 19 | surreal extreme-fantasy-scale penis, about **60 in / 152.4 cm long** and about **8 in / 20.3 cm wide** |
| 20 | absolute extreme-fantasy maximum penis, about **96 in / 243.8 cm long** and about **12 in / 30.5 cm wide** |

## Full audit suite after sequential-anchor review

### Audit 1 — Architecture / coverage

**PASS. No new slider is recommended.**

Final slider fields:

1. `height`
2. `shoulder_width`
3. `chest` with separate female/non-male and male phrase tables
4. `upper_body_build`
5. `midsection_build`
6. `hip_width`
7. `butt_build`
8. `lower_body_build`
9. `arm_length`
10. `leg_length`
11. `penis_size`

The old `muscular` and `waist` concepts are intentionally absorbed into the regional build system. Old muscle-based `arms` becomes `arm_length`; old `legs` remains a length concept under the clearer `leg_length` name. Torso proportion is already expressible through Height + Leg Length, so a separate torso-length slider would add redundancy. Hand size, foot size, neck length, head size, and unusual anatomy remain better handled as exceptional/custom visual description rather than additional default sliders.

### Audit 2 — Ownership / conflict / orthogonality

**PASS after three targeted corrections.**

Corrections made during this audit:

- **Upper-body Build:** removed generic front-`upper-torso` mass wording that could accidentally change the independent Chest slider. Fat/soft wording now targets upper arms, upper back, and side torso; muscular wording targets arms, deltoids, traps, and upper back without claiming structural shoulder width.
- **Arm Length:** removed ordinary fingertip-to-thigh/knee landmarks because those landmarks move when independent Leg Length changes. Percentage of standing height is now the normal anchor. Only the deliberately absurd endpoint-specific relationships requested by the creator remain.
- **Penis Size:** removed forearm-, torso-, hip-to-knee-, and standing-height comparisons because Height, Arm Length, and Leg Length can independently change those landmarks. Absolute dimensions are now the only anchor.

Other high-risk pairs pass:

- Shoulder Width vs Upper-body Build: structural span vs regional mass.
- Hip Width vs Butt Build: lateral span vs rear projection/glute volume.
- Hip Width vs Lower-body Build: lateral span vs thigh/calf mass.
- Butt Build vs Lower-body Build: glutes vs thighs/calves.
- Female/Male Chest vs Upper-body Build: chest morphology/volume vs arms/back/side-torso build.
- Height vs Arm/Leg Length: absolute stature vs proportional limb length.
- Midsection Build vs Hip Width: abdominal projection/softness/muscle vs lateral hip span.

### Audit 3 — Endpoint philosophy

**PASS with no further changes.**

Every 0/20 monotonic endpoint, and every 0/10/20 V-scale anchor, is deliberately excessive. The extremes are not merely `very` versions of normal bodies; they use fantasy-scale measurements or unmistakably extreme landmarks. Ordinary useful values remain well away from the endpoints.

### Audit 4 — Regional-build curve integrity

**PASS with no structural change.**

All four V-shaped build tables use the same logic:

- `0` = maximum soft/fat volume for that region;
- `10` = minimum-mass / emaciated / completely-flat turning point for that region;
- `20` = maximum muscular volume for that region.

Within 0→10, the measurable mass anchor strictly decreases. Within 10→20, the measurable muscular anchor strictly increases. Total mass intentionally reverses direction at 10 because 10 is the V-point, not an average value.

Important usability consequence: **numeric midpoint 10 must never be treated by the application as a neutral/default body value for V-shaped sliders.** Neutral/default values must be field-specific rather than `10` by convention.

### Audit 5 — Female and male Chest as one presentation-specific system

**PASS after a small sequential-landmark correction on female values 7–9.**

Both presentations now share the same abstract V architecture while intentionally using different morphology:

- Female/non-male: huge abnormally sagging soft volume → AA minimum at 10 → huge rounded/high-set/perky volume.
- Male: huge broad flattened adipose pectoral-region volume → flat minimum at 10 → huge muscular pectoral volume.

Female values 7–9 were adjusted so their lowest-point landmarks now rise in a clear order as volume decreases: upper thighs → top-of-pelvis/hip crease → lower abdomen below navel → upper abdomen. They still strongly emphasize abnormal pancake-like sagging all the way through 9.

Male 0–9 continues to avoid breast-morphology wording and describes broad flattened adipose pectoral/chest-wall fullness instead.

### Audit 6 — Combination stress test

**PASS after the ownership corrections above.**

Representative deliberately difficult combinations were checked conceptually:

| Combination | Expected image instruction | Result |
|---|---|---|
| narrow shoulders + extreme muscular upper body | narrow structural shoulder span with huge arm/back muscle | PASS |
| very wide shoulders + emaciated upper body | wide structural span with very thin arms/back | PASS |
| narrow hips + huge soft butt | narrow lateral pelvis/hip span with enormous rear projection | PASS |
| wide hips + completely flat butt | wide lateral hip span with essentially zero rear glute projection | PASS |
| average hips + fantasy-muscular thighs | ordinary lateral hip span with enormous thigh/calf muscle | PASS |
| huge soft thighs + flat butt | large thigh/calf fat volume without added glute projection | PASS |
| very tall + very short legs | large total stature with a long torso relative to legs | PASS |
| short stature + extreme long legs | small total stature with legs taking most of that stature | PASS |
| extremely long arms + very short legs | independent arm/leg proportions with no shared landmark instructions | PASS |
| huge female chest + emaciated upper-body build | huge breasts with very thin arms/back | PASS |
| minimal female chest + fat-volume upper body | AA chest with soft/fat arms/back/side torso | PASS |
| fat-dominant male chest + muscular upper-body build | localized chest adipose fullness with muscular arms/back | PASS |
| muscular male chest + fat-volume upper-body build | large pectoral muscle with soft/fat arms/back/side torso | PASS |
| fat-volume midsection + fantasy-muscular legs | huge soft belly with enormous muscular thighs/calves | PASS |
| emaciated midsection + huge soft butt | sunken abdomen with large soft rear glute volume | PASS |
| fantasy-wide hips + skeletal legs | extreme lateral hip span with very thin thighs/calves | PASS |
| 2'6" height + enormous penis | independent absolute body and penis dimensions | PASS, deliberately bizarre |
| 12' height + tiny penis | independent absolute body and penis dimensions | PASS |

The combinations may be intentionally bizarre, but after the corrections no pair gives the image model mutually exclusive measurements for the same owned trait.

### Audit 7 — Nonstandard-anatomy compatibility

**PASS with an implementation rule required.**

The phrase tables are species-neutral, but not every body has every applicable region. The prompt builder must suppress sliders whose physical structure does not exist instead of forcing ordinary anatomy onto the character.

Recommended applicability rule:

- Use Height whenever standing-height terminology is meaningful; otherwise use a custom anatomy description.
- Use Shoulder Width, Chest, Upper-body Build, and Midsection Build only when the character has the corresponding torso structures.
- When the ordinary lower body is replaced by a nonstandard integrated structure, suppress `hip_width`, `butt_build`, `lower_body_build`, and `leg_length` unless that specific structure genuinely has an analogous authored feature that the numeric scale is intended to control.
- Use `penis_size` only when the active presentation has applicable genital anatomy; otherwise it remains stored but omitted from the image prompt.
- Exceptional anatomy that cannot be represented cleanly by these tables should continue to use a custom descriptive value rather than coercing an unrelated numeric preset.

This is an application/prompt-projection rule, not a reason to add more default sliders.

### Audit 8 — Migration-readiness audit

**PASS. The complete deterministic legacy migration specification is now included later in this document under `Complete legacy 0–10 → new 0–20 migration specification`.**

Migration remains intentionally split into:
- direct numeric remaps where the old and new field meanings remain compatible;
- deterministic multi-source inference where several legacy fields must be reconciled into one regional-build field;
- explicit authored-prose overrides plus safe defaults for concepts the old schema never stored.

Critical rule: **new V-shaped fields never default to 10.** Value 10 is the extreme minimum-mass / flat turning point, not a neutral value.

### Audit 9 — Final document / implementation cleanliness

**PASS.**

This document is now self-contained: one current phrase table per group, one explicit ownership definition per group, one sequential-anchor system, and one audit suite. Superseded experiments are not mixed into the authoritative tables.

The implementation/schema update still needs to rename fields consistently and remove legacy semantics. Recommended final field names are exactly the eleven names listed in the Architecture audit rather than silently retaining misleading legacy names such as `arms`, `legs`, `stomach`, `waist`, or `muscular`.

## Final overall conclusion

**The scale architecture passes. Four targeted wording/anchor corrections were needed, but no slider was added, removed, or structurally redesigned during these audits.**

The main design is sound for its actual purpose: generating ordered image-prompt phrases. The scale design and legacy migration specification are complete. Remaining work is implementation:

1. update the Character schema, editor, validators, preference-file schema, prompt builder, imports/exports, and skill documentation to use the new field names and 0–20 ranges;
2. run the deterministic legacy migration below across every existing character and record any prose/custom-string overrides;
3. validate every migrated character and remove legacy body fields after successful conversion;
4. run image-generation testing across adjacent values and difficult slider combinations, because only empirical rendering can confirm that the image model visually distinguishes every intended one-step change.

# Complete legacy 0–10 → new 0–20 migration specification

This section is the authoritative conversion contract for migrating existing EmberAdventures characters from the old body-field system into the new image-model-oriented system.

The goal is **visual-intent preservation**, not mathematical rescaling. The old body scales were not neutral 0–10 measurements and several old fields represented concepts that no longer exist independently. Never migrate by simply doubling values.

## New authoritative appearance fields

After migration, the body-scale portion of `appearance` uses exactly these eleven fields:

1. `height`
2. `shoulder_width`
3. `chest`
4. `upper_body_build`
5. `midsection_build`
6. `hip_width`
7. `butt_build`
8. `lower_body_build`
9. `arm_length`
10. `leg_length`
11. `penis_size`

Legacy fields removed after successful conversion:

- `muscular`
- `shoulders`
- `stomach`
- `hips`
- `waist`
- `legs`
- `arms`

`height`, `chest`, and `penis_size` keep their field names but their numeric meanings change to the new 0–20 tables.

## Migration precedence

For each character, apply migration evidence in this order:

1. **Explicit authored body prose wins.** If the reviewed dossier, authoritative handoff, or current character prose explicitly states a body property that the legacy number failed to express, migrate to the closest new value that preserves that authored visual intent.
2. Otherwise use the deterministic numeric rules in this section.
3. For a genuinely new property that the old schema never represented, use explicit prose if present; otherwise use the default specified here.
4. Do not infer a new property from an unrelated legacy field merely because the result seems aesthetically likely.
5. If an old body field is a custom string instead of an integer, do not force it through an integer lookup. Interpret the string by its actual visual meaning, split it across new fields if necessary, choose the closest numeric presets, and preserve only irreducible exceptional anatomy in `extra_description` or `extra_description_lower_body`.

## Required defaults when legacy data contains no evidence

These are migration defaults, not universal creation preferences:

| New field | Migration default | Reason |
|---|---:|---|
| `height` | 10 | average standing height |
| `shoulder_width` | 10 | average structural shoulder span |
| `chest` | 13 for canonical non-male; 12 for canonical male | neutral-ish presentation-specific chest when legacy chest is genuinely absent |
| `upper_body_build` | 8 | average-soft regional build; 10 would be emaciated |
| `midsection_build` | 8 | average-soft abdomen; 10 would be emaciated |
| `hip_width` | 10 | average structural hip span |
| `butt_build` | 8 | moderately full/soft neutral default; 10 would be completely flat |
| `lower_body_build` | 8 | average-soft thigh/calf build; 10 would be emaciated |
| `arm_length` | 10 | average proportional arm length |
| `leg_length` | 10 | average proportional leg length |
| `penis_size` | 10 | average-sized new value |

## Direct legacy numeric remaps

### Height

| Old `height` | New `height` |
|---:|---:|
| 0 | 5 |
| 1 | 6 |
| 2 | 7 |
| 3 | 8 |
| 4 | 9 |
| 5 | 10 |
| 6 | 11 |
| 7 | 12 |
| 8 | 13 |
| 9 | 14 |
| 10 | 15 |

The old ordinary 0–10 span becomes the central new 5–15 span. New 0–4 and 16–20 are intentionally beyond the legacy system.

### Shoulder width

| Old `shoulders` | New `shoulder_width` |
|---:|---:|
| 0 | 5 |
| 1 | 6 |
| 2 | 7 |
| 3 | 8 |
| 4 | 9 |
| 5 | 10 |
| 6 | 11 |
| 7 | 12 |
| 8 | 13 |
| 9 | 14 |
| 10 | 15 |

Do not carry old muscular implications into this field. It is structural width only.

### Hip width

| Old `hips` | New `hip_width` |
|---:|---:|
| 0 | 5 |
| 1 | 6 |
| 2 | 7 |
| 3 | 8 |
| 4 | 9 |
| 5 | 10 |
| 6 | 11 |
| 7 | 12 |
| 8 | 13 |
| 9 | 14 |
| 10 | 15 |

The old words `curvy` on values 6 and 9 are **not** copied into `hip_width`; hip width is structural lateral span only. Those legacy `curvy` signals may weakly inform `butt_build` under the butt rules below.

### Leg length

| Old `legs` | New `leg_length` |
|---:|---:|
| 0 | 5 |
| 1 | 6 |
| 2 | 7 |
| 3 | 8 |
| 4 | 9 |
| 5 | 10 |
| 6 | 11 |
| 7 | 12 |
| 8 | 13 |
| 9 | 14 |
| 10 | 15 |

Old `legs` was already a length field. Do not use it as evidence for lower-body fat or musculature.

### Penis size

| Old `penis_size` | New `penis_size` |
|---:|---:|
| 0 | 3 |
| 1 | 5 |
| 2 | 7 |
| 3 | 8 |
| 4 | 10 |
| 5 | 11 |
| 6 | 13 |
| 7 | 14 |
| 8 | 16 |
| 9 | 17 |
| 10 | 18 |

These are exact/near-exact dimensional matches to the new table. New values 19–20 intentionally exceed the old maximum.

## Chest migration — canonical presentation controls the conversion

`appearance.chest` is one shared numeric field whose prompt phrase changes with the active presentation. Therefore the migration must preserve the **canonical/default character presentation first** rather than pretending male and non-male legacy phrase tables can both be preserved exactly with one number.

Canonical presentation buckets:

- `male`, `trans-male`, and `trans male` → use the **male migration table**
- every other canonical gender, including `female`, `futanari`, `futa`, and free-text non-male identities → use the **female/non-male migration table**

Do not choose the migration table from `fallback_name`, fallback outfits, kink tags, or anatomy prose. Use the canonical `gender` field.

### Female / non-male canonical chest migration

| Old `chest` | Old intended phrase | New `chest` |
|---:|---|---:|
| 0 | full large B-cup | 12 |
| 1 | full C-cup | 13 |
| 2 | full D-cup | 14 |
| 3 | full DD/E-cup | 14 |
| 4 | F/G-cup | 15 |
| 5 | H/I-cup | 16 |
| 6 | J/K-cup, approaching head-size | 16 |
| 7 | L/M-cup, approximately head-size | 17 |
| 8 | N/O-cup, visibly larger than head | 17 |
| 9 | R/S-cup, approaching upper-torso scale | 18 |
| 10 | Z-cup, approximately torso-scale | 19 |

All legacy female values map to the new **10→20 rounded/high-set side**. Legacy female values must never be sent to the new 0→9 severely sagging branch unless explicit authored prose independently says the character was intentionally extremely sagging/pendulous.

### Male canonical chest migration

| Old `chest` | Old intended phrase | New `chest` |
|---:|---|---:|
| 0 | flat narrow pectorals | 10 |
| 1 | slight pectoral definition | 11 |
| 2 | lean defined chest | 12 |
| 3 | athletic pectorals | 14 |
| 4 | firm muscular chest | 15 |
| 5 | broad muscular chest | 15 |
| 6 | large powerful pectorals | 16 |
| 7 | very large muscular pectorals | 17 |
| 8 | huge bodybuilder pectorals | 18 |
| 9 | massive heavily defined pectoral muscles | 18 |
| 10 | absurdly massive hyper-muscular pectorals | 19 |

The word `broad` in legacy male chest value 5 does not migrate into structural shoulder width. Shoulder width remains controlled only by old `shoulders`.

## Shared helpers for regional-build migration

Legacy wide-waist values are the only numeric old signal capable of identifying the intentionally heavy/obese characters that previously produced contradictory prompts. They therefore act as a **body-fat override**, but only at the higher values.

### Legacy waist → new fat-side build candidate

| Old `waist` | New fat-side candidate |
|---:|---:|
| 0–5 | no automatic fat override |
| 6 | 7 |
| 7 | 6 |
| 8 | 5 |
| 9 | 4 |
| 10 | 3 |

Numeric legacy data never automatically maps to new fat extremes 0–2. Those values are reserved for newly authored or explicitly documented extreme bodies.

### Legacy muscle level → new muscular-side build candidate

When a regional legacy muscle signal is at least 6:

| Legacy muscle signal | New muscular-side build |
|---:|---:|
| 6 | 14 |
| 7 | 15 |
| 8 | 16 |
| 9 | 17 |
| 10 | 18 |

Legacy numeric data never automatically maps to new muscular extremes 19–20.

## Upper-body Build migration

Sources:
- old `arms`: most specific legacy arm-muscularity/thickness signal;
- old `muscular`: overall musculature signal;
- old `waist` + `stomach`: only used to detect strong legacy obesity/body-fat intent.

First calculate:

```python
upper_muscle_signal = floor((0.60 * old_arms) + (0.40 * old_muscular) + 0.5)
```

Clamp only valid integer legacy inputs 0–10. Do not apply this formula to custom strings.

Then resolve in this exact order:

```python
if old_waist >= 8:
    upper_body_build = {8: 5, 9: 4, 10: 3}[old_waist]

elif old_waist == 7 and 1 <= old_stomach <= 6 and upper_muscle_signal < 8:
    upper_body_build = 6

elif old_waist == 6 and 1 <= old_stomach <= 5 and upper_muscle_signal < 7:
    upper_body_build = 7

elif upper_muscle_signal >= 6:
    upper_body_build = {6: 14, 7: 15, 8: 16, 9: 17, 10: 18}[upper_muscle_signal]

elif upper_muscle_signal == 5 and (old_arms >= 6 or old_muscular >= 6):
    upper_body_build = 13

elif old_arms <= 2 or (old_waist <= 3 and old_stomach <= 1 and old_muscular <= 3):
    upper_body_build = 9

else:
    upper_body_build = 8
```

Interpretation:
- very wide/massive legacy waist wins because this is the corruption/conflict the new system is specifically fixing;
- clear arm/overall muscle intent wins when obesity evidence is not strong;
- old `arms` values 0–2 can preserve an explicitly thin-arm look;
- ordinary ambiguous legacy bodies become new 8 rather than new 10.

## Midsection Build migration

This field intentionally reconciles old `stomach` and old `waist`. Use the following lookup matrix directly.

Rows are old `stomach` 0–10. Columns are old `waist` 0–10. Cell value is new `midsection_build`.

| old stomach ↓ / old waist → | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| **0** | 9 | 9 | 9 | 9 | 9 | 9 | 9 | 9 | 5 | 4 | 3 |
| **1** | 9 | 9 | 9 | 8 | 8 | 8 | 7 | 6 | 5 | 4 | 3 |
| **2** | 9 | 9 | 9 | 8 | 7 | 7 | 7 | 6 | 5 | 4 | 3 |
| **3** | 9 | 9 | 9 | 8 | 8 | 8 | 7 | 6 | 5 | 4 | 3 |
| **4** | 9 | 9 | 9 | 8 | 8 | 8 | 7 | 6 | 5 | 4 | 3 |
| **5** | 9 | 9 | 9 | 8 | 8 | 8 | 7 | 6 | 5 | 4 | 3 |
| **6** | 12 | 12 | 12 | 12 | 12 | 12 | 7 | 6 | 5 | 4 | 3 |
| **7** | 13 | 13 | 13 | 13 | 13 | 13 | 13 | 6 | 5 | 4 | 3 |
| **8** | 14 | 14 | 14 | 14 | 14 | 14 | 14 | 14 | 5 | 4 | 3 |
| **9** | 16 | 16 | 16 | 16 | 16 | 16 | 16 | 16 | 5 | 4 | 3 |
| **10** | 17 | 17 | 17 | 17 | 17 | 17 | 17 | 17 | 5 | 4 | 3 |

Key intentional conflict resolutions:
- old waist 8–10 always forces the fat side, even if old stomach claimed defined/ripped abs; this fixes the exact legacy contradiction that motivated combining the fields;
- old stomach 0 (`very sunken`) is preserved through waist 0–7 rather than being made fat from merely moderate width;
- old waist 0–2 may make a soft/average old stomach leaner, but numeric legacy data never maps automatically to the new skeletal endpoint 10;
- clear old ab definitions map to the muscular branch unless overridden by very wide/massive waist values.

Equivalent algorithm:

```python
STOMACH_BASE = {
    0: 9,
    1: 8,
    2: 7,
    3: 8,
    4: 8,
    5: 8,
    6: 12,
    7: 13,
    8: 14,
    9: 16,
    10: 17,
}

WAIST_FAT = {6: 7, 7: 6, 8: 5, 9: 4, 10: 3}

base = STOMACH_BASE[old_stomach]

if old_waist >= 8:
    midsection_build = WAIST_FAT[old_waist]
elif old_waist == 7:
    midsection_build = 9 if old_stomach == 0 else (base if old_stomach >= 8 else 6)
elif old_waist == 6:
    midsection_build = 9 if old_stomach == 0 else (base if old_stomach >= 7 else 7)
elif old_waist <= 2 and old_stomach <= 5:
    midsection_build = 9
elif old_waist == 3 and old_stomach <= 5:
    midsection_build = max(base, 8)
else:
    midsection_build = base
```

## Lower-body Build migration

Old `legs` is not used here because it represented leg length, not leg mass.

Sources:
- old `muscular`: lower-body muscle signal;
- old `waist` + `stomach`: obesity/body-fat signal.

Resolve in this exact order:

```python
lower_muscle_signal = old_muscular

if old_waist >= 8:
    lower_body_build = {8: 5, 9: 4, 10: 3}[old_waist]

elif old_waist == 7 and 1 <= old_stomach <= 6 and lower_muscle_signal < 8:
    lower_body_build = 6

elif old_waist == 6 and 1 <= old_stomach <= 5 and lower_muscle_signal < 7:
    lower_body_build = 7

elif lower_muscle_signal >= 6:
    lower_body_build = {6: 14, 7: 15, 8: 16, 9: 17, 10: 18}[lower_muscle_signal]

elif old_waist <= 3 and old_stomach <= 1 and old_muscular <= 3:
    lower_body_build = 9

else:
    lower_body_build = 8
```

This intentionally does not infer lower-body muscle from old `arms`, and does not infer lower-body mass from old `legs`.

## Butt / Glute Build migration

The legacy schema had no dedicated butt field. Use explicit authored prose first. If the reviewed dossier/appearance prose clearly says flat, small, large, huge, muscular, soft, etc., choose the closest new `butt_build` phrase directly.

When no explicit butt prose exists, use only these weak legacy signals:

```python
if old_waist >= 8:
    butt_build = {8: 5, 9: 4, 10: 3}[old_waist]

elif old_waist == 7 and 1 <= old_stomach <= 6:
    butt_build = 6

elif old_waist == 6 and 1 <= old_stomach <= 5:
    butt_build = 7

elif old_hips == 9:
    # Old phrase explicitly said "extremely wide curvy hips".
    butt_build = 6

elif old_hips == 6:
    # Old phrase explicitly said "curvy hips".
    butt_build = 7

else:
    butt_build = 8
```

Do **not** infer butt size from old hip width values 0–5, 7–8, or 10 merely because wide/narrow hips may correlate with glute shape in some bodies. The new system intentionally separates those traits.

New butt values 0–2, 9–20 should only be produced from explicit authored evidence or later manual/user edits; numeric legacy data did not encode those distinctions.

## Arm Length migration

Old `arms` was **not an arm-length field**. Its numeric value must never be copied, rescaled, or otherwise used to determine `arm_length`.

Migration rule:

1. If authoritative dossier/body prose explicitly describes unusual arm length or reach, choose the closest new `arm_length` phrase.
2. Otherwise set:

```json
"arm_length": 10
```

Legacy `arms` numeric information is consumed only by `upper_body_build`.

## Nonstandard lower-body handling

Migration still writes structurally valid new fields, but prompt projection must obey the applicability rules from the audit:

- when a replacement lower body makes ordinary hips, buttocks, thighs/calves, or leg length inapplicable, suppress `hip_width`, `butt_build`, `lower_body_build`, and `leg_length` from the generated image prompt;
- do not delete useful authored `extra_description_lower_body`;
- do not invent ordinary legs or glutes merely to satisfy numeric fields;
- keep numeric migrated/default values only as schema data if the schema requires them.

## Custom-string legacy body fields

If any legacy scale field is a string rather than integer:

- never parse a number out of the prose and blindly apply a numeric lookup;
- identify which new field(s) the string actually describes;
- choose the closest new numeric preset when its visual meaning is clearly represented;
- if the string describes exceptional anatomy beyond the new lookup tables, choose the closest numeric preset and retain only the unmapped anatomy in `extra_description` or `extra_description_lower_body`;
- split mixed legacy concepts. Example: a legacy arm string describing both enormous biceps and abnormally long reach should influence `upper_body_build` and `arm_length` separately.

## `extra_description` cleanup after numeric migration

After creating the new scale fields, re-audit `extra_description` and `extra_description_lower_body`.

Remove only body prose that now duplicates the new structured values, including duplicated:
- shoulder width;
- breast/pectoral size;
- upper-arm/back regional build;
- abdominal build;
- hip width;
- butt/glute build;
- thigh/calf build;
- arm length;
- leg length;
- penis size.

Preserve distinct scars, markings, species anatomy, unusual integrated structures, and other durable visual details not represented by a scale.

## Required field-removal order

For each character:

1. Read and preserve all legacy values.
2. Calculate every new value.
3. Apply any explicit-authoritative-prose override.
4. Write all eleven new fields.
5. Validate all new values/types.
6. Only after successful validation, delete legacy `muscular`, `shoulders`, `stomach`, `hips`, `waist`, `legs`, and `arms`.
7. Re-run appearance deduplication and complete Character validation.
8. Increment/update the character schema version and `updated_at` as required by the implementation's versioning rules.

Never delete a legacy field before all new fields that depend on it have been calculated.

## Migration QA invariants

Codex must verify for every migrated character:

- all eleven new fields exist and contain integers from 0 through 20; custom legacy strings have been resolved to the closest supported numeric values;
- every numeric new body value is an integer 0–20;
- no legacy removed body key remains;
- `height`, `shoulder_width`, `hip_width`, `leg_length`, and `penis_size` use the exact lookup tables above when the legacy input was numeric and no explicit prose overrides it;
- `chest` uses the correct canonical-presentation migration table;
- `arm_length` never inherits old muscle-based `arms`;
- `lower_body_build` never inherits old leg-length `legs`;
- new V-shaped build fields do not default to 10;
- strong legacy obesity conflicts (`waist` 8–10) no longer coexist with migrated ab/muscle phrases for the same region;
- `extra_description` does not duplicate the new structured prompt phrases;
- nonstandard replacement lower bodies do not receive ordinary lower-body prompt phrases at runtime.

## Suggested migration implementation skeleton

```python
def migrate_appearance(old, canonical_gender, authored_body_prose=None):
    # Read every old value before modifying the object.
    old_height = old.get("height")
    old_muscular = old.get("muscular")
    old_shoulders = old.get("shoulders")
    old_chest = old.get("chest")
    old_stomach = old.get("stomach")
    old_hips = old.get("hips")
    old_waist = old.get("waist")
    old_legs = old.get("legs")
    old_arms = old.get("arms")
    old_penis = old.get("penis_size")

    # 1. Direct numeric remaps.
    # 2. Canonical-presentation chest remap.
    # 3. Regional build inference using the exact rules above.
    # 4. New-field defaults/explicit prose overrides for arm_length and butt_build.
    # 5. Write all new fields.
    # 6. Validate.
    # 7. Remove legacy keys only after validation succeeds.

    return migrated_appearance
```

The prose above, not this abbreviated skeleton, is authoritative when implementing the converter.

## Final migration-design conclusion

The conversion is now fully specified for every legacy numeric combination:

- direct fields have complete 0–10 → 0–20 lookup tables;
- `midsection_build` has an exhaustive 11×11 old-stomach/old-waist lookup matrix;
- `upper_body_build` and `lower_body_build` have deterministic multi-source algorithms covering every valid numeric legacy combination;
- `butt_build` and `arm_length` have deterministic defaults plus explicit-prose override rules because the old schema never stored those concepts;
- chest migration explicitly resolves the one-shared-number/two-presentation problem by preserving the canonical presentation first;
- custom-string and nonstandard-anatomy cases have explicit handling rules.

Codex should not invent a different rescaling formula.
