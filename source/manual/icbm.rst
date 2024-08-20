ICBM (Interconnected Block Missiles)
====================================

ICBM is a mod adding in new types of explosives and missiles for moving
those explosives. 

Radar Station
-------------

The Radar Station detects nearby missiles and displays them on
screen. Additionally the radar can be configured to alert for any nearby
missiles. The station can be used with a wrench held to configure it's redstone
mode, but it crashed when I attempted to configure it (only tested on
singleplayer, maybe it'll work on a server).

Missile alerts have two parts. There is the safe zone, a spherical area around
the radar that missiles must be targetting to be alerted on. Then there is the
alarm zone, another spherical area around the radar that missiles must be in to
be alerted on.

In effect, the radar will alert when a missile is targeted its safe zone and is
within alarm range.

There are two things the radar station will do when alerting. It'll send a radio
signal containing the position of the missile, most likely to allow an
anti-ballistic missile to be auto-targeted, but nothing in ICBM will actually
respond to this radio signal.

The radar will also emit redstone when alerting. It has two modes; the default
being to emit strength dependent on the aount of total missiles alerting. The
strength is equal to 5 + <the amount of missiles>, capped to 15 of course. The
other mode instead emits redstone to each side depending on how many missiles
are alerting from that side. (Check the redstone strength and what side means
what and if its based on target or position of missile)

Missile Launcher
----------------
The missile launcher is a multiblock capable of launching missiles in a
ballistic trajectory over a long range. Loading and launching of missiles can be
automated.

While the parts of the launcher can be mixed and matched, it's simpler to
display their stats in one table. Each stat is only for the relevant part.

+------+-----------+----------------------+----------------+--------------+-----------------+
| Tier | Range (m) | Inaccuracy\ [#]_ (m) | X/Z Targeting? | Y Targeting? | Remote Control? |
+======+===========+======================+================+==============+=================+
|  1   |   1000    |          15          |      Yes       |      No      |       No        |
+------+-----------+----------------------+----------------+--------------+-----------------+
|  2   |   3000    |          7           |      Yes       |     Yes      |       No        |
+------+-----------+----------------------+----------------+--------------+-----------------+
|  3   |   10000   |          1           |      Yes       |     Yes      |       Yes       |
+------+-----------+----------------------+----------------+--------------+-----------------+

.. [#] Base inaccuracy is 30 m when no support is used.


Launcher Frame
.................

The frame itself is also a multiblock, taking up a 3 block tall 'U' shape. Note
that the frame is a little janky and can place itself rotated and delete
nearby blocks. The frame determines the range of the missile launcher. The
platform is also where missiles are put in manually or via automation.

Launcher Screen
...............

The screen determines the targetting abilities and power consumption of the
launcher. It also is the power input for the launcher and can be given a
redstone signal to launch the missile at the current target. Only the tier 3
screen can be remotely activated via radio items like the remote detonator.

A missile can be immedietely launched by using a redstone dust on the screen or the
screen will check for a redstone signal every 100 ticks (5 seconds) and launch
if its indirectly powered.

Launcher Support
................

The support determines the inaccuracy of the launcher. It also is a multiblock
taking up a 3 block tall pillar. The support is not necessary for the launcher
to form, without it the inaccuracy is 30 m.
