# Web Lab Scanner

A session-aware Python CLI scanner for web security lab environments, currently tested against OWASP Juice Shop and controlled mock targets.

## Overview

Web Lab Scanner is a Python-based CLI tool built to practice web security engineering through a real project instead of one-off scripts. The scanner combines HTTP interaction, limited internal crawling, security header analysis, cookie checks, HTML form parsing, CSRF heuristics, reflected XSS probing, SQL error probing, and report generation.

The project is designed for lab-only use and focuses on controlled, explainable security checks rather than full exploitation.

## Key Features

- Session-aware scanning with a shared HTTP session
- Custom cookie and header injection
- Same-host internal crawling with depth and page limits
- Security header analysis
- Cookie flag analysis
- HTML form extraction
- CSRF token heuristic detection for POST forms
- Reflected XSS indicator probing
- SQL error indicator probing
- Structured findings with severity, confidence, evidence, and recommendations
- JSON and HTML report generation
- Unit and integration tests

## Target Environment

This project is currently tested against:

- OWASP Juice Shop
- Controlled mock HTTP targets used in integration tests

## Project Structure

    src/web_lab_scanner/
      cli.py
      scanner.py
      session_manager.py
      http_client.py
      crawler.py
      config.py
      models.py
      analyzers/
        headers.py
        cookies.py
        forms.py
        csrf.py
        xss.py
        sqli.py
      reporters/
        json_reporter.py
        html_reporter.py

    tests/
    configs/
    examples/
    docs/

## Installation

    python -m pip install -e .[dev]

## Usage

### Scan a target directly

    python -m web_lab_scanner.cli scan http://192.168.168.30:3000/

### Generate JSON and HTML reports

    python -m web_lab_scanner.cli scan http://192.168.168.30:3000/ --json .\examples\sample_report.json --html .\examples\sample_report.html

### Scan using config

    python -m web_lab_scanner.cli scan --config .\configs\juice_shop.yaml

## Configuration Example

    target: http://192.168.168.30:3000/
    max_depth: 2
    max_pages: 30
    timeout: 5

    auth:
      cookies: []
      headers:
        - "User-Agent: WebLabScanner/0.1.0"

    checks:
      headers: true
      cookies: true
      csrf: true
      xss: true
      sqli: true

    output:
      json: examples/sample_report.json
      html: examples/sample_report.html

## Example Findings

Example output from a Juice Shop scan may include:

- Missing Content-Security-Policy header
- Missing Referrer-Policy header
- Missing Permissions-Policy header

## Testing

Run the full test suite with:

    pytest

Current project status:

- 20 tests passing
- Unit tests for analyzers and helpers
- Integration tests for reflected XSS and SQLi indicators

## Screenshots

### Test run

![Pytest passing](docs/screenshots/pytest-20-passed.png)

### CLI scan output

![CLI scan output](docs/screenshots/cli-scan-output.png)

### HTML report

![HTML report](docs/screenshots/html-report.png)

## Architecture

See `docs/architecture.md` for the current component breakdown and scanning flow.

## Current Limitations

- The crawler is designed for server-rendered HTML links and does not execute JavaScript.
- Client-side SPA routes behind fragment identifiers such as `#/...` are not fully enumerated.
- Reflected XSS and SQLi checks are heuristic indicators, not exploit confirmation.
- Root-page scans against modern SPAs may produce fewer crawl results than traditional server-rendered apps.

## Safety Notice

This tool is intended only for:

- Local lab environments
- Training targets
- Systems you own or are explicitly authorized to test

## Current Status

This project currently includes:

- Session-aware target fetching
- Limited internal crawling
- Passive checks for headers and cookies
- Form parsing and CSRF heuristics
- Active reflected XSS and SQLi indicator probes
- JSON and HTML reporting
- Automated test coverage

## Roadmap

Potential next improvements:

- Broader multi-page analysis beyond the initial response
- Richer HTML report styling
- Expanded form-driven probing
- Optional authenticated workflows for additional lab targets