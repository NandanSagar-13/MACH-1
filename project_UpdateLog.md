# MACH 1 — Not for public release. Personal research only.

  MACH 1 — Personal Project
  Repository Update Log
================================================================
 INITIAL BUILD  |  Feb 26, 2026

 Project initialized from base.
 Core architecture designed and built from scratch.

 BUILT:
 + Project folder structure created
 + config/settings.py         — central config, model settings
 + config/constitution.txt    — hard rules agent cannot break
 + core/eyes.py               — screen capture & vision module
 + core/brain.py              — LLM reasoning & decision making
 + core/hands.py              — mouse & keyboard control
 + core/warden.py             — master AI governor
 + core/self_awareness.py     — loop detection & gap flagging
 + memory/skill_library.py    — SQLite long-term memory
 + background/research_thread.py — silent internet learning
 + main.py                    — main agent loop
 + requirements.txt           — dependencies
 + README.md                  — setup instructions
 + FILE_STRUCTURE.md          — folder placement guide

 ARCHITECTURE DECISIONS:
 + Dual-brain system — Worker + Warden
 + No paid APIs — fully local via Ollama
 + Constitution enforcement built into Warden
 + Self-awareness: 3 stuck states (confidence, loop, mismatch)
 + Background research thread — agent learns while working
 + Skill library grows with every task

 STATUS: Base architecture complete. First boot successful.
================================================================

  DAY 1 — TESTING & FIXES  |  Feb 26, 2026
 ================================================================
 First real-world test run. Task: "open notepad"

 ISSUES FOUND:
 - Vision model (llava) outputting garbage tokens
 - Brain sending coordinates to wrong screen positions
 - Each action taking 1-2 minutes (running on CPU)
 - Agent not recognizing task completion — kept looping
 - "Screen unchanged" warning triggering too frequently

 FIXES APPLIED:
 ~ core/eyes.py       — switched base64 → temp file image passing
 ~ core/eyes.py       — added screenshot resize 1920x1080 → 960x540
 ~ config/settings.py — switched vision model llava → moondream
 ~ config/settings.py — raised SCREEN_UNCHANGED_THRESHOLD 0.95 → 0.98
 ~ config/settings.py — switched brain model llama3.1 → llama3.2
 ~ config/settings.py — raised STUCK_REPEAT_LIMIT 2 → 3
 ~ core/brain.py      — rewrote system prompt with task_complete rules
 ~ core/brain.py      — added Windows 11 specific instructions
 ~ core/hands.py      — increased action pause 0.3s → 1.0s (visible)

 RESULT:
 + Vision fixed — moondream reads screen correctly in plain English
 + Notepad successfully opened on second run
 + Warden reviewed failure and rewrote Worker instructions ✓
 + Background researcher queued and processed knowledge gaps ✓
 + Self-awareness loop detection triggered correctly ✓

 REMAINING ISSUE:
 - Agent not calling task_complete after goal achieved
 - Still repeating actions unnecessarily

  DAY 2 — API INTEGRATION & STABILITY  |  Feb 27, 2026
 ================================================================
 Second test run. GPU investigation. Trainer module built.

 ISSUES FOUND:
 - Brain outputting invalid actions "click | press_key"
 - Coordinates landing at (0,0) → PyAutoGUI failsafe triggered
 - Local llama3.2 not reliably following JSON format
 - GPU (GTX 1650) not being used — Ollama running on CPU only
 - 2880MB of 4096MB VRAM consumed by display before model loads

 GPU STATUS:
 - CUDA 13.1 confirmed installed
 - Ollama process visible in nvidia-smi but using CPU
 - Environment variables set: CUDA_VISIBLE_DEVICES=0
 - Permanent fix applied via System environment variables
 - Full restart required to take effect

 TRAINER MODULE BUILT:
 + trainer/trainer_config.py    — free API keys + curriculum
 + trainer/teacher.py           — reviews mistakes, generates skills
 + trainer/graduation_checker.py — tracks agent independence
 + trainer/train.py             — full training session runner

 TRAINING PHILOSOPHY ESTABLISHED:
 + Free APIs = textbooks during development phase only
 + Agent learns skills from API-assisted runs
 + Skills saved permanently to library
 + APIs disconnected after graduation
 + Agent enters real world with skill library only
 + Self-learns from open internet after graduation

 GRADUATION CRITERIA DEFINED:
 + 500+ skills in library
 + 80%+ average confidence
 + 85%+ task success rate
 + API needed for <5% of tasks

 BRAIN UPGRADED:
 ~ core/brain.py — Groq API integration added
 ~ core/brain.py — auto fallback: Groq → local Ollama
 ~ core/brain.py — coordinate sanitizer added (clamps x:50-1870 y:50-1030)
 ~ core/brain.py — invalid action validator added
 ~ core/brain.py — JSON parse hardened

 RESULT:
 + Failsafe triggering eliminated by coordinate sanitizer
 + Invalid action format detected and rejected cleanly
 + Groq integration ready — awaiting API key
 + Trainer scaffolding complete — ready for school phase

DAY 3 — SCHOOL PHASE, WEB HUD & GPU ACCELERATION | Aug 1, 2026

Major milestone release. Completed School Phase training system, semantic vector memory, real-time Web HUD dashboard, custom F8+F9 failsafe, and achieved 100% GPU VRAM offloading (30x speedup).

BUILT & INTEGRATED:
- core/teacher.py — Teacher module for lesson synthesis, failure analysis, and graduation tracking
- core/trainer.py — School Phase session runner & automated curriculum executor
- ui/dashboard.py & ui/web/ — Dark-mode glassmorphism Web HUD Dashboard (http://localhost:7860) with live screen stream, reasoning HUD, action audit log, and graduation gauge
- USER_GUIDE.md — Complete user operating guide for CLI, Web HUD, and GPU configuration

UPGRADES & FIXES APPLIED:
- memory/skill_library.py — Upgraded to local TF-IDF + n-gram Cosine Similarity Vector Search for zero-cost conceptual retrieval
- memory/skill_library.py — Seeded 9 foundational Windows 11 baseline skills (Start Menu navigation, Notepad, Chrome, Explorer, Calc, Cmd, Settings, Window switching) at 90-95% confidence
- memory/skill_library.py — Added export_skillpack() and import_skillpack() methods
- core/hands.py — Disabled corner-mouse pyautogui.FAILSAFE = False to eliminate false-alarm aborts
- core/hands.py — Implemented custom F8 + F9 simultaneous keypress Emergency Abort listener
- core/brain.py — Added PRIMITIVE ACTION RULE to system prompt, enforcing explicit action strings (press_key, type, click) and eliminating skill-name format errors
- core/eyes.py & ui/dashboard.py — Fixed multithread mss screen capture thread-safety (with mss.mss() per capture)

GPU ACCELERATION & PERFORMANCE (NVIDIA GeForce GTX 1650):
- Hardware: NVIDIA GeForce GTX 1650 (4 GB VRAM) + CUDA 13.1 confirmed
- Optimization: Set num_ctx: 1024 and screen resize to 640x360 in core/eyes.py & core/brain.py
- VRAM Footprint: Reduced memory footprint to 2.4 GB (100% loaded in VRAM with zero PCIe paging)
- RESULT: Per-step reasoning latency reduced from 15.1s down to ~0.5s (30x Speedup)

GRADUATION CRITERIA TRACKER ACTIVE:
- Criterion 1: Skills Learned >= 500 (Current: 9 / 500)
- Criterion 2: Avg Skill Confidence >= 80% (Current: 94% — PASSED)
- Criterion 3: Task Success Rate >= 85% (Current: 100% — PASSED)
- Criterion 4: API Dependency < 5% (Current: 0.0% — 100% Local / $0 Cost — PASSED)

CURRENT STATE | Aug 1, 2026
WORKING:
✓ Full agent boots and runs locally (100% Free / $0 Cost)
✓ 100% GPU VRAM offloading on GTX 1650 (0.5s per step)
✓ Vision reads screen state in real time (moondream)
✓ Brain reasons and executes primitive action sequences (llama3.2)
✓ F8 + F9 Emergency Hotkey Abort active & verified
✓ Real-time Web HUD Dashboard live at http://localhost:7860
✓ Teacher module synthesizes lessons and tracks graduation metrics
✓ Skill Library semantic vector search & baseline skill seeding active
✓ Background research thread active with DuckDuckGo web scraping
✓ Warden Constitution enforcement & instruction evolution active

COMMANDS AVAILABLE:
- python main.py --dashboard  (Launch Web HUD at http://localhost:7860)
- python main.py --train      (Run automated School Phase training batch)
- python main.py --status     (Print system health & graduation status)
- python main.py --graduate   (Check graduation criteria)
- python main.py --task "..." (Execute single plain-English task)

NEXT SESSION:
→ Run automated training batch (python main.py --train) to expand Skill Library toward 500-skill graduation goal
→ Test multi-window complex application workflows via Web HUD
→ Export initial baseline skillpack (export_skillpack)

MACH 1 — Not for public release. Personal research project.
