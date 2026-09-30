---
name: vps
description: Servers and infrastructure — remote hosts, SSH, reverse proxies, TLS, systemd, deployment, firewall, and incident response. Triggers on "server", "vps", "ssh", "deploy", "nginx", "caddy", "firewall", "disk full", "cert", "port", "uptime", "service is down".
---

# VPS

## When to use

A machine that stays up, or did not. Nothing here assumes a cloud provider or a specific distro.

## Rules

- Read-only first. Inventory the actual state before changing it: `systemctl status`, `ss -tlnp`,
  `df -h`, `journalctl`. Never fix from a guess about what is running.
- One change at a time, with the rollback stated before the change. Batched changes are undebuggable.
- Destructive or network-facing changes need explicit consent: `rm`, `iptables`, `systemctl stop`,
  anything on a live port. Name the blast radius first.
- Back up the config before editing it, to a path I tell the user about.
- Secrets never go in a shell history, a world-readable file, or a commit. Env files are `chmod 600`.
- SSH: key auth only, no root login, fail2ban, and never `StrictHostKeyChecking=no` as a habit.
- TLS via a real ACME client. No self-signed certs in a path the user will later call production.
- Deploys are restartable: keep the previous release on disk, know the one command to go back.
- Containers bind to `127.0.0.1` unless they are genuinely meant to be reachable.
- Verify after acting: check the port answers, the service is active, the endpoint returns real data.
- Never leave a service "probably running". Start it, watch it, report what the log said.

## Done when

- The service is observed healthy, not assumed.
- The rollback path exists and was stated before the change.
