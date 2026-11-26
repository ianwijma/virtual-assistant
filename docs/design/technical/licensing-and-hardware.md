# Licensing and hardware

The licence of the project and what the hardware goal requires of the
design. Part of [the technical design](README.md).

Status: draft.

## Licence

- The project is open source under GPLv3.
- It earns money later by selling hardware, not software.
- Every dependency, model and voice must allow use in hardware that is
  sold.
- Slint is used under its GPLv3 option, at no cost on any platform,
  including hardware.
- Buyers of hardware must be able to install modified software on it. This
  fits "own your own assistant".
- Apple's App Store terms conflict with the GPL. Publishing there needs a
  contributor agreement for outside contributions.

## Hardware goal

Selling hardware is well beyond the first release, but it constrains the
design now:

- The server is one self-contained binary that runs on low-power ARM
  boxes, with no cloud dependency and simple updates.
- Pairing and first-run setup must work for a non-technical person.
- A local AI model (through Ollama) is the likely brain of a box, so the
  system must be fully usable without any cloud provider.

## Verified and assumed

Verified:

- Slint offers three licences: GPLv3, royalty-free with attribution (not
  for embedded devices), and commercial.

Known traps, from the earlier voice assistant:

- Its default local voices are for non-commercial use only.
- Some speech recognition models have no clear licence.
- The free weather service it uses is for non-commercial use.

## Open questions

- Which speech models and voices have licences that allow selling
  hardware. See [voice](voice/README.md).
