ICBM (Interconnected Block Missiles)
====================================
ICBM is a mod adding in new types of explosives and missiles for moving
those explosives. 

Blocks
------

Radar Station
^^^^^^^^^^^^^
The Radar Station detects nearby missiles and displays them on
screen. Additionally the radar can be configured to alert for any nearby
missiles. The station can be used with a wrench held to configure it's redstone
mode, but it crashed when I attempted to configure it (only tested on
singleplayer, maybe it'll work on a server).

Missile alerts have two conditions. There is the safe zone, a spherical area around
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
^^^^^^^^^^^^^^^^
The missile launcher is a multiblock capable of launching missiles in a
ballistic trajectory over a long range. Loading and launching of missiles can be
automated.

While the parts of the launcher can be mixed and matched, it's simpler to
display their stats in one table. Each stat is only for the relevant part.

+------+-----------+----------------------+--------------+-----------------+------------------------+
| Tier | Range (m) | Inaccuracy\ [#]_ (m) | Y Targeting? |     Radio?      | Energy Consumtion (RF) |
+======+===========+======================+==============+=================+========================+
|  1   |   1000    |          15          |      No      |       No        |         50000          |
+------+-----------+----------------------+--------------+-----------------+------------------------+
|  2   |   3000    |          7           |     Yes      |       No        |         80000          |
+------+-----------+----------------------+--------------+-----------------+------------------------+
|  3   |   10000   |          1           |     Yes      |       Yes       |         100000         |
+------+-----------+----------------------+--------------+-----------------+------------------------+

.. [#] Base inaccuracy is 30 m when no support is used.


Launcher Platform
"""""""""""""""""
The platform itself is also a multiblock, taking up a 3 block tall 'U' shape. Note
that the platform is a little janky and can place itself rotated and delete
nearby blocks. The frame determines the range of the missile launcher. The
platform is also where missiles are put in manually or via automation.

.. Warning:: The platform likes to place itself with the wrong rotation and
             delete nearby blocks.
   

Launcher Control Panel
""""""""""""""""""""""
The control panel determines the targetting abilities and power consumption of
the launcher. It also is the power input for the launcher and can be given a
redstone signal to launch the missile at the current target. Only the tier 3
control panel can be remotely activated via radio items like the remote detonator.

A missile can be immedietely launched by using a redstone dust on the control
panel or it checks for a redstone signal every 100 ticks (5 seconds) and launches
if its indirectly powered.

.. Note:: Remote activation is not linked to the panel itself, instead, it is
          linked a 4-digit radio frequency. It is important to set the frequency
          off the default, otherwise remote activators can begin intefere each
          other.

Launcher Support
""""""""""""""""
The support determines the inaccuracy of the launcher. It also is a multiblock
taking up a 3 block tall pillar. The support is not necessary for the launcher
to form, without it the inaccuracy is 30 m.

Items
-----
Defuser
^^^^^^^
The defuser is used to defuse and collect lit explosives. By attacking an ICBM
explosive, primed tnt, or bomb cart entity they can be instantly returned to
item from for free.

Laser Designator
^^^^^^^^^^^^^^^^
The laser designator is used to remotely target and launch a missile. Using the
designator on the control screen of a missile launcher set's the designator's
frequency, then using it will cast a 200 m ray that collides with blocks. The
connected missile launchers will target and launch a missile at the end of that
ray.

Remote Detonator
^^^^^^^^^^^^^^^^
The remote detonator is used to remotely launch a missile to a pre-determined
location. Using the detonator on a control panel will copy the panel's frequency
to the detonator. Afterwards using the detonator will launch any launcher with
the same frequency.

Rocket Launcher
^^^^^^^^^^^^^^^
The rocket launcher is a hand-held missile launcher capable of launching any
missile tier 2 and below. Additionally the launcher missile can be ridden via
sneaking when the missile is fired.

The rocket launcher costs nothing to fire, and has a firing cooldown of 1 s
[#]_. The launcher searches for ammunition in the order of the inventory's
slots. That is leftmost hotbar first, then in the main inentory the topmost,
then the leftmost slot.

.. [#] Not 20 ticks, 1 real world second not affected by the tps

.. Note:: Since sneaking is also used for dismounting the missile, its necessary
          to stop sneaking after firing the missile. In single player this is a
          tick perfect input, but in multiplayer ping works in your favor.
