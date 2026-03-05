# CLAUDE.md — Setup Guide

## Projekt

Interaktiver Setup Guide fuer Multi-Agent Development mit Claude Code. Erklaert den Weg von einfacher AI-Chat-Nutzung (L1) bis zu autonomen Agent-Teams (L4). Publiziert als GitHub Pages Website.

## Agent-Identitaet

Agent-Identitaet wird vom Orchestrator per Prompt zugewiesen. Status-Files werden vom Orchestrator verwaltet. Agents muessen sich NICHT selbst benennen und NICHT ihr Status-File auf online/offline setzen.

## Tech Stack

- **Static Site:** Jekyll + Cayman Theme + GitHub Pages
- **Content:** Markdown + inline HTML/CSS + SVG-Diagramme
- **URL:** https://sutermarkus-rakoon.github.io/setup-guide/
- **Keine Build-Dependencies:** Nur Jekyll Remote Theme

## Wichtige Dateien

```
index.md                     — Gesamter Content (Tabs, Sub-Tabs, alle Sektionen)
_layouts/default.html        — Layout Template (Cayman Theme Override)
assets/                      — Bilder (Screenshots, Diagramme)
_config.yml                  — Jekyll Config
```

## Struktur

- **Tab-Navigation:** Overview / Basic / Advanced
- **Advanced Sub-Tabs:** Classic / Autonomous
- **5 Autonomie-Level:** L1 (Chatbot) → L2 (Pair Programmer) → L3 (Agent) → L4 (Multi-Agent) → L5 (Self-Improving)
- **Inhalte:** Quick-Start Checklisten, ASCII-Diagramme, Vergleichstabellen, SVG-Grafiken

## Konventionen

- **Sprache:** Englisch (komplett)
- **Styling:** Inline HTML/CSS in Markdown
- **Diagramme:** SVG inline im Markdown
- **Commits:** `feat:` / `fix:` + Beschreibung
