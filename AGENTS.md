<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## Architecture rules
- All writes (cases, documents, evidence, clearances, decisions, roles) go through server functions in `src/lib/actions.functions.ts` that check roles, then write with the admin client and append an `audit_events` row. Why: authenticated users have SELECT-only grants, so state gates can't be bypassed from the browser.
- Release rules live only in `src/lib/rules.ts` (versioned `RULE_PACK_VERSION`), shared by UI and server; tests in `src/test/rules.test.ts`. Why: one deterministic rule source, cited per blocker.
- Case readiness is derived on read (`src/lib/case-bundle.ts`), never stored. Why: avoids stale status and needs no scheduled jobs.
- `audit_events` is append-only (trigger blocks UPDATE/DELETE). Why: replayable audit trail.
- Case documents live in the private `case-documents` bucket under `{institution_id}/{case_id}/…`; files open via short-lived signed URLs. Why: no public file URLs.
- Roles are in `user_roles` (first sign-up gets admin + all staff roles; later sign-ups get `institution`). Why: avoid privilege escalation via profile edits.
