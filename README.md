> **⚠️ EDUCATIONAL USE ONLY — AUTHORIZED TESTING ONLY.**
> This project exists for education, research, and **defense of systems you own
> or hold explicit written authorization to assess**. Unauthorized use is
> prohibited and may be illegal. Read [ETHICS.md](ETHICS.md) and
> [SCOPE.md](SCOPE.md) before use. Use at your own risk; **AS IS**, no warranty.

# SSH Auditor — SSH Security Auditing & Banner Analysis Tool

[![License](https://img.shields.io/github/license/5h4d0wn1k/ssh-auditor)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.1.0-blue)](VERSION)
[![Stars](https://img.shields.io/github/stars/5h4d0wn1k/ssh-auditor)](https://github.com/5h4d0wn1k/ssh-auditor/stargazers)
[![Last Commit](https://img.shields.io/github/last-commit/5h4d0wn1k/ssh-auditor)](https://github.com/5h4d0wn1k/ssh-auditor/commits/main)
[![Issues](https://img.shields.io/github/issues/5h4d0wn1k/ssh-auditor)](https://github.com/5h4d0wn1k/ssh-auditor/issues)

**SSH Auditor** is a lightweight, async Python tool for SSH security auditing:
service availability checks, banner grabbing, and optional credential-file
testing — designed for lab environments and hosts you own or are authorized
to assess.

## Why SSH Auditor?

SSH exposure is one of the most common and dangerous opening vectors in
network security. SSH Auditor gives students and authorized testers a minimal,
readable audit path: validate the target, confirm the SSH service is
reachable, extract its version banner, and — in a lab, with `--creds` — verify
reachability against a hand-curated credential list. It deliberately keeps
dependencies tiny (only `paramiko` as an optional extra), refuses
multicast/unspecified targets, and prints an authorized-use reminder on every
run so the education-first intent stays explicit.

## Features

- **Target validation** — refuses multicast and unspecified IP targets
  (`validate_target`).
- **Async banner grabbing** — grabs the SSH service banner over a TCP
  connection with a configurable timeout.
- **Port & timeout control** — `--port` (default 22) and `--timeout`
  (default 3s) flags.
- **Credential file testing** — optional `user:pass` list via `--creds`
  (lab-only reachability demonstration, no real auth).
- **Zero-dependency core** — stdlib `asyncio`/`socket`; `paramiko` optional.
- **Safety rails** — prints an authorized-use-only notice at startup.

## Quickstart

### Prerequisites

- Python 3.8+
- `pip install paramiko` (optional; only if you want full auth support)

### Run an audit

```bash
git clone https://github.com/5h4d0wn1k/ssh-auditor
cd ssh-auditor
python ssh_audit.py --host <your-host-or-ip>
```

Custom port and timeout:

```bash
python ssh_audit.py --host 192.0.2.10 --port 2222 --timeout 5
```

Lab credential-file check:

```bash
python ssh_audit.py --host localhost --creds creds.txt   # user:pass per line
```

## Project Structure

- `ssh_audit.py` — CLI: target validation, banner grab, credential test.
- `requirements.txt` — Python dependencies.
- `VERSION` — Current release version.
- `ETHICS.md`, `SCOPE.md` — Authorized-use guidelines.

## Documentation

- [ETHICS.md](ETHICS.md) — Educational purpose and authorized use only.
- [SCOPE.md](SCOPE.md) — Authorized scope of testing.
- [SECURITY.md](SECURITY.md), [CONTRIBUTING.md](CONTRIBUTING.md),
  [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Contributing

Contributions for educational and authorized-testing research are welcome. See
[CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## License

MIT License — see [LICENSE](LICENSE) for details.

> **⚠️ EDUCATIONAL USE ONLY — AUTHORIZED TESTING ONLY.**