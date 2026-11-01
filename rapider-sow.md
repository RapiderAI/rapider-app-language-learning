<!-- Rapider Official App SOW & Specification | App #180: Language Learning (language-learning) | Domain: PRS -->

# #180 Language Learning (`language-learning`) — Scope of Work (SOW)

- **App Number & Name:** `#180` — Language Learning
- **Proposed App Key:** `language-learning`
- **Suite / Domain Key & Model Prefix:** `PER` (`Prs*` — `PrsLang*` family)
- **Representative Product (`P1`):** Duolingo
- **Combined Feature Catalog:** [../combined-features/180-language-learning-features.md](../combined-features/180-language-learning-features.md)
- **Target Release Posture:** Owner-Isolated CEFR Language Path, FSRS Spaced-Repetition Vocabulary, Phoneme Pronunciation Coaching, Leveled Immersion Stories & Grounded AI Roleplay Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Personal Learning Problem Solved
Language learners often bounce between gamified apps that lack clear grammar explanations, dry textbooks that lack daily habit momentum, and rigid flashcard decks disconnected from real speaking confidence—while adult learners using corporate devices never want an employer or HR administrator inspecting their beginner pronunciation stumbles or study habits. **Rapider Language Learning (`language-learning`)** delivers a **strictly owner-isolated (`ownerUserRef == authenticatedActor`)** self-paced language studio uniting **Duolingo**-style bite-sized CEFR skill paths, streaks, and AI Roleplay with **Babbel/Busuu**-grade explicit grammar breakdowns, **Memrise**-grade FSRS spaced-repetition vocabulary mastery, and **Rosetta Stone / Microsoft Reading Coach**-style phoneme pronunciation feedback.

### 1.2 Fast-Path Everyday Flow vs. Serious Polyglot Depth
- **Fast-Path Everyday Flow (Casual Learners, Travelers, Beginners):** Pick a target language (or take a 5-minute adaptive Placement Test), complete a 4-minute daily lesson on the CEFR path, tap *Explain My Answer* on any mistake, and build a timezone-safe daily streak.
- **Progressive Polyglot Depth (Intermediate `B1`–`C1` Learners, Heritage Speakers, Self-Directed Students):** Enable **Calm Mode** (zero leaderboards or heart lockouts), curate custom SRS vocabulary decks on `<rapider-kanban>`, drill mispronounced words with WPM/phoneme scores, practice push-to-talk AI Roleplay scenarios (*Apartment Viewing*, *Pharmacy Visit*), pass CEFR checkpoint exams (`0–160` score), and optionally invite a private human tutor via revocable share grants.

### 1.3 Measurable Outcomes
- **>= 88% 30-Day Vocabulary Retention:** Deterministic FSRS interval scheduling (`PrsLangVocabCard`) targets ~90% recall probability across review intervals.
- **Zero Unfair Timezone Streak Loss:** IANA `timezoneId` + earned Streak Freezes eliminate midnight travel bugs across timezones and DST shifts.
- **100% Personal & Voice Privacy:** Ephemeral default speech processing (`retainVoiceAudio = false`) and server-side `ownerUserRef` ACLs guarantee `0` employer/HR visibility (`403 Forbidden`).

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the CEFR `0–160` path, Streaks, Practice Hub, *Explain My Answer*, and AI *Roleplay* of **`P1` Duolingo**, the source-language-tailored grammar notes and everyday dialogues of **`P2` Babbel**, the CEFR checkpoints and opt-in tutor feedback of **`P3` Busuu**, the dialect-aware phoneme speech engine and Stories of **`P4` Rosetta Stone**, the FSRS spaced-repetition flashcard mastery of **`P5` Memrise**, and the read-aloud fluency WPM and targeted word drills of **`P6` Microsoft Reading Coach**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. Global published CEFR curriculum catalog (`PrsLangCourseUnit`: `PRE_A1` to `C1`, script/kana/tone trainers, unit grammar guidebooks, and leveled interactive stories) paired with strictly owner-isolated learner profiles (`PrsLangLearnerProfile`).
2. Adaptive Placement Test, Unit Jump-Ahead challenges, and multi-modal 3–7 minute lesson runner (`PrsLangLessonSession`) with quiet-mode accessibility toggles (*"Can't listen/speak right now"*).
3. FSRS / SM-2 Spaced Repetition vocabulary cards (`PrsLangVocabCard`), `<rapider-kanban>` vocabulary mastery board, custom personal deck/CSV import, and Practice Hub mistake recovery (`PrsLangMistakeEntry`).
4. Push-to-talk phoneme pronunciation & read-aloud WPM scoring (ephemeral audio by default), *Explain My Answer* grammar rationale, and adaptive AI *Roleplay* conversation sessions (`PrsLangConversationSession`).
5. Timezone-safe Streaks, Streak Freezes, **Calm Mode** (gamification opt-out), CEFR band checkpoint exams (`PrsLangCheckpointAttempt`), opt-in private tutor grants (`PrsLangTutorGrant`), full CSV/JSON/PDF export, and cascade erasure.

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Corporate compliance courses, SCORM/xAPI modules, classroom seat rosters, and employer HR skill matrices:** Owned by `LRN` (`online-learning`, `in-class-learning`, `learning-experience-skills` — `LrnCourse`, `LrnEnrollment`, `LrnSkillDefinition`).
- **Ad-hoc live document/file translation and bilingual utility interpreter sessions:** Owned by Rapider Translate (`_rapider-personal-translate`).
- **Two-sided public tutor marketplace billing, escrow, and live Zoom classroom hosting:** Out of scope (`#180` supports bringing an invited personal tutor via `PrsLangTutorGrant`, not operating a paid tutoring marketplace).

### 2.3 Suite Ownership & Integration Contract Matrix

| Domain / App | Owns | Integration Contract with `language-learning` |
| :--- | :--- | :--- |
| **`PER` (`language-learning`)** | `PrsLangCourseUnit` (global catalog), `PrsLangLearnerProfile`, `PrsLangLessonSession`, `PrsLangVocabCard`, `PrsLangMistakeEntry`, `PrsLangConversationSession`, `PrsLangCheckpointAttempt`, `PrsLangTutorGrant` | Exclusive owner of personal language progression, SRS decks, mistakes, roleplay transcripts, and private CEFR checkpoints under `ownerUserRef`. |
| **`PER` (Rapider Translate)** | Ad-hoc personal text/document translations & saved phrasebook entries | Optional user-triggered one-way import pulling saved personal phrases from Rapider Translate into `PrsLangVocabCard` SRS decks. |
| **`PER` (`resume-and-cv-building`, `#182`)** | Personal resumes & skill sections | Optional explicit user push exporting a passed `PrsLangCheckpointAttempt` (`e.g., German — CEFR B1`) into the user's private `#182` CV profile. |
| **`LRN` (`online-learning` / `HR`)** | `LrnCourse`, `LrnEnrollment`, `LrnCredential` | **Strictly isolated:** Personal `#180` activity NEVER writes to employer `LRN` or `HR` tables. |
| **Platform Files, Channels & Home `WorkItem`s** | Encrypted opt-in audio blobs, `projectChannelMessage` threads & invite notifications | Stores opt-in tutor submission audio; hosts tutor feedback & AI Grammar Coach threads; delivers `PrsLangTutorGrant` Home `WorkItem` invites. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (13 Pages)

Every visible sidebar section strictly enforces the **Minimum 3 Visible Items Rule (`>= 3`)** (`Learn & Path`: 3 items, `Review & Fluency`: 3 items, `Progress & Governance`: 3 items = 9 visible items; 4 hidden detail/runner/drawer views).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `learning-path` | **CEFR Skill Path** | `Learn & Path` | `true` (Order 1) | Active language/dialect switcher, CEFR `A1`–`C1` unit nodes (`findSWR`), daily XP & Streak / Streak Freeze header, *Placement Test* / *Jump Here* buttons, and Unit Grammar Guidebook drawer preview. |
| 2 | `stories-immersion` | **Stories, Script & Listening** | `Learn & Path` | `true` (Order 2) | Leveled CEFR short stories & native-speaker dialogues (`0.75x`–`1.25x` audio, tap-word dictionary -> *Add to SRS*), plus Script/Tone trainer tab for non-Latin languages and `#activeFilterTagsBar` with `[Clear all]`. |
| 3 | `ai-roleplay` | **AI Roleplay & Speaking** | `Learn & Path` | `true` (Order 3) | Scenario gallery (*Café Order*, *Train Ticket*, *Job Interview*, *Doctor Visit*) calibrated by CEFR band, push-to-talk / text conversation launcher, and past `PrsLangConversationSession` history table (`findSWR`) with `#activeFilterTagsBar`. |
| 4 | `vocabulary-srs` | **Vocabulary & SRS Kanban** | `Review & Fluency` | `true` (Order 1) | Due-today FSRS review counter + switchable `<rapider-kanban>` mastery board (`NEW` -> `LEARNING` -> `REVIEW_DUE` -> `MASTERED` -> `SUSPENDED`) and searchable lexeme table, `#activeFilterTagsBar`, clickable Term -> `vocab-card-detail`, icon+text `Edit`, and icon-only `Delete`. |
| 5 | `practice-mistakes` | **Practice Hub & Mistakes** | `Review & Fluency` | `true` (Order 2) | Categorized `PrsLangMistakeEntry` error ledger (`VERB_TENSE`, `GRAMMAR_AGREEMENT`, `PRONUNCIATION`, etc.), `#activeFilterTagsBar`, *Explain My Answer* rationale cards, and 1-click **Clear 10 Mistakes** drill launcher. |
| 6 | `pronunciation-lab` | **Pronunciation & Reading Lab** | `Review & Fluency` | `true` (Order 3) | Read-aloud fluency passages & tricky-phoneme word list with push-to-talk accuracy % (`Decimal128`), WPM score, and 3-rep mispronounced word micro-drills. |
| 7 | `checkpoints-scores` | **CEFR Checkpoints & Score** | `Progress & Governance` | `true` (Order 1) | `0–160` composite proficiency gauge (Reading / Listening / Writing / Speaking radar), `PrsLangCheckpointAttempt` exam launcher & history, and 1-click *Export CEFR Badge to Resume (`#182`)*. |
| 8 | `streaks-analytics` | **Streaks, Goals & Calm Mode** | `Progress & Governance` | `true` (Order 2) | Timezone-aware streak calendar, Streak Freeze inventory, study minutes by skill modality across light/dark themes, daily goal selector, and **Calm Mode** (hide leaderboards/timers/hearts) toggle. |
| 9 | `tutor-and-privacy` | **Tutor Sharing & Privacy** | `Progress & Governance` | `true` (Order 3) | Ephemeral voice audio privacy switch (`retainVoiceAudio = false` default), active `PrsLangTutorGrant` permissions, TSV/Anki/Translate deck import, CSV/JSON/PDF export, and cascade vault erasure. |
| 10 | `lesson-runner` | **Interactive Lesson & Checkpoint Runner** | *(Hidden)* | `false` | Distraction-free session view (`#/lesson-runner?unitId=...`) with multi-modal exercises, quiet-commute *Can't speak/listen* skip buttons, inline *Explain My Answer* drawer, pause-aware timer, and `Back to path` state restoration. |
| 11 | `vocab-card-detail` | **Lexeme & SRS History Detail** | *(Hidden)* | `false` | Detailed word/phrase inspector (`#/vocab-card-detail?id=...`) showing example sentences, audio, FSRS stability/difficulty (`Decimal128`), next review date, grammar notes, and `Back to list` state restoration. |
| 12 | `new-vocab-drawer` | **Add Custom Card / Import Deck Drawer** | *(Hidden)* | `false` | Sliding drawer to create/edit custom `PrsLangVocabCard` entries or stage TSV/Rapider Translate imports; resets button in `finally` and auto-closes via `closePageDrawer()`. |
| 13 | `tutor-share-drawer` | **Invite Personal Tutor Drawer** | *(Hidden)* | `false` | Sliding drawer to grant a personal tutor (`PrsLangTutorGrant`, optional E.164 lookup via `<rapider-phone-input>` or email) scoped review access to selected writing/speaking submissions via Home `WorkItem`; calls `closePageDrawer()`. |

---

## 4. Canonical Data Models (`PrsLang*` — 8 Models)

All models omit `projectId`, enforce `ownerUserRef` isolation on personal data (`GLOBAL_PUBLISHED` read-only on `PrsLangCourseUnit`), use platform UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in seeds), store scores/SRS parameters as `Decimal128`, and track optimistic `version`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`PrsLangCourseUnit`** | `id` (UUID), `sourceLanguageCode` (BCP-47, e.g., `en`), `targetLanguageCode` (BCP-47, e.g., `es-MX`, `ja-JP`), `cefrBand` (`PRE_A1` \| `A1` \| `A2` \| `B1` \| `B2` \| `C1`), `unitOrder` (Int), `title` (String), `communicativeGoal` (String), `grammarGuideMarkdown` (String), `lessonBlueprintsJson` (Object[]), `storyPassagesJson` (Object[]), `publishStatus` (`DRAFT` \| `GLOBAL_PUBLISHED` \| `RETIRED`), `version` (Int) | Global curriculum catalog read by `PrsLangLessonSession` | Contains zero user PII; curriculum editors manage `GLOBAL_PUBLISHED` units with zero access to personal `PrsLang*` learner collections. |
| **`PrsLangLearnerProfile`** | `id` (UUID), `ownerUserRef` (UUID), `activeTargetLanguage` (BCP-47), `sourceLanguage` (BCP-47), `currentCefrBand` (String), `proficiencyScore160` (`Decimal128`, `0.00`–`160.00`), `dailyGoalMinutes` (Int), `timezoneId` (IANA String), `currentStreakDays` (Int), `longestStreakDays` (Int), `lastStudyLocalDate` (LocalDate?), `streakFreezesAvailable` (Int), `calmModeEnabled` (Boolean, default `false`), `retainVoiceAudio` (Boolean, default `false`), `version` (Int) | 1:N per `(ownerUserRef, activeTargetLanguage)` | Streak evaluation strictly uses `LocalDate` in `timezoneId`; `retainVoiceAudio` defaults to `false` (ephemeral speech scoring). |
| **`PrsLangLessonSession`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `unitId` (UUID?), `sessionType` (`PATH_LESSON` \| `SRS_REVIEW` \| `MISTAKE_DRILL` \| `STORY` \| `PRONUNCIATION`), `startedAt` (DateTime), `completedAt` (DateTime?), `activeDurationSeconds` (Int), `accuracyPercent` (`Decimal128`), `xpEarned` (Int), `wordsPerMinute` (`Decimal128`?), `status` (`IN_PROGRESS` \| `COMPLETED` \| `ABANDONED`), `version` (Int) | Belongs to `PrsLangLearnerProfile`; updates `PrsLangVocabCard` & `PrsLangMistakeEntry` | `COMPLETED` sessions become immutable progress ledger entries and idempotently credit daily streak/XP once per `idempotencyKey`. |
| **`PrsLangVocabCard`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `targetTerm` (String), `romanization` (String?), `translation` (String), `exampleSentence` (String?), `partOfSpeech` (String?), `deckTag` (String), `masteryStage` (`NEW` \| `LEARNING` \| `REVIEW_DUE` \| `MASTERED` \| `SUSPENDED`), `fsrsStability` (`Decimal128`), `fsrsDifficulty` (`Decimal128`), `reviewCount` (Int), `lapseCount` (Int), `nextReviewAt` (DateTime), `isCustomUserCard` (Boolean), `version` (Int) | Belongs to `PrsLangLearnerProfile` | Unique `(profileId, targetTerm, translation)` prevents duplicate deck clutter; rating (`Again`/`Hard`/`Good`/`Easy`) deterministically updates `fsrsStability`, `fsrsDifficulty`, `masteryStage`, and `nextReviewAt`. |
| **`PrsLangMistakeEntry`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `unitId` (UUID?), `errorCategory` (`GRAMMAR_AGREEMENT` \| `VERB_TENSE` \| `WORD_ORDER` \| `LISTENING` \| `SPELLING` \| `PRONUNCIATION`), `promptText` (String), `learnerAnswer` (String), `expectedAnswer` (String), `aiGrammarExplanation` (String?), `occurrenceCount` (Int), `resolutionState` (`OPEN` \| `CLEARED`), `version` (Int) | Populated by `PrsLangLessonSession`; cleared via `practice-mistakes` | Answering correctly twice in a mistake-clearing session flips `resolutionState = CLEARED`. |
| **`PrsLangConversationSession`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `scenarioKey` (String), `cefrBand` (String), `modality` (`TEXT` \| `PUSH_TO_TALK_VOICE`), `turnsJson` (Embedded `{speaker, text, upgradedPhrasing?, phonemeAccuracy?}`[]), `voiceFileRef` (Platform File UUID?, only if `retainVoiceAudio == true`), `channelThreadRef` (UUID?), `completedAt` (DateTime?), `version` (Int) | Optional tutor review via `PrsLangTutorGrant` + `projectChannelMessage` | Never retains raw audio when `retainVoiceAudio == false`; learner can extract any upgraded phrase directly into `PrsLangVocabCard`. |
| **`PrsLangCheckpointAttempt`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `examType` (`PLACEMENT_TEST` \| `UNIT_CHALLENGE` \| `CEFR_BAND_CHECKPOINT`), `targetCefrBand` (`A1` \| `A2` \| `B1` \| `B2` \| `C1`), `readingScore` (`Decimal128`), `listeningScore` (`Decimal128`), `writingScore` (`Decimal128`), `speakingScore` (`Decimal128`), `compositeScore160` (`Decimal128`), `passed` (Boolean), `completedAt` (DateTime), `version` (Int) | Optional user-pushed badge to `#182` (`resume-and-cv-building`) | Append-only immutable score record once `completedAt` is stamped; private until explicitly exported by owner. |
| **`PrsLangTutorGrant`** | `id` (UUID), `ownerUserRef` (UUID), `profileId` (UUID), `tutorUserRef` (UUID), `tutorPhoneE164` (String?), `sharedSessionIds` (UUID[]), `grantStatus` (`PENDING` \| `ACTIVE` \| `REVOKED`), `workItemRef` (UUID?), `revokedAt` (DateTime?), `version` (Int) | Scopes tutor read/comment access to `sharedSessionIds` only | Tutor can view ONLY explicitly shared `PrsLangConversationSession` / `PrsLangCheckpointAttempt` IDs—zero access to full profile unless granted; instant `403` upon revocation. |

---

## 5. Core End-to-End User Journeys

### 5.1 Adaptive Placement, Bite-Sized Lesson & "Explain My Answer" (`learning-path` -> `lesson-runner` -> `practice-mistakes`)
1. Enrolling in *Spanish (es-MX)* on `#/learning-path`, the learner takes the 5-minute **Placement Test**, scoring `54.00 / 160.00` (`CEFR A2`) and unlocking Units `1–12` automatically.
2. Launching Unit 13 opens `#/lesson-runner?unitId=...`. When the learner types *"Viajé por Madrid para dos semanas"* instead of *"durante / por dos semanas"*, the runner logs a `GRAMMAR_AGREEMENT` `PrsLangMistakeEntry` and offers **Explain My Answer**, rendering a concise `por` vs. `para` duration breakdown grounded in the Unit 13 guidebook.
3. Finishing the lesson credits XP, increments `currentStreakDays` in `America/Chicago`, and updates `#/practice-mistakes` optimistically.

### 5.2 FSRS Vocabulary Review & `<rapider-kanban>` Deck Curation (`vocabulary-srs` -> `vocab-card-detail` -> `vocabulary-srs`)
1. On `#/vocabulary-srs`, `#activeFilterTagsBar` filters by `Stage: "REVIEW_DUE"` (`Stage: "REVIEW_DUE" ✕ [Clear all]`), synchronously filtering both the lexeme table and `<rapider-kanban>` board.
2. Reviewing 12 due flashcards (`Good` / `Again`) updates `fsrsStability`, `fsrsDifficulty` (`Decimal128`), and moves mastered cards into `MASTERED` optimistically.
3. Clicking `"madrugada"` navigates cleanly to `#/vocab-card-detail?id=...` (verified free of `<base href>` 404 diversion) to inspect example sentences and FSRS interval history; clicking `Back to list` restores `#/vocabulary-srs` with `Stage: "REVIEW_DUE"` active.

### 5.3 Ephemeral Pronunciation Drill & Push-to-Talk AI Roleplay (`pronunciation-lab` & `ai-roleplay`)
1. In `#/pronunciation-lab`, the learner reads a `B1` dialogue aloud using push-to-talk. Speech is scored ephemerally in memory (`accuracyPercent = 89.50`, `wordsPerMinute = 112.00`, `0` audio files persisted because `retainVoiceAudio == false`), isolating 2 mispronounced words into an instant 3-rep micro-drill.
2. In `#/ai-roleplay`, the learner completes *Rescheduling a Train Ticket*, reviews inline phrasing upgrades in the post-call transcript, and saves 3 new idioms into `PrsLangVocabCard` in one click.

### 5.4 Calm Mode, Timezone Travel Streak Safety & Tutor Feedback (`streaks-analytics` & `tutor-share-drawer`)
1. Toggling **Calm Mode** on `#/streaks-analytics` hides competitive leaderboards, timers, and heart penalties immediately. Flying from New York to Tokyo updates `timezoneId = Asia/Tokyo` while preserving the learner's 145-day streak without false midnight gaps (using a Streak Freeze only when a full local calendar day is missed).
2. Via `tutor-share-drawer` (with `<rapider-phone-input>` lookup), the learner shares one `B1` writing/roleplay transcript with an invited tutor, dispatching a Rapider Home `WorkItem` and auto-closing via `closePageDrawer()`.

### 5.5 CEFR B2 Checkpoint & Optional Export to `#182 Resume & CV Building` (`checkpoints-scores` -> `#182`)
1. Passing the **CEFR B2 Checkpoint** (`compositeScore160 = 124.50`) stamps an immutable `PrsLangCheckpointAttempt`. Clicking **Add Verified Language Score to My Resume (`#182`)** pushes `Spanish (CEFR B2)` into the user's private `#182` CV profile—never exposing anything to corporate `HR`.

---

## 6. Consolidated Feature Priorities & Work Packages (`P0`, `P1`, `P2`)

### `P0` Foundation Work Packages
- **WP-P0-1 — Owner-Isolated Profile, CEFR Curriculum & Lesson Runner (`PLL-001`–`PLL-005`, `PLL-014`):** Implement `ownerUserRef` server guard (`403` to workspace/HR admins), `PrsLangCourseUnit`, `PrsLangLearnerProfile`, adaptive Placement Test, multi-modal `lesson-runner` with quiet-commute skips, and timezone-safe Streaks + Streak Freezes (`learning-path`, `streaks-analytics`).
- **WP-P0-2 — FSRS Spaced Repetition, `<rapider-kanban>` Mastery & Mistake Hub (`PLL-007`–`PLL-009`):** Deliver deterministic FSRS `PrsLangVocabCard` scheduling, `<rapider-kanban>` `vocabulary-srs`, `vocab-card-detail`, `new-vocab-drawer`, and `PrsLangMistakeEntry` (`practice-mistakes`).
- **WP-P0-3 — Ephemeral Pronunciation Coaching & Data Portability (`PLL-011`, `PLL-017`):** Deliver push-to-talk phoneme/WPM scoring (`pronunciation-lab`), CSV/JSON/PDF study export, and cascade erasure (`tutor-and-privacy`).

### `P1` Immersion, Checkpoints & Tutor Collaboration Work Packages
- **WP-P1-1 — Script Trainer, Leveled Stories, Custom Decks & Explain My Answer (`PLL-006`, `PLL-010`, `PLL-012`, `PLL-019`):** Build non-Latin script/tone drills, leveled interactive `stories-immersion` with tap-word SRS save, TSV/Anki/Rapider Translate deck import, and grounded *Explain My Answer* grammar rationale.
- **WP-P1-2 — CEFR Checkpoints, Calm Mode & Scoped Tutor Grants (`PLL-013`, `PLL-015`, `PLL-016`):** Deliver `PrsLangCheckpointAttempt` (`checkpoints-scores`), **Calm Mode** gamification opt-out, and `PrsLangTutorGrant` via Home `WorkItem`s (`tutor-share-drawer`) + `projectChannelMessage` feedback threads.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1 — Adaptive AI Roleplay, SRS Story Generation & Intra-Personal Links (`PLL-018`, `PLL-020`–`PLL-024`):** Deliver CEFR-calibrated text/voice `ai-roleplay` (`PrsLangConversationSession`), ephemeral voice guard (`retainVoiceAudio = false`), due-vocab story generation, AI error-pattern micro-drill proposals, `#182` CV score push, and `#177` daily study habit linking.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Personal Learner (Owner)** | Full CRUD on own `PrsLangLearnerProfile`, lesson/checkpoint sessions, custom `PrsLangVocabCard` decks, Calm Mode, `retainVoiceAudio` consent, tutor grants, `#182` badge export, data export, and vault erasure. | Read-only on `GLOBAL_PUBLISHED` `PrsLangCourseUnit` curriculum modules; cannot mutate locked `COMPLETED` checkpoint scores. |
| **Invited Personal Tutor (`Grantee`)** | View and comment (`projectChannelMessage`) strictly on the explicit `sharedSessionIds` listed in an `ACTIVE` `PrsLangTutorGrant`. | **Zero access (`403`)** to unshared sessions, full mistake logs, other target languages, or personal profile settings; access ends immediately on grant revocation. |
| **Curriculum Author / Editor** | Author, audio-verify, caption, and publish `GLOBAL_PUBLISHED` `PrsLangCourseUnit` lessons and stories. | **Zero access (`403`)** to any learner's `PrsLangLearnerProfile`, `PrsLangVocabCard`, `PrsLangMistakeEntry`, or `PrsLangConversationSession` records. |
| **Workspace / Employer / Corporate `LRN` Admin** | Enable/disable app availability in workspace catalog and monitor anonymous service uptime. | **STRICTLY BLOCKED (`403 Forbidden`)** from viewing, listing, ranking, or exporting any user's personal language learning progress, scores, streaks, or audio (`PLL-001`). |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every command resolves `ownerUserRef` from authenticated JWT claims and requires `idempotencyKey`, `correlationId`, and `expectedVersion`:
- `per.lang.completeLessonSession` — Records `PrsLangLessonSession`, logs missed items in `PrsLangMistakeEntry`, seeds new `PrsLangVocabCard`s, and updates daily streak/XP in `timezoneId` idempotently.
- `per.lang.reviewVocabCardBatch` — Applies deterministic FSRS `Decimal128` stability/difficulty math for `Again`/`Hard`/`Good`/`Easy` ratings and advances `nextReviewAt` & `masteryStage`.
- `per.lang.submitCheckpointAttempt` — Scores Reading/Listening/Writing/Speaking sections (`Decimal128`), updates `proficiencyScore160` / `currentCefrBand`, and locks the immutable `PrsLangCheckpointAttempt`.
- `per.lang.grantOrRevokeTutorAccess` — Issues `PrsLangTutorGrant` + tutor Home `WorkItem`, or immediately revokes tutor read/comment access (`403`).
- `per.lang.exportOrEraseLearningVault` — Exports CSV/JSON/PDF archives to private Platform Files or executes cascade erasure of all `PrsLang*` records and opt-in audio files.

### 8.2 Domain Events Published & Consumed (Kafka)
- **Published:** `per.lang.lesson.completed.v1`, `per.lang.checkpoint.passed.v1`, `per.lang.streak.updated.v1`, `per.lang.tutor.grantChanged.v1`, `per.lang.vault.erased.v1` (opaque IDs only—zero language choices, mistakes, or audio transcripts).
- **Consumed:** `platform.file.malware_scan_completed.v1` (validates TSV/Anki deck imports and opt-in tutor audio clips).

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `personalLanguageStreakAndFreezeRolloverWorkflow` — Evaluates daily study completion at local midnight per learner's IANA `timezoneId` and consumes a `streakFreezesAvailable` token before resetting streaks.
2. `personalLanguageDeckImportAndExportWorkflow` — Parses TSV/CSV/Anki/Rapider Translate phrase imports with deduplication and packages portable CSV/JSON/PDF exports.
3. `personalLanguageAiRoleplayAndGrammarWorkflow` — Executes CEFR-calibrated Roleplay turns, ephemeral phoneme pronunciation scoring, and curriculum-grounded *Explain My Answer* notes.
4. `personalLanguageVaultErasureWorkflow` — Revokes tutor grants, deletes opt-in Platform File audio clips, and purges all personal `PrsLang*` documents.

### 8.4 Grounded Rapider AI Rules
- *Explain My Answer* (`PLL-019`) MUST ground grammar explanations in canonical `PrsLangCourseUnit.grammarGuideMarkdown` rules and dictionary metadata—never inventing fake conjugation paradigms.
- Speech scoring and AI Roleplay (`PLL-011`, `PLL-020`, `PLL-024`) process learner voice streams ephemerally (`retainVoiceAudio == false` default), never train global speech/LLM models on personal learner audio, and stage suggested micro-drills or SRS cards for explicit learner confirmation.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Voice & Educational Privacy (GDPR / CCPA / Workplace Non-Surveillance):** Voice pronunciation samples are treated as sensitive personal data—processed ephemerally in RAM by default and persisted to encrypted Platform Files only when the learner explicitly enables `retainVoiceAudio = true`. Whether on a `\$0.00` free personal tier or `\$7.99`/month Max-style personal plan, employer/HR admins receive `403 Forbidden` on all `PrsLang*` learner data.
- **Accessibility & Quiet-Commute Inclusivity (WCAG 2.2 AA):** Learners with hearing or speech disabilities—or learners on quiet public transit—can toggle *Skip Listening / Speaking* for `100%` curriculum progression parity without streak or score penalties. Full keyboard navigation, captions on all audio/stories, ARIA labels on icon-only Delete buttons, and `#ffffff !important` button contrast in light/dark themes across `390px`, `768px`, and `1440px` viewports.

---

## 10. Deterministic Acceptance Criteria

1. **Owner-Only & Corporate `LRN` Isolation (`403 Forbidden`):** Queries by a Workspace Administrator, HR Manager, or `LRN` Administrator against another user's `PrsLangLearnerProfile`, `PrsLangVocabCard`, or `PrsLangConversationSession` return `403 Forbidden` / `0` records, and lesson completions create zero `LrnEnrollment` records.
2. **Sidebar 3-Item Section Rule:** `app.manifest.json` defines 3 visible sidebar sections (`Learn & Path`, `Review & Fluency`, `Progress & Governance`), each containing 3 visible menu items (`displayOnMenu: true`), while all 4 runner/detail/drawer pages set `displayOnMenu: false`.
3. **SWR & Clean Query Compliance:** All initial page loads call `findSWR` / `countSWR` with zero manual `isDeleted` filter clauses in API payloads and filter `item.isDeleted !== true` in memory.
4. **Deterministic FSRS `Decimal128` Scheduling:** Rating a `REVIEW_DUE` `PrsLangVocabCard` as `Good` vs. `Again` deterministically updates `fsrsStability`, `fsrsDifficulty` (`Decimal128`), `masteryStage`, and `nextReviewAt`, synchronously updating `<rapider-kanban>` on `vocabulary-srs`.
5. **Timezone-Safe Streak & Streak Freeze Protection:** Missing one calendar day in `timezoneId` when `streakFreezesAvailable >= 1` decrements `streakFreezesAvailable` by `1` and preserves `currentStreakDays` intact.
6. **Ephemeral Default Voice Privacy:** Completing a speaking exercise or voice Roleplay with `retainVoiceAudio == false` (default) writes `voiceFileRef = null` and stores zero audio blobs in Platform Files.
7. **Quiet-Mode Accessibility Parity:** Clicking *"Can't speak right now"* or *"Can't listen right now"* inside `lesson-runner` substitutes non-audio/non-mic items cleanly so the lesson still completes with `100%` streak credit.
8. **Calm Mode Toggle:** Enabling `calmModeEnabled = true` on `streaks-analytics` immediately hides countdown timers, heart lockouts, and competitive leaderboards across all learner surfaces.
9. **Active Filter Tags, Table Standard & Custom Elements:** Entering search/filter criteria on `vocabulary-srs`, `practice-mistakes`, `stories-immersion`, or `ai-roleplay` displays HTML-escaped chips in `#activeFilterTagsBar` with `[Clear all]`; tables omit standalone "View" buttons, render icon+text `Edit` and icon-only `Delete` (`#rapiderConfirmOkBtn`, zero `alert`/`confirm`/`prompt`), `vocabulary-srs` uses `<rapider-kanban>`, and `tutor-share-drawer` uses `<rapider-phone-input>` and closes via `closePageDrawer()`.
10. **Scoped Tutor Grant & Instant Revocation:** A tutor granted access to `sessionId = X` receives `403 Forbidden` when requesting `sessionId = Y`, and revoking `PrsLangTutorGrant` immediately blocks access to `sessionId = X`.
11. **Click-Through Navigation & Base-URL Guard:** Clicking a vocabulary term or unit node transitions to `#/vocab-card-detail?id=...` or `#/lesson-runner?unitId=...` without `<base href>` 404 diversion, and `Back to list` restores prior filter chips.
12. **No `projectId` Leakage & Theme Contrast:** Zero `PrsLang*` schemas or API payloads contain `projectId`, and all 13 pages pass `validate_theme` across light and dark modes with `#ffffff !important` primary/danger button text.
