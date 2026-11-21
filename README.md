# soren-blog-keepalive

Daily GitHub Actions ping for the Supabase project behind `blog.sorens.dev`.

Supabase pauses free projects after **7 days of low database activity**, and its
docs say a few requests **each day** over the previous week are typically
needed. This workflow calls the `ping()` RPC daily at 03:17 UTC.

The workflow also writes a monthly `.keepalive` commit so GitHub does not
disable the scheduled workflow for repository inactivity.

## Required repository secrets

- `SUPABASE_URL` — `https://xexpqikdhmggwpuuloca.supabase.co`
- `SUPABASE_ANON_KEY` — the project's publishable key

The key is public by design; it is stored as a secret only to keep the workflow
configuration tidy.

## Manual run

Actions → **Supabase keepalive** → **Run workflow**. A successful run returns
`{"ok":true}` from the `ping` RPC.

## If the project is already paused

Open the Supabase dashboard once to resume it, then run this workflow manually.
