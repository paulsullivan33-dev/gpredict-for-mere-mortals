# Your Ground Station

The outcome of this chapter: Gpredict
knows where on Earth you are, and you can
prove it — the map centres on your
station and the pass predictions are
computed for your sky, not someone
else's. Every number in the program is
relative to this one point, so fifteen
minutes here is the best-spent time in
the whole guide.

Open **Edit → Preferences → General →
Ground Stations**. The table has columns
for name, location, latitude, longitude,
altitude, grid locator and a *Default*
tick. On a fresh install it holds exactly
one row — a sample station in Copenhagen,
Denmark, that ships with the program so
the first launch has somewhere to stand.
That sample is also your template: its
file is at `~/.config/Gpredict/sample.qth`
and reads, in full:

```ini
DESCRIPTION=Copenhagen, Denmark [Sample file - do not edit]
LAT=55.6167
LON=12.6500
ALT=5
WX=EKCH
LOCATOR=JO65HO
```

A station is that simple: plain text,
degrees as decimals (south and west
negative, as the sample's eastern
longitude is positive), altitude in
metres, and a **Maidenhead locator** —
the grid-square code radio amateurs use
for "where I am" in six characters. You
do not have to compute the locator
yourself; give the program coordinates
and it works the locator out, as the lab
saw when its test station at 40.0000,
−100.0000 came back with locator **EN00AA**
filled in.

To make your own station, use the
**Add new** button on that Preferences
page. The editor asks for a name and
description, the location in words, the
latitude with a north/south choice, the
longitude with east/west, the locator
(optional — it will be computed), the
altitude, and a weather-station code,
which you may leave empty. Nothing here
needs to be precise to the metre: a
station placed within a kilometre of the
truth predicts passes to the same second
for any practical purpose. Use your
town's coordinates, not your house's, if
you prefer — the predictions will not
notice, and chapter 1 has already said
why the file deserves that much care.

Two behaviours to learn now, while they
are cheap:

**A module keeps its own station.** The
*Default* tick decides which station a
*new* module starts from. A module that
already exists points at its station in
its own file — the lab proved this by
ticking a new default and watching the
open module stay exactly where it was.
To move an existing module, use the
module's own menu (the button in the
module's top-right corner) → **Configure**,
set the **Ground station** drop-down to
your station, and confirm. The check:
the map header over the world view names
the station and its location, and the
module file — `~/.config/Gpredict/modules/<name>.mod`
— now says `QTHFILE=<your-station>.qth`.

**Because the file is plain text, you
can also write it by hand.** The lab did
exactly that for its fictional station
(`prairie.qth`: `LAT=40.0000`,
`LON=-100.0000`, `ALT=700`), restarted
the program, and found the station
listed, locator and all. The editor is
the supported route and the one to use;
the file format matters because it makes
your station data yours — readable,
back-up-able, and diff-able — not a
secret the program keeps from you.

The lab's transcript of all of this is
`gpredict-lab/transcripts/t03-ground-station.txt`.
