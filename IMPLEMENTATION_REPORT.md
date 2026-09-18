# Implementation report

## Compatibility approach

The pass remains additive wherever Stellaris permits it. The custom authority stays in `common/governments/authorities`, Council agendas and their finish modifiers live in new files, and new Rate identities extend the working trait file. The dependency's public government and policy IDs remain intact for presets and saves.

The only narrow dependency overrides are:

- `gov_ecumene_council`, to accept both the custom Ecumene authority and vanilla oligarchy.
- `forerunner_rates`, to preserve its policy ID while expanding Rate Primacy.
- `00_species_traits_forerunner.txt`, retained from the boot-fix pass to replace obsolete dependency syntax.

No vanilla technology list, automated-research file, authority collection, or dependency leader-trait collection is broadly replaced.

## Authority classification

`auth_forerunner_ecumene` retains its 1,100-year term, 100-year variance, four candidates, emergency elections, agendas, and oligarchic ruler council position. It uses the native `oligarchic` election type and `AUTHORITY_ELECTION_OLIGARCHIC` tag, and now explicitly enables factions and disallows reelection.

This is the clean engine-supported oligarchic classification. Some vanilla scripts check the literal `auth_oligarchic` ID rather than an election tag. Making all of those recognize a custom authority would require broad vanilla overrides. `is_forerunner_oligarchic_government` is provided as an additive public hook for compatible submods.

## Rate/class mapping

| Rate | Eligible leader classes | Allowed exceptional pairing |
| --- | --- | --- |
| Builder | Scientist, Official | Lifeworker or Engineer |
| Miner | Scientist, Official | Lifeworker |
| Lifeworker | Scientist, Official | Builder or Miner |
| Juridical | Official | Warrior-Servant |
| Warrior-Servant | Commander | Juridical |
| Engineer | Scientist, Official | Builder |
| Theoretical | Scientist | Historian |
| Historian | Scientist, Official | Theoretical |
| Weaver | Official | Speaker |
| Speaker | Official | Weaver or Interpreter |
| Interpreter | Scientist, Official | Speaker |

The allowed-pair graph is triangle-free. That preserves naturally emergent dual-Rate leaders—including Miner + Lifeworker and Builder + Lifeworker—while each allowed pair still opposes every possible third ordinary Rate. Existing dual-Rate leaders are not stripped or normalized.

Builder Security and Promethean are retained as non-random specializations rather than ordinary Rate identities. Promethean remains an elite Warrior-Servant case.

## Ruler and agenda identities

Each ordinary Rate has a distinct First Councilor effect and a corresponding agenda. Builders focus solely on rapid, inexpensive construction; Engineers on upkeep, engineering, and cheaper ships; Juridicals on administration rather than Mantle doctrine; and Interpreters own the Mantle-specific governance identity.

Theoretical rulers, Theoretical Primacy, and Unbounded Inquiry use the engine's category modifiers for Rare and Dangerous technology draw chance plus research alternatives. This avoids a hardcoded technology-ID list. These modifiers improve which options become available, including the pool seen by research automation.

Stellaris does not expose a narrow global hook for rescoring automated research choices after options have been drawn. Implementing a stronger post-draw bias would require overriding individual technology weights or a broad automation definition. That unsafe portion is intentionally deferred.

## Rate Primacy

All eleven ordinary Rates have Primacy options. Effects are deliberately moderate and represent institutional influence; they do not prevent other Rates from generating, serving on the Council, or retaining their traits. Agenda AI weights respond to both the current Primacy flag and the ruler's Rate, while all Rate agendas remain available to the player.

## Names and localization

The Forerunner namelist now contains more than 150 leader names spread across poetic statement-names, verb/dedication forms, declarative generational forms, court or craft titles, and shorter ceremonial names. Existing canonical names are preserved.

English localization explicitly covers the authority, government, ruler title, every Rate trait, every Rate Primacy option, all Council positions defined by the submod, all agendas, and all agenda finish modifiers. This prevents raw `leader_trait_*`, policy-option, agenda, and government identifiers from appearing in the English UI.

## Validation targets

- Clausewitz brace and quote balance for every `.txt`, `.gfx`, and `.yml` file.
- Every custom trait reference resolves to a declared trait.
- Every custom agenda finish modifier resolves to a declared static modifier.
- Every custom trait, policy option, agenda, authority, government, and councilor has an English localization key.
- No `requires_governments` member is present on Rate traits; that member caused the earlier trait-reader crash.

An in-game 4.4.6 smoke test is still required for final engine/UI confirmation because no local Stellaris installation is available in this workspace.
