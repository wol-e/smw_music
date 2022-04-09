# smw_music/spc

`spc_tool`is a helper for working with SPC files for Super Mario World custom music on Linux. Basically a scripts to conveniently handle common spc tasks like
- Creating an spc from a txt file via Addmusick
- Playback of spc via SPC Player 700
- Converting spc to wav (work in progress)

## Requirements

You need to
- use Linux system, all scripts are tested on Ubuntu
- wine installed (e.g. using ubuntu `sudo apt-get install wine-stable` as of writing this)
- Downloaded Addmusick (aka AMK, tested version is 1.0.6)
- Downloaded SNES SPC700 Player

## Setup

After clonign this repo the script 'spc_tool' needs to be marked as an executable via running `chmod +x scp_tool` on command line working inside the directory where the file 'spc_tool' is located (aka the directory of this readme). After this you cann call the script from command line via running `./spc_tool` from this directory (you can of course add it to your path to call it from any folder via `spc_tool`, this can be done for the current session via `source setip.sh`).

An important setup step is you need to set environment variables for the locations of SPC700 player and AddmusicK. For example:

`export SPC700_DIR=/path/to/your/spcplay-2.18.4.7379`

`export AMK_DIR=/path/to/your/AddmusicK_1.0.8'`

It is suggested to permanently add these to variables your shell profiles for convenience. If you don't want to refer to the scripts location when using it you can add this directory to your path, e.g. via `export PATH=$PATH:$(pwd)` (when your current working directory is this directory).

## Usage

To display an overview of it's usage on the command line simply run `./spc_tool -h`. Then you will see this output, which should get you everywhere:

-h   display this help text
play   launches SPC 700 Player via wine and plays spc file provided as 2nd argument.
build   converts a composition in .txt format via AddmusicK and wine to an .spc file.
wav   converts an .spc file to a .wav audio file via ffmpeg (in development, results may be poor)

For example,

- if you want to create an .spc file 'test.spc' from an existing composition 'test.txt' you need to run
`./spc_tool build test.txt test.spc`

- if you want to playback an .spc file, say 'test.spc', run `./spc_tool play test.spc`.

- if you want to convert an .spc to .wav run for example `./spc_tool wav test.spc test.wav 00:05:30` (note: since an spc is intended to loop, when ceonverting you need to parse a duration for the target wav file, since the programm would not know how often to loop. This feature is in development and will be improved hopefully).
