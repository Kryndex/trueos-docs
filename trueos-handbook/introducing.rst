.. index:: introduction
.. _Introduction:

Introduction
************

Written by users of the |trueos| operating system. Maintained and edited
by Dru Lavigne and Tim Moore.

Welcome to |trueos|!

This Handbook covers the installation and use of |trueos|. This Handbook
is a work in progress and relies on the contributions of many
individuals. To assist with the Handbook, refer to the documentation
`README <https://github.com/trueos/trueos-docs/blob/master/trueos-handbook/README.md>`_.
If using IRC Freenode, join the #trueos channel and converse with many
other |trueos| users. `Gitter <https://gitter.im/trueos>`_ is another
popular option for users.

`TrueOS® <https://www.trueos.org>`_ (formerly known as |pcbsd|) began in
2005 when Kris Moore presented the first beta version of a FreeBSD
operating system pre-configured for desktop use. Since then, |trueos|
has matured into a polished, feature-rich, free-of-charge, open source
operating system that meets the desktop or server needs of the beginner
to the advanced user alike.

|trueos| is essentially a customized installation of FreeBSD, not a
forked derivative. Since the underlying FreeBSD system is kept intact,
you have a fully functional FreeBSD system under the hood. |trueos|
provides an easy-to-use installer which can be used to install a
desktop or a server version of FreeBSD. Other differences from FreeBSD
include:

* |trueos| pre-configures the BSD-licensed |lumina| desktop environment
  during a desktop installation. Additional desktop environments can be
  installed and appear in the login menu, allowing the user to select
  their environment.

* The |trueos| installer supports configuring ZFS and encryption during
  installation.

* |trueos| provides both a graphical and command line software
  management system.

* |trueos| provides many graphical utilities for configuration and
  management. These utilities have both a command line equivalent and
  a REST and WebSocket API so they can also be used to manage multiple
  systems.

* |trueos| comes pre-configured with a number of automatic scripts for
  performing tasks like connecting digital cameras or USB memory sticks.

* The |trueos| boot menu supports boot environments or snapshots of the
  operating system, and the |trueos| Update Manager automatically adds
  a new boot environment to the boot menu before updating the operating
  system or software. With this functionality, if an update fails the
  system can reboot into the previous version of the operating system,
  before the update installed.

While it began as an independent project, |trueos| is financially backed
and supported by the enterprise-class hardware solutions provider
`iXsystems <https://www.ixsystems.com/>`_ since October 2006.


.. index:: features
.. _Features:

Features
========

|trueos| provides many features:

* **Easy installation:** To install either a graphical desktop or
  command-line server, simply insert the installation media, reboot the
  system to start the installer, and answer a few questions in the
  installation menus.

* **Automatically configured hardware:** Video, sound, network, and
  other devices configure automatically during installation.

* **Customizable desktop interface:** |trueos| installs the |lumina|
  desktop, but additional desktop environments can be installed to
  support day-to-day computing needs.

* **Easy software management:** With the |sysadm|
  :sysclbk:`AppCafe <appcafe>`, installing, upgrading, and uninstalling
  software is safe and easy.

* **Lots of software available:** |appcafe| is used to install software
  ported to FreeBSD (currently over 26,100 applications).

* **Easy to update:** |trueos| (with |sysadm|) provides a built-in
  :sysclbk:`Update Manager <update-manager>` which provides
  notifications of available updates. This utility makes it easy to
  apply operating system security fixes, bug fixes, and system
  enhancements. Additionally, the Update Manager is used to upgrade the
  operating system or update installed software.

* **No defragmentation:** |trueos| hard drives never need defragmenting
  and are formatted with OpenZFS, a self-healing filesystem.

* **Laptop support:** Provides power saving, swap space encryption, and
  automatic switching between wired and wifi network connections. Also,
  the rolling release model of |trueos| provides an environment to
  quickly add support for new hardware.

* **Easy system administration:** |trueos| provides many graphical tools
  for performing system administration.

* **Localization:** |trueos| supports a variety of native languages and
  locales.

* **Vibrant community:** |trueos| has a friendly and helpful
  :ref:`community <TrueOS Community>`.

.. index:: security
.. _Security:

Security
--------

Your |trueos| system is secure by default. This section provides an
overview of the built-in security features. If you want to know more
about increasing the security of your system beyond its current level,
additional resources are also provided in this section.

The security features built into |trueos| include:

* **Naturally immune to viruses and other malware:** Most viruses are
  written to exploit Windows systems and do not understand the binaries
  or paths found on a |trueos| system. Antivirus software is still
  available in the Security section of |appcafe|, as this is useful when
  sending or forwarding email attachments to users running other
  operating systems.

* **Potential for serious damage is limited:** File and directory
  ownership and permissions along with separate user and group functions
  mean, as an ordinary user, any program executed is only granted the
  abilities and access of the user. A user not a member of the *wheel*
  group can not switch to administrative access and can not enter or
  list the contents of a directory not been set for universal access.

* **Built-in firewall:** The default firewall ruleset allows accessing
  the Internet and the shares available on your network, but does not
  allow any inbound connections to your computer.

* **Very few services are enabled by default:** View which services are
  started at boot time by reading through the output of
  :command:`rc-update`.

* **SSH is disabled by default:** SSH can only be enabled by the
  superuser. This setting prevents bots and other users from trying to
  access your system. If SSH is needed, add :command:`sshd_enable=YES`
  to :file:`/etc/rc.conf`. Start the service by typing
  :command:`service sshd start`. A firewall rule also needs to be added
  using the |sysadm| :sysclbk:`Firewall Manager <firewall-manager>` to
  allow SSH connections over TCP port 22.

* **SSH root logins are disabled by default:** If SSH is enabled, login
  as a regular user and use :command:`su` or :command:`sudo` when
  administrative actions are required. Do not change this setting, as it
  prevents an unwanted user from having complete access to the system.

* **sudo is installed:** It is configured to allow users in the *wheel*
  group permission to run an administrative command after typing their
  password. By default, the first user created during installation
  is added to the *wheel* group. Use the |sysadm|
  :sysclbk:`User Manager <user-manager>` to add other users to this
  group. Change the default :command:`sudo` configuration using
  :command:`visudo` as the superuser.

* :wiki:`AES instruction set <AES_instruction_set>` (AESNI) support is
  loaded by default for the Intel Core i5/i7 processors that support
  this encryption set. This support speeds up AES encryption and
  decryption.

* **Automatic notification of security advisories:**
  The |sysadm| :sysclbk:`Update Manager <update-manager>` automatically
  notifies you if an update is available as the result of a
  `security advisory <https://www.freebsd.org/security/advisories.html>`_
  affecting |trueos|. This allows you to keep your operating system
  fully patched with just the click of a mouse.

* The |trueos| operating system and its available software packages are
  built with `LibreSSL <http://www.libressl.org/>`_, which has fewer
  vulnerabilities than OpenSSL.

* :sysclbk:`PersonaCrypt <personacrypt>` allows a user to use a
  removable, encrypted device as their home directory.

* :ref:`Tor Mode` can be used to anonymously access Internet sites as it
  automatically forwards all Internet traffic through the
  `Tor Project's <https://www.torproject.org/>`_ transparent proxy
  service.

To learn more about security on FreeBSD and |trueos| systems,
:command:`man security` is a good place to start. These resources
provide more information about security on FreeBSD-based operating
systems:

* `FreeBSD Security Information <https://www.freebsd.org/security/>`_

* `Security Section of FreeBSD Handbook <https://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/security.html>`_

* `Hardening FreeBSD <http://www.bsdguides.org/2005/hardening-freebsd/>`_

.. index:: ZFS overview
.. _ZFS Overview:

ZFS Overview
------------

ZFS is an enterprise grade file-system, which provides many features.
These include: support for high storage capacities, high reliability,
the ability to quickly take snapshots, boot environments, continuous
integrity checking and automatic repair, RAIDZ which was designed to
overcome the limitations of hardware RAID, and native NFSv4 ACLs.

If new to ZFS, the Wikipedia entry on :wiki:`ZFS` provides an
excellent starting point to learn about its features. Additionally,
`FreeBSD Mastery: ZFS <https://www.michaelwlucas.com/os/fmzfs>`_
by Michael W Lucas and Allan Jude is a helpful ZFS resource as it
is implemented in FreeBSD.

These resources are also useful to bookmark and peruse as needed:

* `ZFS Evil Tuning Guide <https://www.solaris-cookbook.eu/solaris/solaris-10-zfs-evil-tuning-guide/>`_

* `FreeBSD ZFS Tuning Guide <https://wiki.FreeBSD.org/ZFSTuningGuide>`_

* `ZFS Best Practices Guide <https://documents.irf.se/get_document.php?group=Computer&docid=311>`_

* `ZFS Administration Guide <https://docs.oracle.com/cd/E19253-01/819-5461/index.html>`_

* `Becoming a ZFS Ninja (video) <https://blogs.oracle.com/video/becoming-a-zfs-ninja>`_

* `Blog post explaining how ZFS simplifies the storage stack <https://blogs.oracle.com/bonwick/rampant-layering-violation>`_

:numref:`Table %s <zfsterms>` is a brief glossary of terms used by ZFS:

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.20\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.80\linewidth-2\tabcolsep}|

.. _zfsterms:

.. table:: ZFS Terms
   :class: longtable

   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Term     | Description                                                                                                                                  |
   +==========+==============================================================================================================================================+
   | Pool     | A collection of devices providing physical storage and data replication managed by ZFS. This pooled storage model eliminates the concept of  |
   |          | volumes and the associated problems of partitions, provisioning, wasted bandwidth, and stranded storage. Thousands of filesystems can draw   |
   |          | from a common storage pool, each one consuming only its required space. The combined I/O bandwidth of all devices in the pool is available   |
   |          | at all times to all filesystems. The `Storage Pools Recommendations <http://zqscm.qiniucdn.com/data/20091118230710/index.html>`_ of the ZFS  |
   |          | Best Practices Guide provides detailed recommendations for creating the storage pool.                                                        |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror   | A form of RAID where all data is mirrored onto two or more disks, creating a redundant copy should a disk fail.                              |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | RAIDZ    | ZFS software solution equivalent to RAID5, as it allows one disk to fail without losing data. Requires at least *3* disks.                   |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | RAIDZ2   | Double-parity ZFS software solution similar to RAID6, as it allows two disks to fail without losing data. Requires a minimum of *4* disks.   |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | RAIDZ3   | Triple-parity ZFS software solution. RAIDZ3 offers three parity drives and can operate in degraded mode if up to three drives fail with no   |
   |          | restrictions on which drives can fail.                                                                                                       |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Dataset  | Once a pool is created, it can be divided into datasets. A dataset is similar to a folder as it supports permissions. A dataset is also      |
   |          | similar to a filesystem since properties such as quotas and compression can be set.                                                          |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Snapshot | A read-only, point-in-time copy of a filesystem. Snapshots can be created quickly and, if little data changes, new snapshots take very       |
   |          | little space. For example, a snapshot with no changed files takes 0 MB of storage, but a changed 10 GB file will store both old and new      |
   |          | versions. Snapshots provide a clever way of keeping a history of files, should an older copy or even a deleted file need to be recovered.    |
   |          | For this reason, many administrators snapshot often (e.g. every 15 minutes), store them for a period of time (e.g. for a month), and store   |
   |          | them on another system. Such a strategy allows the administrator to roll the system back to a specific time, or if there is a catastrophic   |
   |          | loss, an off-site snapshot can restore the system up to the last snapshot interval (e.g. within 15 minutes of the data loss). Snapshots can  |
   |          | be cloned or rolled back, but the files on the snapshot can not be accessed independently.                                                   |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Clone    | A writable copy of a snapshot which can only be created on the same ZFS volume. Clones provide an extremely space efficient way to store     |
   |          | many copies of mostly-shared data such as workspaces, software installations, and diskless clients. Clones do not inherit the properties of  |
   |          | the parent dataset, but rather inherit the properties based on where the clone is created in the ZFS pool. Because a clone initially shares  |
   |          | all its disk space with the original snapshot, its used property is initially zero. As changes are made to the clone, it uses more space.    |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ZIL      | A filesystem journal that manages writes. The ZIL is a temporary storage area for sync writes until they are written asynchronously to the   |
   |          | ZFS pool. If the system has many sync writes, such as from a database server, performance can be increased by adding a dedicated log device  |
   |          | known as a SLOG (Secondary LOG). If the system has few sync writes, a SLOG will not speed up writes. When creating a dedicated log device,   |
   |          | it is recommended to use a fast SSD with a supercapacitor or a bank of capacitors able to handle writing the contents of the SSD's RAM to    |
   |          | the SSD. If a dedicated log device is needed, the SSD should be half the size of system RAM, as anything larger is unused capacity. Note a   |
   |          | dedicated log device can not be shared between ZFS pools, and the same device cannot hold both a log and a cache device.                     |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | L2ARC    | ZFS uses a RAM cache to reduce read latency. If an SSD is dedicated as a cache device, it is known as an L2ARC and ZFS uses it to store more |
   |          | reads which can increase random read performance. However, adding a cache device will not improve a system with too little RAM and actually  |
   |          | decreases performance, as ZFS uses RAM to track the contents of L2ARC. RAM is always faster than disks, so always add as much RAM as         |
   |          | possible before determining if the system would benefit from a L2ARC device. If a lot of applications do large amounts of random reads on a  |
   |          | dataset small enough to fit into the L2ARC, read performance may be increased by adding a dedicated cache device. SSD cache devices only     |
   |          | help if the working set is larger than system RAM, but small enough that a significant percentage of it fits on the SSD. Note a dedicated    |
   |          | L2ARC device can not be shared between ZFS pools.                                                                                            |
   +----------+----------------------------------------------------------------------------------------------------------------------------------------------+

|trueos| Comparisons
====================

As |trueos| grows and evolves, many users appreciate comparisons with
other operating systems. These comparisons are intended to help new
users deciding to install and try |trueos|, with accuracy being
the chief concern.

.. index:: FreeBSD/PC-BSD comparison
.. _FreeBSD and PCBSD:

FreeBSD and PC-BSD
------------------

These features or enhancements were introduced for |trueos| and now
separate |trueos| from |pcbsd|:

.. note:: |pcbsd| and FreeBSD are placed together as both are very
   similar "under the hood". Differences for either OS to |trueos| are
   listed here.

* Based on FreeBSD-CURRENT.

* The GRUB bootloader has been replaced by the FreeBSD bootloader, which
  now provides both GELI and boot environment support.

* **Quick boot times with OpenRC:** |trueos| is using
  `OpenRC <https://github.com/OpenRC/openrc>`_ as part of the init
  process to start services in parallel. This results in dramatically
  improved system boot times for |trueos|. OpenRC is also used to
  improve general service management, in addition to adding the
  functionality to automatically run when new elements are introduced to
  the system, such as plugging in an ethernet cable. Use of OpenRC
  introduces a new level of differentiation from FreeBSD as |trueos| now
  uses some different system services. These differences are listed in
  :numref:`Table %s <sysserv>`

  .. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}
                      |>{\RaggedRight}p{\dimexpr 0.30\linewidth-2\tabcolsep}
                      |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}|

  .. _sysserv:

  .. table:: Different system services between |trueos| and FreeBSD
     :class: longtable

     +------------------+--------------+-----------------+
     | |trueos| Service | Started From | FreeBSD Service |
     +==================+==============+=================+
     | openntpd         | Ports        | ntpd            |
     +------------------+--------------+-----------------+
     | network          | Base         | netif           |
     +------------------+--------------+-----------------+
     | wpa_supplicant   | Ports; Start | wpa_supplicant  |
     |                  | with network | (from Base)     |
     +------------------+--------------+-----------------+
     | dhcpcd           | Ports        | dhclient        |
     +------------------+--------------+-----------------+

  .. note:: The :ref:`sysserv` table is updated as development
     continues on the |trueos| implementation of OpenRC. For a
     complete list of all available services through OpenRC, see
     :ref:`rcuprnlvl`.

* A |trueos| installation installs the |lumina| Desktop. Additional
  window managers can be installed using |appcafe|.

* The `SysAdm™ Client <https://sysadm.us/handbook/client/>`_
  and `Server <https://sysadm.us/handbook/server/>`_ has replaced
  Control Panel. Most of the utilities from the Control Panel are
  rewritten to use the |sysadm| middleware. Under the hood, |sysadm|
  provides REST and WebSocket APIs for securely managing local and
  remote FreeBSD and |trueos| systems.

* Many utilities have been converted to the |sysadm| API and are
  available through `SysAdm <https://sysadm.us/handbook/client/>`_:

  * AppCafe
  * Update Manager
  * Boot Environment Manager
  * Life Preserver
  * Firewall Manager
  * User Manager
  * Network Manager

* The functionality provided by the *About* utility is incorporated into
  :lumbk:`Lumina Information <luminautl.html#information>`.

* The functionality provided by the
  :sysclbk:`Service Manager <service-manager>`
  (:command:`pc-servicemanager`) is integrated into |sysadm|.

* The Active Directory & LDAP utility (:command:`pc-adsldap`) is
  deprecated.

* Login Manager (:command:`pc-dmconf`) is replaced by
  :command:`pcdm-config`).

* System Manager (:command:`pc-sysmanager`) is deprecated.

* :command:`freebsd-update` is retired in favor of using :command:`pkg`
  for system updates.

* The option to use the SCFB display driver is added to the installer.
  This driver is suitable for newer UEFI laptops as it automatically
  detects native resolution and is a good solution for newer Intel
  drivers that have not been ported yet to FreeBSD. Before selecting
  this driver, check the BIOS and ensure the CSM module is disabled.
  This driver does not support a dual-head configuration, such as an
  external port for presentations, or suspend and resume.

* :guilabel:`Customize` is removed from the :ref:`System Selection`
  screen in order to reduce the size of the installation media.
  Additional software can be installed post-installation using
  |appcafe|.

* The :guilabel:`Boot to console (Disable X)` option has been added to
  the graphical boot menu.

* These new utilites are available in the *SysAdm Client*:
  :sysclbk:`Managing Remote Connections <managing-remote-connections>`
  and :sysclbk:`Task Manager <task-manager>`.

* The graphical and command line versions of PBI Manager and Warden are
  removed.

* :command:`pc-thinclient` is removed as it is deprecated.

.. index:: Linux and TrueOS
.. _Linux and TrueOS:

Linux and |trueos|
------------------

|trueos| is based on FreeBSD, meaning it is not a Linux distribution. If
you have used Linux before, you may find some features you are used to
have different names on a BSD system and some commands are different.
This section covers some of these differences.

BSD and Linux use different filesystems during installation. Many Linux
distros use EXT2, EXT3, EXT4, or ReiserFS, while |trueos| uses OpenZFS.
This means if you wish to dual-boot with Linux or access data on an
external drive formatted with another filesystem, you will want to
research if the data is accessible to both operating systems.

:numref:`Table %s <filesys support>` summarizes the various filesystems
commonly used by desktop systems. |trueos| automatically mounts several
filesystems: *FAT16*, *FAT32*, *EXT2*, *EXT3* (without journaling),
*EXT4* (read-only), *NTFS5*, *NTFS6*, and *XFS*. See the section on
:ref:`Files and File Sharing` for a comparison of some graphical file
manager utilities.

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.15\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.15\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.15\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.55\linewidth-2\tabcolsep}|

.. _filesys support:

.. table:: Filesystem Support on |trueos|
   :class: longtable

   +------------+-----------+--------------+--------------------------------------------------------+
   | Filesystem | Native to | Non-native   | Usage notes                                            |
   |            |           | support type |                                                        |
   +============+===========+==============+========================================================+
   | Btrfs      | Linux     | none         |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | exFAT      | Windows   | none         | requires a license from Microsoft                      |
   +------------+-----------+--------------+--------------------------------------------------------+
   | EXT2       | Linux     | r/w support  |                                                        |
   |            |           | loaded by    |                                                        |
   |            |           | default      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | EXT3       | Linux     | r/w support  | since EXT3 journaling is not supported, you will not   |
   |            |           | loaded by    | be able to mount a filesystem requiring a journal      |
   |            |           | default      | replay unless you :command:`fsck` it using an          |
   |            |           |              | external utility such as                               |
   |            |           |              | `e2fsprogs <http://e2fsprogs.sourceforge.net>`_        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | EXT4       | Linux     | r/o support  | EXT3 journaling, extended attributes, and inodes       |
   |            |           | loaded by    | greater than 128 bytes are not supported; EXT3         |
   |            |           | default      | filesystems converted to EXT4 may have better          |
   |            |           |              | performance                                            |
   +------------+-----------+--------------+--------------------------------------------------------+
   | FAT16      | Windows   | r/w support  |                                                        |
   |            |           | loaded by    |                                                        |
   |            |           | default      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | FAT32      | Windows   | r/w support  |                                                        |
   |            |           | loaded by    |                                                        |
   |            |           | default      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | HFS+       | Mac OS X  | none         | older Mac versions might work with                     |
   |            |           |              | `hfsexplorer <http://www.catacombae.org/hfsexplorer>`_ |
   +------------+-----------+--------------+--------------------------------------------------------+
   | JFS        | Linux     | none         |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | NTFS5      | Windows   | full r/w     |                                                        |
   |            |           | support      |                                                        |
   |            |           | loaded       |                                                        |
   |            |           | by default   |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | NTFS6      | Windows   | r/w support  |                                                        |
   |            |           | loaded by    |                                                        |
   |            |           | default      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | ReiserFS   | Linux     | r/o support  |                                                        |
   |            |           | is loaded by |                                                        |
   |            |           | default      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | UFS2       | FreeBSD   | check if a   | changed to r/o support in Mac Lion                     |
   |            |           | Linux distro |                                                        |
   |            |           | provides     |                                                        |
   |            |           | ufsutils;    |                                                        |
   |            |           | r/w support  |                                                        |
   |            |           | on Mac; UFS  |                                                        |
   |            |           | Explorer can |                                                        |
   |            |           | be used on   |                                                        |
   |            |           | Windows      |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+
   | ZFS        | |trueos|, |              |                                                        |
   |            | FreeBSD   |              |                                                        |
   +------------+-----------+--------------+--------------------------------------------------------+

Linux and BSD use different naming conventions for devices. For example:

* In Linux, Ethernet interfaces begin with :file:`eth`. With BSD,
  interface names indicate the name of the driver. For example, an
  Ethernet interface may be listed as :file:`re0`, indicating it uses
  the Realtek :file:`re` driver. The advantage of this convention is
  you can read the **man 4** page for the driver (e.g. type
  :command:`man 4 re`) to see which models and features are provided by
  the driver.

* BSD disk names differ from Linux. IDE drives begin with :file:`ad` and
  SCSI and USB drives begin with :file:`da`.

Some of the features used by BSD have similar counterparts to Linux, but
the name of the feature is different. :numref:`Table %s <feature names>`
provides some common examples:

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.30\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.25\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.45\linewidth-2\tabcolsep}|

.. _feature names:

.. table:: BSD and Linux Feature Names
   :class: longtable

   +--------------------------------+---------------------+--------------------------------+
   | TrueOS                         | Linux               | Description                    |
   +================================+=====================+================================+
   | IPFW                           | iptables            | Default firewall               |
   +--------------------------------+---------------------+--------------------------------+
   | :file:`/etc/init.d/` for       | :file:`rc0.d/`,     | In |trueos|, the directories   |
   | operating system and           | :file:`rc1.d/`,     | containing the startup scripts |
   | :file:`/usr/local/etc/init.d/` | etc.                | do not link to runlevels as    |
   | for applications               |                     | there are no runlevels. System |
   |                                |                     | startup scripts are separated  |
   |                                |                     | from third-party application   |
   |                                |                     | scripts.                       |
   +--------------------------------+---------------------+--------------------------------+
   | :file:`/etc/ttys` and          | :command:`telinit`, | Terminals configured in *ttys* |
   | :file:`/etc/rc.conf`           | :file:`init.d/`     | and *rc.conf* indicate which   |
   |                                |                     | services start at boot time.   |
   +--------------------------------+---------------------+--------------------------------+

Users comfortable with the command line may find some of the common
Linux commands have different names on BSD.
:numref:`Table %s <common commands>` lists some common commands and
what they are used for.

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.45\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.55\linewidth-2\tabcolsep}|

.. _common commands:

.. table:: Common BSD and Linux Commands
   :class: longtable

   +-----------------------------------+-----------------------------+
   | Command                           | Used                        |
   +===================================+=============================+
   | :command:`dmesg`                  | discover what hardware was  |
   |                                   | detected by the kernel      |
   +-----------------------------------+-----------------------------+
   | :command:`sysctl dev`             | display configured devices  |
   +-----------------------------------+-----------------------------+
   | :command:`pciconf -l -cv`         | show PCI devices            |
   +-----------------------------------+-----------------------------+
   | :command:`dmesg | grep usb`       | show USB devices            |
   +-----------------------------------+-----------------------------+
   | :command:`kldstat`                | list all modules loaded in  |
   |                                   | the kernel                  |
   +-----------------------------------+-----------------------------+
   | :command:`kldload <module>`       | load a kernel module for    |
   |                                   | the current session         |
   +-----------------------------------+-----------------------------+
   | :command:`pkg install <pkgname>`  | install software from the   |
   |                                   | command line                |
   +-----------------------------------+-----------------------------+
   | :command:`sysctl hw.realmem`      | display hardware memory     |
   +-----------------------------------+-----------------------------+
   | :command:`sysctl hw.model`        | display CPU model           |
   +-----------------------------------+-----------------------------+
   | :command:`sysctl hw.machine_arch` | display CPU Architecture    |
   +-----------------------------------+-----------------------------+
   | :command:`sysctl hw.ncpu`         | display number of CPUs      |
   +-----------------------------------+-----------------------------+
   | :command:`uname -vm`              | get release version         |
   |                                   | information                 |
   +-----------------------------------+-----------------------------+
   | :command:`gpart show`             | show device partition       |
   |                                   | information                 |
   +-----------------------------------+-----------------------------+
   | :command:`fuser`                  | list IDs of all processes   |
   |                                   | with one or more files open |
   +-----------------------------------+-----------------------------+

There are many articles and videos which provide additional information
about some of the differences between BSD and Linux:

* `Comparing BSD and Linux <https://www.freebsd.org/doc/en/articles/explaining-bsd/comparing-bsd-and-linux.html>`_

* `FreeBSD Quickstart Guide for Linux® Users <https://www.freebsd.org/doc/en/articles/linux-users/index.html>`_

* `BSD vs Linux <http://www.over-yonder.net/~fullermd/rants/bsd4linux/01>`_

* `Why Choose FreeBSD? <https://www.freebsd.org/advocacy/whyusefreebsd.html>`_

* `Interview: BSD for Human Beings <https://www.unixmen.com/bsd-for-human-beings-interview/>`_

* `Video: BSD 4 Linux Users <https://www.youtube.com/watch?v=xk6ouxX51NI>`_

* `Why you should use a BSD style license for your Open Source Project <https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html>`_

* `A Sysadmin's Unixersal Translator (ROSETTA STONE) <http://bhami.com/rosetta.html>`_

.. index:: TrueOS and Windows
.. _compareWindows:

TrueOS and Windows
------------------

|trueos| uses several similar, but different elements to their
counterparts on Windows. :numref:`Table %s <troswinapps>` highlights a
few of these:

.. note:: This table isn't meant to be an exhaustive listing of
   applications, but simply provide a few TrueOS/FreeBSD
   equivalents for users familiar with their previous operating
   system.

.. tabularcolumns:: |>{\RaggedRight}p{\dimexpr 0.30\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}
                    |>{\RaggedRight}p{\dimexpr 0.35\linewidth-2\tabcolsep}|

.. _troswinapps:
.. table:: TrueOS/Windows equivalents

   +---------------------+-------------------+-------------------+
   | Element             | Windows           | TrueOS            |
   +=====================+===================+===================+
   | Office Applications | Microsoft Office  | LibreOffice       |
   +---------------------+-------------------+-------------------+
   | Image editing       | Photoshop         | GIMP              |
   +---------------------+-------------------+-------------------+
   | PDF viewing         | Acrobat           | Okular            |
   +---------------------+-------------------+-------------------+
   | Media Player        | Windows Media     | VLC Media Player  |
   +---------------------+-------------------+-------------------+
   | Internet Browsing   | Internet Explorer | Chromium, Firefox |
   |                     | and many options  | and many options  |
   +---------------------+-------------------+-------------------+

Here are a few resources that go into greater detail examining the
differences between Windows and BSD:

* `FreeBSD is NOT Windows <http://vtbsd.net/notwindows.html>`_
* General `Comparison of Operating Systems <https://en.wikipedia.org/wiki/Comparison_of_operating_systems>`_
* `Open Source Alternatives <https://opensource.com/alternatives>`_

.. TODO: Expand this section
   .. index:: MacOSX and TrueOS
   .. _compareMacOSX:

   Mac OS X and TrueOS
   -------------------

   Mac OS X is actually related to FreeBSD, resulting in some system
   level similarities. However, application development has diverged
   pretty strongly, so here are some suggestions for TrueOS/FreeBSD
   applications which may "fill the void" from your Mac system.

.. index:: virtualization
.. _Virtualization:

Virtualization
==============

A virtualized environment allows a user to test drive an operating
system without overwriting the current operating system. This is an
excellent way to practice installation, determine whether the hardware
is supported, or to try multiple versions of different operating
systems. Virtualization software effectively creates windows (known as
virtual machines) to install and use an operating system. The only
limitation to virtualization is the hardware, as each virtual machine
uses CPU and RAM. Depending upon the amount of CPU and RAM in the
computer, the installed operating system using virtualization software
may run slowly. If the computer slows down, try closing other
applications running on the computer to free up some RAM.

To run virtualization software on |trueos|, search for *virtualbox*
within the |sysadm| :sysclbk:`AppCafe <appcafe>` and install the
`VirtualBox <https://www.virtualbox.org/>`_ open source virtualization
program and the
`VirtualBox Guest Additions <http://www.virtualbox.org/manual/ch04.html>`_.
The guest additions add mouse pointer integration, shared folders
between the host and guest, better video support, and a shared
clipboard.

.. note:: The first time running VirtualBox on a |trueos| system, a
   background script automatically gives the user account the
   permissions required to run this application. This might break any
   existing shortcuts to VirtualBox. To fix the shortcut, logout and in
   again.

If the computer is running another operating system, download the binary
for the specific operating system from the
`VirtualBox Downloads page <https://www.virtualbox.org/wiki/Downloads>`_.
VirtualBox runs on Windows, Linux, Macintosh, and OpenSolaris. It
supports a large number of virtual machine installable operating
systems.

This section describes how to prepare VirtualBox for an installation of
|trueos| using an :file:`.iso` file.

.. index:: create virtual machine for an iso
.. _Creating a Virtual Machine for an ISO File:

Creating a Virtual Machine for an ISO File
------------------------------------------

Once the |trueos| ISO is downloaded and VirtualBox installed on the
current system, create a virtual machine and use the ISO to install
|trueos| into the virtual machine. The virtual machine must meet several
minimum requirements and this section will demonstrate how to configure
these:

* 1024 MB base memory size.

* A virtual disk **at least 20 GB in size** for a server installation or
  **at least 50 GB in size** for a desktop installation.

* A bridged adapter.

To create the virtual machine, start VirtualBox to see the screen shown
in :numref:`Figure %s <vbox1>`.

.. _vbox1:

.. figure:: images/vbox1a.png
   :scale: 100%

   VirtualBox Menu

Click :guilabel:`New` to start the new virtual machine wizard and
display the screen in :numref:`Figure %s <vbox2>`.

.. _vbox2:

.. figure:: images/vbox2a.png
   :scale: 100%

   Create Virtual Machine - Name, Type, and Version

Enter a name for the virtual machine; it can be anything which makes
sense to you. Click the :guilabel:`Operating System` drop-down menu and
select :guilabel:`BSD`. In the :guilabel:`Version` drop-down menu,
select :guilabel:`FreeBSD (64 bit)`. Click :guilabel:`Next` to see the
screen in :numref:`Figure %s <vbox3>`.

.. _vbox3:

.. figure:: images/vbox3a.png
   :scale: 100%

   Virtual Machine Reserved Memory

The base memory size must be changed to **at least 1024 MB.** If the
system has a lot of RAM, use more. Any number within the green area is
considered a safe value by VirtualBox, meaning it should not slow down
the computer too much. When finished, click :guilabel:`Next` to see the
screen in :numref:`Figure %s <vbox4>`.

.. _vbox4:

.. figure:: images/vbox4a.png
   :scale: 100%

   Virtual Hard Drive - New or Existing

This screen is used to create the virtual hard drive, or the amount of
disk space available to the virtual machine. If this is your first
virtual machine, keep the default of
:guilabel:`Create a virtual hard drive now` and click
:guilabel:`Create` to go to the screen shown in
:numref:`Figure %s <vbox5>`. If you have created a virtual machine in
the past and wish to reuse its disk space, select
:guilabel:`Use an existing virtual hard drive file` from the drop-down
menu. Create as many virtual machines as desired. However, if the
computer is getting low on disk space, consider reusing existing virtual
hard drives to prevent the physical hard drive from being used up by old
virtual machines.

.. _vbox5:

.. figure:: images/vbox5a.png
   :scale: 100%

   Hard Drive Type

Select :guilabel:`VDI` and click :guilabel:`Next` to see the screen in
:numref:`Figure %s <vbox6>`.

.. _vbox6:

.. figure:: images/vbox6a.png
   :scale: 100%

   Storage Type

Now choose whether to have :guilabel:`Dynamically allocated` or
:guilabel:`Fixed size` storage. The first option uses disk space as
needed until it reaches the maximum size set in the next screen. The
second option creates a disk the same size as that specified amount of
disk space, whether it is used or not. Choose the first option if disk
space is a concern; otherwise choose the second option as it allows
VirtualBox to run slightly faster. Once :guilabel:`Next` is selected,
the screen in :numref:`Figure %s <vbox7>` displays.

.. _vbox7:

.. figure:: images/vbox7a.png
   :scale: 100%

   Virtual Disk - File Name and Size

This screen is used to set the size (or upper limit) of the virtual
machine. If planning to install |trueos| into the virtual machine,
**increase the size to at least 20 GB** or an error will display during
the |trueos| installation. If planning to install KDE, GNOME, multiple
desktop managers, or applications within the virtual machine, choose at
least **50 GB**. Whatever size is set, be sure the computer has enough
free disk space to support it. Use the :guilabel:`folder` icon to browse
to a directory on disk with sufficient space to hold the virtual
machine.

Once the selections are made, press :guilabel:`Create` to finish using
the wizard. The virtual machine will now show up in the left box, as
seen in the example in :numref:`Figure %s <vbox8>`.

.. _vbox8:

.. figure:: images/vbox8a.png
   :scale: 100%

   New Virtual Machine "test"

In order to use the network card, configure bridging on the virtual
machine. To do this, go to :menuselection:`Settings --> Network`. In the
:guilabel:`Attached to` drop-down menu select
:guilabel:`Bridged Adapter`, then select the name of the physical
interface from the :guilabel:`Name` drop-down menu. In the example shown
in :numref:`Figure %s <vbox9>`, the Intel Pro/1000 Ethernet card is
attached to the network and has a device name of :file:`re0`.

.. _vbox9:

.. figure:: images/vbox9a.png
   :scale: 100%

   VirtualBox Bridged Adapter Configuration

Before starting the virtual machine, configure it to use the
installation media. Click the :guilabel:`Storage` hyperlink in the right
frame to access the storage screen seen in :numref:`Figure %s <vbox10>`.

.. _vbox10:

.. figure:: images/vbox10a.png
   :scale: 100%

   Virtual Machine Storage Settings

Double-click the word :guilabel:`Empty`, which represents the DVD
reader. To access the |trueos| installer from the DVD reader,
double-check the :guilabel:`Slot` is pointing to the correct location
(e.g. :guilabel:`IDE Secondary Master`) and use the drop-down menu to
change it if the location is incorrect.

If using an ISO stored on the hard disk is preferred, click the
:guilabel:`DVD` icon then :guilabel:`Choose a virtual CD/DVD disk file`
to open a browser menu to navigate to the location of the ISO. Highlight
the desired ISO and click :guilabel:`Open`. The name of the ISO will now
appear in the :guilabel:`Storage Tree` section.

|trueos| is now ready to be installed into the virtual machine.
Highlight the virtual machine and click on the green :guilabel:`Start`
icon. A window opens, indicating the virtual machine is starting. If a
DVD is inserted, it should audibly spin and the machine will start to
boot into the installation program. If it does not or if using an ISO
stored on the hard disk, press :kbd:`F12` to select the boot device
when the message to do so appears, then press :kbd:`c` to boot from
CD-ROM. Proceed through the installation as described in the
:ref:`Install` section.

.. note:: If the installer GUI doesn't appear to load after configuring
   your virtual machine, you may need to enable **EFI** in Virtualbox by
   navigating :menuselection:`Settings --> System --> Motherboard` and
   checking :guilabel:`Enable EFI (special OSes only)`.

.. index:: supported hardware
.. _Supported Hardware:

Supported Hardware
==================

While the |trueos| installer is very easy to use, installing a brand new
operating system can sometimes be a daunting task.

Before beginning, there are a few things to check to ensure the system
is ready to install |trueos|.

* **Dual-booting or installing over the entire drive?** If dual-booting,
  please ensure a primary partition is available. Refer to the chapter
  on :ref:`Dual Booting`.

* **Is your important data backed up?** Any irreplaceable data, such as
  emails, bookmarks, or important files and documents should **always**
  be backed up to an external media, such as a removable drive or
  another system, **before** installing or upgrading any operating
  system.

To determine if the chosen hardware is detected by |trueos|, start a
new installation and click the :guilabel:`Hardware Compatibility` icon
in the lower left corner of the :ref:`Language` screen.

If any problems arise with the installation, refer to the
:ref:`Troubleshooting` section of this handbook.

This section discusses the |trueos| hardware requirements and some
supported hardware.

.. index:: Minimum Requirements
.. _Minimum Requirements:

Minimum Requirements
--------------------

|trueos| has moderate hardware requirements and typically uses less
resources than its commercial counterparts. Before installing |trueos|,
make sure the hardware or virtual machine meets at least the minimum
requirements. To get the most out of your |trueos| experience, use a
system exceeding the minimum or recommended system requirements.

At **bare minimum**, these requirements must be met in order to install
|trueos|:

**Minimum**

* 64-bit processor

* 1 GB RAM

* 20 GB of free hard drive space on a primary partition for a
  command-line server installation.

* Network card

Here are the **recommended** requirements. More RAM and available disk
space improves the computing experience:

**Recommended**

* 64-bit processor

* 4 GB of RAM

* 50 GB of free hard drive space on a primary partition for a graphical
  desktop installation.

* Network card

* Sound card

* 3D-accelerated video card

|trueos| does not require 50 GB for its installation. The minimum
recommendation is to provide sufficient room for the installation of
applications and to store local ZFS snapshots and boot environments.
These can be used to retrieve earlier versions of files, rollback the
operating system to an earlier point in time, or clone the operating
system.

More RAM is always recommended, so install as much as you can afford.
To play modern video games, use a fast CPU. To create a collection of
music and movies on the computer, sufficient disk space is required.

.. index:: Supported Processors
.. _Processor:

Processor
---------

|trueos| installs on any system containing a 64-bit (also called
*amd64*) processor. Despite the name, a 64-bit processor does **not**
need to be manufactured by AMD in order to be supported. The
`FreeBSD Hardware Notes - amd64 <https://www.freebsd.org/releases/11.0R/hardware.html#proc-amd64>`_
lists the *amd64* processors known to work.

.. index:: Supported Graphics
.. _Graphics:

Graphics
--------

Like many open source operating systems, |trueos| uses
`X.org <https://www.x.org/wiki/>`_ drivers for graphics support.
|trueos| automatically detects the optimal video settings for
supported video drivers. Verify the graphics hardware is supported by
clicking the :guilabel:`Hardware Compatibility` icon within the
installer.

Here is the major graphic vendor support:

**NVIDIA:** 3D acceleration on NVIDIA is provided by native FreeBSD
drivers. If an NVIDIA video card is detected, an
:guilabel:`nVidia settings` icon will be added to
:guilabel:`Browse Applications` for managing NVIDIA settings.

**Intel:** 3D acceleration on most Intel graphics is supported. This
includes Skylake, Haswell, Broadwell, and ValleyView.

**ATI/Radeon:** 3D acceleration on most ATI and Radeon cards is
supported.

**Optimus:** At this time there is no switching support between the two
graphics adapters provided by Optimus. Optimus implementations vary, so
|trueos| may or may not be able to successfully load a graphics driver
on hardware. If a blank screen shows after installation, check the BIOS
to see if it has an option to disable one of the graphics adapters
or to set *discrete* mode. If the BIOS does not provide a *discrete*
mode, |trueos| defaults to the 3D Intel driver and disables NVIDIA. This
will change in the future when the NVIDIA driver supports Optimus.

.. index:: supported wireless cards
.. _Wireless:

Wireless
--------

|trueos| has built-in support for most wireless networking cards.
|trueos| automatically detects available wireless networks for supported
wireless devices. Verify the device is supported by clicking the
:guilabel:`Hardware Compatibility` icon within the installer. If it is
an external wireless device, insert it before running the installer.

Certain Broadcom devices, typically found in less expensive laptops, are
buggy and can have lockups when in *DMA* mode. If the device freezes,
try switching to *PIO* mode in the BIOS. Alternately, add
:command:`hw.bwn.usedma=0` to :file:`/boot/loader.conf` and reboot to
see if anything changes.

.. index:: supported laptops
.. _Laptops:

Laptops
-------

Many |trueos| users successfully run |trueos| on their laptops. However,
some issues may occur, depending upon the model of laptop. These
typically deal with:

* **Sleep/suspend:** Unfortunately,
  :wiki:`Advanced Configuration and Power Interface <Advanced_Configuration_and_Power_Interface>`
  (ACPI) is not an exact science, meaning experimentation with various
  :command:`sysctl` variables may be required to achieve successful
  sleep and suspend states on your particular laptop model. If the
  laptop is a ThinkPad,
  `ThinkWiki <http://www.thinkwiki.org/wiki/ThinkWiki>`_ is an
  excellent resource. For other types of laptops, try reading the
  *SYSCTL VARIABLES* section of :command:`man 4 acpi` and check to see
  if there is an ACPI man page specific to the laptop's vendor by typing
  :command:`apropos acpi.` The
  `Tuning with sysctl(8) <https://www.freebsd.org/doc/en/books/handbook/configtuning-sysctl.html>`_
  section of the FreeBSD Handbook demonstrates how to determine the
  current :command:`sysctl` values, modify a value, and make a modified
  value persist after a reboot.

* **Synaptics:** Disabling the system's touchpad may be dependant upon
  the hardware. This
  `forum post <https://forums.freebsd.org/threads/17370/#post-100670>`_
  describes how to enable Synaptics and some of the :command:`sysctl`
  options this feature provides.

  The `SysAdm Mouse Settings <https://sysadm.us/handbook/client/>`_
  also has options for disabling a system's touchpad, if one is
  detected.

To test the laptop's hardware, use the
:guilabel:`Hardware Compatibility` icon in the :ref:`Language` screen
before continuing with the installation.

To install |trueos| onto an Asus Eee PC, review the
`FreeBSD Eee page <https://wiki.FreeBSD.org/AsusEee>`_ first.

The FreeBSD
`Tuning Power Consumption page <https://wiki.FreeBSD.org/TuningPowerConsumption>`_
has some tips for reducing power consumption.

.. index:: thinkpad

With regards to specific hardware, the ThinkPad T420 may panic during
install. If it does, go into the BIOS and set the video mode to
"discrete", which should allow the installation to complete. Some
Thinkpads have a BIOS bug preventing them from booting from
GPT-labeled disks. If unable to boot into a new installation, restart
the installer and go into :guilabel:`Advanced Mode` in the
:ref:`Disk Selection` screen. Make sure
:guilabel:`GPT (Best for new hardware)` is unchecked. If it was
checked previously, redo the installation with the box unchecked.
