# The Moving Parts

By the end of this chapter you can name
every piece inside Gpredict and say which
piece holds what — so that when something
looks wrong later, you can guess *which*
piece is lying to you. There are seven
worth knowing.

**The TLE data.** One small file per
satellite, in `~/.config/Gpredict/satdata/`,
each holding that satellite's two-line
element set and its names. Gpredict
arrives with a bundled set of these —
hundreds of satellites — and chapter 5
will show you why the bundle is a
starting point and not an answer: in the
lab, the bundled elements for the space
station were dated January 2021, nearly
six years old, and an orbit that stale is
a story about where a satellite *used to*
go. The data is replaceable, and the
program has a built-in updater for
exactly that reason.

**The propagator.** Inside the program,
the **SGP4** model turns a TLE plus a
clock time into a position: latitude,
longitude, altitude, velocity. Everything
else in Gpredict is presentation and
bookkeeping around this one calculation,
repeated for every satellite on screen,
several times a second. When two tracking
programs disagree about a satellite, they
are almost never disagreeing about SGP4 —
they are working from TLEs of different
ages.

**The ground station (the QTH).** Your
end of the geometry: a name, a latitude
and longitude, an altitude, stored as a
small plain-text file ending in `.qth` in
the same config directory. From the
station and the satellite, Gpredict
derives the numbers an operator actually
uses — azimuth and elevation (where to
point), slant range (how far away, which
sets the signal delay and loss), range
rate (how fast the distance is closing,
which sets the Doppler shift), and the
sub-satellite point's own grid locator.
Chapter 4 builds one.

**Modules.** A module is one window onto
the sky: a ground station plus a chosen
set of satellites plus a layout of views.
You might keep one module for amateur
repeaters, one for weather satellites,
one for the space station alone. Each
module is a small file in
`~/.config/Gpredict/modules/` — chapter 8
opens one and reads it — and a module
remembers *its own* station, which is why
changing the program-wide default station
does not move a module that already
exists. That surprised the lab; it is in
the troubleshooting chapter so it does
not surprise you.

**The three views.** A module's window
combines a **map view** (the world, the
satellites, their ground tracks and the
circle each one can see), a **polar
view** (your sky as a radar plot —
horizon at the rim, overhead in the
middle, the next pass counted down), and
a **single-satellite data panel** (one
satellite's numbers, live). Chapter 6
walks all three. There is also a list
layout — the Modules preferences offer
several — but the three-view layout is
the default and the one this guide
teaches.

**The transponder database.** A second
data set, one file per satellite in
`~/.config/Gpredict/trsp/`, describing
what the satellite's radios do: beacon
frequencies, repeater uplinks and
downlinks, telemetry modes. It comes from
the **SatNOGS** community database, is
fetched separately from the TLEs
(chapter 5), and matters the moment you
want Gpredict to drive a radio: without
it, the program knows where the satellite
is but not what frequency it speaks on.

**The hardware bridge.** Gpredict does
not talk to radios or rotators directly.
It talks, over a local network
connection, to **Hamlib** daemons —
`rigctld` for a radio, `rotctld` for a
rotator — and the daemons talk to the
hardware. Your radio and rotator are
defined in Preferences as a host and a
port, and saved, again, as small INI
files in `~/.config/Gpredict/hwconf/`
(`.rig` and `.rot`). Chapter 9 runs the
whole bridge against Hamlib's software
stand-ins, so every step is demonstrated
before any real equipment is involved.

Hold those seven in mind — data,
propagator, station, module, views,
transponders, bridge — and the rest of
the guide is just each one, taken slowly.
