# Predicting Passes

The outcome of this chapter: given a
satellite, you can produce its timetable
over your station for the next several
days — when each pass starts and ends,
how long it lasts, and how good it will
be — and defend the claim that the best
pass is not always the soonest one.

A **pass** is the interval between AOS
and LOS: the satellite rises over your
horizon, crosses your sky, and sets. For
a low-orbit satellite a pass lasts eight
to thirteen minutes. Everything in this
chapter is a way of asking the
propagator to run ahead of the clock and
report the passes it finds.

**The per-satellite table.** Right-click
a satellite — in the polar view, where
the lab did it — and the menu offers
*Satellite info*, *Show current pass*,
*Show next pass*, *Future passes* and a
*Sky track* tick. Choose **Future
passes**. The window that opens, titled
*Upcoming passes for …*, lists one row
per pass with six columns:

- **AOS** and **LOS** — the rise and set
  times, to the second;
- **Duration** — how long the pass
  lasts;
- **Max El** — the highest elevation the
  satellite reaches during the pass, in
  degrees;
- **AOS Az** and **LOS Az** — the
  compass bearings of the rise and set
  points, which tell you the shape of
  the crossing: north-to-south over the
  top, or a low skim along one horizon.

Here are the lab's first rows for AO-91
from its invented station, with the full
table in `gpredict-lab/transcripts/t04-pass-predictions.txt`:

```text
AOS                  LOS                  Dur.     MaxEl  AOSAz  LOSAz
2026/11/02 15:23:31  2026/11/02 15:36:43  00:13:11  31.58  187.7  337.8
2026/11/03 02:58:02  2026/11/03 03:08:45  00:10:42  26.47   23.3  168.0
2026/11/03 15:11:10  2026/11/03 15:23:58  00:12:47  44.43  181.8  341.4
2026/11/04 14:58:13  2026/11/04 15:11:10  00:12:56  63.18  174.3  345.0
```

Read the **Max El** column like a
weather forecast. A pass peaking at 12°
never clears the trees and rooftops for
most stations, and its signal spends the
whole pass at maximum distance. A pass
peaking at 63° — the fourth row — comes
nearly overhead: closest approach, the
strongest signal, and the fastest
Doppler swing. Operators plan their day
around the high ones and let the low
ones go. Note, too, the pattern in the
times: passes arrive in clusters (a run
of orbits whose ground tracks pass near
you), then a gap of hours. The table
scrolls forward for days; the dialog's
**Print** and **Save** buttons will put
the list on paper or in a file — the lab
did not use them and says so, but the
table itself was produced live.

**The wide view.** The module menu's
**Sky at a glance** draws one horizontal
timeline — the lab's ran 16:00 to 23:00
UTC — with one coloured block per pass
per satellite. It answers the scheduling
question the table cannot: *what is the
shape of my evening?* In the lab's
window, SO-50 came up three times and
AO-73 twice, the first AO-73 block
starting at the same 20:40 the data
panel was counting down to — two views
of the same mathematics, agreeing.

**The quick answers.** Half the time you
need none of this machinery: the polar
view's *Next:* countdown for "what's
next", the data panel's *Next Event* for
one satellite, and the *Show next pass*
menu item, which draws the coming
pass's track across the polar plot so
you can see the path before it happens.

A word about trust. These predictions
are only as good as the elements behind
them (chapter 5) — with fresh TLEs,
expect AOS times good to a few seconds
for well-tracked satellites, drifting as
the elements age. And the **Time
Controller**, also on the module menu,
lets you stop the clock or run it
forward and watch all three views
recompute for the simulated moment — the
program's own way of rehearsing a pass
before it happens. The lab did not
exercise the Time Controller and does
not pretend otherwise; the pass table
above, produced live, is the evidence
this chapter stands on.
