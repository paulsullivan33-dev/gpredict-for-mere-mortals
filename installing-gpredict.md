# Installing Gpredict

The outcome of this chapter: Gpredict
installed from your distribution's own
package source, and the evidence on disk
that it is really there. On the lab's
Ubuntu 24.04 machine the whole install is
one command, because Ubuntu carries
Gpredict in its *universe* repository:

```bash
sudo apt update
sudo apt install gpredict
```

That is the same source the project
points Linux users at: the distribution
package. The lab's run is recorded in
`gpredict-lab/transcripts/t00-install.txt`,
and the version evidence is worth reading
once, because Gpredict will not give it
to you the way most programs do:

```console
$ apt-cache policy gpredict
gpredict:
  Installed: 2.3-115-g0f3beb6-3build3
  Candidate: 2.3-115-g0f3beb6-3build3
```

The package version is **2.3** (the
`115-g0f3beb6` after it is the upstream
snapshot the packagers built from). Now
the trap: ask the program itself and it
has nothing to say.

```console
$ gpredict --version
(no version output -- there is no such option)
```

Gpredict has no `--version`, and no
command-line mode at all. It is a
graphical program through and through:
without a display it stops at startup
with a Gtk warning that it cannot open
one. That is not a defect to fix; it is a
fact to plan around. On a desktop, launch
it from the applications menu or type
`gpredict` in a terminal. On a headless
machine — the lab's situation — it runs
perfectly well under a virtual display
such as **Xvfb**, which is how every
screenshot in this guide was taken:

```bash
xvfb-run -a gpredict
```

The check that the install worked is the
first launch itself, which is chapter 6.
Before that, two pieces of housekeeping.
First, notice what else arrived with the
package: the Hamlib utilities. The lab
found `rigctld`, `rotctld` and `rigctl`
already on the system afterwards
(Hamlib **4.5.5**) — chapter 9 needs them,
and on Ubuntu they come along for the
ride. Second, know where the program
keeps its life: everything it remembers
lives under `~/.config/Gpredict/` —
`satdata/`, `trsp/`, `modules/`,
`hwconf/`, `logs/`, and your `.qth`
station files. You will meet every one of
those by name in later chapters, and the
troubleshooting chapter's first move is
usually to read a file from that tree.

Builds for Windows and macOS exist on the
project's site, and the program is in
most Linux distributions' repositories;
this guide's lab is the Ubuntu package,
and platform differences are confined to
how the program arrives, not how it
behaves once it is running.
