# OpenVisionBridge Security Policy

## 1. Purpose

OpenVisionBridge may process images, OCR output, visual metadata, local files, AI model outputs, and optional external services. Security and privacy are therefore part of the project architecture.

## 2. Supported Versions

| Version | Security Support |
|---|---|
| Current stable release | Supported |
| Previous stable release | Security fixes where practical |
| Development branches | Best effort |
| Experimental/unreleased code | Not guaranteed |

Update this table for each release.

## 3. Report Privately

Please report privately when an issue could cause:

- arbitrary or remote code execution;
- unauthorized file access;
- authentication/authorization bypass;
- exposure of private image data;
- credential or secret disclosure;
- unintended network access;
- visual-evidence manipulation;
- security-boundary bypass;
- significant denial of service;
- compromise of connected AI systems;
- unsafe file parsing or deserialization;
- serious privacy violations.

## 4. Visual-AI Security

Treat visual input as untrusted.

### OCR Injection

Text inside an image can contain instructions intended to manipulate a downstream AI.

OCR output must be treated as data, not as trusted system instructions.

### Prompt Injection

Extracted visual text must not automatically become system-level instructions.

### Malicious Files

Image decoders and processing libraries may be exposed to malformed or adversarial files.

### Metadata

Images may contain GPS, device, timestamp, author, or other metadata. Applications should control metadata handling where privacy requires it.

## 5. Reporting Channel

Do not initially disclose exploitable vulnerabilities in public GitHub issues.

Use GitHub Security Advisories when enabled, or the project's designated private security contact.

The repository should publish the current security contact separately.

## 6. Report Contents

Include, where safe:

```text
Title
Affected component
Affected version/commit
Description
Security impact
Reproduction steps
Proof of concept
Expected behavior
Actual behavior
Potential mitigation
Environment
```

Do not include real credentials, private images, or unnecessary personal information.

## 7. Responsible Disclosure

The project requests reasonable time for:

```text
Report
  ->
Triage
  ->
Reproduction
  ->
Impact assessment
  ->
Fix
  ->
Testing
  ->
Release
  ->
Disclosure
```

The timeline may vary according to severity.

## 8. Severity

### Critical
Potential for remote code execution, broad compromise, or large-scale sensitive-data exposure.

### High
Significant unauthorized access, serious data exposure, or security-boundary bypass.

### Medium
Meaningful security impact requiring specific conditions.

### Low
Limited practical impact.

Severity may change after investigation.

## 9. Dependencies and Models

Review dependencies and models for:

- known vulnerabilities;
- abandoned maintenance;
- unsafe versions;
- malicious packages;
- incompatible licenses;
- unnecessary permissions.

Document model source, version, license, permissions, network requirements, and execution requirements.

## 10. Local-First Security

Local execution reduces some data-exposure risks but does not eliminate:

- file-permission risks;
- malicious input;
- dependency vulnerabilities;
- model integrity issues;
- cache exposure;
- sensitive logging.

## 11. Security Boundaries

Treat these as untrusted by default:

```text
Image
OCR output
User text
Model output
Third-party model
Third-party adapter
External URL
External metadata
```

Detection output is evidence, not authority.

## 12. Security Testing

Security-sensitive components should consider:

- malformed images;
- oversized images;
- decompression bombs;
- unexpected file formats;
- path traversal;
- malicious OCR text;
- prompt injection;
- resource exhaustion;
- dependency vulnerabilities;
- unauthorized network access.

## 13. Researcher Credit

With permission, security researchers may be acknowledged in advisories or release notes.

## 14. Contact

The official repository should publish the current private security reporting channel.

Do not place exploitable details in ordinary public issue discussions.
