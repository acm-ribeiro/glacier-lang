# Changelog

All notable changes to the Glacier language support extension for Visual Studio Code will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned

- Continue improving Glacier syntax highlighting and language support.

## [0.0.1]

### Added

- Initial support for the Glacier specification language.
- Language registration for files using the `.glc` extension.
- Syntax highlighting for HTTP operation headers, including `GET`, `POST`, `PUT`, and `DELETE`.
- Highlighting for Glacier contract sections: `invariants`, `requires`, and `ensures`.
- Highlighting for control keywords, request and response operations, Boolean values, null-like values, operators, response codes, integers, function calls, and punctuation.
- YAML syntax highlighting support within Glacier files.
- Editor support for line comments, block comments, bracket matching, automatic pair closing, and selection surrounding.