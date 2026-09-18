# Forerunner Ecumene: Rates and Council

An additive Stellaris 4.4.6 submod for **Halo: Forerunner Ships & Portraits** (Steam Workshop ID `2268843111`). The dependency is required and must load before this mod.

## Install

Place the `mod` directory beside the relevant `.mod` launcher descriptor, enable both mods, and load this mod after the dependency. The dependency's assets and unrelated content are not bundled here.

## What it changes

- Adds `auth_forerunner_ecumene`: oligarchic candidate elections, agendas and emergency-election behavior, with a nominal 1,100-year term and 100-year variance.
- Makes the Ecumene authority available in empire creation while retaining vanilla oligarchy compatibility for the dependency's existing pre-scripted country.
- Gives normal organic Forerunner leaders an ordinary Rate through selectable, randomized initial leader traits—no startup events or generated-leader scripting. A triangle-free compatibility graph preserves rare dual-Rate combinations while preventing normal three-Rate stacking.
- Implements Builders, Miners, Lifeworkers, Juridicals, Warrior-Servants, Engineers, Theoreticals, Historians, Weavers, Speakers, and Interpreters. Builder Security and Promethean remain specializations rather than ordinary Rates.
- Adds distinct First Councilor effects for all eleven ordinary Rates and eleven Rate-associated Council agendas.
- Reworks `forerunner_rates` into Rate Primacy—an empire-scale institutional emphasis separate from individual identity.
- Preserves and re-credentials the dependency's Builder, Miner and Juridical council positions; adds Lifeworker, Engineer and Warrior-Servant offices.
- Expands the Forerunner leader-name pool with more than 150 canonical and original lore-compatible names across several naming patterns.

## Intentional dependency overrides

`gov_ecumene_council`, `forerunner_rates`, and the dependency's obsolete species-trait file are narrowly redefined. Their public IDs are preserved so presets, saves, and references remain compatible. No vanilla technology, authority, civic, or leader-trait collection is broadly replaced.

## Compatibility hooks

`is_forerunner_ecumene`, `is_forerunner_oligarchic_government`, `is_organic_forerunner_leader`, `has_forerunner_rate`, and the individual `is_forerunner_*` Rate triggers are public scripted hooks for submods.

## Engine caveat

Rate traits use the normal initial-leader-trait system. Rare and Dangerous technology draw modifiers provide a clean category-based Theoretical hook and also improve the set presented to research automation. Stellaris exposes no narrow global hook for changing automated choice scoring after options are drawn; this mod therefore does not overwrite every vanilla technology merely to force that choice.

The custom authority uses the native oligarchic election type, oligarchic election tag, oligarchic ruler council position, factions, and emergency elections. Some vanilla scripts still test the exact `auth_oligarchic` ID. Making every such script recognize a custom authority would require broad vanilla overrides, so the submod provides a public compatibility trigger instead.
