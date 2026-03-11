# Changelog

All notable changes to this project will be documented in this file.

## [0.1.0] - 2026-03-11

### Added
- Initial Python package structure under `src/web_lab_scanner`
- CLI entry point for running scans from the command line
- YAML-based configuration loading
- Shared HTTP session handling with cookie and header injection
- Basic HTTP fetch wrapper with error handling
- Same-host crawler with crawl depth and page-count limits
- Security header analyzer
- Cookie flag analyzer
- HTML form parser
- CSRF heuristic analyzer for POST forms
- Reflected XSS indicator probing
- SQL error indicator probing
- Structured findings model with severity, confidence, evidence, and recommendation fields
- JSON report generation
- HTML report generation
- Sample report artifacts under `examples/`
- Architecture notes in `docs/architecture.md`
- Unit tests for helpers, analyzers, and reporters
- Integration tests using controlled mock HTTP targets
- Screenshot assets for portfolio presentation

### Validated
- Successful scanning against OWASP Juice Shop
- Real lab findings for missing security headers
- Controlled reflected XSS detection in integration tests
- Controlled SQLi indicator detection in integration tests

### Notes
- Current crawler is optimized for server-rendered HTML and does not execute JavaScript
- Client-side SPA routes are not fully enumerated in the current version
- XSS and SQLi checks are heuristic indicators, not exploit confirmation