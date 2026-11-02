# Radio and Rotator Control

The outcome of this chapter: Gpredict
connected to a radio and an antenna
rotator, tuning the radio to a
satellite's frequency, chasing its
Doppler shift in real time, and parking
the antenna where the next pass will
rise. The lab ran all of it — against
software stand-in radios, because its
machine has no radio attached and no
antenna on the roof. That is not a
compromise to apologise for; it is the
right order to do this in, and this
chapter will show you how to repeat it
before your own hardware is involved.

**The bridge.** Gpredict speaks to
hardware through **Hamlib**. Two daemons
do the talking: `rigctld` (radio) and
`rotctld` (rotator). Each listens on a
TCP port — 4532 and 4533 are the
customary defaults — and each is started
with the model number of the device
behind it. Hamlib's catalogue includes a
device that costs nothing and cannot be
damaged: **model 1, the Dummy**. A dummy
rig obeys every command and holds its
frequency; a dummy rotator slews toward
commanded positions and reports where it
has got to. Start the pair the way the
lab did (its port was 18084; yours can
be the standard ports):

```bash
rigctld -m 1 -t 4532      # dummy radio
rotctld -m 1 -t 4533      # dummy rotator
```

Prove the daemon before involving
Gpredict — `rigctl`, told to use model 2
("a rigctld is my radio"), reads and
sets a frequency on the dummy:

```console
$ printf 'f\nF 145960000\nf\n' | rigctl -m 2 -r localhost:4532
Rig command: Frequency: 145000000
Rig command: Frequency: 145960000
```

**Telling Gpredict.** In **Preferences →
Interfaces**, the **Radios** and
**Rotators** tabs keep the device lists.
*Add new* on Radios opens an editor:
name, host, port, **radio type** —
*RX only*, simplex or duplex, which
decides whether the program drives an
uplink as well as a downlink — PTT
behaviour, the VFO arrangement, and
**LO offsets** for stations whose radio
sits behind a transverter. The rotator
editor takes the same host and port plus
the rotator's travel limits (the lab
used 0–450° azimuth, 0–180° elevation).
Saving writes the small INI files from
chapter 2 (`hwconf/<name>.rig`,
`hwconf/<name>.rot`) — read yours once;
it is the whole configuration.

**Driving.** From the module menu,
**Radio Control** and **Antenna Control**
open the two panels. Each has the same
grammar: pick a **Target** satellite and
(for the radio) a transponder from the
chapter 5 data; pick the **Device**;
press **Engage**; press **Track**. In
the lab, engaging the radio put the
dummy on AO-73's beacon frequency,
145.890 MHz, exactly. Tracking is where
it comes alive: read back from the dummy
itself, ten seconds apart —

```text
Frequency: 145891969
Frequency: 145891978
Frequency: 145891988
```

— 145.890 MHz plus 1,988 Hz of Doppler,
creeping about a hertz a second as the
satellite's range rate changed, with the
panel's own *Radio:* readout agreeing to
the hertz. The rotator told the same
story in degrees: engaged, it slewed to
its setpoints (elevation arrived at
45.00°, the panel reading the position
back live); with Track on and the
satellite still below the horizon, it
drove elevation to **0.00** — rotators
are never sent under the floor — and
pre-positioned at azimuth **107.98°**,
the bearing of the next pass's rise
point, and waited there. When the pass
comes, a tracking station is already
standing where the satellite will
appear.

**Two cautions the lab earned.** First,
write the host as a literal address
(`127.0.0.1`) if a daemon is local: the
lab's first engage failed *silently*
because `localhost` resolved to an IPv6
address the IPv4-only daemon was not
listening on — no error, no log line a
new user would find, nothing. Second,
remember what is *not* proven here: a
dummy cannot tell you whether your real
radio accepts the same commands, whether
your rotator's limits match its
controller's, or whether the station
works under RF. Those checks are yours,
on your hardware, at low power and with
the manual open — the Hamlib guide in
this series covers the daemon side
deeper. What *is* proven is Gpredict's
half of the conversation, end to end:
transcripts `t06-radio-control.txt` and
`t07-rotator-control.txt`.
