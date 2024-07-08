qb2
===

This is a fork of Q2PRO with "bigmap" capability introduced in some Quake engine compilers and based on implementation from Kmquake2 code.  The protocol supports map bounds increase from 4096 (+ and - in each axis) to 1048576, although 32768 is the max tested.  Requires q2tools compiler unless some other compiler adopts it.

The bigmap feature is separate from qbsp support:  bigmaps allows greater physical size of maps;  qbsp raises the limits of map components and entities to allow more detailed levels.

Due to protocol change affecting networking, savegames, and demos, qb2 is not compatible with other engines.  For example, there is not a way that I could find for checking demo files.

Standard protocol sends 2 bytes per coordinate.  The bigmap protocol sends 3 bytes per coordinate, therefore increasing packet size whenever anything moves. A potential reduction would be packing extended coordinates into a single extra byte that gets sent with any coordinate change; say 3 bits X, 3 bits Y, and 2 bits Z, for limits of 32768 x 32768 x 16384.

A debug utility when compiled with USE_BITCOUNT_DEBUG counts the frequency of each message bit flag.  These bits signal various entity state changes including position, effects, and animation frame.  Ideally the most frequently used bits would be first so that empty flags are not sent, reducing message size.  Based on limited testing reording the sequence may be more efficient. 


Q2PRO
=====

Q2PRO is an enhanced, multiplayer oriented Quake 2 client and server.

Features include:

* rewritten OpenGL renderer optimized for stable FPS
* enhanced client console with persistent history
* ZIP packfiles (.pkz), JPEG and PNG textures, MD3 models
* fast HTTP downloads
* multichannel sound using OpenAL
* recording from demos, forward and backward seeking
* server side multiview demos and GTV capabilities

For building Q2PRO, consult the INSTALL.md file.

Nightly Windows builds are available at https://skuller.net/q2pro/

For information on using and configuring Q2PRO, refer to client and server
manuals available in doc/ subdirectory.
