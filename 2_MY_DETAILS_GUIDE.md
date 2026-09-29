# NEXUS: My Personal Guide (Not for Gamma)

## 1. Before Submitting the PPT (Deadline: Sep 30, 11:59 AM)
- [ ] Fill Team Name, Team ID, College in Slide 1
- [ ] Confirm exactly 6 slides (Slide 7 is optional and we have no demo yet)
- [ ] No fake demo, screenshot, or "deployed" claim anywhere
- [ ] Check spelling of "Qoneqt", "HackBriven", "CTRL FREAK"
- [ ] Export as **PDF or PPT**, whichever the submission form asks for (Gamma: Share → Export)
- [ ] Open the exported file once on your phone to check it looks right

## 2. The Idea in Plain Words (say this to anyone)
"Normal AI tools make a video and stop. Ours checks its own video like a strict teacher, gives it marks out of 100, and if marks are below 80, it fixes the mistakes and tries again by itself. Only good videos get published to Qoneqt."

## 3. Why Judges Should Pick Us (Slide-by-slide reasoning)
| Slide | Purpose | Key message |
|---|---|---|
| 1 | Identity | Clear name and tagline |
| 2 | Show the gap | Quality control is missing in AI video |
| 3 | Solution | Self-scoring and auto-retry |
| 4 | Prove it is real | Clear architecture, realistic stack |
| 5 | Show innovation | 5 features, the quality loop stands out |
| 6 | Show value | Real impact, low cost, scalable |

## 4. Scoring Rubric (memorize)
| Dimension | Points |
|---|---|
| Hook strength (first 3 sec) | 30 |
| Clarity | 25 |
| Pacing | 20 |
| Visual variety | 15 |
| Technical QA (audio, captions, 9:16, no broken assets) | 10 |

Pass mark: **80**. Max retries: **3**. After 3 tries, keep the best version and flag it for human review.
Be honest: score = AI judge + rule-based checks (duration, captions, resolution, audio).

## 5. Likely Judge Questions and Short Answers
**Q: How is this different from other AI video tools?**
A: Others generate once. NEXUS evaluates its own output and improves it automatically before publishing.

**Q: How do you know the score is reliable?**
A: We combine an AI critic with a strict rubric and objective checks like duration, caption coverage, resolution and audio. We calibrate it against known good and bad examples.

**Q: What if the AI keeps failing?**
A: Max 3 retries, then the best attempt is saved and flagged for human review, so there is no infinite loop.

**Q: Can it scale?**
A: Yes. Each video is an independent job, so a queue and more workers give more throughput. Models are swappable.

**Q: What is the cost per video?**
A: Small. A few LLM calls, one voice generation, and free local FFmpeg rendering. Retries add cost, which is why we cap them. (Calculate real numbers once APIs are chosen.)

**Q: Why is this good for Qoneqt?**
A: Qoneqt is community-first. It needs steady, good content on the Global Feed. NEXUS provides consistent quality without a large editing team.

**Q: Is it built?**
A: Be honest: "This is our proposed solution and plan. We will build and ship the working version for the finale."

## 6. What to Prepare Before Oct 4
1. Get API keys and test each end to end: LLM, image or video, text-to-speech.
2. Prototype the score-and-retry loop on scripts only (fastest proof).
3. Write the critic prompt and rubric, and test it on 5 good and 5 bad scripts.
4. Prepare the FFmpeg composer (9:16, captions, music).
5. Ask the Qoneqt team how to publish a video to the Global Feed.
6. Ask organizers whether pre-written code is allowed. If not, prepare only designs, prompts, and test assets.
7. Split team roles: **Backend/AI**, **Media/FFmpeg**, **Frontend/Deploy**, **Pitch/Docs/Demo video**.

## 7. Finale Day Timeline (8 hours)
| Time | Goal |
|---|---|
| 0:00-0:45 | Setup, repo, skeleton |
| 0:45-2:30 | Script agent + critic + retry loop |
| 2:30-4:30 | Visuals + voice + captions + composer |
| 4:30-5:30 | Video critic + full loop end to end |
| 5:30-6:30 | Dashboard + deploy |
| 6:30-7:15 | Generate final videos, **publish to Qoneqt**, record demo video |
| 7:15-8:00 | README + rehearse |

Rule: have an ugly end-to-end version by hour 5. Polish only after that.

## 8. Required Deliverables Checklist
- [ ] Public GitHub repo with README
- [ ] Live deployment link
- [ ] Demo video
- [ ] At least one video published on Qoneqt Global Feed
- [ ] Working pipeline demonstrated live

## 9. 3-Minute Pitch Script
1. (20s) "AI video is easy. Consistent quality at scale is not."
2. (30s) Type a topic live.
3. (60s) Show score 62 → retry → 79 → retry → 87 → approved.
4. (30s) Play the video, click Publish to Qoneqt.
5. (30s) Show batch mode with 5 topics and a score table.
6. (10s) "We built the quality engine Qoneqt needs to publish AI content at scale."

Prepare a **backup pre-generated video** in case Wi-Fi or an API fails.

## 10. Risks and Fixes
| Risk | Fix |
|---|---|
| AI video too slow or costly | Images + motion + voice + captions via FFmpeg; AI clip only for the hook |
| API failure or rate limit | Fallback provider + cached assets |
| Critic scores everything high | Strict rubric, JSON-only output, calibration examples |
| No Qoneqt publish API | Ask Qoneqt team; manual upload of the final MP4 is fine |
| Time runs out | Cut stretch features, never cut the score loop or the publish step |

## 11. Honest Reality Check
No PPT or idea guarantees selection. Judges reward what works live. A simple pipeline with a real, visible self-improvement loop beats a huge one that half-works.

## 12. Gamma Tips
- Always use "Preserve this exact text" so it does not rewrite or add fluff.
- After generating, delete any extra slides Gamma adds.
- Check every slide for text overflow.
- Slide 4 diagram is the most important slide. If Gamma draws it badly, rebuild it manually using shapes, or generate the diagram separately and insert it as an image.
