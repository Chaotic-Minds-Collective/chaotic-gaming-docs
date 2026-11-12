# Integration Overview

## Website

The Next.js website is a separate application. It uses server-side proxy routes to Core. Player bearer tokens remain in HttpOnly cookies and are never returned to browser JavaScript.

Current pages and API proxies:
- Account registration, login, logout and profile
- Player entitlements
- Product catalogue and pending order API foundation
- Public production server status
- Validated plugin catalogue

Checkout and payment provider integration are not enabled.

## Glitch Bot

The Discord bot remains an independent application. The optional Core API client reports configured server heartbeats only when a Core URL and service credential are present. Existing Discord functionality is not made dependent on Core.

## 7 Days to Die

The existing Server Bridge Web API client and SSE parser are the primary integration path. Operators must use endpoint paths and event names from the OpenAPI/RapiDoc documentation exposed by the exact running server build. The bridge maps provider event names explicitly, requires provider event IDs, writes a local durable spool and forwards normalized events to Core.

The optional Telnet helper is restricted to read-only health commands and is not the preferred game-data integration.

## ATLAS

The ATLAS repository contains a minimal Windows x64 C++ lifecycle proof of concept. It exports plugin initialization and unload functions only. The AtlasApi 1.71 ABI, manifest format and plugin folder layout still require validation against the exact server build in an isolated environment.

## ARK: Survival Evolved

ARK is reserved for a later stage. Its cluster/map/survivor/tribe data model is represented in Core, but no server adapter or plugin is claimed as implemented.
