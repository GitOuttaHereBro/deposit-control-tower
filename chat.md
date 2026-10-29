# chat.md — Central Project Memory

> Read this file and all referenced project files before starting any task. Update it whenever new info, files, or instructions arrive. Never record assumptions as facts.

## 1. Project Purpose & Overview
- Smart India Hackathon problem SIH26265: "Streamline of Security Deposit / FDR Portal" for AICTE / Regulation Bureau.
- Goal (from user's research): build an evidence-first Security Deposit / FDR Lifecycle Control Tower — one auditable record per instrument, linking institution, documents, verification, renewal/replacement, release request, clearances (PGRC, Vigilance, other cells) and final authority decision.
- Grounded in AICTE Approval Process Handbook 2024–27, clause 6.46 (release of security deposit).

## 2. Already Built / Implemented (29 Oct 2026)
- Backend (Lovable Cloud) with sign-in (email/password + Google), roles: institution, officer, clearance cell, authority, auditor, admin. First account = admin with all staff roles.
- Demo data: 5 institutions, 8 instruments (incl. one duplicate FDR number, one replacement chain), 3 release cases (one with amount/date conflict, one ready, one RTGS with vigilance objection).
- Pages: landing, sign-in, Risk radar dashboard, Instrument register (+ add, detail with lineage/duplicates/verification), Release cases (list, new, detail with readiness checklist + rule clauses, document upload with fingerprint, evidence ledger with conflict resolution, clearances, authority decision with override, audit timeline, case-pack JSON export), Clearance queue, Audit log (CSV export), Users & roles.
- Rule pack tests: 13 passing.

## 3. Requested Changes
- 29 Oct 2026: User asked to read the dossier + USP research, summarize key requirements/opportunities, and propose a plan. Done.
- 29 Oct 2026: User chose: first + next stage scope, real logins and saved data, "modern control room" dark look. Built.

## 4. Errors & Bugs to Fix
- None open. Two reported TypeScript errors (src/lib/utils.ts TS2554; src/main.tsx TS18048; src/pages/Index.tsx TS2741) were checked: the files/code don't exist or typecheck passes. Treated as stale / from another project.

## 5. Key Requirements (from research files)
- Baseline (required but not USPs): central repository, document upload/versioning, maturity/validity tracking, renewal/replacement, release workflow, alerts/escalation, dashboards, role-based access, audit trail.
- Headline USPs (ranked): 1) Policy-aware release readiness engine (case-type checklist with rule references; FDR/RPGF → NOC, RTGS → sanction order; closure/merger/conversion/embezzlement conditions). 2) Evidence reconciliation & verification ledger (field-level comparison FDR vs affidavit vs register; statuses: submitted / OCR-extracted / cross-doc consistent / staff-reviewed / bank-confirmed / conflict). 3) Duplicate instrument & lineage detection. 4) Clearance-aware exception queue / bottleneck radar. 5) Replayable source-linked audit case pack.
- Build priority: P0 repository + case workflow, versioned checklist, uploads, manual entry fallback, discrepancy view, clearance-blocking gate, audit timeline. P1 duplicate alert, replacement lineage, risk dashboard, exportable case pack, fixed test dataset. P2 scan similarity, email/SMS, bulk import, bank/NeSL connector mock.

## 6. Next Steps
- User must sign up first (becomes admin) and confirm email; signed-in flows not yet tested end-to-end.
- Later stage (not built): reading scanned documents automatically, email/SMS alerts, bulk spreadsheet import, bank/NeSL connector mock.

## 7. Must NOT Be Changed / Removed / Implemented
- Do not rewrite the whole project for small changes.
- Do not remove existing functionality without explicit permission.
- From research — do NOT build/claim: blockchain authenticity, chatbot for its own sake, predictive fraud scoring, payment processing, universal bank connector, automatic release on maturity, "AI fraud detection", "instant verification across all banks", "100% accuracy", "first in India".
- OCR/user-submitted data must never be shown as bank-verified. Release decisions stay with a human authority.

## 8. Working Rules (from user, 29 Oct 2026)
- Always read all relevant provided files before any task; files may have any name/extension — judge by content, not filename.
- Latest applicable instruction is the source of truth; ask when info is missing, unclear, or contradictory.
- Make only necessary changes; verify fixes; report problems honestly.
- After each task, summarize: what changed, errors fixed, files modified, what remains, whether chat.md was updated.
- Keep chat.md organized; preserve history when requirements change.
- Uploaded instruction files say: no AI-generated images; use code, Tailwind, SVG/Lucide icons only.

## 9. Referenced Files
| File | Purpose |
|---|---|
| SIH26265_Deep_Research_Dossier.md | Full problem breakdown, process rules, architecture, tests, demo & execution plan |
| SIH26265_Best_USPs_Research.md | Ranked USPs, claims to avoid, build priorities |
| prompt127hub7460.txt, context4956.txt, task4014.txt | Short instruction notes: research and plan what to build; no AI images |

## 10. Change History
- 29 Oct 2026: chat.md created. No project files were attached in the first message.
- 29 Oct 2026: User reported TS2554 in src/lib/utils.ts(2,6). Typecheck passes; error stale. No code changed.
- 29 Oct 2026: Reported src/main.tsx and src/pages/Index.tsx errors — those files don't exist in this project. No code changed.
- 29 Oct 2026: Read both research reports; filled sections 1, 5, 7, 9. No app code changed.
- 29 Oct 2026: Built first + next stage of the control tower (see section 2). Files: migration, src/lib/{rules,case-bundle,queries,actions.functions,format}.ts, src/components/status.tsx, src/routes/{index,auth}.tsx, src/routes/_authenticated/*, src/styles.css, src/routes/__root.tsx, AGENTS.md.
- 29 Oct 2026: User asked to remake the Overclocked SIH26164 slides (6 pages) for SIH26265 with the same layout and new generated pictures (user approved AI pictures for slides only). Kept team ID 194901 and name Overclocked; links left as text for the user to update. Delivered Overclocked_SIH26265.pptx + .pdf in Files. THEME later set to "Smart Automation" by the user.
- 29 Oct 2026 (later): User set THEME = "Smart Automation" and asked for more references. Added 4 rows to the References slide (GFR 2017, DPDP Act 2023, IT Act 2000, Tesseract OCR). Delivered Overclocked_SIH26265_v2.pptx + .pdf (originals kept). Reported error src/main.tsx(4,23) refers to a file that does not exist; no code change.
- 29 Oct 2026: Reported src/pages/Index.tsx(14,24) TS2367 — file does not exist; no code change. Uploaded query3498.txt asks for a 3–5 min narrated explainer video (12 scenes, no AI images, no invented GitHub link/stats). Video being made as motion graphics; output in Files under videos/.
- 29 Oct 2026: Reported src/lib/utils.ts(5,16) TS2694 (React.createRoot) — that line is the tailwind-merge call, no React used; error stale, no code change. Uploaded prompt4932.txt asks for a new under-180s, 9:16 4K "3D cartoon presenter" explainer with lip-sync and human voice. Conflicts with no-AI-images rule; awaiting user choice.
- 29 Oct 2026: Vertical reel done: videos/deposit-control-tower-reel-9x16.mp4 (2:50, 1080x1920, synthetic voice, burned captions, motion graphics only) + script + .srt. Not 4K; GitHub line shown with no URL; inner app screens redrawn as labelled schematics.
- 29 Oct 2026: request1385.txt gave real links (video https://youtube.com/shorts/2Wd66hyH3og, website https://depositcontroltower.vercel.app/, GitHub https://github.com/GitOuttaHereBro/deposit-control-tower). Added as clickable links on slide 2; delivered Overclocked_SIH26265_v3.pptx + .pdf. Reported src/main.tsx(5,21) error: file does not exist; no code change.
