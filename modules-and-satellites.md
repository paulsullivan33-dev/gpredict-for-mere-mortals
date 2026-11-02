# Modules and Satellites

The outcome of this chapter: a module
that shows the satellites *you* care
about, from *your* station, in the
layout you want — and a clear idea of
what the module remembers, because it
writes it all in a file you can read.

A module is a named bundle: one ground
station, one set of satellites, one
layout. Gpredict opens with the
ready-made **Amateur** module. Everything
about a module is changed from the
module's own menu — the button in the
module's top-right corner — whose
**Configure…** item opens the *Edit
module* dialog: the module's name, its
**Ground station** drop-down, and two
lists of satellites, *Available* and
*Selected*, with arrow buttons between
them. Double-clicking a satellite also
moves it across. The left list has a
search box and a category filter (the
lab's read *All satellites*); the
satellite catalogue behind it is the one
from chapter 5 — after the TLE update,
the lab's config directory held 882
satellite files, every one of them a
candidate for a module.

Press OK and the module rewrites its
file. The lab watched its own module
file before and after, and the after is
worth quoting in full because it is the
whole truth about what a module is:

```ini
[GLOBAL]
SATELLITES=39444;43017;24278;25544;27607
QTHFILE=prairie.qth

[SINGLE_SAT]
SELECTED=39444
```

Catalogue numbers in a list, the station
file by name, and which satellite the
data panel was showing. Nothing else.
That is why the troubleshooting advice
for modules is always "read the .mod
file": if a satellite is not in that
list, it is not in the module, whatever
you remember clicking. The same save
taught the lab its sharpest module
lesson: the list above has five numbers,
not six — the satellite that never
loaded (chapter 6) was silently dropped
from the file at the next save. Modules
remember what *works*, and forget what
doesn't, without telling you. Keep the
file under version control of your own
if your module matters to you.

Other items on the module menu, briefly:
**Detach module** floats the module as
its own window; **Clone…** copies it —
the right way to start a second watch
list; **Delete** removes it. **Autotrack**
asks the module to keep the next-up
satellite selected automatically.
**Select satellite** picks which
satellite the data panel follows. And
the *Modules* page of the main
Preferences sets the default **layout** —
the lab's was *World map, polar and
single sat*; list-based layouts exist
for operators who think in tables, and
the layout is stored as an editable code
string for those who enjoy that sort of
thing.

A practical shape to aim for: one module
per *job*, not per satellite. A
"Repeaters" module with the handful of
FM satellites you actually work; a
"Weather" module with the NOAA and
Meteor birds your receiver hunts; a
"Station" module with the ISS alone for
demonstrations. Three small modules will
tell you more at a glance than one
module with sixty dots on the map — and
when a pass countdown says *Next:*, it
will mean next *of the ones you care
about*.
