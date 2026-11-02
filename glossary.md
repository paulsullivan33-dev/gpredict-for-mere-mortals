# Glossary

**AOS** — acquisition of signal: the
moment a satellite rises above your
station's horizon and a pass begins.
Gpredict reports it to the second.

**Azimuth** — the compass bearing to
point at, in degrees clockwise from
north: 0° north, 90° east, 180° south.

**CelesTrak** — the long-running public
service that publishes orbital element
sets for thousands of tracked objects.
One of the two sources Gpredict's
updater fetches by default; AMSAT,
the amateur satellite organisation,
is the other.

**Doppler shift** — the change in a
signal's received frequency caused by
the satellite's motion toward or away
from you. On a 145 MHz downlink it
amounts to a few kilohertz across a
pass — enough to slide a narrow signal
out of a receiver's passband if
uncorrected, which is why chapter 9's
tracking exists.

**Elevation** — the pointing angle
above the horizon, in degrees. Below
zero, the satellite is under your
floor; 90° is straight overhead.

**Epoch** — the moment a TLE describes
the orbit *at*, encoded in its first
line as a two-digit year and a day of
the year. The freshness date of the
data; chapter 5 teaches reading it.

**Footprint** — the circle of Earth's
surface from which a satellite is
above the horizon at a given moment —
equivalently, the region the satellite
can see. Drawn on the map view around
every satellite.

**Ground station (QTH)** — your end of
the geometry: a named latitude,
longitude and altitude, stored in a
`.qth` file. *QTH* is the old radio
code for "my location".

**Ground track** — the line across the
map traced by the point directly under
the satellite as it orbits.

**Hamlib** — the library, and its
`rigctld` / `rotctld` daemons, through
which programs control radios and
rotators. Gpredict speaks to the
daemons, never to the hardware
directly.

**Maidenhead locator** — a compact
grid-square code for a place on Earth
(six characters, such as the lab
station's EN00AA), used by radio
amateurs in place of coordinates.
Gpredict computes it from a station's
latitude and longitude, and shows the
locator of the ground point under a
satellite.

**Module** — one Gpredict window onto
the sky: a ground station, a chosen
set of satellites, and a layout,
stored in a `.mod` file.

**NORAD catalogue number** — the
permanent ID of a tracked object (the
space station is 25544). Satellite and
transponder files in Gpredict's config
directory are named by it.

**Pass** — one visit: the interval
between AOS and LOS while a satellite
crosses your sky, typically eight to
thirteen minutes for low orbits.

**Range rate** — the rate at which the
distance to the satellite is changing,
in km/s. Negative means closing. It is
the Doppler shift before the shift is
expressed in hertz.

**SatNOGS** — the community satellite
ground-station network whose open
database of satellite transmitters is
the source of Gpredict's transponder
data.

**SGP4** — the standard mathematical
model that turns a TLE into a position
at a chosen time. The engine inside
every serious tracker, Gpredict
included.

**Slant range** — the straight-line
distance from your station to the
satellite, in kilometres — what sets
the signal's travel time and loss.

**Sub-satellite point** — the point on
Earth's surface directly beneath the
satellite at a given moment.

**TLE** — a two-line element set: the
standard two lines of numbers
describing one object's orbit at its
epoch. The raw material of all
prediction in this guide.

**Transponder** — a satellite radio
that retransmits what it hears: it
receives on an **uplink** frequency
and answers on a **downlink**. A
**beacon** is a transmitter that only
sends — a signal to find and measure,
carrying telemetry or a simple
identification.

**LOS** — loss of signal: the moment
the satellite sets below your horizon
and the pass ends.
