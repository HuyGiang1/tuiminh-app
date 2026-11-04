# 02 — Design system / interaction / motion

## Creative direction: "interactive storybook"
Not a static pink dashboard and not a web landing page wrapped in WebView. Build a **native Flutter app** whose home screen feels like a long-form illustrated landing experience with sections; other routes stay clean, task-focused and fast.

## Primary navigation (5 tabs)
1. Home / Nhà mình: interactive mascot hero, relationship count, next anniversary, quick send-heart, today timeline teaser.
2. Moments / Kỷ niệm: photo timeline, date filters, capture/upload, recap carousel.
3. Plans / Hẹn hò: calendar, plans, wish list, preparation checklist.
4. Funds / Quỹ chung: goals and ledger, funding progress (not bank payments).
5. Us / Hai đứa: profiles, preferences, privacy, export/delete, themes.

## Key flows
Solo onboarding -> couple invite -> joined confirmation -> relationship date -> Home.
Home -> upload photo -> confirm preview -> upload progress -> timeline event -> partner receives notification.
Plans -> new plan -> choose date/activities/budget -> invite partner to edit -> saved event.
Moments -> weekly recap -> see eligible photos -> exclusions/template -> render -> preview/share or save.

## Visual tokens — initial starting point only
| Token | Value | Use |
|---|---|---|
| canvas | #FFF9F8 | warm background |
| card | #FFFFFF | surfaces |
| rose | #F16E9A | primary accent, CTA |
| blush | #FFDBE6 | highlights |
| berry | #54354B | main text |
| muted | #7D6977 | secondary text |
| lilac | #E8DDF9 | plan cards |
| sunny | #FFE5A8 | milestones |
| success | #35765A | completed state |

Text font **Be Vietnam Pro**; display font **Quicksand** (verify glyph coverage in real Vietnamese copy). 8pt spacing system with half steps (4/8/12/16/24/32). Cards 16–24 radius, buttons 14–18; respect iOS dynamic type and Android text scaling. Verify AA contrast on all critical text, avoid white text on light rose without a darker tone. Reusable shadows and gradients should be subtle.

## Mascot / illustration system
- Two original customizable characters: Mây and Nắng (temporary), or abstract bunny/bear pair. Do NOT imitate copyrighted characters.
- Rive state machines: idle, tap reaction, reunited, countdown celebration, happy upload, empty photo gallery.
- Simple confetti/hearts: Lottie, assets with verifiable redistribution rights or originals.
- Page/card transitions: Flutter implicit animations or explicit AnimationController, Hero shared element where helpful.
- Static PNG/SVG fallback when reduced-motion accessibility setting is on.
- Only one attention-grabbing looping animation in the active viewport; pause off-screen animation, keep 60fps goal.

## Page composition
Home scrolls in sections like a landing page:
- Immersive hero with two-person illustration and day count.
- "Ngày đáng nhớ" upcoming anniversary countdown.
- "Hôm nay mình làm gì?" plan CTA.
- "Bức ảnh mới nhất" timeline teaser.
- "Chuyện tuần này" recap preview.
But **navigation is app screens and components**, not separate website landings. Do not use large web hero sections everywhere, and avoid heavy motion in forms and finance pages.

## Figma workflow
1. `00 Moodboard`: references, adjectives and Do/Don't examples.
2. `01 Foundations`: tokens, typography, iconography, asset usage.
3. `02 Components`: buttons, sheets, tab bars, cards, mascots, empty states, loaders.
4. `03 Flows`: user journeys and wireframes.
5. `04 High Fidelity`: iOS and Android frames, adaptive layouts, dark mode optional.
6. `05 Prototype`: tap interactions and end-to-end flows.
7. `06 Developer Handoff`: annotated states, spacing, exported icons and animation mapping.

Use named component variants, Auto Layout, variables and consistent layer names. Figma is source of visual truth; exported Flutter widget code from third-party tools is a starter, not production architecture. Rive editor is source of mascot interactive state machines. End every UI task with before/after screenshots for review and requested exact edits ("increase card height", "reduce hearts", etc.).

## Design QA
Inspect on small Android device, modern iPhone, large text, reduced motion, airplane mode, long Vietnamese names, empty states, validation errors, dark backgrounds (if supported), low network speed, voiceover/screen reader.
