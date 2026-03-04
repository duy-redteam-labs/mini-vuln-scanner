# Mini Web Vuln Scanner (Lab-Safe)

## Overview
A small CLI scanner for lab web apps (DVWA/Juice Shop) to check basic security posture:
- Security headers
- Heuristic CSRF checks
- Basic reflected XSS / SQLi tests (lab-only)

## Scope (Lab-only)
Run only against your own lab targets. No scanning of real systems.

## Tech Stack
- Python or Go
- Output: JSON + HTML report
- Tests: unit tests

## How to Run
1. Install dependencies
2. Run CLI against lab URL
3. View JSON/HTML output

## Deliverables
- CLI tool + README usage examples
- Unit tests
- Scan reports: docs/reports/

## Status
- [ ] CLI skeleton
- [ ] Header checks
- [ ] CSRF heuristic
- [ ] XSS/SQLi lab tests
- [ ] HTML/JSON reporting
- [ ] Unit tests
