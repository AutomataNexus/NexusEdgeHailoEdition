# Changelog

All notable changes to NexusEdge Hailo Edition will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-05-24

Public release.

### Added
- **OTA Logic Deploy Pipeline** — Remote logic deployment with ed25519 signing, controller signature verification, hot-reload, and operational health check. Sandbox editor for testing before deploy. Automatic backup before overwrite, one-click rollback.
- **NexusEdge Console** — Multi-tenant fleet management platform with 13 pages: Dashboard, Controllers, Logic Deploy, Backups, Audit Trail, Security, Fleet Graph, AegisDB Admin, Organization, Downloads, Status, Profile, Settings.
- **3-Level RBAC** — App-level (Firebase auth → org), org-level (granular permissions per member), site-level (restrict members to specific locations). Zero cross-org, zero cross-site visibility.
- **Controller Count Enforcement** — Community: 1, Pro: 10, Business: 25, Enterprise: 50, Enterprise+: unlimited. Server-side enforced on provisioning.
- **Thoth HVAC Fault Classifier** — 24 equipment-specific on-device Hailo NPU models. 42 fault categories (mechanical, control, operational, system). 0.914–0.960 F1. Auto-loads per equipment type from site config.
- **Anubis SIEM Threat Detector** — On-device Hailo NPU security model. 34 threat categories. 0.982 F1. Classifies NexusShield audit events in real time.
- **150+ Embedded Neural Models** — Nehebkau LSTM + Medjed GRU + Thoth fault classifier + Anubis SIEM + Sage BOW. Chip-aware loading (Hailo-8 vs Hailo-10H auto-detected).
- **AegisDB 13-Paradigm Backend** — Document Store, Key-Value, Streaming, Graph, Time Series, OTA Updates, Vault, Shield, Query Builder, Compliance, Admin, Auth, Cluster. All wired end-to-end through AN server.
- **NexusShield SIEM Export** — Audit trail forwarding to Syslog (UDP/TCP), Elasticsearch, Splunk HEC, and webhook destinations.
- **Firebase → AegisDB Write-Through Sync** — Every Firebase write (user, org, controller, membership) synced to AegisDB document store + KV + SQL.
- **Console Remote Push** — Controllers push sensor metrics (15s), status + alarms (60s), audit trail (5m) to AN server for Console display.
- **Cream/Black Deployment** — Blue/green deployment for AN server landing + console and controller binary. Auto-failover watchdog with 30s health checks.
- **Paid Tier Gating** — Console pages tier-gated. OTA deploy requires Pro+. Org management requires Business+.
- **Headless Installer Improvements** — `--accept-eula`, `-y` auto-accept, WiFi rescan before connect, non-interactive mode when email+password provided.

### Changed
- **Landing Page Overhaul** — Updated all sections: hero, platform (42 algos, 150+ models, 13-paradigm DB), quick-start (6 tabs), architecture (6 layers), console (OTA/SIEM/RBAC), use cases, pricing (controller limits), FAQ (10 questions), community.
- **Pricing Tiers** — Added controller limits per tier. Added sandbox + OTA deploy to Pro. Added fleet console + org RBAC to Business. Removed unbuilt claims (SSO/SOC2/white-label).
- **EULA** — Removed NexusRT/nexus-serve references. "NexusEdge Hailo Edition" naming. Broader restriction on proprietary component extraction.
- **Privacy Policy** — Rewritten with honest per-tier data handling. Sections 03/04 as proper HTML lists. Added Console reporting disclosure for paid tiers.
- **Terms of Service** — Updated to match EULA changes.
- **Docker Image** — Renamed from `nexusedge-hailocommunityedition` to `nexusedge-hailoedition`.

### Fixed
- **Axum 0.8 Route Syntax** — Path parameters updated from `:key` to `{key}`.
- **Chip Detection** — Auto-detect Hailo-8 vs Hailo-10H from firmware, load correct model variants.

## [0.9.0] - 2026-05-22

### Added
- Initial release with 42 algorithms, 24 equipment types, 98 embedded Hailo HEF models
- AegisDB embedded time-series database with NexusCompress columnar compression
- NexusVault AES-256-GCM encrypted credential storage
- NexusShield security middleware, RBAC, breach detection
- TMC (Thermal Momentum Control) algorithm — field-validated across 113 units
- 8 board types (MegaBAS, MegaIND, 16 Univ-In/Out, 16/8 Relay, 16 SSR, 8 RTD)
- Setup Wizard v2 — 8-step guided first-boot configuration
- Headless + GUI installers with server-side provisioning
- SLSA Level 3 supply chain attestation
- Tauri desktop UI + embedded web server on port 8000
