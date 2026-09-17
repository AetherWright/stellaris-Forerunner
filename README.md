# Forerunner Ecumene: Rates and Council

An additive Stellaris 4.4.6 submod for **Halo: Forerunner Ships & Portraits** (Steam Workshop ID `2268843111`). The dependency is required and must load before this mod.

## Install

Place the `mod` directory beside the relevant `.mod` launcher descriptor, enable both mods, and load this mod after the dependency. The dependency's assets and unrelated content are not bundled here.

## What it changes

- Adds `auth_forerunner_ecumene`: oligarchic candidate elections, agendas and emergency-election behavior, with a nominal 1,100-year term and 100-year variance.
- Makes the Ecumene authority available in empire creation while retaining vanilla oligarchy compatibility for the dependency's existing pre-scripted country.
- Gives organic Forerunner leaders exactly one mutually exclusive Rate through selectable, randomized initial leader traits—no startup events or generated-leader scripting.
- Uses class-specific mappings: Builders, Miners, Lifeworkers and Engineers serve as Scientists/Officials; Juridicals as Officials; Warrior-Servants, Builder Security and rare Prometheans as Commanders.
- Reworks `forerunner_rates` into Rate Primacy—an empire-scale policy separate from individual identity.
- Preserves and re-credentials the dependency's Builder, Miner and Juridical council positions; adds Lifeworker, Engineer and Warrior-Servant offices.

## Intentional dependency overrides

Only `gov_ecumene_council` and `forerunner_rates` are redefined. Their IDs are preserved so the dependency's presets and references remain compatible. No dependency assets, technologies, species traits, civics, or vanilla definitions are copied or broadly overridden.

## Compatibility hooks

`is_forerunner_ecumene`, `is_organic_forerunner_leader`, `has_forerunner_rate`, and the individual `is_forerunner_*` Rate triggers are public scripted hooks for submods.

## Deliberate scope

The dependency and reliable high-level canon support the six great Rates represented here. No speculative minor/older Rate names are added. Promethean Knights are intentionally excluded for a future Galactic Paragons-focused extension.

## Engine caveat

Rate traits use the normal initial-leader-trait system. A player can select one appropriate Rate for the starting ruler, while eligible organic Forerunner leaders receive one at random. This avoids brittle UI or lifecycle-event overrides.
