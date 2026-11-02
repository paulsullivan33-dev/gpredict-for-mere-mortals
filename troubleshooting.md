# Troubleshooting

**A satellite in my module never
appears.** The catalogue may hold no
usable data for it — the module then
shows every *other* satellite and says
nothing. Check the program's log in
`~/.config/Gpredict/logs/` for a
"could not load" line naming the
catalogue number, and check whether a
file for it exists in `satdata/` at all
(the lab's default module listed six
satellites and loaded five; the sixth
had no bundled file, and the *Missing*
count in chapter 5's update is the same
phenomenon at scale). Fix: update the
TLE data; if the satellite is genuinely
uncatalogued in the fetched lists, no
module can show it. And note the cruel
detail from chapter 8: saving the module
drops the phantom from the `.mod` file,
so read the file *before* you save if
you want the evidence.

**The predictions are wrong — minutes
or hours off.** Stale elements, almost
every time. Read the epoch:
`grep TLE1 ~/.config/Gpredict/satdata/<number>.sat`
— the first line's year-and-day field
(chapter 5 shows the format). If the
epoch is old, run **Edit → Update TLE
data from network** and compare panels
before and after. If the epoch is fresh
and the error is small and *constant*,
check your station's coordinates
(chapter 4) and whether the program is
showing UTC while you are thinking in
local time — Preferences → General →
Number Formats has a "show local time"
tick, and a clock offset of whole hours
is a timezone until proven otherwise.

**I changed the default station and my
module did not move.** Working as
designed, unhelpfully. The default
applies to new modules; an existing
module points at its station in its own
file. Move it with the module menu →
Configure → Ground station, and verify
in the `.mod` file (`QTHFILE=`).

**The radio will not engage — no error,
nothing happens.** The lab's exact
failure, and its order of checks is the
point. One: is the daemon actually
listening? `ss -tlnp` should show
`rigctld` on the port your device entry
names. Two: can a *client* drive it
without Gpredict? The `rigctl` exchange
in chapter 9 isolates the daemon from
the GUI — if that fails, the problem is
Hamlib's, not Gpredict's. Three: is the
host resolving where you think?
`localhost` may resolve to IPv6 (`::1`)
while the daemon listens on IPv4 only;
`getent hosts localhost` shows the
order, and writing the literal
`127.0.0.1` in the device entry (or the
`.rig` file) ends the ambiguity. Four:
only then suspect the device entry
itself — re-read the `.rig`/`.rot` file
and compare port and type against the
daemon's.

**The rotator drives to the wrong place
or slams a limit.** The travel limits in
the rotator's Preferences entry are
claims *you* made about the hardware.
If the real rotator turns 0–360 and the
entry says 0–450, the program will
happily command the impossible. Set the
entry to the hardware's truth, and use
the Antenna panel's **Monitor** mode —
watch the readouts without sending
position commands — the first time a
new rotator is connected.

**The TLE update "worked" but a
satellite is still stale.** The update
only refreshes satellites named in the
files it fetches. The finished dialog's
*Missing* count is the tell: those
satellites keep whatever elements they
had. A niche satellite may need an
element set from a different published
list than the built-in set; the TLE
preferences page is where the sources
live.

**Updating transponders filled the log
with "Failed to remove" warnings.** The
lab saw hundreds of these during a
successful update: the updater tried to
clear old files and complained as it
went, then wrote fresh ones that parsed
and worked (chapter 9's radio panel used
them the same hour). Treat them as noise
on an update that otherwise finished —
but check the outcome, not the tone:
count the files in `trsp/` afterwards
(the lab's healthy count was 2,695).

**"Cannot open display" on a headless
machine.** Gpredict is a graphical
program with no console mode (chapter
3). Give it a display — a real desktop,
an X forwarding session, or a virtual
framebuffer (`xvfb-run -a gpredict`).
There is no flag that makes it a
command-line tool, and asking the shell
for a version will only get you the same
silence.

**Buttons that ignore clicks (a lab
note, kept for honesty).** Under the
lab's window-manager-less virtual
display, several of the program's
dialog buttons ignored synthetic mouse
clicks while menus, lists and keyboard
input behaved normally; Tab-plus-Return
drove every dialog to completion. On a
real desktop this does not arise — but
if you ever automate this program, drive
it by keyboard and verify state from its
files, as the lab's transcripts do.
