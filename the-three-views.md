# First Launch and the Three Views

The outcome of this chapter: the program
open, one module on screen, and you able
to say what every part of the window is
telling you. Launch Gpredict and it
opens a single module named **Amateur**,
already stocked with a handful of
well-known amateur satellites, standing
on the sample ground station in
Copenhagen until you give it your own
(chapter 4). Three views share the
window.

**The map view** is the top half: the
world, flattened, with every satellite
in the module drawn as a dot with its
name. Around each dot is an ellipse —
the satellite's **footprint**, the circle
of Earth that can see it (and that it
can see) right now. The sweeping line
through a satellite is its **ground
track**, the path its footprint is
travelling. The pale shading is night.
Your station is a small marker — the
lab's screenshots show it first on
Denmark, then, after chapter 4, standing
on the US plains with the header over
the map reading *prairie · Example, USA*.
Read the map for *geography*: which
satellites exist, roughly where, and
what is coming toward your side of the
planet.

**The polar view** is the bottom-left:
your sky, drawn the way a radar scope
would. The rim is your horizon, the
centre is straight overhead, and north
is up. A satellite below your horizon is
simply not plotted — so what you see
here is only what is, or is about to be,
*reachable*. The header over this view
carries the single most-used sentence in
the program: **`Next: SO-50 in 27:51`** —
the next satellite to rise over *this*
station, and the countdown to it. During
a pass, the satellite's path is drawn
across this plot as it crosses your sky,
which is the picture an antenna operator
actually steers by (chapter 9 shows the
same plot inside the rotator panel, with
the minutes marked along the track).

**The single-satellite panel** is the
bottom-right: one satellite's live
numbers, for whichever satellite is
selected. The lab's transcript quotes
AO-73's panel; every field earns its
place:

- **Azimuth / Elevation** — where to
  point, in degrees. Elevation below
  zero means below your horizon.
- **Slant Range** — the straight-line
  distance to the satellite, in km. Far
  satellites are weaker and later.
- **Range Rate** — how fast that distance
  is changing; negative means closing.
  This number *is* the Doppler shift,
  before it is expressed in hertz.
- **Next Event** — the next AOS or LOS
  for this satellite at your station,
  with the time.
- **SSP Loc** — the Maidenhead locator of
  the ground point directly under the
  satellite.
- **Footprint** — the diameter, in km,
  of the circle the satellite can see.
- **Altitude / Velocity** — the
  satellite's own height and speed
  (expect roughly 7.5 km/s; these things
  are not dawdling).
- **Doppler@100M** — the frequency shift
  the motion would cause on a 100 MHz
  signal; scale it to the band you care
  about.
- **Sig. Loss / Sig. Delay** — free-space
  path loss in dB, and the signal's
  one-way travel time in milliseconds —
  on the space station's panels you can
  watch the delay breathe between about
  3 and 15 ms as it comes and goes.
- **Mean Anom. / Orbit Phase / Orbit
  Num** — where the satellite is in its
  current revolution, and how many
  revolutions it has completed in its
  life. The orbit number is a quiet
  freshness check: after the lab updated
  its data, AO-73's panel showed orbit
  70056 — *lower* than the 70114 the
  stale data had claimed, because the old
  elements had been extrapolating a
  wrong count for years.

The first-launch run, stale data and
all, is `gpredict-lab/transcripts/t01-first-launch.txt`;
screenshots are in `gpredict-lab/screenshots/`.
One honest warning from that transcript:
on the lab's first launch, one of the
module's six satellites produced a log
error and quietly never appeared — the
catalogue had no data for it. Five dots
on the map, six names in the module.
Chapter 13 (troubleshooting) teaches you
to spot that; chapter 8 shows you the
module file where the truth is written.
