# Scope

## Project Goal

Build a session-aware Python CLI scanner for web security lab environments, with practical detection logic and report generation suitable for portfolio use.

## Current Target Environment

This project is currently validated against:

- OWASP Juice Shop
- Controlled mock HTTP targets used in integration tests

## In Scope

- Shared HTTP session handling with `requests.Session()`
- Cookie and custom header injection
- Same-host internal crawling
- Crawl depth limiting
- Maximum page limiting
- Security header analysis
- Cookie flag analysis
- HTML form extraction
- CSRF heuristic analysis for POST forms
- Reflected XSS indicator probing
- SQL error indicator probing
- Structured findings with:
  - severity
  - confidence
  - evidence
  - recommendation
- JSON report generation
- HTML report generation
- Unit tests for helpers and analyzers
- Integration tests for controlled XSS and SQLi scenarios

## Out of Scope

- JavaScript execution
- Browser automation
- Full SPA route enumeration
- Exploit confirmation
- Real-world target scanning
- Authentication bypass testing
- Credential attacks
- Network or infrastructure scanning
- Vulnerability exploitation beyond basic lab-safe probing

## Design Constraints

- The scanner is intended to remain understandable and explainable in interviews.
- Detection logic should favor clear heuristics over overly complex or fragile behavior.
- Findings should be described as indicators or heuristics where appropriate, not as guaranteed exploit confirmation.
- The project should remain suitable for safe lab use and portfolio demonstration.

## Deliverables

- Python CLI scanner
- Modular analyzer structure
- JSON report output
- HTML report output
- Sample report artifacts
- Unit tests
- Integration tests
- README documentation
- Architecture notes
- Screenshots for portfolio presentation

## Success Criteria

This project is considered complete when it can:

- Scan a Juice Shop lab target successfully
- Produce structured findings
- Export JSON and HTML reports
- Demonstrate automated test coverage
- Show at least one real lab scan result
- Show controlled integration validation for reflected XSS and SQLi detection logic

## Safety

This project is intended only for:

- Local lab environments
- Training targets
- Systems owned by the operator
- Systems where explicit authorization has been granted