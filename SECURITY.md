# Security Policy

## Supported Versions

Only the latest release of the `pair-programming` skill receives security fixes. Please update to the newest version before reporting an issue.

## Scope

This repository contains an agent skill made of plain instructions, with no runtime code, scripts or dependencies. Relevant reports include:

- Instructions in the skill that could lead an agent to take actions the developer has not approved, such as running commands, changing files, committing, pushing or making network requests.
- Weaknesses in the GitHub Actions workflow in `.github/workflows`, such as excessive permissions or unsafe handling of untrusted input.

## Reporting a Vulnerability

Please do not open a public issue for a vulnerability.

Report it privately through GitHub: open the **Security** tab of this repository and choose **Report a vulnerability**.

Please include what you found, how to reproduce it and which version it affects.

You can expect an acknowledgement within a few days. After that I will assess the report, tell you whether it is accepted or declined, and keep you updated on the fix. This is a personally maintained project, so I cannot promise fixed response times.
