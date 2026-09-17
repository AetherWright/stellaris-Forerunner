# Implementation report

## Files created

The installable content is under `mod/`: descriptor, custom authority, Ecumene government and Rate Primacy policy override, Rate leader traits, scripted triggers/effects, lifecycle events/on-actions, council positions, and English localization. The root descriptor and README support manual installation.

## Intentional overrides

`gov_ecumene_council` is redefined only to require the new Ecumene authority while retaining its First Councilor title and established ID. `forerunner_rates` retains its ID but becomes Rate Primacy. Existing councilor IDs are redefined only to require their appropriate Rate trait. The dependency's specialist leader traits are left intact rather than removed: the new assignment system never grants them, avoiding save-breaking deletion.

## Rate/class mapping

| Rate | Leader classes |
| --- | --- |
| Builder | Scientist, Official |
| Builder Security | Commander |
| Miner | Scientist, Official |
| Lifeworker | Scientist, Official |
| Juridical | Official |
| Engineer | Scientist, Official |
| Warrior-Servant | Commander |
| Promethean | Commander (15% of newly generated organic Forerunner commanders) |

Every Rate trait is mutually exclusive with the rest. Builder Security is deliberately a Commander-specific Builder manifestation; the Builder trigger recognizes both traits.

## Assignment

`on_game_start_country` assigns Rates to existing owned and pool leaders. `on_leader_spawned` assigns a Rate to each newly spawned organic Forerunner that does not already have one. The scripted effect excludes non-Forerunners and will not replace an existing Rate.

## Authority and council

`auth_forerunner_ecumene` uses `oligarchic_election`, an 1100-year term, and 100-year variance. The existing preset is converted from vanilla oligarchy during country initialization. Rate-specific offices require their Rate trait, while the visible council remains a small cabinet rather than a claim to represent the entire Ecumene Council.

## Validation performed

- Inspected dependency definitions for its generic trait, specialist traits, policy, government, councilors, civics, on-actions, startup events, preset, icons, and supported version.
- Searched this mod for duplicate IDs and unintended vanilla-definition replacements; only documented dependency IDs are repeated.
- Verified all custom localization keys have matching definitions and all custom trait references are declared.

## Remaining runtime check

Run Stellaris with `-debug_mode`, start the Forerunner Ecumene, and inspect `error.log` plus the leader pool. A local 4.4.6 game installation was not available here, so engine parsing and UI placement require that final in-game pass.
