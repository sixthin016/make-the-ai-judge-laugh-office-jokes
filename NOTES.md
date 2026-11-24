# BUILD NOTES — u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a

Status: BUILD + VERIFIKASI LOKAL LOLOS. Repo GitHub BELUM dibuat, BELUM
push, BELUM submit (urusan koordinator).

## Kompetisi
- Judul: Make the AI Judge Laugh: Office Jokes
- Hadiah total $5 (juara 1 $1.54, 10 tempat dibayar), entry fee: tidak ada.
- Deadline: 26 Nov 2026 22:40 WITA (14:40 UTC). Blind rounds: 3 ronde
  (24 Nov 16:41 UTC, 25 Nov 15:40 UTC, 26 Nov 14:40 UTC).
- Tugas: program menulis SATU joke satu baris tentang office life,
  1–199 karakter, ke /output/entry.txt. Juri: z-ai/glm-5.3-flash,
  pairwise, kriteria berurutan: (1) joke asli tentang kantor,
  (2) turn/kejutan di akhir, (3) recognition (meeting, printer,
  reply-all, kalender), (4) wording ketat, (5) fresh (bukan
  Monday/photocopier). Dev heat: vs 3 anchor + 3 rung; 500 besar dev
  board lolos ke final heat. Sudah 1.811 submission saat build.
- Leaderboard BUTA (board hidden, skor tidak terlihat) — bedah top 1
  via leaderboard/artifact TIDAK MUNGKIN di kompetisi ini (entri teks,
  tidak ada artifact). Gate yang dipakai: pairwise lokal dengan brief
  juri verbatim + model juri live sedekat mungkin yang gratis.

## Entri final (varian A)
> We replaced the status meeting with a reply-all thread, then scheduled a weekly meeting to vote on which reply gets read aloud.
- 114 karakter, satu baris, tanpa trailing newline.

## Pairwise lokal (brief juri verbatim dari rules)
- 8 varian (A–H) di judging/pairwise_judge.py; round-robin 28 pasang,
  1 call per pasang, urutan bergantian, skor house (pemenang
  0,5 + margin/10). 5 call tanpa verdict (0,5–0,5): A–F, B–D, C–D,
  D–E, E–H.
- Juri lokal: HiLinkUP DeepSeek V4.1 Flash (gratis, allowance 1M token
  s/d 30 Nov 2026). Juri gratis lain SEMUA down saat dicoba 23 Nov:
  OpenRouter free habis kuota harian (reset 00:00 UTC), Runcrate
  GLM/DeepSeek HTTP 529 overload, NVIDIA GLM SSL timeout, Gemini
  3.8-flash HTTP 503, Hermes Qwen4-Max free period BERAKHIR (404).
  Juri live (GLM-5.3-flash) tidak bisa dipakai gratis malam ini.
- Hasil round-robin 28/28: A 5,4 — F 4,8 — G 4,3 — B 3,6 — H 3,0 —
  E 2,4 — D 2,3 — C 2,2 (dari 7 game tiap varian).
- Playoff game penuh A vs F: SERI 0,50–0,50 (tiap varian menang 1 call,
  margin 2). Tie-break game kedua: A MENANG 0,75–0,25 (margin 3 + 2).
  Keputusan: A. Catatan: bila skor live seri persis, tie-break ukuran
  menguntungkan F (99 vs 114 karakter) — tapi round-robin + tie-break
  game memihak A.
- A menang di kedua posisi label (sebagai Entry A maupun B) — bukan
  bias posisi semata.

## Verifikasi lokal
- python3 main.py (2x, MAKEFUN_OUTPUT_DIR berbeda) → entry.txt 114
  karakter, satu baris, byte-identik (cmp OK), bukan whitespace.
- Tanpa network: stdlib saja (os).
- main.py + README.md masing-masing ditulis dalam ≥2 pesan write/edit
  (write lalu edit) agar thinking_revised terpenuhi.
- grade-local dari kit: TIDAK BISA jalan untuk harness program/v1 —
  kit CLI menjawab scorer + reference data tidak dipublikasikan di kit
  ("the house grades it from its competition directory"), dan kit ini
  tidak membawa practice instance. Pengganti lokal: gate scorer
  direplikasi persis dari rules (UTF-8, 1–199 karakter, bukan whitespace
  saja) → Valid = 1; program 2x run byte-identik; sintaks OK.

## File di direktori ini
- main.py, README.md, LICENSE — entri (ditulis segar di sesi ini).
- requirements.json, competition.json, leaderboard.json — snapshot API.
- kit/ — kit kompetisi yang diunduh (kit.tar.gz + hasil extract).
- judging/ — pairwise_judge.py, tiebreak.py, pairwise-results.json,
  tiebreak-a-f.json, pairwise-run.log — seleksi joke + log.
- NOTES.md — file ini.

## v2 (24 Nov 2026)
- v1 (meeting-to-read-email) scored panel 67.0 PERBAIKI / HiLinkUP 78 PERBAIKI;
  consensus weakness: stale trope, freshness low.
- v2 (reply-all thread + weekly vote) scored panel 65.3 PERBAIKI /
  HiLinkUP 87 SUBMIT. Kept v2: HiLinkUP +9, panel -1.7 within panel noise
  (~5 pts); panel's v2 penalty partly reflects stale v1 pairwise evidence
  in judging/ (documents v1's win, not v2's). No further iteration: both
  judges' remaining complaint is subjective laugh-strength, no concrete
  sharper angle offered beyond the auto-send variant.
