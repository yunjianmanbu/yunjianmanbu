# yunjianmanbu

**Pilot** — a local-first autonomous coding agent that runs on your own computer, plus the two
phone-side ends and a self-hosted relay that go with it. Four repositories, four directions of
control, one permission model and one redacted audit log.

**English** | [中文](README.zh-CN.md)

**Website & downloads:** <https://pilot.medpilot.cc/> — one page with every installer.
**Docs:** [Wiki](https://github.com/yunjianmanbu/pilot/wiki) · [Responsible use](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md)

## The four repositories

| Repo | What it is | Who controls whom | Version |
| --- | --- | --- | --- |
| **[pilot](https://github.com/yunjianmanbu/pilot)** | Desktop agent: reads your code, runs commands, edits files, verifies the result. Electron + React, DeepSeek or any OpenAI-compatible model, no sign-in, no cloud database. | person → computer | v0.1.88 |
| **[pilot-link](https://github.com/yunjianmanbu/pilot-link)** | Phone app (uni-app) that turns your phone into a remote control for that desktop agent: send a prompt, read the answer, approve or refuse a tool call. | phone → computer | v1.1.4 |
| **[pilot-client](https://github.com/yunjianmanbu/pilot-client)** | The reverse direction: the desktop sees and operates the phone — screen, taps, notifications, files — behind a 12-group capability catalogue and an audit log. **Beta**: everything needing an Android system service still answers `not_granted`. | computer → phone | beta · v1.0.5 |
| **[pilot-connector](https://github.com/yunjianmanbu/pilot-connector)** | Relay + connector you host yourself, so pairing and command traffic never touch a server you do not own. The project ships no public relay. | phone ↔ computer ↔ desktop | v0.2.3 |

```
 phone (Pilot Link) ──┐
                      ├── relays you host (pilot-connector)
 phone (Pilot Client) ┘              │
                                     │  ECDH P-256 + AES-256-GCM, per-pairing keys
                                     ▼
                        desktop agent (Pilot) — your files, your model key
```

## Start here

| If you want to… | Go to |
| --- | --- |
| Try the agent on your machine | [pilot README · Quick start](https://github.com/yunjianmanbu/pilot#quick-start) |
| Drive it from your phone | [pilot README · Phone connection](https://github.com/yunjianmanbu/pilot#phone-connection) |
| Run it headless on a server, with a browser console | [pilot README · Headless server mode](https://github.com/yunjianmanbu/pilot#headless-server-mode) |
| Pair a phone without any third-party server | [pilot-connector](https://github.com/yunjianmanbu/pilot-connector) |
| Understand the permission gates before installing | [pilot README · Security](https://github.com/yunjianmanbu/pilot#security) · [RESPONSIBLE_USE.md](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md) |
| See what changed, per release | [pilot](https://github.com/yunjianmanbu/pilot/blob/main/CHANGELOG.md) · [pilot-link](https://github.com/yunjianmanbu/pilot-link/blob/main/CHANGELOG.md) · [pilot-client](https://github.com/yunjianmanbu/pilot-client/blob/main/CHANGELOG.md) · [pilot-connector](https://github.com/yunjianmanbu/pilot-connector/blob/main/CHANGELOG.md) |

## Three things that are not negotiable

1. **Nothing leaves your machine unless you point it at a model.** No account system, no cloud
   database, no telemetry; the API key you type stays in the local config.
2. **Every action is gated, and refusals are logged.** Destructive commands sit above the policy
   ceiling, level-2+ phone actions need an on-phone confirmation, and the audit log redacts
   clipboard text, SMS bodies, file paths and phone numbers.
3. **Use it only on devices you own or are authorized to control.** Covert monitoring, bulk account
   farming and help-desk scams are out of scope, and the project says so in public:
   [RESPONSIBLE_USE.md](https://github.com/yunjianmanbu/pilot/blob/main/RESPONSIBLE_USE.md).

All four repositories are Apache-2.0. Bug reports and ideas are welcome in
[Issues](https://github.com/yunjianmanbu/pilot/issues/new/choose) and
[Discussions](https://github.com/yunjianmanbu/pilot/discussions); security issues go through
[SECURITY.md](https://github.com/yunjianmanbu/pilot/blob/main/SECURITY.md).
