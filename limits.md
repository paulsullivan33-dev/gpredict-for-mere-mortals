# Limits

What Gpredict cannot do, stated as
plainly as what it can.

**Its answers age.** A prediction is a
TLE plus arithmetic. The arithmetic is
exact; the TLE is a snapshot. Elements a
few days old predict well-tracked
satellites to seconds; elements a few
weeks old can be off by minutes; the
bundled data this guide found — years
old — was off by hours and whole orbits.
Gpredict will never warn you that its
data is stale. The epoch check in
chapter 5 is a habit you supply, not a
feature it has.

**It propagates; it does not know.**
SGP4 models the orbit the TLE describes.
It does not know about a satellite that
manoeuvred yesterday, a collision
avoidance burn, a satellite that died,
or one that was never given public
elements at all. Classified satellites
have no CelesTrak file, and Gpredict
cannot invent them. When a satellite
re-enters, its last TLEs degrade
catastrophically in the final days —
predictions for dying satellites are
fiction with decimal places.

**It never receives.** No decoding, no
recording, no audio. The radio control
in chapter 9 tunes and points; the
signal's content belongs to other
software entirely. Similarly, Gpredict
displays Doppler and can correct a
radio for it, but it is not a receiver's
front end and makes no weak signal
stronger.

**One station per module.** A module
stands in exactly one place. Comparing
"what will the pass look like from home
and from the cabin" means two modules —
or editing the station — and there is no
view that overlays two stations' skies.
Travelling operators keep a module per
place.

**It is a screen, only a screen.**
There is no command-line mode, no
headless output, no API to ask "when is
the next pass?" from a script; the
program has no `--version`, let alone a
query interface. What it computes lives
in its windows and its files. (The files
are at least honest: a determined script
can read `.sat` data and compute for
itself — but then the script, not
Gpredict, is doing the work.)

**Control is best-effort.** The Hamlib
bridge drives what the daemons can
drive. Radios differ in which commands
they accept; a duplex satellite radio is
a different animal from the receive-only
setup the lab demonstrated, and PTT —
actually keying a transmitter — is a
step this guide deliberately never took:
engagement in the lab moved frequencies
and antenna bearings on devices that
cannot transmit. Real transmit control
also inherits your licence conditions:
the program will tune where it is told,
and the responsibility for where that is
stays with the operator.

**Precision has edges.** Rise and set
times are computed against a spherical
horizon at 0° — not your trees, your
rooftop, or the hill to your west, and
not against atmospheric refraction's
small kindnesses. A pass predicted to
peak at 8° may be a fine radio pass and
a completely invisible optical one.
Local obstructions are local knowledge;
the program does not have it.
