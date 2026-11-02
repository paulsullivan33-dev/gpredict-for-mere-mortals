# Recipes

Each recipe assumes the earlier chapters
are done: a station set (chapter 4),
fresh data (chapter 5), and a module
with the satellites you care about
(chapter 8).

**Plan a listening session for this
evening.** Open the module for the job —
say the weather-satellite module. From
the module menu, open **Sky at a
glance**: one timeline of the evening's
passes. Pick the block whose satellite
you want and check its height by opening
that satellite's **Future passes** from
the polar view's right-click menu; note
the AOS time, the max elevation and the
AOS/LOS azimuths. Ten minutes before
AOS, start your receiver software (the
neighbours chapter names the usual
suspects) and let Gpredict's polar view
count down. The check that you planned
well: the recording starts before the
satellite's footprint reaches you and
the pass peaks within a few degrees of
the predicted Max El.

**Choose the one good pass out of a
day of bad ones.** Future-passes table,
one satellite, and eyes on the **Max El**
column only. In the lab's AO-91 table
there were nine passes in three days and
exactly one above 45° — the 63.18° pass.
Put the session on that one. Low passes
are for testing whether anything works
at all; high passes are for the contact
or the picture you actually want.

**Build a visitor demonstration.**
Clone the Amateur module (module menu →
*Clone…*), name the copy for the visit,
and strip its satellite list down to the
space station alone in Configure. With
one satellite, every view becomes a
story: the footprint crawling across the
map, the *Next:* countdown, and a
Future-passes table you can pick a
spectacular pass from days ahead — pick
one that peaks high, arrives at a civil
hour, and read the AOS azimuth aloud so
everyone knows which rooftop edge to
watch. (At night, a high ISS pass is
visible to the naked eye exactly when
the table says; that never gets old.)

**Rehearse a pass before it happens.**
Select the satellite, note the AOS, then
open the module menu's **Time
Controller** and step the clock to a
minute before AOS: the map, polar plot
and data panel all recompute for the
simulated moment, so you can watch the
pass's shape — where it rises, how the
track bends across the polar plot, when
the Doppler swings fastest — without
waiting four hours for the real one.
Return the clock to *now* afterwards.
(This recipe is assembled from the
program's documented controls; the lab
demonstrated the live predictions it
depends on, not the controller itself.)

**Stand a station up for a pass with
radio and rotator.** Chapter 9's setup,
in order: daemons running, devices
defined, transponder data fresh. Open
**Radio Control**, choose the satellite
and the transponder you intend to use,
**Engage**, **Track**. Open **Antenna
Control**, **Engage**, **Track** — the
antenna will walk itself to the rise
point and wait. Verify both panels are
reading live values (the radio panel's
*Radio:* line moving with the Doppler
readout; the rotator panel's *Read:*
line matching its setpoints) a full
orbit before you need them, not during
the nine minutes that count.
