# Creator Content Supply Chain Platform
## MVP Roadmap: Layered Build Strategy

---

## Philosophy

**Start narrow, prove value, then expand.**

The full platform has 144 user stories across 7 modules. Attempting to build all at once guarantees failure. Instead, we build in layers where each layer:
1. Delivers standalone value to paying customers
2. Validates assumptions before investing in the next layer
3. Generates revenue to fund continued development

---

## Target: Two Launch Bundles

| Bundle | Price | Modules | Why These First |
|--------|-------|---------|-----------------|
| **Podcaster** | $40/mo | Story, Distribute, Archive | Simplest workflow, audio-only distribution |
| **Creator** | $55/mo | Story, Distribute, Clips, Archive | Adds video + short-form, higher value |

These two bundles share 90% of infrastructure. The Creator bundle adds AI clip generation, which is a differentiator worth the $15/mo premium.

---

## Layer 0: Foundation (Weeks 1-2)

**Goal**: Infrastructure that all other layers depend on.

### What We Build
| Component | Tech | Purpose |
|-----------|------|---------|
| Object Storage | Backblaze B2 | All content storage, 11 nines durability |
| CDN | Cloudflare R2 + Stream | Zero-egress delivery |
| Observability | OpenTelemetry + Grafana | Metering, debugging, billing data |
| Auth | Clerk or Auth.js | User accounts, OAuth for platforms |
| Database | PostgreSQL (RDS) | Core data, append-only patterns |
| Task Queue | BullMQ + Redis | Async job processing |

### User Stories: None
This layer has no user-facing stories. It's pure infrastructure.

### Validation Gate
- [ ] Can upload a 1GB file to B2 and serve via Cloudflare
- [ ] OpenTelemetry traces visible in Grafana
- [ ] User can sign up and authenticate

### Cost: ~$200/mo
### Timeline: 2 weeks
### Team: 1 DevOps/infra engineer

---

## Layer 1: Core Loop (Weeks 3-5)

**Goal**: One recording → One platform (YouTube). The simplest possible proof of value.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Create Story from scratch | Story 1.1 | 2 |
| Upload raw footage | Story 3.2 | 5 |
| Basic transcript generation | (subset of 1.2) | 3 |
| Edit Hook Block | Story 2.1 | 3 |
| Edit Body Block | Story 2.2 | 5 |
| Manage Asset Block | Story 2.4 | 3 |
| YouTube OAuth connection | Distribute 1.1 | 3 |
| Publish to YouTube with chapters | Distribute 2.1 | 5 |
| Basic archive storage | Archive 1.1 | 5 |

**Total: 9 stories, 34 points**

### Technical Components
- **Transcription**: Whisper API or AssemblyAI
- **Video Processing**: FFmpeg Lambda for basic transcode
- **YouTube API**: Upload, chapters, metadata
- **UI**: Next.js, minimal Story Block editor

### The "Hello World" Flow
```
Creator uploads video
    → Transcript generated (5 min)
    → Creator edits Hook/Body blocks
    → Creator adds thumbnail
    → One click → Published to YouTube with chapters
```

### Validation Gate
- [ ] End-to-end: upload video → published on YouTube in < 15 minutes
- [ ] 5 beta users complete the flow successfully
- [ ] YouTube chapters appear correctly

### What We DON'T Build Yet
- Multi-platform distribution
- AI clip suggestions
- Live streaming
- Rights tracking
- Team collaboration
- Billing (free beta)

### Cost: ~$400/mo (+ transcription API costs)
### Timeline: 3 weeks
### Team: 1 full-stack engineer + 1 frontend

---

## Layer 2: Podcaster Bundle (Weeks 6-8)

**Goal**: Launch the $40/mo Podcaster bundle. Audio distribution to Spotify/Apple.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Connect Podcast Platforms | Distribute 1.2 | 5 |
| Publish podcast episode | Distribute 2.2 | 3 |
| AI show notes generation | Story 4.4 | 3 |
| Storage usage monitoring | Archive 1.4 | 2 |
| Schedule future publish | Distribute 4.1 | 3 |
| Real-time publish status | Distribute 5.1 | 3 |
| Auto-retry transient failures | Distribute 5.3 | 2 |
| EBU R128 loudness normalization | Archive 7.1 | 3 |

**Total: 8 stories, 24 points**

### Technical Components
- **RSS Feed Generation**: Auto-generate compliant RSS
- **Spotify/Apple APIs**: OAuth + episode upload
- **FFmpeg**: Audio extraction, loudness normalization
- **Lago**: Subscription billing activated

### Validation Gate
- [ ] Podcast episode publishes to Spotify + Apple + RSS
- [ ] Audio passes loudness compliance check
- [ ] 10 paying customers at $40/mo = $400 MRR

### Pricing Activation
- Stripe integration
- Lago for subscription management
- Podcaster bundle: $40/mo

### Cost: ~$600/mo
### Timeline: 3 weeks
### Revenue Target: $400/mo (10 customers)

---

## Layer 3: Creator Bundle (Weeks 9-12)

**Goal**: Launch the $55/mo Creator bundle. AI clips + multi-platform distribution.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Auto clip identification (3 clips) | Archive/Clips 3.1 | 8 |
| Vertical format conversion | Archive/Clips 3.2 | 5 |
| Clip preview + confidence scores | Archive/Clips 3.3 | 3 |
| In-out point adjustment | Archive/Clips 4.1 | 3 |
| Crop/reframe adjustment | Archive/Clips 4.2 | 3 |
| Connect social accounts | Distribute 1.3 | 5 |
| Publish to TikTok/Reels/Shorts | Distribute 2.3 | 5 |
| Auto vertical crop | Distribute 3.1 | 5 |
| Duration limit enforcement | Distribute 3.2 | 2 |
| One-click multi-platform publish | Distribute 2.4 | 8 |
| Platform-specific captions | Distribute 7.1 | 3 |
| Auto hashtags | Distribute 7.2 | 2 |

**Total: 12 stories, 52 points**

### Technical Components
- **AI Clip Detection**: Custom model or API (Runway, Twelve Labs)
- **Face Detection**: MediaPipe or AWS Rekognition for smart crop
- **Platform APIs**: TikTok, Instagram Graph, X API v2

### The "Magic Moment"
```
Creator uploads 60-minute video
    → AI suggests 3 best clips
    → Creator approves with one tap each
    → Clips auto-formatted for vertical
    → Published to YouTube, TikTok, Reels, Shorts simultaneously
```

### Validation Gate
- [ ] AI clips achieve 70%+ approval rate (creator uses suggested clips)
- [ ] Multi-platform publish completes in < 5 minutes
- [ ] 25 paying customers (mix of $40 + $55)
- [ ] $1,000 MRR

### Cost: ~$950/mo
### Timeline: 4 weeks
### Revenue Target: $1,000/mo (break-even)

---

## Layer 4: Quality & Reliability (Weeks 13-15)

**Goal**: Production-grade reliability. Reduce support burden. Increase trust.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Automated QC scanning | Archive 6.1 | 5 |
| Lip-sync drift detection | Archive 6.2 | 5 |
| Visual artifact detection | Archive 6.3 | 3 |
| Human approval workflow | Archive 6.4 | 5 |
| Single-variant rollback | Archive 5.1 | 5 |
| Full story rollback | Archive 5.2 | 5 |
| Publishing error handling | Distribute 5.2 | 3 |
| Queue dashboard | Distribute 4.2 | 3 |

**Total: 8 stories, 34 points**

### Why This Layer Matters
Before scaling, we need:
- Automated quality gates (no broken content reaches platforms)
- Rollback capability (mistakes are recoverable)
- Clear status visibility (creators trust the system)

### Validation Gate
- [ ] QC catches 95%+ of detectable issues before publish
- [ ] Rollback executes in < 1 second
- [ ] Support tickets per customer decrease 50%

### Cost: ~$950/mo (no increase)
### Timeline: 3 weeks

---

## Layer 5: Live Streaming (Weeks 16-20)

**Goal**: Launch Interview Show bundle at $75/mo.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| One-button multi-platform go-live | Live 001 | 5 |
| Platform selection | Live 002 | 3 |
| WebRTC guest links | Live 006 | 3 |
| Multi-guest support (8) | Live 007 | 5 |
| Per-guest audio mixing | Live 008 | 5 |
| Browser-based studio | Live 011 | 8 |
| Multi-camera switching | Live 012 | 5 |
| Auto-recording to archive | Live 017 | 3 |
| Auto-transcript | Live 018 | 3 |
| Auto Story Block creation | Live 019 | 3 |
| Auto highlight clips | Live 020 | 5 |

**Total: 11 stories, 48 points**

### Technical Components
- **SRT Ingest**: Custom FFmpeg relay on EC2
- **WebRTC**: Daily.co or LiveKit
- **Multistream**: RTMP relay to all platforms

### New Bundle
- Interview Show: $75/mo (adds Live to Creator)

### Validation Gate
- [ ] 8-guest stream runs stable for 2+ hours
- [ ] Post-stream automation creates clips within 30 min
- [ ] 50 paying customers, $2,500 MRR

### Cost: ~$1,200/mo
### Timeline: 5 weeks
### Revenue Target: $2,500/mo

---

## Layer 6: Team & Scale (Weeks 21-24)

**Goal**: Launch Media Brand bundle at $130/mo. Multi-user support.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Invite team members | Story 5.1 | 3 |
| Assign story to member | Story 5.2 | 2 |
| Story status workflow | Story 1.5 | 3 |
| Story tagging | Story 1.6 | 2 |
| Archive search | Archive 1.3 | 3 |
| First-frame preview | Archive 1.2 | 3 |
| Premiere Pro integration | Archive 2.1 | 5 |
| DaVinci Resolve integration | Archive 2.2 | 5 |
| Pipeline rollback | Archive 5.3 | 8 |

**Total: 9 stories, 34 points**

### New Bundle
- Media Brand: $130/mo (all features except monetization)

### Validation Gate
- [ ] 3+ person team successfully collaborates on content
- [ ] Zero-download editing works reliably
- [ ] 75 paying customers, $5,000 MRR

### Cost: ~$1,500/mo
### Timeline: 4 weeks
### Revenue Target: $5,000/mo

---

## Layer 7: Monetization (Weeks 25-30)

**Goal**: Launch IP Business bundle at $175/mo. Rights tracking + FAST channels.

### What We Build
| Feature | Stories | Points |
|---------|---------|--------|
| Register asset in rights ledger | Rights 1.1 | 3 |
| View rights history | Rights 1.2 | 5 |
| Bulk import catalog | Rights 1.3 | 5 |
| Territory-specific license | Rights 2.1 | 5 |
| License duration/renewal | Rights 2.2 | 3 |
| Create FAST channel | Rights 3.1 | 8 |
| Configure ad breaks | Rights 3.2 | 5 |
| Connect FAST distributors | Rights 3.3 | 8 |
| Track CPM revenue | Rights 5.1 | 5 |
| Usage metering | Rights 6.1 | 5 |
| Usage-based billing | Rights 6.2 | 5 |

**Total: 11 stories, 57 points**

### Technical Components
- **Rights Ledger**: PostgreSQL append-only with SHA-256 chain
- **FAST Playout**: Amagi Cloudport or custom FFmpeg
- **SCTE-35**: Ad marker insertion

### New Bundle
- IP Business: $175/mo (full platform)

### Validation Gate
- [ ] FAST channel live on at least one distributor
- [ ] Rights ledger passes integrity audit
- [ ] 100 paying customers, $8,000+ MRR

### Cost: ~$2,000/mo
### Timeline: 6 weeks
### Revenue Target: $8,000/mo

---

## Summary: Layer Progression

| Layer | Weeks | Stories | Points | Bundle | MRR Target |
|-------|-------|---------|--------|--------|------------|
| 0: Foundation | 1-2 | 0 | 0 | - | $0 |
| 1: Core Loop | 3-5 | 9 | 34 | Beta | $0 |
| 2: Podcaster | 6-8 | 8 | 24 | $40 | $400 |
| 3: Creator | 9-12 | 12 | 52 | $55 | $1,000 |
| 4: Quality | 13-15 | 8 | 34 | - | $1,500 |
| 5: Live | 16-20 | 11 | 48 | $75 | $2,500 |
| 6: Team | 21-24 | 9 | 34 | $130 | $5,000 |
| 7: Monetize | 25-30 | 11 | 57 | $175 | $8,000 |
| **Total** | **30 wks** | **68** | **283** | | |

### What This Means
- **68 stories** (47% of full backlog) delivers **all 5 bundles**
- **30 weeks** (~7 months) to full product
- **Break-even at Layer 3** (~$1,000 MRR vs ~$950/mo infra)
- **Layer 1-3 is the true MVP**: 29 stories, 110 points, 12 weeks

---

## The 12-Week MVP (Layers 0-3)

If you can only build for 12 weeks before needing revenue:

### Scope
| Layer | Stories | Points |
|-------|---------|--------|
| Foundation | 0 | 0 |
| Core Loop | 9 | 34 |
| Podcaster | 8 | 24 |
| Creator | 12 | 52 |
| **Total** | **29** | **110** |

### Team Required
- 1 Full-stack engineer (backend + infra)
- 1 Frontend engineer (UI + integrations)
- 1 Product/founder (design + customer dev)

### What You Ship
1. Create stories from uploaded video
2. AI transcript + chapter generation
3. Publish to YouTube with chapters
4. Publish audio to Spotify/Apple/RSS
5. AI clip generation (3 clips per video)
6. Vertical format conversion
7. Multi-platform short-form distribution (TikTok, Reels, Shorts)
8. Basic storage + archive

### What You DON'T Ship
- Live streaming
- Team collaboration
- Rights tracking
- FAST channels
- Advanced QC
- Rollback (manual recovery only)

### Revenue Model
| Month | Podcaster ($40) | Creator ($55) | MRR |
|-------|-----------------|---------------|-----|
| 3 | 5 | 5 | $475 |
| 4 | 10 | 10 | $950 |
| 5 | 15 | 15 | $1,425 |
| 6 | 25 | 25 | $2,375 |

**Target: 50 customers, ~$2,400 MRR by month 6**

---

## Risk Mitigation

### Technical Risks
| Risk | Mitigation |
|------|------------|
| AI clip detection quality poor | Start with manual clip selection, add AI as enhancement |
| YouTube API quota limits | Apply for higher quota early, implement retry logic |
| Transcription costs spike | Batch processing, cache results, consider self-hosted Whisper |
| Platform API changes | Abstract integrations, monitor changelogs, maintain fallbacks |

### Business Risks
| Risk | Mitigation |
|------|------------|
| Creators won't pay | Validate with 5 design partners before Layer 2 |
| Churn after trial | Focus on "magic moment" in onboarding |
| Feature creep | Strict layer gates, no skipping ahead |
| Competitor launches similar | Speed to market, niche focus on podcast/YouTube crossover |

---

## Decision Points

### Layer 1 → Layer 2
**Go** if: 5+ beta users complete full flow, positive feedback
**Pivot** if: Users abandon mid-flow, transcription quality complaints

### Layer 3 → Layer 4
**Go** if: 25+ paying customers, < 5% churn
**Pause** if: Revenue flat, high support volume

### Layer 5 → Layer 6
**Go** if: Interview Show bundle has demand (waitlist > 20)
**Skip** if: Existing customers not requesting live streaming

### Layer 6 → Layer 7
**Go** if: Media Brand customers request rights tracking
**Delay** if: FAST channel partnerships not secured

---

## Next Steps

1. **Week 1**: Set up Foundation (Backblaze, Cloudflare, Postgres, Auth)
2. **Week 2**: Complete infrastructure, deploy OpenTelemetry
3. **Week 3**: Begin Core Loop - video upload + transcription
4. **Week 4**: Story Block editor + YouTube publish
5. **Week 5**: End-to-end testing with beta users

### First Milestone
**Week 5**: One beta user uploads video → publishes to YouTube with chapters

---

*This document should be updated as layers complete and assumptions are validated.*
