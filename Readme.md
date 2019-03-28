The readme for Dolphin/Ishiiruka is [here](https://github.com/project-slippi/Ishiiruka/README.md).

## What's special about this build

I intend to train neural nets on Melee frames. This process is made much easier if [you can generate corpora automatically](sverona/meleedb-corpus), for which [Project Slippi](project-slippi/project-slippi) is invaluable.

However, this use case requires a couple of additions:

### Logging dropped frames

.slp files (the JSON dumps output by Slippi that contain time-series of certain values in Melee's memory) do not automatically line up with Dolphin frame dumps, which drop frames at an irregular rate. Thus we need to track which frames get dropped.

This is done by adding a logging call to [AVIDump::AddFrame].

### Opening up output UBJSON format

At present, it suffices to learn data already present in .slp files. One direction for future work is learning things like camera pose whose [representation is not fully understood](https://gist.github.com/sverona/22823f3463eb4ca78e12354abf74bd87#file-ssbmscratchpad-txt-L3940).

To do this, it would be helpful to have a means of specifying which values need to be tracked.

This hasn't been tackled yet.
