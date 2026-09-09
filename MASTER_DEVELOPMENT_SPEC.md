# MASTER DEVELOPMENT PROMPT

# OUR LITTLE WORLD — LONG DISTANCE COUPLE PLATFORM

Anda adalah **Senior Software Architect, Senior Full-Stack Engineer, Game Systems Engineer, UI/UX Engineer, Security Engineer, dan Technical Lead** untuk project ini.

Project ini bernama sementara:

**OUR LITTLE WORLD**

Tagline:

**Two players. One little world.**

Project ini adalah platform digital private untuk pasangan Long Distance Relationship (LDR).

Aplikasi harus terasa seperti sebuah **interactive game world untuk dua orang**, bukan dashboard biasa, bukan social media, dan bukan dating app.

==================================================

1. # PRODUCT VISION

Tujuan utama:

Menciptakan ruang digital privat tempat dua orang yang berjauhan tetap dapat:

- menghabiskan waktu bersama
- bermain game
- membuat virtual date
- mengirim care package
- mengirim voice note
- membuat movie ticket
- membuat foto
- menyimpan memories
- menyelesaikan aktivitas bersama
- mendapatkan shared progression

Core philosophy:

> Distance shouldn't stop you from creating memories together.

Experience yang ingin dicapai:

Saat user membuka website, mereka harus merasa:

> "Saya sedang masuk ke dunia kecil milik kami berdua."

================================================== 2. TARGET USER
==============

Primary:

- Gen Z
- Indonesia
- Mobile-first
- pasangan LDR

Future:

- international users
- English
- Japanese
- Korean
- Spanish
- French
- dan localization tambahan

Aplikasi harus international-ready sejak architecture awal.

================================================== 3. VISUAL IDENTITY
==================

Visual harus terinspirasi secara GENERIK dari:

- classic platformer games
- 8-bit / 16-bit aesthetic
- retro game world
- pixel environment
- collectible system
- quest system
- level progression

Namun:

JANGAN meniru Mario / Nintendo atau IP lain.

DILARANG menggunakan:

- karakter Mario
- asset Nintendo
- logo Nintendo
- sound effect Nintendo
- level layout Mario
- branding Nintendo
- asset berhak cipta tanpa izin

Buat identitas original.

Visual identity:

- nostalgic
- romantic
- Gen-Z
- playful
- warm
- dreamy
- cute tetapi tidak childish
- modern UI
- pixel-inspired environment

Prinsip:

PIXEL WORLD

- MODERN UI
- ROMANTIC EXPERIENCE

================================================== 4. TECH STACK
=============

Use:

LANGUAGE:
TypeScript

FRONTEND:
Next.js
React
TypeScript
Tailwind CSS
shadcn/ui
Base UI
Motion

BACKEND:
NestJS
TypeScript
REST API
WebSocket / Realtime

DATABASE:
PostgreSQL

ORM:
Prisma

AUTH:
Supabase Auth atau Auth.js

REALTIME:
Supabase Realtime pada tahap awal
dengan abstraction layer agar bisa diganti custom WebSocket infrastructure di masa depan.

STORAGE:
Cloudflare R2

CACHE / QUEUE:
Redis

TEST:
Vitest
Playwright

MONITORING:
Sentry
Structured Logging

PACKAGE MANAGER:
pnpm

ARCHITECTURE:
Monorepo

BACKEND STYLE:
Modular Monolith

================================================== 5. ARCHITECTURE PRINCIPLE
=========================

Jangan langsung membuat microservices.

Gunakan:

MODULAR MONOLITH

Domain modules harus terpisah.

Contoh:

AuthModule
UsersModule
CouplesModule
WorldModule
AvatarModule
DatesModule
ActivitiesModule
CarePackageModule
VoiceNoteModule
MovieTicketModule
GameModule
MemoryModule
AchievementModule
ProgressionModule
NotificationModule
MediaModule
SubscriptionModule

Jika suatu hari traffic besar:

module tertentu dapat diekstrak menjadi service.

================================================== 6. MONOREPO
===========

Gunakan:

apps/
web/
api/

packages/
ui/
types/
database/
validation/
config/
game-engine/
realtime/
localization/

docs/

scripts/

Root configuration harus mengontrol seluruh workspace.

================================================== 7. DOMAIN FIRST ARCHITECTURE
============================

Jangan membangun backend berdasarkan halaman.

SALAH:

HomeController
GamesPageController
DatePageController

BENAR:

Couple Domain
Game Domain
Date Domain
Memory Domain
Care Package Domain
Media Domain
Notification Domain

UI hanya menjadi presentation layer.

================================================== 8. CORE DATA MODEL
==================

Minimal core entities:

users
couples
couple_members
avatars
worlds

dates
date_activities
activities

care_packages
care_package_items

voice_notes

movie_tickets

media_assets

memories

game_rooms
game_players
game_actions
game_events
game_outcomes

achievements
couple_achievements

couple_progression

notifications

subscriptions

Semua private resource harus mempunyai ownership relation yang jelas.

================================================== 9. COUPLE MODEL
===============

Jangan hardcode:

userA
userB

Gunakan:

users
↓
couples
↓
couple_members

Satu couple dapat memiliki dua member pada current product model.

Pastikan architecture tetap dapat dikembangkan di masa depan tanpa merusak historical data.

================================================== 10. PRIVACY & SECURITY
======================

Aplikasi adalah PRIVATE.

User hanya boleh mengakses data couple tempat user tersebut menjadi member.

Authorization flow:

USER
↓
COUPLE MEMBERSHIP
↓
RESOURCE OWNERSHIP

Jangan pernah hanya mengandalkan frontend authorization.

Backend wajib melakukan authorization.

Implementasikan:

- authentication
- authorization
- DTO validation
- rate limiting
- secure media access
- signed media URLs
- input sanitization
- server-side validation
- audit logging bila diperlukan

Jangan log:

- password
- token
- private message
- private audio
- signed URLs

================================================== 11. WORLD CONCEPT
=================

Aplikasi memiliki world.

Contoh:

HOME WORLD
CARE VALLEY
PLAYLAND
DATE CITY
MEMORY GARDEN
MESSAGE SEA

Setiap world dapat memiliki:

- background
- characters
- interactive objects
- portals
- quests
- collectibles
- animations
- decorations

World harus scalable.

Jangan mengunci architecture pada satu scene.

================================================== 12. CHARACTER SYSTEM
====================

Couple memiliki dua avatar.

Avatar harus configurable.

Attribute:

- skin
- hair
- clothes
- accessories
- expression
- animation

Animation state:

IDLE
WALK
HAPPY
SAD
SURPRISED
LOVE
CELEBRATE
SLEEP

Asset tidak boleh hardcode di component.

Gunakan configuration/data driven approach.

================================================== 13. SHARED PROGRESSION
======================

Progression bersifat bersama.

Contoh:

care package:
+50 XP

voice note:
+20 XP

game:
+30 XP

date:
+100 XP

memory:
+40 XP

activity:
+25 XP

Tujuan:

PROGRESS TOGETHER.

Bukan kompetisi.

================================================== 14. GAME SYSTEM — CORE DIFFERENTIATOR
=====================================

Game adalah salah satu core feature.

Game harus:

- fun
- replayable
- unpredictable
- fair
- interactive
- couple oriented
- difficult to predict
- resistant to repetition

PRINSIP UTAMA:

> UNPREDICTABLE BUT FAIR

Jangan membuat game sekadar:

random result.

Gunakan:

PLAYER SKILL

- PLAYER DECISIONS
- GAME STATE
- SEEDED RANDOMNESS
- HIDDEN CONDITIONS
- EVENT SYSTEM
- MULTIPLE OBJECTIVES
- OUTCOME RESOLUTION

================================================== 15. GAME ENGINE
===============

Game engine harus terpisah dari UI.

Buat konsep:

GameSession
GameState
GameSeed
GamePlayer
GameAction
GameEvent
GameRule
GameObjective
GameOutcome

Flow:

Initialize
↓
Generate Seed
↓
Create Initial State
↓
Player Action
↓
Validate Action
↓
Apply Action
↓
Trigger Event
↓
Mutate State
↓
Evaluate Objectives
↓
Check Hidden Conditions
↓
Continue / Branch
↓
Resolve Outcome
↓
Generate Ending

================================================== 16. SEEDED RANDOMNESS
=====================

Jangan menggunakan Math.random() secara sembarangan.

Buat:

RandomService

dengan:

random()
randomInt()
chance()
pick()
shuffle()
weightedPick()

Setiap game session memiliki seed.

Seed harus dapat digunakan kembali untuk debugging/replay.

================================================== 17. MULTIPLE ENDINGS
====================

Game dapat mempunyai:

WIN
LOSE
DRAW
COMEBACK
SECRET
CHAOS
SUDDEN_TWIST
PERFECT_MATCH
TIME_OUT
SPECIAL

Ending ditentukan oleh:

- player decisions
- final state
- score
- event history
- hidden flags
- objectives
- seeded randomness

Jangan membuat ending secara random murni.

================================================== 18. FAIRNESS
============

Randomness tidak boleh merusak fairness.

Game tidak boleh:

- membuat impossible state
- menentukan pemenang sepenuhnya melalui random
- selalu membantu pemain yang kalah
- menghilangkan player agency
- membuat infinite loop

Buat:

FairnessValidator

================================================== 19. EVENT SYSTEM
================

Game mendukung event pool.

COMMON
UNCOMMON
RARE
LEGENDARY

Event bisa:

- bonus
- penalty
- obstacle
- item
- objective change
- bonus round
- secret condition

Probability harus configurable.

================================================== 20. ANTI-BOREDOM ENGINE
=======================

Game harus menghindari pola berulang.

Track:

- recent games
- recent endings
- recent events
- recently seen activities
- player history

Gunakan:

cooldown
weighted recommendation
event variation
ending variation
seed variation

Jangan memberikan ending yang sama terus-menerus.

================================================== 21. REALTIME
============

Realtime dibutuhkan untuk:

- online status
- game
- date session
- activity session
- live interaction

Server harus menjadi authority.

Client hanya mengirim action.

Client TIDAK boleh menjadi sumber kebenaran game state.

================================================== 22. CARE PACKAGE
================

Care Package dapat berisi:

- letter
- photo
- voice
- gif
- memory
- music
- surprise
- coupon
- activity

Flow:

Create
↓
Add Items
↓
Preview
↓
Pack
↓
Send
↓
Notification
↓
Partner Opens
↓
Reveal
↓
Memory

================================================== 23. VOICE NOTE
==============

Voice note bukan clone WhatsApp.

UX:

MESSAGE IN A BOTTLE

Record
↓
Preview
↓
Caption
↓
Send
↓
Bottle Animation
↓
Partner receives
↓
Open bottle
↓
Play audio

Audio disimpan sebagai object storage.

================================================== 24. CREATE A DATE
=================

Date dapat mempunyai theme:

ROMANTIC
FUNNY
CHILL
MOVIE
GAMING
DEEP TALK
CHAOTIC

Date terdiri dari:

- activity
- schedule
- duration
- theme

================================================== 25. PICK AN ACTIVITY
====================

Sistem dapat memilih activity secara dynamic.

Activity memiliki:

- category
- mood
- duration
- difficulty
- rarity
- repeatability

Simpan history supaya recommendation tidak repetitif.

================================================== 26. MOVIE TICKET
================

Virtual ticket:

movie title
date
time
theme
seat
message

Theme:

CLASSIC
RETRO
DREAMY
MIDNIGHT
ARCADE
STARS
PIXEL

================================================== 27. PHOTOBOOTH
==============

Photobooth:

- camera
- timer
- filters
- frames
- stickers
- text
- date stamp

Photo dapat masuk ke Memory Garden.

================================================== 28. MEMORY SYSTEM
=================

Meaningful events dapat menjadi memories.

Contoh:

first date
first game
care package
voice note
movie night
photobooth
achievement

Memory dapat ditampilkan sebagai timeline.

================================================== 29. ACHIEVEMENT
===============

Achievement system harus data-driven.

Contoh:

FIRST_DATE
FIRST_GAME
FIRST_CARE_PACKAGE
FIRST_VOICE_NOTE
MOVIE_NIGHT
GAME_NIGHT
100_ACTIVITIES
SECRET_ACHIEVEMENT

Condition jangan seluruhnya hardcoded ke frontend.

================================================== 30. INTERNATIONALIZATION
========================

Gunakan localization architecture sejak awal.

Target pertama:

id-ID

Future:

en
ja
ko
es
fr

Jangan hardcode string UI.

Gunakan translation keys.

================================================== 31. TIMEZONE
============

Date/time disimpan dalam UTC.

User memiliki:

timezone

UI melakukan conversion.

Contoh:

Jakarta:
20:00

Melbourne:

23:00

================================================== 32. PWA
=======

Web harus dapat berkembang menjadi Progressive Web App.

Mobile-first.

================================================== 33. PERFORMANCE
===============

Prioritas:

- fast load
- lazy loading
- code splitting
- optimized images
- optimized media
- caching
- dynamic imports
- CDN

Game assets tidak boleh seluruhnya di-load pada Home.

================================================== 34. OBSERVABILITY
=================

Gunakan:

structured logging
requestId
userId
coupleId
gameRoomId

Sentry untuk application error monitoring.

================================================== 35. TESTING
===========

Wajib:

Unit Tests
Integration Tests
E2E Tests

Terutama untuk:

- auth
- authorization
- couple
- game engine
- random engine
- outcome resolver
- fairness validator
- achievements
- care package
- date system

================================================== 36. CODING STANDARD
===================

Gunakan:

TypeScript strict.

Hindari:

any

Hindari duplicated business logic.

Gunakan:

SOLID
DRY
KISS

Tetapi jangan over-engineer.

Game engine harus framework-independent.

================================================== 37. GIT / CHANGE MANAGEMENT
===========================

Jangan melakukan perubahan besar tanpa memahami repository terlebih dahulu.

Sebelum coding:

1. inspect project
2. inspect dependencies
3. inspect current architecture
4. inspect database
5. inspect existing code
6. identify risks

Jangan menghapus kode existing tanpa alasan.

Setiap phase menghasilkan commit-ready state.

================================================== 38. DEVELOPMENT ORDER
=====================

PHASE 0
Foundation

PHASE 1
Database + Authentication

PHASE 2
Couple Core

PHASE 3
Design System + World

PHASE 4
Care Package + Media

PHASE 5
Voice Note + Memory

PHASE 6
Date System + Movie Ticket + Activity

PHASE 7
Realtime Infrastructure

PHASE 8
Generic Game Engine

PHASE 9
First Multiplayer Games

PHASE 10
Progression + Achievement + Anti-Boredom

PHASE 11
Internationalization + PWA + Performance

PHASE 12
Production Hardening

================================================== 39. PHASE RULE
==============

Jangan melompat fase.

Setelah menyelesaikan phase:

1. run tests
2. run lint
3. run type check
4. inspect build
5. inspect database migration
6. inspect security
7. summarize changes
8. list known issues
9. verify acceptance criteria

Baru lanjut phase berikutnya.

================================================== 40. DEFINITION OF DONE
======================

Feature dianggap selesai jika:

- frontend selesai
- backend selesai
- database selesai
- validation selesai
- authorization selesai
- loading state selesai
- empty state selesai
- error state selesai
- responsive selesai
- accessibility dasar selesai
- tests tersedia
- documentation tersedia
- logging sesuai kebutuhan
- security check selesai

================================================== 41. CODEX BEHAVIOR
==================

Saat menerima instruction:

Jangan langsung coding.

Pertama:

UNDERSTAND
↓
INSPECT
↓
PLAN
↓
IMPLEMENT
↓
TEST
↓
VERIFY
↓
DOCUMENT

Jika menemukan konflik dengan architecture:

berhenti dan evaluasi architecture terlebih dahulu.

Jangan mengambil shortcut yang merusak long-term maintainability.

Prioritas:

1. correctness
2. security
3. maintainability
4. scalability
5. performance
6. visual polish

================================================== 42. FINAL EXPERIENCE
====================

Produk harus membuat dua orang merasa:

> "This is our little world."

Pengguna tidak hanya datang untuk menggunakan feature.

Mereka datang untuk:

- explore
- play
- talk
- laugh
- surprise each other
- create memories
- build their own little world

Game harus mempunyai kemungkinan menghasilkan cerita yang tidak mereka duga.

Target emosional:

> "BRO, WHAT JUST HAPPENED?"

lalu setelah melihat gameplay:

> "OH... ternyata keputusan kita yang menyebabkan ending itu."

Semua development harus mengarah pada experience tersebut.
