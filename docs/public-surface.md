# Public Surface

This document defines what Skill Router publicly guarantees, what it may rely on locally, and where the boundary sits.

## Public guarantees

Skill Router publicly guarantees that it will:
- resolve from the user's actual installed environment first
- prefer reuse of sufficient installed skills before discovery
- move to discovery only when current capability is clearly insufficient
- recommend some form of safety review before unfamiliar third-party installation
- stay quiet when routing adds no value

These guarantees are product promises.
They should remain true even when the surrounding skill ecosystem changes.

## What is not guaranteed

Skill Router does **not** publicly guarantee:
- that a specific local skill name exists
- that a dedicated discovery skill is installed
- that a dedicated vetting skill is installed
- that one workspace's local shortcut map applies everywhere

If those helpers exist, Skill Router may name them.
If they do not, Skill Router should describe the next step generically.

## Local layers are optional

Local maps, overrides, and preferred helper skills are valid local optimizations.
They are not part of the public contract.

Examples of local-only layers:
- preferring one browser-control skill over another in a known workspace
- naming a specific discovery skill because that environment already has it
- naming a specific vetting skill because that environment already trusts it

## Product rule

Public behavior must remain stable even when local names disappear.

That is the practical meaning of:

> Installed reality beats local preference.
