# Security Policy

## Supported Version

The latest version on the `main` branch is supported.

## Privacy Model

Quizely processes CSV files entirely inside the user's browser. It does not send quiz files to a server, API, analytics service, or database.

## Reporting a Vulnerability

If you find a security or privacy issue, please open a GitHub issue with a clear description and reproduction steps. If the issue includes sensitive details, contact the repository owner privately through GitHub before posting public proof-of-concept material.

## Security Expectations

- Do not add remote data collection.
- Do not introduce required backend services.
- Do not store quiz content outside the user's browser without explicit user control.
- Escape user-provided question and answer content before rendering.
