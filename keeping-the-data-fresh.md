# Keeping the Data Fresh

The outcome of this chapter: orbital
data on your machine that is days old
instead of years, and a way to prove its
age by reading one number. Nothing else
in this guide matters if this chapter is
skipped, because every prediction is
computed from this data — and the data
Gpredict ships with is old.

How old? The lab checked the space
station's stored elements before touching
anything. Every TLE carries its own
birthdate in its first line, the
**epoch**: two digits of year, then the
day of the year. The bundled file said
`21024.238` — year 2021, day 24. Nearly
six years stale, on a satellite that is
dragged, boosted and nudged regularly.
An SGP4 run on elements that old does
not give slightly wrong answers; by now
it gives answers about a ghost — the lab
watched the station's own panel change
its story completely the moment fresh
data landed (its predicted next pass
moved by hours, and its orbit number by
58).

The fix is built in: **Edit → Update TLE
data from network**. The dialog shows
its work as it goes — the lab watched it
fetch the AMSAT file
(`amsat.org/.../nasabare.txt`) first, then
CelesTrak's amateur file
(`celestrak.org/NORAD/elements/amateur.txt`),
then the rest of its built-in list; the
whole sweep took about two and a half
minutes. The finished dialog reports
four counts, and the lab's were:

- **49 updated** — satellites whose
  stored elements were replaced,
- **0 skipped**,
- **785 missing** — bundled satellite
  files no fetched list mentioned, so
  they keep their old elements (or none),
- **48 new** — satellites the lists
  brought that the bundle never had.

Afterwards the station's epoch read
`26305.789` — year 2026, day 305, the day
before the lab ran. That one number,
read with `grep TLE1 ~/.config/Gpredict/satdata/25544.sat`,
is the check this chapter promised: learn
to read an epoch and you can audit any
tracking program's data, not just this
one. The *Preferences → General → TLE
Update* page is where the update's own
settings live — how often to check, and
whether to fetch on startup; set it to
look regularly, because elements age in
days, and a weekly habit is a good one.
(The updater can also read TLE files from
local disk instead of the network — the
same dialog family offers it — for
machines that fetch their data another
way. The lab used the network path; the
local-file path is documented in the
program's manual and is not demonstrated
here.)

There is a second database, updated
separately: **Edit → Update transponder
data**. This one fetches a single file —
`transmitters.json`, the export of the
**SatNOGS** community database — and
unpacks it into one small file per
satellite in `~/.config/Gpredict/trsp/`:
2,695 of them in the lab's run, covering
beacons, repeaters and telemetry
transmitters. You only need it for
chapter 9's radio work, but fetch it now
while you are here; a radio panel that
knows no frequencies is a radio panel
that cannot help you. The lab's file for
AO-91 shows the shape of the data:

```ini
[Mode U/V FM Voice (no CTCSS any longer)]
UP_LOW=435250000
DOWN_LOW=145960000
MODE=FM
```

Frequencies in hertz: that satellite's
repeater listens on 435.250 MHz and
answers on 145.960 MHz. Chapter 9 spends
this data; this chapter just makes sure
it exists. Both updates are recorded in
`gpredict-lab/transcripts/t02-tle-update.txt`
and `t05-transponder-update.txt`.
