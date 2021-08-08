# SPC music for VARIA Customizer

In this folder is stored all the data needed to apply custom SPC music in the VARIA customizer. First of all, be aware that this is different from MSU music. MSU patch is applied by default on all VARIA seeds, and you should just follow the necessary steps similar to vanilla or any other MSU-patched games to have a high qualty custom soundtrack.

The music here is for the native SNES sound processor, the SPC-700, and has to be written in accordance to the engine used by Super Metroid (N-SPC). The steps to follow to port or compose music are to first write your music in the IT tracker format, and then use mITroid (https://github.com/tewtal/mITroid/releases) tool to convert them. This process will not be described further here.

# Music Data / Music Track

In Super Metroid, there is a distinction between music data (samples used etc.) and music tracks (actual songs played). For VARIA customizer, we did everything so that you don't have to worry about it and just choose music tracks to replace the vanilla ones. Once all the track metadata (see below) has been loaded, the only thing you need to care about is the music track name.

# Data Organization

For a music track, we need its name, a N-SPC file (a binary blob that will be dumped in the ROM by the customizer), an optional (but heavily recommended) SPC file for music preview in the web interface, and some optional info (original author, SM port author, and a track description saying for example the game it was taken from, usage notes etc.) All this data will be presented to the user in the web interface when the track is selected.

The data files can be stored anywhere in this folder, what's important is their description in the JSON metadata files, located in the _metadata subfolder.

Example metadata for a single track:

```
    "Metroid Prime - Nostalgia Clad In Ice (Phendrana Drifts Cover)": {
        "nspc_path": "prime/NostalgiaCladInIce_PhendranaCover.nspc",
        "track_index": 0,
        "original_author": "Kenji Yamamoto",
        "port_author": "Black Falcon",
        "description": "Metroid Prim Phendrana Drifts SM cover",
        "spc_path": "prime/NostalgiaCladInIce_PhendranaCover.spc"
    }
```

The key is the track name that will be presented to the user. track_index will usually be 0, unless you go through the hurdles of making multiple tracks in a single data file. Paths are relatvie to this folder.

It is a good idea to prefix the track name with something if it's part of a song set, or to identify source game for example. That way, all tracks with the same prefix will be displayed alongside each other.

As long as this is in a JSON file present in the _metadata folder, that's it, the track will be available for usage in the VARIA customizer!

# Vanilla soundtrack

Do not touch vanilla/ subfolder as well as _metadata/vanilla.json file, as they contain the vanilla soundtrack for non-replaced tracks, and the description of all the addresses where tracks are referenced in the game.

# Constraints files

The _constraints special folder is used to store constraints as to which tracks must be preserved or can be discarded, as well as usable space in ROM to store music (PC addresses). Constraint files are provided for vanilla ROM and VARIA seeds, and are automatically used by the customizer. They are still in external data files to be able to patch other kinds of ROM such as ROM hacks (in which case the vanilla.json file would have to be modified to match the addresses used in the hack.

