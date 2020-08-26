Ostanes Steadfast Tool Addressing Needs to Evoke Software is in simple terms a glorified package manager. In many ways it's like _portage_ while also borrowing features and styles from homebrew, vcpkg, and other package managers. It supports a wide range of platforms while trying to keep the usage uniform across all of them. It is supposed to be flexible enough to address deficiencies in existing package managers and at the same time easy to configure or expand by adding and maintaining packages. The name is a reference to the [legendary Persian mage](https://iranicaonline.org/articles/ostanes).

# Definitions
- *ostanes*: the program
- *spirit*: a particular version of a software package with particular build configurations (e.g. boost 1.74, with-ICE, with-zlib, etc)
- *nomen*: a class of spirits sharing the same name or a name and a major version number (e.g. boost, python3, sqlite3, etc)
- *summon/banish*: install/uninstall a spirit
- *superior*: a spirit that must be summoned before another (e.g. a library or toolset dependency)
- *ritual*: a script with an optional set of instructions that can be used to summon a certain class of spirits
- *grimoire*: an indexed collection of rituals; equivalent of a repository for other package managers
- *vessel*: local storage where the summoned spirits dwell (e.g. /usr/local/ostanes/vessel)
- *orbuculum*: on systems that support symlinks, a local storage path containing only symlinks to actual files or directories in the vessel (e.g. /usr/local/ostanes/orb)
- *binding*: binding a nomen to a spirit is to make the nomen symlinks in the orbuculum refer to the spirit, in other words, setting the spirit as the default for the nomen
- *abode*: remote location where a particular spirit to be summoned is dwelling (e.g. download URL: https://dl.bintray.com/boostorg/release/1.74.0/source/boost_1_74_0.7z)
- *altar*: local storage that can be used by rituals for downloading, extracting, configuring, patching, building, etc (/tmp/altar)
- *charm*: a query that identifies a subset of the spirits governed by a ritual (e.g. { "name": "boost", version: "1.74" })

# Features
- Command line interface features commands to summon, banish, or locate a spirit using inline or infile charms.
- CLI can be used to configure ostanes grimoires (add/remove, enable/disable) and vessels (add/remove, select)
- Rituals can be defined to provide parameters, then, based on the values assigned to those parmeters at the time of performing the ritual, they prescribe such things as charms for superior spirits, abode(s), and commands to patch files, configure build tree, build the software, install, etc. Some of these are optional.
- A ritual can be a combination of declarative and procedural description where the procedural part can be omitted.
- CLI can be used to initialize new local grimoires, create new rituals and add them to existing local grimoires. You can upload the grimoir to your remote location after performing the necessary changes.
- ostanes allows multiple versions of the same software and even multiple configurations of the same version to be installed alongside one another. CLI can be used to banish older versions of all or of a particular software.
- orbuculum contains a set of symlinks (executables, libs, docs, etc) for every nomen with summoned spirits. The set of symlinks for every nomen help select a default spirit for each nomen. Its structure follows that of /usr/local, therefore its _bin_ directory can be added to path environment variable and it could be used as a prefix to find packages in cmake, pkgconfig, etc.
- Path environment variable is automatically configured to refer to orbuculum.
- CLI can be used for viewing all the summoned spirits of a nomen and bindin a spirit for a nomen.
- By default, if no spirit is set as default for 
- Summoning spirits by name (without version) assumes the latest version.
- Rituals or indexes are not cached locally as accessing the remote grimoire is fast enough given a reliable connection. Grimoire indexes are broken down to small enough chunks based on the initial letters of the package names they contain. When summoning a spirit, if not found in the vessel, only the required piece of the remote index is downloaded.
