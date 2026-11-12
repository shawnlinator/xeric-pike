# Threat model

## What this project does and where untrusted input enters
A torrent client/manager (Go). Untrusted input: torrent files and magnet links, tracker protocol
responses, and the HTTP API. Parsing of untrusted torrent metadata and tracker messages is the
main surface.

## Components that matter most / least
- most: the torrent/magnet parsing and the tracker-protocol handling.
- less: the UI, docs.

## How to exercise it
Load crafted .torrent files and magnet links; feed crafted tracker responses.

## How you rate severity
- Memory-safety or RCE from parsing untrusted torrent/tracker data: critical/high.
- Logic bugs: medium. DoS: medium.

## Anything to leave alone
- Vendored third-party modules are lower priority than the project code.
