# NIXX WOP Roblox Access API

Executor-facing API for the NIXX username-only 24-hour access system.

Endpoint: `POST /api/roblox/access`

The WOP deployment MUST use the exact same Upstash Redis database as the main NIXX website.

Required Vercel environment variables:
- `UPSTASH_REDIS_REST_URL`
- `UPSTASH_REDIS_REST_TOKEN`

Request from the Roblox script:
```json
{
  "mode":"check",
  "robloxUserId":5208000032,
  "robloxUsername":"zararuuu"
}
```

The website creates the record under `roblox_access:<UserId>` with a 86400-second TTL. WOP only checks it when `mode=check`; it does not extend the timer.
