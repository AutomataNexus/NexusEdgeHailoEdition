# Changelog

All notable changes to NexusEdge Hailo Edition will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

> Every version tag publishes SLSA L3-attested binaries for Raspberry Pi 5 /
> Compute Module 5 (aarch64) and x86_64; Raspberry Pi 4 (Bullseye) headless
> builds ship as their own labeled assets.

## [1.8.1] - 2026-06-06

### Hardware
- Dedicated, independently-attested build for the Raspberry Pi Compute Module 5 (eMMC); the installer auto-detects the CM5 on fresh install and update.

## [1.8.0] - 2026-06-06

### Reliability & safety
- Resilient hardware I/O — an offline or missing board is re-probed with backoff instead of polled continuously, preventing bus stalls.
- Engine-level life-safety interlock drives all outputs off ahead of normal control on a smoke/fire signal.
- Clearer health reporting and startup diagnostics so a configuration problem can't quietly leave control inactive.

### Performance
- Faster on-device data compression (lossless).

## [1.7.0] - 2026-06-06

### Security & reliability
- Strengthened binary anti-tamper protection for production deployments.
- Reproducible, supply-chain-attested (SLSA L3) builds.
- Hardened configuration loading so a malformed config can't silently leave a controller with no equipment running.

## [1.6.5] - 2026-06-04

### Changed
- Refreshed the controller sign-in screen to match the NexusEdge Console (light + dark).

### Added
- One-click commissioning — provision a controller directly into an organization.

### Fixed
- Pre-configured installs now come up fully set up instead of re-prompting the setup wizard.

## [1.6.4] - 2026-06-03

### Added
- Mobile app integration with longer-lived sign-in sessions and remote equipment control.
- Multi-tenant organization scoping — each site sees only its own equipment, metrics, and users.
- Faster manual-control response on networked controllers.

## [1.6.3] - 2026-06-03

### Added
- Manage controllers from the Console — remote update, reboot, and one-click rollback, each moving equipment to a safe state first.
- Signed control-logic deployment with versioned backups.

### Fixed
- More accurate online/offline status on the fleet dashboard.
- Headless (no-display) controllers now report telemetry correctly.

## [1.6.2] - 2026-06-03

### Fixed
- More reliable controller identity and organization/licensing assignment across re-provisioning.
- Fault-detection refinements using outdoor-air-temperature context.

## [1.6.1] - 2026-06-02

### Added
- Embedded fault-detection and prediction models tuned for natatorium (indoor pool) systems.
- Read-only diagnostic snapshot for a Console-initiated AI diagnosis.

### Fixed
- Corrected loading of the on-device fault-classifier models.

## [1.6.0] - 2026-06-02

### Added
- **NexusOracle AI diagnostics (paid tiers)** — natural-language questions about equipment faults; the controller shares only a read-only snapshot of its own state, with per-user usage limits. The Community tier keeps the built-in retrieval assistant.
- **Live Hailo NPU dashboard** — real-time silicon telemetry (temperature, power, throttling, throughput) plus live model inference results.
- Continuous on-device security threat scanning with a NexusShield status panel.

### Changed
- The AxonML page is now a full model-management hub (load/unload, deploy, registry); advanced MPC control is gated to paid tiers.
- Analytics charts clamp to each sensor's physical range so a stuck reading can't distort the scale.

## [1.5.0] - 2026-06-01

### Fixed
- Resolved a class of installs where control could start with no equipment loaded.
- Output / relay board states now report correctly to the UI and telemetry.
- More reliable hardware board detection during install.

### Added
- Engage / release a controller's safe state remotely from the Console (persists across reboot).
- Engineering-unit input scaling so 0–10 V transducers and current sensors read in real units (%RH, PSI, amps).
- Organization-level license numbers for paid tiers.
- On-device document store mirroring Console data, persisted and compressed across reboots.
- Setup wizard gains the full algorithm catalog (Community-gated), transducer / current-sensor input types, and per-channel scaling.

### Changed
- Expanded natatorium control with electric reheat and additional supply-air safety interlocks (fan proof, airflow switch, high-limit cutout).

## [1.2.0] - 2026-05-29

### Changed
- Lower-latency on-device control path.
- Input channel modes are configured automatically from each input's signal type.

### Added
- Raspberry Pi 4 (Bullseye) headless builds as their own release line (arm64 + armhf).

## [1.1.0] - 2026-05-28

### Added
- Platform-administration tools and multi-factor-authentication hardening.

### Changed
- Algorithm refinements across the catalog.

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
