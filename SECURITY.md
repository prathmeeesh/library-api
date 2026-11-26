# Security Policy

## Supported versions

This repository holds the original .NET 8 prototype of the Library API. It is not maintained and receives no security fixes. .NET 8 reached end of support on 10 November 2026.

## Historical credential exposure

Commits `50fa502` and `034580f` included a JWT signing key in `appsettings.json`. The key is treated as compromised:

- It has been removed from the current branch, but it remains in Git history and in any existing clones.
- It must never be used. Any environment that trusted it must switch to a newly generated key. Changing the key invalidates every token signed with the old one.
- The Folio (.NET 10) implementation refuses to start with this key.

The committed connection string used Windows integrated authentication and contained no password.

## Configuration

Never commit keys, passwords or connection strings that contain credentials. Supply them through environment variables or untracked configuration files.

## Reporting a vulnerability

Please do not open a public issue containing exploit details or secret values. Report privately through GitHub's private vulnerability reporting (Security tab, "Report a vulnerability") if it is enabled, or contact the maintainer through their GitHub profile.
