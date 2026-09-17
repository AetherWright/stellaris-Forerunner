# Forerunner Ecumene: Rates and Council

An additive Stellaris 4.4.6 submod for **Halo: Forerunner Ships & Portraits** (Steam Workshop ID `2268843111`). The dependency is required and must load before this mod.

## Install

Place the `mod` directory beside the relevant `.mod` launcher descriptor, enable both mods, and load this mod after the dependency. The dependency's assets and unrelated content are not bundled here.

## What it changes

- Adds `auth_forerunner_ecumene`: oligarchic candidate elections, agendas and emergency-election behavior, with a nominal 1,100-year term and 100-year variance.
- Converts the dependency's starting Ecumene from `auth_oligarchic` at game initialization without copying its prescripted-country definition.
- Gives organic Forerunner leaders exactly one mutually exclusive Rate through a leader-spawn hook and initializes pre-existing leaders/pools at game start.
- Uses class-specific mappings: Builders, Miners, Lifeworkers and Engineers serve as Scientists/Officials; Juridicals as Officials; Warrior-Servants, Builder Security and rare Prometheans as Commanders.
- Reworks `forerunner_rates` into Rate Primacy—an empire-scale policy separate from individual identity.
- Preserves and re-credentials the dependency's Builder, Miner and Juridical council positions; adds Lifeworker, Engineer and Warrior-Servant offices.

## Intentional dependency overrides

Only `gov_ecumene_council` and `forerunner_rates` are redefined. Their IDs are preserved so the dependency's presets and references remain compatible. No dependency assets, technologies, species traits, civics, or vanilla definitions are copied or broadly overridden.

## Compatibility hooks

`is_forerunner_ecumene`, `is_organic_forerunner_leader`, `has_forerunner_rate`, and the individual `is_forerunner_*` Rate triggers are public scripted hooks for submods. `forerunner_assign_rate` is the leader-scoped assignment effect.

## Deliberate scope

The dependency and reliable high-level canon support the six great Rates represented here. No speculative minor/older Rate names are added. Promethean Knights are intentionally excluded for a future Galactic Paragons-focused extension.

## Engine caveat

Stellaris does not expose a clean, per-ruler Rate picker in empire creation through ordinary data scripting. The custom authority is selectable there; the first ruler is assigned a single appropriate Rate at initialization. This avoids a brittle UI override and preserves the dependency's custom preset.
