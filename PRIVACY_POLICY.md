# PushyUncommit Privacy Policy

**Effective Date:** May 17, 2026
_Last updated: November 9, 2026_
**Version:** 1.2.0

PushyUncommit ("we," "our," or "us") is a developer tool you run on your own machine. It is a Python command-line program (`puc`) that scans directories for git repositories and reports which ones have uncommitted or unpushed work, with an optional local web dashboard, an optional GitHub integration, and an optional plugin system for notifications. This Privacy Policy explains what information the tool handles, what leaves your machine, and the choices you have. By installing or using PushyUncommit you agree to the practices described below.

## Information We Collect

### Location Data

- PushyUncommit does not collect location data.

### Account Information

- **No PushyUncommit account exists.** There is no sign-up, no login and no server of ours to log in to.
- If you use the GitHub integration, the tool reads a GitHub personal access token from the `GITHUB_TOKEN` environment variable, or one you pass in, and sends it to GitHub with each request. The token stays on your machine otherwise; we never receive it.

### Local Data

- Repository paths, git status summaries, branch and commit counts, the directories you scan and your configuration are read from and written to your own machine, under `~/.PushyUncommit/`.
- **We receive none of it.** There is no Sudarshan Tech Labs server for this tool, so there is nowhere for it to be sent.

## How We Use Your Information

### Location Sharing

- PushyUncommit does not use your location.

### What the Tool Does

- Scans the directories you point it at, finds git repositories, and reports uncommitted and unpushed work.
- Serves that report on a local web dashboard if you start one.
- Queries GitHub only when you use a GitHub feature.
- Sends a notification to a Slack, Discord, generic webhook or email destination **only if you configure a plugin with that destination yourself.**

### Service Improvement

- **The tool contains no analytics or telemetry that reports to us.** There is a bundled "analytics" plugin, but it writes to a local file (`~/.PushyUncommit/analytics.json`) and uploads nothing anywhere.
- We do not sell, rent or monetize anything about your repositories. We never receive it in the first place.

## Storage and Retention

### Data Storage

- Configuration, registered webhooks (`~/.PushyUncommit/webhooks.json`), local analytics (`~/.PushyUncommit/analytics.json`) and local backups (`~/.PushyUncommit/backups/`) are stored in your home directory.
- Repository status is read from your local git repositories each time you scan. The tool keeps no copy of your code.
- GitHub data is requested directly from GitHub by your machine when you use a GitHub feature.

### Data Retention

- Local files under `~/.PushyUncommit/` remain until you delete them or uninstall the tool.
- Your git repositories are untouched; PushyUncommit reads them and does not modify their history.

### Data Security

- Local data sits in your home directory under your operating system's own file permissions. The tool adds no encryption of its own, so anything readable by your user account is readable by anything else running as your user account.
- Network communication with GitHub uses HTTPS.
- **The local web dashboard binds to `127.0.0.1:8080` by default and is reachable only from your own machine at that address.** It supports an optional bearer token read from the `PUSHYUNCOMMIT_DASHBOARD_TOKEN` environment variable. **With that variable unset there is no authentication at all**, so do not bind the dashboard to a network-reachable address without setting it — anyone who can reach the port would see your repository paths and status.
- You should protect your machine with a screen lock and your GitHub account with two-factor authentication, since those are what stand between someone else and this data.

## Data Sharing

### Sharing With Other People

- **PushyUncommit has no accounts, no pairing and no collaboration features.** Nothing is shared with anyone unless you configure a notification plugin or run the dashboard somewhere others can reach.

### Third Parties

- **GitHub** (`https://api.github.com`) receives API requests, and your token if you supplied one, only when you use a GitHub feature.
- **unpkg.com and cdn.jsdelivr.net** receive a request from your browser whenever you open the local web dashboard. The dashboard page loads three third-party scripts from them — Vue and Axios from `https://unpkg.com`, Chart.js from `https://cdn.jsdelivr.net` — so those content delivery networks see your IP address, your browser's user agent and the fact that you loaded the page. They do not receive your repository paths or contents, which stay in the local response your own machine serves. This disclosure was missing from earlier versions of this policy.
- **A notification destination you configure yourself.** The Slack, Discord and generic webhook plugins post to a URL you supply, and what they send includes the repository name, the issue type and **the repository's path on your filesystem**. The email plugin sends through an SMTP server you supply, using credentials you supply. None of these is enabled by default, and none of them sends anything to us.
- **No repository contents and no code are sent anywhere by the tool**, to us or to anyone else.

### The VS Code, Desktop and Mobile Front Ends

PushyUncommit also ships three optional front ends. None of them contacts us or any third party:

- **The VS Code extension** makes no network request at all. It runs `git` on your machine and reads the result. Note that its commit-and-push action does run `git push`, which sends your commits to whichever remote that repository already points at — your own GitHub, GitLab or other host. That is the same thing as pushing from your terminal, and it happens only when you use that action.
- **The Electron desktop app** loads only files bundled inside it, enforced by a content security policy of `default-src 'self'`. It fetches nothing from the internet, including from a CDN.
- **The React Native mobile app** connects to one address: the dashboard URL you type into it yourself, normally your own machine on your own network. It stores that URL and the dashboard token in the phone's `AsyncStorage`, which is ordinary app storage and not the device keychain. **If you type an `http://` address rather than `https://`, that traffic is unencrypted**, so anyone else on the same Wi-Fi can read your repository list and capture the dashboard token as it goes past. Use it on a network you trust.

We do **not** share your data with:

- Data brokers
- Unrelated advertising networks, unless advertising is explicitly listed above for this app
- Third parties unrelated to the app features described in this policy

## Permissions and Access

### What the Tool Needs

* **Filesystem read access** to the directories you ask it to scan, and to the git metadata inside them. This is how it works out what is uncommitted.
* **Write access to `~/.PushyUncommit/`** for configuration, webhook registrations, local analytics and local backups.
* **Network access** only for the GitHub integration, for a notification destination you configured, and for the dashboard page's three third-party scripts. Without those features the tool makes no outbound network connection.

PushyUncommit is not an Android app and has no mobile permission model. Earlier versions of this policy described Android permissions and Android Settings; neither applies.

### Optional Integrations

* The GitHub integration, the local web dashboard and every notification plugin are off until you configure them.

## Your Rights and Controls

### Location Sharing Control

- No location sharing exists in PushyUncommit.

### Account Management

- There is no PushyUncommit account to manage. GitHub account and token controls live in your GitHub settings, where a token can be revoked at any time.

### Data Access

- Everything the tool stores is a plain file under `~/.PushyUncommit/` that you can read, edit or delete yourself.

### GDPR Rights (EU Users)

If you are in the European Union, you have additional rights:

- **Right to Access**: Request a copy of your personal data
- **Right to Rectification**: Correct inaccurate data
- **Right to Erasure**: Request deletion of your data
- **Right to Restrict Processing**: Limit how we use your data
- **Right to Data Portability**: Receive your data in a portable format
- **Right to Object**: Object to certain types of processing

In practice we hold no personal data about you to access, correct or erase, because the tool sends us nothing. To exercise these rights anyway, contact us using the methods in the Contact Us section.

### Turning Integrations Off

- Remove the GitHub token, or unset `GITHUB_TOKEN`, and the GitHub integration stops.
- Stop the dashboard process and nothing is served, and no CDN request is made.
- Remove a notification plugin's configuration and it stops sending.

## Children's Privacy

- Our app is **not intended for children under 13**.
- We do not knowingly collect data from children under 13.
- If you are a parent or guardian and believe your child has provided personal information, please contact us to request deletion.
- Parents and guardians should supervise children's use of apps that store personal content.

## Security

- Local data is protected by your operating system's file permissions. PushyUncommit adds no encryption of its own.
- Network communication with GitHub uses HTTPS.
- The local dashboard is unauthenticated unless you set `PUSHYUNCOMMIT_DASHBOARD_TOKEN`. Keep it bound to `127.0.0.1` if you do not set it.
- Third-party services named in this policy provide their own security controls and privacy policies.
- You are responsible for protecting your machine, your GitHub token and any SMTP or webhook credentials you put in a plugin's configuration.
- We do not sell your personal data. We never receive it.

## Changes to This Policy

We may update this Privacy Policy to reflect new features, legal requirements, or changes in our practices. Significant changes will be:

- Noted in the app release notes or repository when applicable
- Reflected with a new "Last updated" date
- Communicated in the app or project page if the change is significant

The "Last updated" date at the top of this policy indicates when revisions occurred. Continued use of the app after changes constitutes acceptance of the updated policy.

## Contact Us

If you have questions about this Privacy Policy, wish to request data deletion, or have privacy concerns:

* **GitHub Repository:** https://github.com/SUDARSHANCHAUDHARI/pushyuncommit-privacy-policy
* **Email:** sunny.sudarshan@gmail.com
* **Main App Repository:** https://github.com/SUDARSHANCHAUDHARI/PushyUncommit

We will respond as quickly as possible, typically within 48 hours.

## Data Deletion

### How to Delete Your Account

There is no account. Everything the tool keeps is local, so deletion is something you do yourself:

#### Option 1: Delete the Local Files

1. Delete `~/.PushyUncommit/` to remove the configuration, registered webhooks, local analytics and local backups.
2. Uninstall the package (`pip uninstall pushyuncommit`) to remove the tool itself.
3. Your git repositories are not touched by either step.

#### Option 2: Email Deletion Request

Send an email to: **support@sudarshantechlabs.com** or **sunny.sudarshan@gmail.com**

- Subject: "Data Deletion Request - PushyUncommit"
- We will answer honestly that we hold nothing of yours, because the tool sends us nothing, and confirm that in writing if you need it for a record

#### Option 3: Revoke What You Granted Elsewhere

1. Revoke the GitHub personal access token in your GitHub settings.
2. Delete any Slack or Discord webhook URL you created, at Slack or Discord.
3. Ask a notification destination's operator to delete messages already delivered there — we cannot, because we never had them.

### What Gets Deleted

- Everything under `~/.PushyUncommit/`: configuration, `webhooks.json`, `analytics.json` and `backups/`
- Nothing on our side, because there is nothing on our side

### Data Retention After Deletion

- **Immediate:** deleting `~/.PushyUncommit/` removes all local tool data at once
- **Uninstall:** removes the program; it does not remove `~/.PushyUncommit/`, so delete that too
- **Notifications already sent:** remain wherever you sent them — a Slack channel, a Discord server, a mailbox, your own webhook endpoint — until deleted there

## Third-Party Services

The tool itself contacts exactly one service, and only when you ask it to:

- **GitHub API** (`https://api.github.com`), for the optional GitHub integration

The local web dashboard additionally loads three scripts from two content delivery networks when you open it in a browser:

- **unpkg.com** — Vue and Axios
- **cdn.jsdelivr.net** — Chart.js

**The tool uses no Firebase and no Google service of any kind.** Earlier versions of this policy named Firebase three times, including as a security control and in a section heading, and linked the Firebase and Google privacy policies. There is no Firebase in the source: it appears nowhere in the code. Those claims were wrong and have been removed. There is also no advertising SDK, no crash reporting and no backend of ours.

Please review the relevant third-party policies:

- [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-privacy-statement)
- [npm (unpkg) Privacy Policy](https://docs.npmjs.com/policies/privacy)
- [jsDelivr Privacy Policy](https://www.jsdelivr.com/terms/privacy-policy-jsdelivr-net)

## About PushyUncommit

PushyUncommit is built with privacy in mind. The tool is built with:

- Python, as a command-line program (`puc`)
- Local git inspection, reading your repositories where they already are
- A FastAPI local web dashboard, bound to `127.0.0.1` by default
- An optional GitHub integration, using a token you supply
- An optional plugin system for notifications, each off until you configure it

Your code never leaves your machine. The things that can leave it are a GitHub API request, a notification you configured, and the three CDN script requests your browser makes when you open the dashboard — and this policy now names all of them.

---

**Last Updated:** November 9, 2026

---

## Recent Updates (Version 1.2.0 - November 9, 2026)

- **Removed the false Firebase claims.** The policy named Firebase as a security control protecting your data, titled a whole section "Firebase and Google Services", and linked the Firebase privacy policy. PushyUncommit contains no Firebase and no Google service at all. A policy naming a service that is not in the app is wrong even when the claim sounds reassuring.
- **Disclosed the two content delivery networks the dashboard loads from.** Opening the local web dashboard makes your browser fetch Vue and Axios from `unpkg.com` and Chart.js from `cdn.jsdelivr.net`, so both see your IP address. Neither was mentioned anywhere in the previous policy. They receive no repository data.
- **Said what the notification plugins send and where.** The Slack, Discord and generic webhook plugins post the repository name, the issue type and **the repository's path on your filesystem** to a URL you configure; the email plugin uses an SMTP server you supply. The old policy's "GitHub receives API requests only when you use GitHub integration" implied GitHub was the only destination.
- **Named `api.github.com` as the only host the tool itself contacts**, and said the GitHub token is read from `GITHUB_TOKEN` and sent to GitHub with each request.
- **Said the local dashboard is unauthenticated unless `PUSHYUNCOMMIT_DASHBOARD_TOKEN` is set**, and that it binds to `127.0.0.1:8080` by default. This is a real limit worth knowing before exposing the port.
- **Said the bundled analytics plugin is local-only.** It writes `~/.PushyUncommit/analytics.json` and uploads nothing. "Analytics" in a privacy policy usually means the opposite, so it is worth stating plainly.
- **Removed the Android and browser-app scaffold.** PushyUncommit is a Python command-line tool, not an Android app: the policy told you to revoke permissions in "Android Settings -> Apps -> PushyUncommit", which does not exist. The "Family Groups" heading, shared with sibling policies, is also gone — there is no pairing or sharing in this tool.
- **Replaced the mobile deletion steps with the real ones:** delete `~/.PushyUncommit/`, uninstall the package, and revoke the GitHub token and any webhook URLs at the services that issued them.
- **Covered the three optional front ends**, which the policy had never distinguished from the command-line tool. The VS Code extension makes no network request but can run `git push` for you; the Electron desktop app loads only bundled files under a `default-src 'self'` policy; the mobile app talks only to the dashboard address you type in, keeps that address and the dashboard token in ordinary `AsyncStorage` rather than the keychain, and **sends them in clear text if you give it an `http://` address.**

## Recent Updates (Version 1.1.0 - May 17, 2026)

- **Aligned policy with the shared privacy-policy structure.**
- **Clarified local developer-tool data, local server use, and GitHub integration.**
