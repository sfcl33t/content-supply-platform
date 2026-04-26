# Live Module User Stories

## Creator Content Supply Chain Platform

---

## Epic 1: Go-Live Workflow (Multistreaming)

### LIV-001: One-Button Multi-Platform Go-Live
**Priority:** MVP | **Story Points:** 5

**As a** YouTube Creator  
**I want to** start a live stream to all my connected platforms with one button  
**So that** I can maximize my audience reach without managing multiple encoder configurations

**Acceptance Criteria:**
- Single "Go Live" button initiates stream to all enabled platforms simultaneously
- Platforms supported: YouTube Live, TikTok Live, Instagram Live, Facebook Live, X Live, LinkedIn Live, Twitch, Kick, Rumble, Custom RTMP
- Stream starts within 3 seconds of button press on all platforms
- Visual confirmation shows connected status for each platform
- Failed platform connections display error with retry option
- Stream keys are securely stored and auto-populated from OAuth connections

---

### LIV-002: Platform Selection Before Go-Live
**Priority:** MVP | **Story Points:** 3

**As a** Media Brand  
**I want to** select which platforms to stream to before going live  
**So that** I can tailor my broadcast distribution based on content type and audience

**Acceptance Criteria:**
- Toggle switches for each connected platform visible in pre-live screen
- Platform selections persist as default for future streams
- Quick presets available (e.g., "All Platforms", "Gaming Only", "Professional Only")
- Platform-specific status indicators show connection health before going live
- Warning displayed if no platforms are selected

---

### LIV-003: Custom RTMP Destination Configuration
**Priority:** MVP | **Story Points:** 2

**As an** IP Business  
**I want to** add custom RTMP destinations beyond the pre-integrated platforms  
**So that** I can stream to proprietary platforms, white-label services, or regional platforms

**Acceptance Criteria:**
- Input fields for RTMP URL and stream key
- Support for multiple custom RTMP destinations (up to 5)
- Test connection button validates RTMP endpoint before go-live
- Custom destinations can be named for easy identification
- Secure storage of stream keys with encryption at rest

---

### LIV-004: Platform-Specific Automatic Formatting
**Priority:** MVP | **Story Points:** 5

**As a** Solo Podcaster  
**I want to** have my stream automatically formatted for each platform's requirements  
**So that** I do not have to manually configure aspect ratios and encoding settings

**Acceptance Criteria:**
- TikTok Live receives vertical crop (9:16) automatically
- YouTube Live receives 16:9 horizontal format
- Instagram Live respects 4-hour platform limit with countdown warning at 3:45
- Bitrate and resolution optimized per platform requirements
- Audio normalization applied per platform specifications

---

### LIV-005: Scheduled Live Stream Setup
**Priority:** Post-MVP | **Story Points:** 3

**As an** Interview Show Host  
**I want to** schedule a live stream in advance with a countdown page  
**So that** my audience can set reminders and guests can prepare

**Acceptance Criteria:**
- Schedule streams up to 30 days in advance
- Automatic creation of "Coming Soon" events on supported platforms (YouTube, Facebook, LinkedIn)
- Shareable countdown link generated
- Email/notification reminders sent to creator 1 hour and 15 minutes before scheduled time
- Guest links automatically generated and emailed when stream is scheduled

---

## Epic 2: Guest Management (WebRTC)

### LIV-006: WebRTC Guest Invitation Links
**Priority:** MVP | **Story Points:** 3

**As an** Interview Show Host  
**I want to** generate unique browser links for remote guests  
**So that** guests can join my live stream without downloading any software

**Acceptance Criteria:**
- Generate unique WebRTC join link per guest
- Links work in Chrome, Firefox, Safari, and Edge
- No software download required for guests
- Links expire after stream ends or after 24 hours (whichever is sooner)
- Optional password protection for guest links
- Guest preview room allows audio/video check before joining live

---

### LIV-007: Multi-Guest Support (Up to 8)
**Priority:** MVP | **Story Points:** 5

**As a** Media Brand  
**I want to** host panel discussions with up to 8 simultaneous guests  
**So that** I can produce roundtable shows and multi-expert segments

**Acceptance Criteria:**
- Support for exactly 8 simultaneous WebRTC guests
- Grid view shows all connected guests to host
- Individual guest video quality adapts based on available bandwidth
- Host can see guest count and individual connection status
- Warning displayed when approaching guest limit (7/8 connected)

---

### LIV-008: Per-Guest Audio Mixing
**Priority:** MVP | **Story Points:** 5

**As an** Interview Show Host  
**I want to** independently control audio levels for each guest  
**So that** I can balance voices and mute interruptions in real-time

**Acceptance Criteria:**
- Individual volume slider for each guest (0-200%)
- One-click mute/unmute per guest
- Visual audio level meters per guest showing real-time dB
- Master output meter showing combined audio levels
- Audio mixing changes take effect within 50ms
- Host audio has separate control from guest audio

---

### LIV-009: Guest Waiting Room
**Priority:** MVP | **Story Points:** 2

**As a** YouTube Creator  
**I want to** place guests in a waiting room before bringing them on-air  
**So that** I can control when guests appear during the broadcast

**Acceptance Criteria:**
- Guests automatically enter waiting room when joining via link
- Host sees list of guests in waiting room with video preview
- One-click "Bring On Air" button per guest
- Guests see "Waiting to be admitted" message with their video preview
- Host can send text messages to waiting guests
- Guests can be returned to waiting room during stream

---

### LIV-010: Guest Audio/Video Permissions
**Priority:** Post-MVP | **Story Points:** 2

**As an** Interview Show Host  
**I want to** control which guests have their video enabled versus audio-only  
**So that** I can bring on callers without video or manage visual composition

**Acceptance Criteria:**
- Toggle video on/off per guest (guest camera disabled remotely)
- Audio-only guests display customizable avatar or name card
- Guest notified when their video is disabled by host
- Settings persist if guest reconnects during same stream

---

## Epic 3: Studio Controls (Browser-Based)

### LIV-011: Browser-Based Studio Interface
**Priority:** MVP | **Story Points:** 8

**As a** Solo Podcaster  
**I want to** access a full production studio in my web browser  
**So that** I can produce professional live streams without downloading software

**Acceptance Criteria:**
- Studio loads in Chrome, Firefox, Safari, Edge without plugins
- Camera selection dropdown for multi-camera setups
- Microphone selection with input level preview
- Preview window shows exactly what viewers will see
- Studio interface responsive down to 1280px viewport width
- All controls accessible via keyboard shortcuts

---

### LIV-012: Multi-Camera Switching
**Priority:** MVP | **Story Points:** 5

**As a** YouTube Creator  
**I want to** switch between multiple camera angles with instant response  
**So that** I can create dynamic visual content during live broadcasts

**Acceptance Criteria:**
- Support for switching between host camera, guest cameras, and screen share
- Switching response time under 20ms
- Keyboard shortcuts for quick camera switching (1-9 keys)
- Visual preview of all sources in multiview
- Smooth transitions available (cut, dissolve, fade)
- Current active source clearly highlighted in interface

---

### LIV-013: Real-Time Lower Thirds
**Priority:** MVP | **Story Points:** 3

**As a** Media Brand  
**I want to** display lower third graphics with guest names and titles  
**So that** viewers can identify speakers during interviews and panels

**Acceptance Criteria:**
- Pre-configured lower third templates (name, title, social handle)
- Lower thirds appear/disappear with animation
- Assignable to specific guests with one-click activation
- Custom text entry for ad-hoc lower thirds
- Position adjustable (bottom left, bottom center, bottom right)
- Lower thirds display within 100ms of activation

---

### LIV-014: On-Screen Graphics and Overlays
**Priority:** MVP | **Story Points:** 3

**As an** IP Business  
**I want to** display branded graphics, logos, and overlays during streams  
**So that** I maintain brand consistency across all live content

**Acceptance Criteria:**
- Upload custom PNG/WebP overlays with transparency
- Logo placement in any corner with size adjustment
- Full-screen graphic overlays for transitions
- Graphics library persists between streams
- Quick-access buttons for frequently used graphics
- Support for animated GIF overlays

---

### LIV-015: Screen Share Functionality
**Priority:** MVP | **Story Points:** 3

**As a** YouTube Creator  
**I want to** share my screen or specific application windows  
**So that** I can demonstrate software, show slides, or display content during streams

**Acceptance Criteria:**
- Share entire screen, specific window, or browser tab
- Screen share audio captured (system audio)
- Picture-in-picture mode with camera overlay on screen share
- Switch between screen share and camera with <20ms response
- Screen share resolution up to 1080p at 30fps
- Guest screen share capability with host approval

---

### LIV-016: Scene Presets
**Priority:** Post-MVP | **Story Points:** 3

**As a** Media Brand  
**I want to** save and recall scene layouts with pre-configured sources and graphics  
**So that** I can quickly switch between show segments without manual reconfiguration

**Acceptance Criteria:**
- Save current layout as named scene
- Unlimited scene presets per account
- One-click scene switching
- Scenes include: active cameras, graphics, lower thirds, audio mix
- Keyboard shortcuts assignable to scenes
- Scenes shareable between team members

---

## Epic 4: Post-Live Automation

### LIV-017: Automatic Recording to Archive
**Priority:** MVP | **Story Points:** 3

**As a** Solo Podcaster  
**I want to** have my entire live stream automatically saved to my archive  
**So that** I have a high-quality master recording without manual export

**Acceptance Criteria:**
- Full recording saved in original quality (up to 4K)
- Recording starts automatically when stream begins
- Recording saved to Archive module within 10 minutes of stream end
- Recording includes all camera switches as they occurred
- Separate ISO recordings per source available (post-MVP)
- Recording accessible immediately after stream for editing

---

### LIV-018: Automatic Transcript Generation
**Priority:** MVP | **Story Points:** 3

**As an** Interview Show Host  
**I want to** receive a full transcript of my live stream within minutes of ending  
**So that** I can repurpose content and create written materials quickly

**Acceptance Criteria:**
- Transcript generated within 5 minutes of stream end
- Speaker diarization identifies different speakers
- Timestamps included at paragraph breaks
- Transcript accuracy of 95%+ for clear audio
- Editable transcript interface for corrections
- Export options: TXT, SRT, VTT, DOCX

---

### LIV-019: Automatic Story Block Creation
**Priority:** MVP | **Story Points:** 3

**As a** YouTube Creator  
**I want to** have a Story Block automatically created from my live stream  
**So that** I can immediately begin creating derivative content

**Acceptance Criteria:**
- Story Block created with: recording, transcript, metadata
- Stream title becomes Story Block title
- Platform chat highlights captured (where API permits)
- Tags auto-suggested based on transcript content
- Story Block linked to original stream analytics
- Story Block available in Story module within 15 minutes of stream end

---

### LIV-020: Auto-Generated Highlight Clips
**Priority:** MVP | **Story Points:** 5

**As a** Media Brand  
**I want to** receive 3 automatically identified highlight clips from my live stream  
**So that** I can quickly share the strongest moments on social platforms

**Acceptance Criteria:**
- AI identifies 3 strongest moments based on: audio energy, keyword density, chat engagement
- Clips are 30-90 seconds in length
- Clips formatted for vertical (TikTok/Reels) and horizontal (YouTube Shorts)
- Clips available for review within 30 minutes of stream end
- One-tap approval publishes clips via Distribute module
- Manual clip selection available if auto-suggestions are rejected

---

### LIV-021: YouTube VOD Chapter Generation
**Priority:** MVP | **Story Points:** 2

**As a** YouTube Creator  
**I want to** have chapters automatically added to my YouTube VOD  
**So that** viewers can navigate to specific topics in my archived stream

**Acceptance Criteria:**
- Chapters generated from transcript topic analysis
- Minimum 3 chapters, maximum 15 chapters per stream
- Chapter titles are concise (under 40 characters)
- Chapters editable before publishing to YouTube
- Chapters formatted per YouTube timestamp requirements
- Option to auto-publish or require manual approval

---

### LIV-022: Audio Strip to Podcast
**Priority:** MVP | **Story Points:** 3

**As a** Solo Podcaster  
**I want to** have the audio from my live stream automatically published as a podcast episode  
**So that** I reach audio-only listeners without manual export and upload

**Acceptance Criteria:**
- Audio extracted at original quality (or 320kbps MP3 if higher)
- Loudness normalized to podcast standards (-16 LUFS)
- Episode metadata populated from stream title and description
- Published to RSS feed via Distribute module
- Distribution to Spotify, Apple Podcasts upon approval
- Intro/outro segments can be auto-prepended (post-MVP)

---

### LIV-023: Post-Stream Analytics Summary
**Priority:** Post-MVP | **Story Points:** 2

**As a** Media Brand  
**I want to** receive a consolidated analytics summary after my stream  
**So that** I can understand performance across all platforms in one view

**Acceptance Criteria:**
- Peak concurrent viewers aggregated across platforms
- Total unique viewers per platform
- Chat message volume and engagement highlights
- Stream duration and any interruptions logged
- Summary delivered via email and in-app notification
- Data available within 2 hours of stream end

---

## Epic 5: Stream Monitoring and Error Recovery

### LIV-024: Real-Time Stream Health Dashboard
**Priority:** MVP | **Story Points:** 3

**As an** Interview Show Host  
**I want to** monitor the health of my stream to all platforms in real-time  
**So that** I can identify and address issues before viewers complain

**Acceptance Criteria:**
- Per-platform status indicators (green/yellow/red)
- Current bitrate displayed per platform
- Dropped frame percentage visible
- Network quality indicator for host connection
- Latency display per platform
- Dashboard updates every 1 second

---

### LIV-025: Automatic Stream Recovery
**Priority:** MVP | **Story Points:** 5

**As a** YouTube Creator  
**I want to** have failed platform connections automatically recover  
**So that** temporary network issues do not require manual intervention

**Acceptance Criteria:**
- Automatic reconnection attempt within 5 seconds of disconnect
- Up to 3 retry attempts with exponential backoff
- Host notified of reconnection attempt and result
- Stream to other platforms continues uninterrupted during recovery
- Recovery logged in stream analytics
- Manual "Force Reconnect" button available if auto-recovery fails

---

### LIV-026: Guest Connection Monitoring
**Priority:** MVP | **Story Points:** 2

**As an** Interview Show Host  
**I want to** see connection quality indicators for each guest  
**So that** I can proactively address technical issues during interviews

**Acceptance Criteria:**
- Connection quality icon per guest (excellent/good/poor/disconnected)
- Audio/video latency displayed per guest
- Packet loss percentage visible on hover
- Warning alert when guest quality degrades below threshold
- Option to reduce guest video quality to improve stability

---

### LIV-027: Backup Stream Recording
**Priority:** MVP | **Story Points:** 3

**As a** Media Brand  
**I want to** have a local backup recording in case of cloud upload failure  
**So that** I never lose content due to network issues

**Acceptance Criteria:**
- Browser-local recording runs parallel to cloud recording
- Local recording available immediately if stream ends unexpectedly
- Upload local recording to archive if cloud recording is incomplete
- Storage warning displayed if local disk is low
- Local recording automatically cleaned up after successful cloud backup

---

### LIV-028: Platform-Specific Error Alerts
**Priority:** Post-MVP | **Story Points:** 2

**As an** IP Business  
**I want to** receive detailed error messages specific to each platform  
**So that** I can understand why a platform rejected or dropped my stream

**Acceptance Criteria:**
- Error codes mapped to human-readable explanations
- Suggested remediation displayed (e.g., "Instagram requires re-authentication")
- Platform-specific error logs downloadable for support
- Error notification pushed even after stream ends
- Historical error patterns visible in analytics

---

### LIV-029: Emergency Stream Termination
**Priority:** MVP | **Story Points:** 1

**As a** Solo Podcaster  
**I want to** immediately terminate all streams with one button  
**So that** I can quickly end broadcasts in case of emergency or technical failure

**Acceptance Criteria:**
- "End All Streams" button prominently displayed
- Confirmation dialog prevents accidental clicks
- All platform streams terminated within 2 seconds
- Recording saved up to termination point
- Post-stream automation still triggers for available content

---

## Story Summary

| Epic | MVP Stories | Post-MVP Stories | Total Story Points |
|------|-------------|------------------|-------------------|
| Go-Live Workflow | 4 | 1 | 18 |
| Guest Management | 4 | 1 | 17 |
| Studio Controls | 5 | 1 | 25 |
| Post-Live Automation | 6 | 1 | 21 |
| Stream Monitoring | 5 | 1 | 16 |
| **Total** | **24** | **5** | **97** |

---

## MVP Scope Recommendation

**Phase 1 MVP (Sprint 1-3):** Stories LIV-001 through LIV-004, LIV-006 through LIV-009, LIV-011 through LIV-015, LIV-017 through LIV-022, LIV-024 through LIV-027, LIV-029

**Phase 2 Post-MVP:** Stories LIV-005, LIV-010, LIV-016, LIV-023, LIV-028

---

## Technical Dependencies

1. **SRT Ingest Endpoint:** Required for LIV-001 through LIV-004 (custom SRT relay + FFmpeg on EC2)
2. **Daily.co API Integration:** Required for LIV-006 through LIV-010 (WebRTC guest links)
3. **FFmpeg Lambda Functions:** Required for LIV-017, LIV-018, LIV-020, LIV-022
4. **Archive Module:** Required for LIV-017, LIV-019
5. **Distribute Module:** Required for LIV-020, LIV-022
6. **Clips Module:** Required for LIV-020
7. **OpenTelemetry:** Required for LIV-024 through LIV-028 (stream monitoring metrics)
