# NEXUS: Autonomous Viral Content Engine for Qoneqt
**CTRL FREAK 2026 | Qoneqt AI Challenge | Finale: 4 Oct 2026, 8 hours, York·IE Ahmedabad**

---

## 1. One-Line Pitch
> Every team builds *topic → LLM → video*. NEXUS builds a pipeline that **judges its own video, scores it 0-100, and automatically regenerates until it is good enough to publish.**

Not a video generator. **A quality-controlled content factory for the Qoneqt Global Feed.**

---

## 2. Why This Wins
| What the challenge says | What NEXUS does |
|---|---|
| "Not a single generation, a **repeatable pipeline**" | Batch mode: many topics in, many scored videos out |
| "Publish-ready content **at scale**" | Auto quality gate removes the human reviewer |
| "We judge what you **build and ship**" | Working loop, live demo, real publish |
| Must have: public GitHub, live deployment, demo video, one video on Qoneqt feed | All four planned (see section 9) |

**The differentiator judges will remember:** a live visible score, e.g. *Attempt 1: 64, Attempt 2: 71, Attempt 3: 86, Published.*

---

## 3. The Pipeline

```
Topic / Prompt / Trend
        ↓
[1] Script Agent      → Hook + Script + Scene Plan (LLM, JSON output)
        ↓
[2] Critic Agent      → Scores SCRIPT 0-100 (cheap, fast check)
        ↓ (below 80? rewrite with critic feedback)
[3] Media Agents      → Images/clips + Voice (TTS) + Captions
        ↓
[4] Composer          → FFmpeg: 9:16 video, subtitles, music, timing
        ↓
[5] Video Critic      → Scores FINAL video 0-100
        ↓
   Score ≥ 80 ?
     YES → Publish-ready MP4 → Qoneqt Global Feed
     NO  → Feedback goes back to step 1 or 3 → retry (max 3 attempts)
```

**Key rule:** the critic's *written feedback* is fed into the next attempt ("hook is generic, use a question or surprising number"), so each retry is targeted, not random.

---

## 4. Scoring Rubric (Total 100)

| Dimension | Weight | What is checked |
|---|---|---|
| Hook strength | 30 | First 3 seconds create curiosity or a strong claim |
| Clarity | 25 | One clear idea, easy to follow, no jargon dumps |
| Pacing | 20 | Scene length 2-5 sec, total duration on target |
| Visual variety | 15 | No repeated visuals, image matches narration |
| Technical QA | 10 | Audio present, captions synced, 9:16, no broken assets |

**Threshold:** 80 to publish. **Max retries:** 3. If still below 80, publish the best attempt and flag it "needs human review."

**Be honest in the pitch:** the score is an LLM-as-judge plus rule-based technical checks. Say so. Judges respect it; overclaiming loses trust. Add real rule checks (duration, caption coverage, resolution, loudness) so the score is not only "AI opinion."

---

## 5. Key Features (Only 5, as the PPT guide asks)
1. **Prompt → Script → Scene Plan:** structured JSON, not free text.
2. **Self-Evaluating Quality Loop (killer feature):** score, feedback, auto-retry.
3. **Multimodal Generation:** visuals, TTS voice, auto captions.
4. **Automated Video Assembly:** FFmpeg composer, vertical format, timed subtitles.
5. **Batch + Publish Mode:** queue of topics, one-click "Publish to Qoneqt", dashboard of all runs with scores.

**Stretch (only if time remains):** multilingual output (English + Hindi), source cards for factual videos, 2 style variants scored against each other.

---

## 6. Architecture + Tech Stack

| Layer | Choice |
|---|---|
| Frontend | React or Next.js (dashboard, live progress, score chart) |
| Backend | Python + FastAPI |
| Orchestration | Simple async state machine (avoid heavy frameworks, easier to debug in 8 hrs) |
| LLM | Claude / Gemini / GPT via API (JSON mode) for script + critic |
| Visuals | Image-generation API, or stock/AI clips as fallback |
| Voice | ElevenLabs or Google TTS |
| Captions | Whisper or timestamps from TTS |
| Video | FFmpeg / MoviePy |
| Storage | Local + cloud bucket (S3 / Supabase) |
| DB | SQLite / Postgres (runs, attempts, scores) |
| Deploy | Render / Railway / Vercel + a small server for FFmpeg |

**Tip:** put every model call behind an interface so any provider can be swapped or a fallback used if one fails or rate-limits.

---

## 7. Demo Script (3 minutes, memorize this)
1. **(20s)** State the problem: AI video is easy, *consistent quality at scale* is not.
2. **(30s)** Enter topic live, e.g. "5 AI tools every student should know."
3. **(60s)** Show dashboard: script generated, **score 62**, feedback shown, retry, **score 79**, retry, **score 87**, approved.
4. **(30s)** Play the final video, then hit **Publish to Qoneqt**.
5. **(30s)** Show batch mode: 5 topics queued, score table, average score improvement across attempts.
6. **Close:** "We didn't build a generator. We built the quality control Qoneqt needs to publish AI content at scale."

**Pre-generate one backup video** in case Wi-Fi or an API fails on stage.

---

## 8. PPT Outline (Round 2: 6 slides, dark background, purple accent)
1. **Title:** NEXUS, tagline, team name/ID, college.
2. **Problem + Gap:** AI video tools produce one-off, unchecked content; no quality control, so quality at scale is unsolved.
3. **Solution:** one prompt in, self-scored publish-ready video out; show the score-retry loop diagram.
4. **Architecture + Tech Stack:** the pipeline diagram from section 3 plus the stack table.
5. **Key Features:** the 5 features above, killer feature highlighted.
6. **Impact + Feasibility:** creators save hours; Qoneqt gets scalable, consistent feed content; low cost per video; modular and deployable. End with the implementation plan.

**Rules for the deck:** big headline, one diagram, very few words. Do **not** claim a live demo or deployed app if it does not exist yet. Present it as a proposed solution and plan.

**Deadline: PPT submission closes Sep 30, 11:59 AM.**

---

## 9. Execution Plan

### Before the finale (Sep 28 to Oct 3)
- Finalize team and PPT, submit by Sep 30.
- Get API keys and test each service (LLM, image, TTS) end to end.
- Prototype the score-and-retry loop on scripts only (fastest proof of concept).
- Prepare the FFmpeg composer as a standalone script.
- **Check the rules with organizers:** confirm whether pre-written code is allowed, since it is an 8-hour build. If not allowed, prepare designs, prompts, rubric, and test assets only. Never hide pre-built work.

### 8-hour finale timeline
| Time | Goal |
|---|---|
| 0:00-0:45 | Setup, repo, backend skeleton, confirm APIs |
| 0:45-2:30 | Script agent + critic agent + retry loop working |
| 2:30-4:30 | Visuals + voice + captions + FFmpeg composer |
| 4:30-5:30 | Video critic + full loop end to end |
| 5:30-6:30 | Frontend dashboard + deploy |
| 6:30-7:15 | Generate final videos, **publish to Qoneqt feed**, record demo video |
| 7:15-8:00 | README, polish, rehearse pitch |

**Golden rule:** get an ugly end-to-end version working by hour 5. Polish after, never before.

### Required deliverables checklist
- [ ] Public GitHub repo with clear README
- [ ] Live deployment link
- [ ] Demo video
- [ ] At least one generated video published on the Qoneqt Global Feed
- [ ] Working AI pipeline shown live

---

## 10. Risks and Fixes
| Risk | Fix |
|---|---|
| Video model too slow or costly | Use image + Ken Burns motion + voice + captions via FFmpeg; reserve AI video clips for the hook only |
| API rate limits or failure | Fallback providers, cached backup assets |
| Critic always gives high scores | Strict rubric, JSON-only output, calibrate on a few known bad and good examples |
| Infinite retry loop | Max 3 attempts, keep best result |
| Publishing to Qoneqt has no API | Ask Qoneqt team for the method early; otherwise manual upload of the final MP4 is fine, since the brief only requires publication |
| Running out of time | Cut stretch features, never cut the score loop or the publish step |

---

## 11. Closing Line for the Judges
> "NEXUS doesn't just generate content. It decides whether the content is good enough to publish, and fixes it when it isn't."

**Reality check:** no idea guarantees a win. Judges reward what works live. A simple pipeline with a real, visible self-improvement loop beats an ambitious one that half-works.
