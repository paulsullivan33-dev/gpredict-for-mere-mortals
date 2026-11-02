# What Gpredict Is

A satellite in low orbit circles the Earth
in about ninety minutes. From your garden
it is above the horizon for perhaps ten
of those minutes, moving fast enough that
its radio signal slides noticeably in
frequency as it passes. Everything about
that motion is knowable in advance,
because the orbit is tracked — by radar,
by volunteers, by the people who launched
the thing — and the result is published
for anyone to use.

**Gpredict is the program that turns
those published orbits into answers.**
You tell it where you are standing. It
tells you where a satellite is right now,
drawn on a map with the circle of Earth
it can currently see; when it will next
rise above your horizon (its **AOS**,
acquisition of signal); when it will set
again (**LOS**, loss of signal); how high
it will climb; and which way to point an
antenna, minute by minute, while it is
up. Given a radio connected to the
computer, it will also do the pointing
and tuning for you, correcting for the
**Doppler shift** — the frequency slide
caused by the satellite's speed toward or
away from you — as it goes.

The orbit data has a name and a shape you
will meet everywhere in this guide: a
**TLE**, a two-line element set. It is a
small block of text, two long lines of
numbers, that describes one satellite's
orbit at one moment. **CelesTrak** and
**AMSAT** publish TLE files for thousands
of objects, updated daily. Gpredict
downloads them, stores one small file
per satellite, and runs each through a
standard orbit model called **SGP4** —
the same model the whole tracking world
uses, which is why Gpredict's answers
agree with everyone else's.

One boundary is worth drawing on the
first page, because it decides what this
tool is for. **Gpredict does not receive
anything.** It has no ear. It will show
you a weather satellite crossing your sky
at 14:02 and it will tune a radio to the
satellite's frequency at 14:02 — but the
picture the satellite sends is decoded by
other software (the neighbours chapter
names it), and the voice coming back
through a repeater is heard through a
radio, not through Gpredict. Watching and
listening are different jobs; this is the
watching, done very well.

There is a second, quieter boundary, and
this series states it early wherever it
applies. A ground station in Gpredict is
a latitude, a longitude and an altitude —
which is to say, **your location is in
the program's files**, in plain text,
under your home directory. Nothing about
that is secret or sent anywhere: tracking
runs entirely on your machine, and the
only network traffic is fetching the
public orbit data. But screenshots of
your map, or a module file you share,
will show the world where your station
is, the way a photo of your desk shows
your street if the window is open. This
guide's lab therefore uses an invented
station in the middle of nowhere in
particular, and chapter 4 shows you the
file your own station lives in, so you
know exactly what would be shared if you
shared it.

Who uses this? Amateur radio operators
working the satellite repeaters and the
International Space Station; listeners
who pull weather pictures out of the sky
and need to know when to start the
recorder; teachers who want a class to
watch a pass arrive on the minute it was
predicted. All of them are asking the
same three questions — *where is it, when
is it mine, and where do I point* — and
those are the questions the next chapters
take in order.
