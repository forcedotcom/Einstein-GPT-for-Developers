# Extension version policy

Remote compatibility floor for Agentforce Vibes. Clients fetch this document from:

`https://raw.githubusercontent.com/forcedotcom/Einstein-GPT-for-Developers/main/version-policy.json`

## Fields

| Field | Meaning |
| --- | --- |
| `requiredVersion` | Hard floor. Installed versions **strictly below** this value refuse Agentforce Vibes LLM turns until the extension is updated. |
| `recommendedVersion` | Soft nudge. Installed versions at or above `requiredVersion` but **strictly below** this value keep chat enabled and may show a dismissible update banner. |

Both values must be exact SemVer strings. Unknown fields are ignored so future keys (`latestVersion`, changelog text, etc.) can land without breaking older clients.

## Operator rules

1. Raising `recommendedVersion` and raising `requiredVersion` are **separate reviewed** actions. Prefer nudging (`recommendedVersion`) before enforcing (`requiredVersion`).
2. Never publish `requiredVersion` greater than `recommendedVersion`. Clients treat that document as invalid and fail open.
3. Rollback lowers `requiredVersion` (and may lower `recommendedVersion` independently). Clients adopt a successful fetch; a failed fetch keeps the last good cached document for that host.
4. Clients may take up to **24 hours** plus the lifetime of an already-running host to observe a change.
5. Fetch or parse failure **fails open** (chat continues). This is best-effort compatibility guidance, not a security boundary.
6. Releases shipped before the client that reads this file are out of reach of the gate.

## Day-one no-op

Shipping `0.0.0` / `0.0.0` means every installed build is at or above both floors, so no client refuses turns and no recommended banner appears until operators deliberately raise a field.
