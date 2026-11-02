# The Neighbours

Gpredict sits in the middle of a small
ecosystem. Each tool here overlaps it at
exactly one edge; knowing the edges
keeps you from asking any of them to do
the wrong job.

**SatDump — the listener.** Where
Gpredict predicts and points, SatDump
*receives*: it drives a software-defined
radio, records a satellite's downlink as
it passes, and decodes it into weather
images, telemetry and data products.
The overlap is real — SatDump has its
own tracker view and can even steer the
schedule — so why both? Because
Gpredict's prediction and hardware
control cover *every* catalogued
satellite and talk to Hamlib radios and
rotators, while SatDump's genius starts
where the signal arrives. A common
station runs Gpredict for the timetable
and the pointing, and SatDump for the
ears. This series has a SatDump guide;
the two tools are complements, not
rivals.

**TinyGS — the network.** TinyGS is a
volunteer network of small ground
stations receiving the LoRa beacons of
tiny satellites and cubesats, pooling
what they hear into a shared map.
Gpredict will happily predict a TinyGS
satellite's passes for your own station;
what it will never do is *join* anything
— no uploads, no network, no account.
If your aim is to contribute receptions
to a commons, TinyGS is the door; if
your aim is to know when a satellite is
over *your* roof, that is Gpredict's
question.

**The web predictors — Heavens-Above,
N2YO, CelesTrak's own pages.** Type a
location into a browser and get the same
pass tables this guide's chapter 7
produced, with nothing to install. For
a one-off "when does the station fly
over?" they are unbeatable, and they are
also a fine cross-check on a local
setup. What they cannot do: work
offline, track your whole watch list at
a glance, drive your radio, or keep
your exact location off a third party's
server logs. Gpredict is the same maths
moved onto your own machine and wired
to your own hardware.

**Orbitron and the classic trackers.**
Orbitron, the long-lived Windows
tracker, is Gpredict's closest relative:
same TLE diet, same map-and-passes
shape, a generation of operators raised
on it. The honest difference is era and
reach — Gpredict is maintained,
cross-platform, and built around the
Hamlib bridge from the start.

**Hamlib — the layer underneath.** Not
a tracker at all: the library and
daemons that let any program drive
hundreds of radios and rotators.
Gpredict is one of its customers; so
are logging programs, digital-mode
programs and SatDump. When chapter 9's
setup works, it is Hamlib that worked —
which is why this series gives Hamlib
its own guide, and why a control problem
is so often fixed at the daemon, not in
Gpredict.

**And the data sources — CelesTrak and
AMSAT.** Not software you run, but worth
naming as neighbours: the publishers of
the element sets everything above eats.
When all the trackers agree, it is
because they are all reading the same
public numbers from the same two
shelves.
