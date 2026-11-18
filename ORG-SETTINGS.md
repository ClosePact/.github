# Organisation settings (apply by hand)

These settings are public. An organisation owner applies them in the GitHub web UI. They are not changed by automation, because the current CLI token has `read:org` only, and avatars cannot be set through the API.

## Settings → Profile (`https://github.com/organizations/ClosePact/settings/profile`)

| Field | Value |
|---|---|
| Organization display name | `Closepact` |
| Description | `Swedish business software for service companies. Quotes, e-signatures, ROT/RUT invoicing, accounting exports and APIs.` |
| URL | `https://closepact.com` |
| Profile picture | `assets/avatar-512.png` (512×512 PNG, Closepact's Cp monogram on indigo `#4A3AFF`) |
| Public email | leave empty, or a role address the team reads; never a personal address |
| Location | `Sweden` |

## Verified domain (`closepact.com`)

Source: GitHub Docs, *Verifying or approving a domain for your organization* (read 2026-11-18).

1. *Settings → Verified and approved domains → Add a domain* → `closepact.com`.
2. Under *Add a DNS TXT record*, GitHub shows the record's name and value. They exist only in that dialog, so copy them from there; GitHub's documentation does not state their form, and they are not reproduced here.
3. Add the TXT record in the DNS for closepact.com (Cloudflare). Check it with `dig <record name> +nostats +nocomments +nocmd TXT`; GitHub says it can take up to 72 hours. Then use *Continue verifying* on the pending domain.
4. The *Verified* badge appears only if the website and email shown on the profile are on the verified domain. Keep the URL `https://closepact.com`, and any public email `@closepact.com`.
5. The TXT record may be deleted once the badge shows.

The DNS change is the owner's decision and is not made by automation.

## After the first public repository

- Make `ClosePact/.github` public, so the profile README is shown.
- Pin `rot-rut-xml`.
- Pin `sie4-validator` only after its release gate (real imports into Fortnox and Spiris, or the owner's explicit decision).
- Don't pin anything private, empty or planned.
- Turn on *Private vulnerability reporting* for each public repository (*Settings → Code security*).
