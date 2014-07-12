somfy-rts-fhem
==============

SOMFY - Somfy RTS / Simu Hz protocol support for [FHEM](http://www.fhem.de).

This code currently supports sending Somfy commands, as the corresponding CULFW has no RX support yet.

##### Define

	define <name> SOMFY <address> [<encryption-key>] [<rolling-code>]

The `address` is a 6-digit hex code, that uniquely identifies a single remote control channel.
It is used to pair the remote to the blind or dimmer it should control.

Pairing is done by setting the blind in programming mode, 
either by disconnecting/reconnecting the power, or by pressing the program button on an already associated remote.

Once the blind is in programming mode, send the `prog` command from within FHEM to complete the pairing.
The blind will move up and down shortly to indicate completion.

You are now able to control this blind from FHEM, the receiver thinks it is just another remote control.