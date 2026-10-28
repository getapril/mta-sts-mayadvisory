# MTA-STS static hosting (mayadvisory.com)

This repository serves the [MTA-STS](https://www.rfc-editor.org/rfc/rfc8461) policy for **mayadvisory.com** as a static GitHub Pages site on the `mta-sts.mayadvisory.com` subdomain.

The policy previously lived in [`getapril/may-marketing-website`](https://github.com/getapril/may-marketing-website) (`public/.well-known/mta-sts.txt`) and is now hosted here independently of the marketing site.

Sending mail servers fetch:

```text
https://mta-sts.mayadvisory.com/.well-known/mta-sts.txt
```

## Files

| Path | Purpose |
| --- | --- |
| `.well-known/mta-sts.txt` | Published MTA-STS policy (RFC 8461) |
| `CNAME` | GitHub Pages custom domain: `mta-sts.mayadvisory.com` |
| `.nojekyll` | Tells GitHub Pages to serve the `.well-known` directory as-is |

## Policy

The current policy is in **testing** mode with a 7-day `max_age` (`604800` seconds) and the standard Google Workspace MX hosts:

- `aspmx.l.google.com`
- `alt1.aspmx.l.google.com`
- `alt2.aspmx.l.google.com`
- `alt3.aspmx.l.google.com`
- `alt4.aspmx.l.google.com`

Leave `mode: testing` until HTTPS serving and MX alignment are confirmed. Then change that line to `mode: enforce`, commit, push, and bump the `_mta-sts` TXT `id` in DNS so senders refetch the policy.
