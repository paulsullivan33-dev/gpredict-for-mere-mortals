# Writing criteria for this guide

Every "for Mere Mortals" guide is written to the same nine-point
standard, so a reader who trusts one can trust the rest. Here it
is, with the verification notes for this particular guide below.

1. **Fix it first.** Reader outcomes lead, not action items: each
   chapter opens by naming the outcome it delivers, shows a check
   the reader can run to confirm they got it, and a reasonable
   reader finishes able to state what was done, what it means,
   and what to try next.
2. **Plain language.** Short sentences, everyday vocabulary,
   technical terms defined on first use. No slang, and no
   idioms that only make sense in one country — the reader may
   be translating as they go.
3. **No dead ends.** A guide never tells the reader to do
   something it cannot show them how to verify. Every claim a
   reader relies on — an install, a command, an output — is
   something this guide demonstrates or clearly labels
   documented-only below.
4. **Live-verified where it matters.** Procedures are run for
   real in the guide's lab wherever the build machine allows it,
   and the transcripts kept in the repository are the evidence.
   What could not be run is listed honestly below, never
   presented as if it had been.
5. **General audiences.** Nothing in this guide — examples,
   fixtures, names, addresses — is modelled on any particular
   reader or author's real life, network, or organisations.
   The lab's one invented fixture is a fictional ground
   station at round-number coordinates; its satellites are
   real, public catalogue entries.
6. **Standalone.** A reader needs this guide, its lab, and
   nothing else. Where another guide would genuinely help, it
   is pointed to once, by name, and the chapter still completes
   without it.
7. **Honest about limits.** Chapter 12 names what the tool
   cannot do: predictions computed from element sets that age
   by the day and are never flagged stale by the program, an
   SGP4 that knows nothing of manoeuvres or dead satellites,
   no receiving or decoding of any signal, one ground station
   per module, no command-line or headless mode at all, and a
   0-degree mathematical horizon that knows nothing of your
   trees and rooftops.
8. **The ethics rule is in the text, early.** Gpredict tracks
   objects whose orbits are published for everyone, and using
   it raises no interception question — it receives nothing.
   Its own line, drawn in chapter 1 and the README, is about
   the operator's location: a ground station is a latitude and
   longitude stored in plain text, so station files, module
   files and map screenshots are location data and are shared
   with the same care as any other location data. The lab's
   station is therefore invented, and no real call sign,
   station or operator appears anywhere in this guide. Where
   the tool touches transmitting at all — radio control — the
   text states plainly that the licence and the responsibility
   stay with the operator.
9. **Builds clean.** The site builds with MkDocs in strict mode
   with no warnings, and a fresh reader following the chapters
   in order reaches the stated outcome of each.

## Verification notes for this guide

The build machine is a 2-CPU, 7.7 GB Ubuntu 24.04 sandbox,
shared with other work while the lab ran. The lab machine has
**no display, no radio, no rotator and no sky**: Gpredict ran
under a virtual framebuffer (Xvfb) driven by synthetic input,
and the radio and rotator were Hamlib's software **Dummy**
devices (model 1), which obey the real protocols and keep real
state but radiate nothing. Where the dummy's behaviour could
differ from hardware — slew rates, command acceptance, RF —
the guide says the hardware half of the check belongs to the
reader. Gpredict **2.3-115-g0f3beb6-3build3** was installed
from Ubuntu noble/universe, unmodified; Hamlib **4.5.5**
utilities were already on the system from the package's
dependency tree. The only server the lab started was
`rigctld` / `rotctld` on loopback, on the lab's one assigned
port, and both were stopped when the lab ended. All
transcripts live in `gpredict-lab/transcripts/` and all
screenshots in `gpredict-lab/screenshots/`; every screenshot
in the lab was genuinely produced by the running program.

Run for real, with transcripts as evidence:

- Installation from apt, the package version evidence, the
  absence of any `--version` or command-line mode, and the
  program's refusal to start without a display (t00).
- First launch under Xvfb: the stock Amateur module on the
  bundled Copenhagen sample station, the three views live,
  847 bundled `.sat` files whose ISS elements carry a
  **January 2021 epoch**, and one module satellite (40967)
  failing to load with a log error and no on-screen notice
  (t01).
- The network TLE update, watched as it fetched the AMSAT
  and CelesTrak files: **49 updated, 0 skipped, 785 missing,
  48 new**, `.sat` files 847 → 882, the ISS epoch moving to
  2026 day 305, and AO-73's panel changing its next AOS by
  hours and its orbit number from 70114 to 70056 (t02).
- A ground station defined for an invented prairie location
  (40.0000, −100.0000, 700 m): the station editor inspected
  on screen, the `.qth` written as a file in the app's own
  format after editor text entry proved unreliable under
  the lab's window-manager-less display, the app reading it
  back and computing locator **EN00AA** itself, and an
  existing module switched to it via Configure — with the
  rewritten `.mod` file (including its silent drop of the
  unloadable satellite) quoted as proof (t03).
- Pass prediction, live: the polar view's right-click menu,
  the full **Upcoming passes for AO-91** table (AOS, LOS,
  duration, max elevation, rise/set azimuths for nine passes
  across three days), and **Sky at a glance** rendering the
  evening's SO-50 and AO-73 passes on a UTC timeline that
  agreed with the data panel's countdown (t04).
- The transponder update: `transmitters.json` fetched from
  the SatNOGS database, **2,695 `.trsp` files** written, and
  AO-91's file read field by field (FM repeater 435.250 up /
  145.960 down); the log's hundreds of "Failed to remove"
  warnings during that otherwise successful update are
  reported in the transcript, not tidied away (t05).
- Radio control end to end: `rigctld` running the Dummy
  rig, proven first with `rigctl` alone; the radio defined
  in Preferences (RX only, port as assigned) and its saved
  `hwconf/LabDummy.rig` quoted; **Engage** connecting (the
  live TCP connection shown) and parking the dummy on
  145.890 MHz; **Track** chasing AO-73's Doppler —
  145891969 → 145891978 → 145891988 Hz over twenty seconds,
  matching the panel's own readout to the hertz. The first
  engage attempt's silent failure, traced to `localhost`
  resolving to IPv6 while the daemon listened on IPv4, is
  recorded with its fix (t06).
- Rotator control end to end: `rotctld` and the Dummy
  rotator; a rotator config written directly as
  `hwconf/LabRotor.rot` (the format mirrors the `.rig` file
  and the program loaded it without complaint — the guide
  presents the Preferences editor as the supported route);
  Engage connecting, the panel reading live positions back
  as the dummy slewed (elevation arriving at 45.00°), and
  Track driving elevation to the 0.00° horizon clamp and
  pre-positioning azimuth at **107.98°**, the next pass's
  rise bearing, where it held (t07).

Documented only — described from the project's documentation
and the interfaces observed, not run, and the text does not
claim otherwise:

- The Time Controller (listed on the module menu and used
  by one recipe, which flags it): the clock was never
  stopped or stepped in the lab, and no screenshot shows it.
- The passes dialog's Print and Save buttons, the Satellite
  info dialog, the "Show current/next pass" displays, the
  list-view module layouts, and the TLE update's local-file
  source — all seen as menu items or settings, none driven.
- The rotator and radio editors' full option sets beyond
  the fields the lab set (duplex radio types, PTT modes,
  transverter LO values in real use, azimuth type variants):
  the fields are described from their labels.
- Windows and macOS builds, and distributions other than
  Ubuntu: installation only was verified, on Ubuntu.
- Any real radio or rotator, any transmitted signal, and
  any actual satellite reception. The antenna behaviour was
  demonstrated against a mathematical dummy whose slew is
  faster and tidier than machinery; the guide says so where
  it matters.
- The neighbour tools of chapter 11 — characterised from
  their documentation and this series' own guides, not run
  for this guide.

Fixtures are this guide's own and deliberately generic: one
invented ground station ("prairie", near the centre of the
United States at round-number coordinates), the program's own
bundled Copenhagen sample, and the public catalogue data of
real satellites — names, frequencies and orbits that are
published for everyone. No person's station, call sign,
network or organisation appears anywhere in the lab.
