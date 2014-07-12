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

##### Parameters
* `address` is a 6 digit hex number that uniquely identifies FHEM as a new remote control channel.

	You should use a different one for each device definition, and group them using a structure.

* `encryption-key` (optional) is a 2 digit hex number (first letter should always be A) that can be set to clone an existing remote control channel.

* `rolling-code` (optional) is a 4 digit hex number that can be set
   to clone an existing remote control channel.
   
If you set one of them, you need to pick the same address as an existing remote.

Be aware that the receiver might not accept commands from the remote any longer, if you used FHEM to clone an existing remote.

This is because the receiver's and the original remote's codes are out of sync.

##### Examples:
	define rollo_1 SOMFY 000001
	define rollo_2 SOMFY 000002
	define rollo_3_original SOMFY 42ABCD A5 0A1C