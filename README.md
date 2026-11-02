# GPredict for Mere Mortals

Somewhere above you right now, a satellite
is crossing the sky — too fast and usually
too faint to see, but not too fast to
predict. Its orbit is public information,
published as a small block of numbers
called a **TLE**. Feed those numbers to
the right maths and you can say, to the
second, where the satellite is now, where
it will be in ten minutes, and when it
will next rise over your roof. **Gpredict**
is the program that does that maths and
draws it: a world map with the satellite's
footprint on it, a radar-style view of
your own sky, and a table of the next
passes over your station. Point it at a
radio and an antenna rotator and it stops
being a picture — it will tune the radio,
chase the Doppler shift as the satellite
screams overhead, and swing the antenna to
follow, all by itself.

This guide explains how Gpredict turns
orbital data into predictions, how to set
up your own ground station, and how to
read what it shows you. Then it puts the
program to work: predicting real passes
days ahead, and driving a radio and a
rotator through **Hamlib**, the standard
control layer for amateur radio gear.

The lab that wrote this guide ran the real
thing: **Gpredict 2.3** on Linux, under a
virtual display on a machine with no
monitor at all — which is why every claim
here rests on something checkable: the
files the program writes, the numbers in
its own panels, and, for the radio work, a
software "dummy" radio and rotator that
obey commands and report their state. The
lab's ground station is an invented one —
a round-number spot in the middle of the
United States — because a station location
is exactly the kind of detail a guide
should make up. What the lab could not do
is labelled, not faked: it had no real
radio, no real antenna, and no sky.
`criteria.md` keeps the full ledger of
what was run and what was only read.

## What this guide covers

- [**What Gpredict is**](what-gpredict-is.md) —
  the mental model: public orbital data
  in, positions and pass times out, and
  the line between watching and listening
- [**The moving parts**](the-moving-parts.md) —
  TLE data, the SGP4 propagator, ground
  stations, modules, the three views, the
  transponder database, and the Hamlib
  bridge to real hardware
- [**Installing Gpredict**](installing-gpredict.md) —
  the distribution package, the version
  evidence, and why the program wants a
  display even to say hello
- [**Your ground station**](your-ground-station.md) —
  telling the program where on Earth you
  are, the plain-text station file, and
  why an old module ignores a new default
- [**Keeping the data fresh**](keeping-the-data-fresh.md) —
  updating the orbital data from the
  network, the six-year-old data set the
  program ships with, and the transponder
  update that feeds radio control
- [**First launch and the three views**](the-three-views.md) —
  the map, the polar plot and the data
  panel, and what every number in the
  data panel means
- [**Predicting passes**](predicting-passes.md) —
  the future-passes table, the sky at a
  glance, AOS and LOS, and how to tell a
  good pass from a horizon-scraper
- [**Modules and satellites**](modules-and-satellites.md) —
  building watch lists, adding and
  removing satellites, and what a module
  remembers in its file
- [**Radio and rotator control**](radio-and-rotator-control.md) —
  Hamlib daemons, the Engage and Track
  buttons, Doppler chasing, and an
  antenna that parks itself where the
  satellite will rise
- [**Recipes**](recipes.md) — plan a pass
  session end to end, build a watch list
  for a family of satellites, and set up
  for a pass that is still days away
- [**The neighbours**](the-neighbours.md) —
  SatDump listening to the downlink,
  TinyGS and its packet network, the web
  predictors, and Hamlib underneath it
  all: what each does that Gpredict
  doesn't, and vice versa
- [**Limits**](limits.md) — predictions
  only as good as the data's age, no
  receiving or decoding, one station per
  module, and a program that only speaks
  through a screen
- [**Troubleshooting**](troubleshooting.md) —
  the satellite that silently isn't
  there, the update that changed nothing
  you could see, the radio that would not
  engage, and the traps this guide's lab
  fell into so you don't have to
- [**Glossary**](glossary.md) — the
  terms, collected in one place

## What it doesn't cover

Receiving anything. Gpredict predicts and
points; it never listens. Decoding a
satellite's signal — weather pictures,
telemetry, voice through a repeater — is
work for a receiver and other software,
and the neighbours chapter points at the
tools that do it. This guide also does
not teach radio operation itself: what a
repeater is, how a satellite contact
works, or how to get licensed. It assumes
you want to know *where the satellite is*
and *when it will be back*, and it stays
on that ground.

## How to use this guide

Read chapter 1 for the model and chapter
2 before installing anything — knowing
which part holds what turns later
confusion into a named problem. Chapters
3 to 5 get you a program, a station and
fresh data; chapter 6 is the tour of the
screen. Chapter 7, predicting passes, is
the heart of the tool — read it slowly.
Chapter 9 is the one to read before
connecting any real hardware: the lab ran
it against software stand-ins precisely
so the steps are proven before a real
radio is on the desk. The lab's
transcripts live in
`gpredict-lab/transcripts/` and its
screenshots in `gpredict-lab/screenshots/`.

---

## Part of the series

This guide is one of the [For Mere Mortals](https://paulsullivan33-dev.github.io/mere-mortals/) guides: plain-language guides to the tools programmers and makers use.

Related guides:

- [Ham Radio for Mere Mortals](https://paulsullivan33-dev.github.io/ham-radio-for-mere-mortals/)
- [SatDump for Mere Mortals](https://paulsullivan33-dev.github.io/satdump-for-mere-mortals/)
- [TinyGS for Mere Mortals](https://paulsullivan33-dev.github.io/tinygs-for-mere-mortals/)
- [Hamlib for Mere Mortals](https://paulsullivan33-dev.github.io/hamlib-for-mere-mortals/)

## License

The writing in this guide is licensed under [CC BY 4.0](https://github.com/paulsullivan33-dev/gpredict-for-mere-mortals/blob/main/LICENSE). Code examples and lab scripts are licensed under the [MIT License](https://github.com/paulsullivan33-dev/gpredict-for-mere-mortals/blob/main/LICENSE-CODE).
