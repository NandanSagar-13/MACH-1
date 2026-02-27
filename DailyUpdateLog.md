# MACH 1 — Not for public release. Personal research only.

================================================================
  MACH 1 — Personal Project
  Repository Update Log
================================================================

────────────────────────────────────────────────────────────────
 INITIAL BUILD  |  Feb 26, 2026
────────────────────────────────────────────────────────────────

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


────────────────────────────────────────────────────────────────
 DAY 1 — TESTING & FIXES  |  Feb 26, 2026
────────────────────────────────────────────────────────────────

 First real-world test run. Task: "open notepad"

 ISSUES FOUND:
 - Vision model (llava) outputting garbage tokens <s> <unk>
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


────────────────────────────────────────────────────────────────
 DAY 2 — API INTEGRATION & STABILITY  |  Feb 27, 2026
────────────────────────────────────────────────────────────────

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


────────────────────────────────────────────────────────────────
 CURRENT STATE  |  Feb 27, 2026
────────────────────────────────────────────────────────────────

 WORKING:
 ✓ Full agent boots and runs
 ✓ Vision reads screen correctly (moondream)
 ✓ Self-awareness detects loops and gaps
 ✓ Background research thread active
 ✓ Warden reviews and improves after every task
 ✓ Skill library saving and querying
 ✓ Constitution enforcement active
 ✓ Coordinate safety layer in place

 IN PROGRESS:
 ~ GPU acceleration (restart pending)
 ~ Groq API key setup (trainer_config.py)
 ~ First training session

 NEXT SESSION:
 → Add Groq API key to trainer_config.py
 → Run: python trainer/train.py --seed
 → Run: python trainer/train.py
 → Monitor graduation progress
 → Add Gemini + Tavily keys for full teacher capability

================================================================
  MACH 1 — Not for public release. Personal research only.
================================================================
