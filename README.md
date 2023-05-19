# rancid-arubaos
*A Perl module for Aruba devices in RANCID*

This is a fork of https://github.com/miken32/rancid-aruba.

miken32 no longer has any of these sorts of devices but has still been accepting patches
that look sensible.

At the moment there is little if any divergence between this modiule and miken32's.

Since the token `aruba` is somewhat misleading now amongst the many operating systems Aruba
now has, I am tending to use the token `arubaos` to be clearer, hence the naming of this
repository.  If this fork does materially diverge, I may well change the token as used
in the rancid configs too, but it remains `aruba` as noted below for now.

miken32's original notes (more or less):

This was tested by me on a limited number of legacy Aruba devices (6000 and 7210 wireless mobility access controllers running ArubaOS 6.3 and 6.4; and S1500 and S2500 switches running ArubaOS 7.1 and 7.2) but has since been used successfully on devices running 8.x software.

Note that **modern Aruba-branded switches are derived from HPE's ProVision switch line, and should be considered HP switches for the purposes of RANCID**.

Install `aruba.pm` into your Perl module directory - in my Scientific Linux install it's at `/usr/share/perl5/vendor_perl/rancid/`.

There is no need for a separate login script. The included `clogin` works fine, as long as you remember to disable paging manually at login. Here is suggested content for your `/etc/rancid/rancid.types.conf` file; note I'm disabling encryption of certain passwords in the output. This may not be desirable for all.

    # ArubaOS device
    aruba;script;rancid -t aruba
    aruba;login;clogin
    aruba;module;aruba
    aruba;inloop;aruba::inloop
    aruba;command;aruba::RunCommand;no paging
    aruba;command;aruba::RunCommand;encrypt disable
    aruba;command;aruba::ShowVersion;show version
    aruba;command;aruba::ShowMasterRedundancy;show master-redundancy
    aruba;command;aruba::ShowBoot;show boot
    aruba;command;aruba::ShowImageVersion;show image version
    aruba;command;aruba::Dir;dir
    aruba;command;aruba::ShowInterfaceTransceivers;show interface transceivers
    aruba;command;aruba::ShowPacketCapture;show packet-capture
    aruba;command;aruba::ShowInventory;show inventory
    aruba;command;aruba::ShowVLAN;show vlan
    aruba;command;aruba::WriteTerm;write term
