title: Mixxx 2.5 Released
authors: Evelynne Veys
tags: 2.5, release announcement
comments: yes
status: draft

#### All I want for DJ-ing is ...

Home alone? Scrooged? The sound of music? Die hard?
Change plans: this year you will be having something better to do than watching old Christmas movies.

Mixxx is now your secret "Santa comin' to town", our elves had "good hearts with the burning desire to work hard",
to get you "Rockin' around the Christmas tree at the party hop" with "something mighty sweet to see".
"For the present, look high, not low": Mixxx's "presents 'neath the tree"

#### So this is the last goodbye ...

Important: OS-Support.
macOS versions earlier than 11 can have a "Last Christmas".
Windows versions earlier than version 10 build 1809 can be "Driving home for Christmas".
For Ubuntu versions earlier than 22.04 "Christmas Will Break Your Heart".

By stepping over from Qt5 to Qt6 Mixxx is forced to increase the minimum system requirements to match those mandated by Qt.
That's why the support has been dropped for macOS earlier than 11, Windows versions earlier then version 10 build 1889 and Ubuntu earlier then 22.04.

#### Let's cheer for the elves

Ho Ho Ho, our sleigh is filled with many shiny presents:

A red box filled with improvements to waveforms: 'SlipMode waveform' gives you visual aid while scratchin':

@Video(https://www.youtube.com/watch?v=6VRz48Ler9o)

The 'beats until next marker' helps you to never miss the break:

@Video(https://www.youtube.com/watch?v=uYCXhKeJVFo)

The GL ES support makes the waveforms run smooth:

@Video(https://www.youtube.com/watch?v=5VJBuUR_cn8)

With a nice yellow bow around it, the new Skin & Interface features: the menubar can be hidden,
reworked toggles (fullscreen, cue popup, vinyl control), improved tooltips, improved controls and checks (AutoDJ,
effects), new command line interface options...

@Video(https://www.youtube.com/watch?v=qMRcJvntboE)

Our engine became a V8 sleigh: undo function for BPM/beats, beatloop anchor, rate tap button...

@Video(https://www.youtube.com/watch?v=7XKGodjiTNg)

"Rudolph, the Red-Nosed Reindeer" will sound much better with the compressor and glitch effects and the improved backend, which now supports also native Audio Unit (AU) effect plugins on macOS.


@Video(https://www.youtube.com/watch?v=klOjBuZm0Qg)

Your "Jingles" and "Bells" can be sorted and found easier with the new library features: Cut, Copy and Paste in tracklists:

@Video(https://www.youtube.com/watch?v=2qPXCCaGVGI)

Tracks can be moved with Alt+Up/Down/PgUp/PgDn:

@Video(https://www.youtube.com/watch?v=MVvEP18a0xw)

With a summary containing the number of tracks and the total duration added to the name of crates, playlists and historylists makes it easy to find the right list:

@Video(https://www.youtube.com/watch?v=0HtpOOIpjaM)

The searchengine received new BPM filters, an 'OR'-operator, new import possibilities, custom track colors for missing or played tracks...

@Video(https://www.youtube.com/watch?v=qfnH7jWw0iY)

"Santa Tell Me" what's new in preferences: some improved layout, the fetching of the soundcard's sample rate is fixed, a new setting for 'first hotcue', multiple options can be selected in the MIDI input editor.

Many "Days Of Christmas" full of improved Controller Mappings for Denon MC7000, Numark Scratch, Pioneer DDJ-FLX4, Traktor Kontrol S4 MK3 and MIDI for light.

A Controller Backend as a "Fairytale of New York" to map your controller: sysex, deck's track menu, support for bulk devices. We also dropped the lodash dependency.

Qt5 will Be Home For Christmas because Mixxx is using [Qt6](https://www.qt.io/product/qt6) now, a lot of work has been put in study, preparation, testing, upgrading procedures, adapting routines, dialogs, widgets, libraries. Upgrading to Qt6 wasn't just sitting "underneath the Mistletoe" but now Mixxx is in "Winter Wonderland". "Thank you Santa" Developers!

So many rafactorings have been made, improvements of the code by progressive insight, because of new possibilities in C++ and Qt, because of studies in acoustics, user experiences...
The list is too long to write or make a selection here, it would be failing all contributors, you can find the complete list further in this announcement, full of "Christmas Lights".


#### So this is Christmas

"Baby, It's Cold Outside", so our present will be lots of fun exploring this new version. You'll need quiet some time to get used to all new features, discover the real possibilities,
to get some adapted workflow with new handles. Mixxx whishes you a "Wonderful Christmas Time".

Mic drop, "Light the Candles All Around the World"


#### ... and a happy 2.5

Start using your brand new toy, grab it from the [Download page](https://mixxx.org/download/).
Unwrap your gift, [the complete changelog 2.5](https://github.com/mixxxdj/mixxx/blob/2.5/CHANGELOG.md)

#### All Changes


##### Modernized Platform: Update to Qt6

* Mixxx is now using Qt6, offering improved performance and enhanced compatibility with modern systems.
  [#11863](https://github.com/mixxxdj/mixxx/pull/11863)
  [#11892](https://github.com/mixxxdj/mixxx/pull/11892)
* Build system defaults to Qt6. Qt5 build support will be dropped with Mixxx 2.6
  [#11934](https://github.com/mixxxdj/mixxx/pull/11934)
* Drop support for macOS versions earlier than 11
* Drop support for Windows versions earlier than Windows 10 build 1809
* Drop support for Ubuntu versions earlier than 22.04
* Require a C++20 compiler
* Support GCC 14
  [#13504](https://github.com/mixxxdj/mixxx/pull/13504)
  [#13467](https://github.com/mixxxdj/mixxx/issues/13467)
* DlgAbout: Add Qt version to the dialog [#11862](https://github.com/mixxxdj/mixxx/pull/11862)
* WWidget: Disable touch events on macOS (fixing trackpad issues on Qt 6) [#11870](https://github.com/mixxxdj/mixxx/pull/11870)
* Various Skin adjustments
  [#11970](https://github.com/mixxxdj/mixxx/pull/11970)
  [#11957](https://github.com/mixxxdj/mixxx/issues/11957)
  [#12050](https://github.com/mixxxdj/mixxx/pull/12050)
  [#12939](https://github.com/mixxxdj/mixxx/pull/12939)
  [#13242](https://github.com/mixxxdj/mixxx/pull/13242)
  [#14014](https://github.com/mixxxdj/mixxx/pull/14014)
  [#13535](https://github.com/mixxxdj/mixxx/pull/13535)
  [#14013](https://github.com/mixxxdj/mixxx/pull/14013)
  [#13959](https://github.com/mixxxdj/mixxx/issues/13959)
  [#14034](https://github.com/mixxxdj/mixxx/pull/14034)
  [#12972](https://github.com/mixxxdj/mixxx/issues/12972)
  [#14035](https://github.com/mixxxdj/mixxx/pull/14035)
* Various Library adjustments
  [#12380](https://github.com/mixxxdj/mixxx/pull/12380)
  [#12478](https://github.com/mixxxdj/mixxx/pull/12478)
  [#13035](https://github.com/mixxxdj/mixxx/pull/13035)
  [#13033](https://github.com/mixxxdj/mixxx/issues/13033)
  [#12488](https://github.com/mixxxdj/mixxx/pull/12488)
  [#12216](https://github.com/mixxxdj/mixxx/pull/12216)
  [#13448](https://github.com/mixxxdj/mixxx/pull/13448)

##### Engine

* Beats: allow undoing the last BPM/beats change [#12954](https://github.com/mixxxdj/mixxx/pull/12954)
  [#12774](https://github.com/mixxxdj/mixxx/issues/12774)
  [#10138](https://github.com/mixxxdj/mixxx/issues/10138)
  [#13339](https://github.com/mixxxdj/mixxx/pull/13339)
* Add beatloop anchor to set and adjust loop from either start or end
  [#12745](https://github.com/mixxxdj/mixxx/pull/12745)
  [#13241](https://github.com/mixxxdj/mixxx/pull/13241)
* Add Rate Tap button [#12104](https://github.com/mixxxdj/mixxx/pull/12104)
* Store/restore regular loop when toggling rolling loops
  [#12475](https://github.com/mixxxdj/mixxx/pull/12475)
  [#8947](https://github.com/mixxxdj/mixxx/issues/8947)
* Add `beats_translate_move` ControlEncoder [#12376](https://github.com/mixxxdj/mixxx/pull/12376)
* Looping/Beatjump: use seconds if track has no beats
  [#12961](https://github.com/mixxxdj/mixxx/pull/12961)
  [#11124](https://github.com/mixxxdj/mixxx/issues/11124)
* Add Track colour palette cycling controls `track_color_next` and `track_color_prev` to library, decks and samplers
  [#13066](https://github.com/mixxxdj/mixxx/pull/13066)
  [#12905](https://github.com/mixxxdj/mixxx/issues/12905)
* Add Tempo locking controls
  [#13041](https://github.com/mixxxdj/mixxx/pull/13041)
  [#13041](https://github.com/mixxxdj/mixxx/pull/13041)
  [#13038](https://github.com/mixxxdj/mixxx/issues/13038)
  [#13199](https://github.com/mixxxdj/mixxx/pull/13199)
* Recording: Fix bogus timestamp in CUE sheet after restarting a recording
  [#13966](https://github.com/mixxxdj/mixxx/pull/13966)
  [#13964](https://github.com/mixxxdj/mixxx/issues/13964)
* Improve Taglib/SoundSource logging [#13541](https://github.com/mixxxdj/mixxx/pull/13541)

##### Skins / Interface

* Toggle the menubar with single Alt key press (auto hide)
  [#11526](https://github.com/mixxxdj/mixxx/pull/11526)
  [#13301](https://github.com/mixxxdj/mixxx/pull/13301)
* Fullscreen toggle rework
  [#11566](https://github.com/mixxxdj/mixxx/pull/11566)
  [#13189](https://github.com/mixxxdj/mixxx/pull/13189)
  [#13030](https://github.com/mixxxdj/mixxx/issues/13030)
* Allow to edit track title and artist directly within the decks via a delayed double-click
  [#11755](https://github.com/mixxxdj/mixxx/pull/11755)
  [#13930](https://github.com/mixxxdj/mixxx/pull/13930)
* Require a minimum movement before initiating the drag&drop of tracks [#12903](https://github.com/mixxxdj/mixxx/pull/12903)
* Add type toggle to cue popup [#13215](https://github.com/mixxxdj/mixxx/pull/13215)
* Effect Meta Knob: draws arc from default meta position
  [#12638](https://github.com/mixxxdj/mixxx/pull/12638)
  [#12634](https://github.com/mixxxdj/mixxx/issues/12634)
* Handle not supported files when dragging to waveforms and spinnies
  [#13206](https://github.com/mixxxdj/mixxx/issues/13206)
* Tooltips: Improve `rate_up/down` description regarding pitch vs. speed [#12590](https://github.com/mixxxdj/mixxx/pull/12590)
* Tooltips: Add description for expand/collapse samplers buttons
  [#13005](https://github.com/mixxxdj/mixxx/pull/13005)
  [#12998](https://github.com/mixxxdj/mixxx/issues/12998)
* Track label widgets: Set `show_track_menu` only for main decks [#12978](https://github.com/mixxxdj/mixxx/pull/12978)
* MacOS: App proxy icon of the playing track to the window title [#12116](https://github.com/mixxxdj/mixxx/pull/12116)
* Auto DJ: Force-show decks 3/4 if we are going to use them [#13455](https://github.com/mixxxdj/mixxx/pull/13455)
* Auto DJ: Add new random tracks if one track does not exists [#13551](https://github.com/mixxxdj/mixxx/pull/13551)
* Allow to set LaunchImage style per color scheme [#13731](https://github.com/mixxxdj/mixxx/pull/13731)
* Show wait cursor when re/loading a skin (not during startup) [#13747](https://github.com/mixxxdj/mixxx/pull/13747)
* LateNight: Merge vinyl control toggle and status light
  [#12947](https://github.com/mixxxdj/mixxx/pull/12947)
  [#10192](https://github.com/mixxxdj/mixxx/issues/10192)
* LateNight, Deere, Tango: Deactivate beatgrid edit controls if BPM is locked
  [#13320](https://github.com/mixxxdj/mixxx/pull/13320)
  [#13323](https://github.com/mixxxdj/mixxx/pull/13323)
  [#13325](https://github.com/mixxxdj/mixxx/pull/13325)
* LateNight: Add/tweak CueDelete icons
  [#13495](https://github.com/mixxxdj/mixxx/pull/13495)
  [#13492](https://github.com/mixxxdj/mixxx/issues/13492)
* LateNight: Use Classic launch image style also for 64 samplers version [#13796](https://github.com/mixxxdj/mixxx/pull/13796)
* Adjust some skin controls, to allow point-and-click mapping
  [#13906](https://github.com/mixxxdj/mixxx/pull/13906)
* PreviewDeckN,LoadSelectedTrackAndPlay toggles play/pause if the track is already loaded
  [#12920](https://github.com/mixxxdj/mixxx/pull/12920)
  [#9819](https://github.com/mixxxdj/mixxx/issues/9819)
* Command line interface: Determine whether to color output based on `TERM` variable
  [#13486](https://github.com/mixxxdj/mixxx/pull/13486)
* Command line interface: Add option `--start-autodj` to start Auto DJ immediately after Mixxx start.
  [#13017](https://github.com/mixxxdj/mixxx/pull/13017)
  [#10189](https://github.com/mixxxdj/mixxx/issues/10189)
* Logging: Include timestamps in messages by default [#11861](https://github.com/mixxxdj/mixxx/pull/11861)
* Logging: Limit mixxx.log size to 100 MB or via --log-max-file-size
  [#13684](https://github.com/mixxxdj/mixxx/pull/13684)
  [#13660](https://github.com/mixxxdj/mixxx/issues/13660)
* Fix skin reload after changing color scheme [#13847](https://github.com/mixxxdj/mixxx/pull/13847)

##### Effects

* Add Compressor effect [#12523](https://github.com/mixxxdj/mixxx/pull/12523)
* add Glitch effect [#11329](https://github.com/mixxxdj/mixxx/pull/11329)
* Add backend for Audio Unit (AU) plugins on macOS
  [#12112](https://github.com/mixxxdj/mixxx/pull/12112)
  [#13938](https://github.com/mixxxdj/mixxx/pull/13938)
* Effect Meta knob: Draw arc from default meta position
  [#12638](https://github.com/mixxxdj/mixxx/pull/12638)
  [#12634](https://github.com/mixxxdj/mixxx/issues/12634)
* Show newly added effects, read/write HiddenEffects
  [#13326](https://github.com/mixxxdj/mixxx/pull/13326)
  [#11343](https://github.com/mixxxdj/mixxx/issues/11343)

##### Library

* Shortkeys Cut, Copy, Paste for track list management
  [#12020](https://github.com/mixxxdj/mixxx/pull/12020)
  [#13361](https://github.com/mixxxdj/mixxx/issues/13361)
  [#13364](https://github.com/mixxxdj/mixxx/pull/13364)
  [#13958](https://github.com/mixxxdj/mixxx/pull/13958)
  [#13100](https://github.com/mixxxdj/mixxx/issues/13100)
* Playlists: move tracks with Alt + Up/Down/PageUp/PageDown/Home/End
  [#13092](https://github.com/mixxxdj/mixxx/pull/13092)
  [#10826](https://github.com/mixxxdj/mixxx/issues/10826)
  [#13098](https://github.com/mixxxdj/mixxx/pull/13098)
* Search: Add special BPM filters
  [#12072](https://github.com/mixxxdj/mixxx/pull/12072)
  [#8191](https://github.com/mixxxdj/mixxx/issues/8191)
* Search: Add "OR" search operator
  [#12061](https://github.com/mixxxdj/mixxx/pull/12061)
  [#8881](https://github.com/mixxxdj/mixxx/issues/8881)
* Search: Add 'type' filter
  [#13338](https://github.com/mixxxdj/mixxx/issues/13338)
* Search: Add 'id' filter [#13694](https://github.com/mixxxdj/mixxx/pull/13694)
* Search related Tracks menu: Allow to use multiple filters at once
  [#12213](https://github.com/mixxxdj/mixxx/pull/12213)
  [#12211](https://github.com/mixxxdj/mixxx/issues/12211)
* Track menu: Rephrase "Reset" to "Clear" [#12955](https://github.com/mixxxdj/mixxx/pull/12955)
* Track menu: Add support for scaling BPM by different ratios
  [#12934](https://github.com/mixxxdj/mixxx/pull/12934)
  [#9133](https://github.com/mixxxdj/mixxx/issues/9133)
* Track menu: Remove from disk: stop and eject all affected decks [#13214](https://github.com/mixxxdj/mixxx/pull/13214)
* Track menu: add star rating
  [#12700](https://github.com/mixxxdj/mixxx/pull/12700)
  [#10652](https://github.com/mixxxdj/mixxx/issues/10652)
* Track menu: Show Properties in Missing and Hidden view [#13426](https://github.com/mixxxdj/mixxx/pull/13426)
* Add multi-track property editor / batch tag editor
  [#12548](https://github.com/mixxxdj/mixxx/pull/12548)
  [#9023](https://github.com/mixxxdj/mixxx/issues/9023)
  [#13299](https://github.com/mixxxdj/mixxx/pull/13299)
  [#13609](https://github.com/mixxxdj/mixxx/pull/13609)
  [#13597](https://github.com/mixxxdj/mixxx/issues/13597)
  [#13631](https://github.com/mixxxdj/mixxx/pull/13631)
* Track property editor: focus the editing field in the track properties that corresponds to the focused column
  [#13841](https://github.com/mixxxdj/mixxx/pull/13841)
  [#14036](https://github.com/mixxxdj/mixxx/pull/14036)
* Computer feature: add sidebar action "Refresh directory tree" [#12908](https://github.com/mixxxdj/mixxx/pull/12908)
* Add feedback to directory operations (add, remove, relink)
  [#12436](https://github.com/mixxxdj/mixxx/pull/12436)
  [#10481](https://github.com/mixxxdj/mixxx/issues/10481)
* Add ability to import external playlists as crates [#11852](https://github.com/mixxxdj/mixxx/pull/11852)
* Add 'Shuffle playlist' sidebar action
  [#12498](https://github.com/mixxxdj/mixxx/pull/12498)
  [#6988](https://github.com/mixxxdj/mixxx/issues/6988)
* Playlists: Update of playlist labels after adding tracks [#12866](https://github.com/mixxxdj/mixxx/pull/12866) [#12761](https://github.com/mixxxdj/mixxx/issues/12761)
* Tracks: Custom color for missing tracks [#12895](https://github.com/mixxxdj/mixxx/pull/12895)
* Tracks: Custom text color for played tracks (qss)
  [#12744](https://github.com/mixxxdj/mixxx/pull/12744)
  [#5911](https://github.com/mixxxdj/mixxx/issues/5911)
  [#12912](https://github.com/mixxxdj/mixxx/pull/12912)
  [#13538](https://github.com/mixxxdj/mixxx/pull/13538)
* History: Show track count and duration in sidebar
  [#12811](https://github.com/mixxxdj/mixxx/pull/12811)
  [#12788](https://github.com/mixxxdj/mixxx/issues/12788)
* Don't allow pasting tracks into locked playlists/crates or History [#12926](https://github.com/mixxxdj/mixxx/pull/12926)
* Optimize Library scrolling [#13358](https://github.com/mixxxdj/mixxx/pull/13358)
* Keep the metadata key text unchanged, use it as the origin of information
  [#11096](https://github.com/mixxxdj/mixxx/pull/11096)
  [#11095](https://github.com/mixxxdj/mixxx/issues/11095)
  [#13650](https://github.com/mixxxdj/mixxx/pull/13650)
  [#14011](https://github.com/mixxxdj/mixxx/pull/14011)
  [#14008](https://github.com/mixxxdj/mixxx/pull/14008)
  [#14020](https://github.com/mixxxdj/mixxx/pull/14020)
* Center date values, right-align Track # [#13674](https://github.com/mixxxdj/mixxx/pull/13674)
* Analysis: Fix stop button when analyzing crate/playlist [#13902](https://github.com/mixxxdj/mixxx/pull/13902)
* Add a debug message, which appears when event loop processing in Mixxx application takes very long
  [#12094](https://github.com/mixxxdj/mixxx/pull/12094)
  [#13900](https://github.com/mixxxdj/mixxx/pull/13900)
  [#13889](https://github.com/mixxxdj/mixxx/pull/13889)
  [#13903](https://github.com/mixxxdj/mixxx/pull/13903)
  [#14012](https://github.com/mixxxdj/mixxx/pull/14012)

##### Preferences

* Add load point option 'First hotcue'
  [#12869](https://github.com/mixxxdj/mixxx/pull/12869)
  [#12740](https://github.com/mixxxdj/mixxx/issues/12740)
* MIDI Input editor: allow selecting multiple Options [#12348](https://github.com/mixxxdj/mixxx/pull/12348)
* Apply changes only after pressing Apply in color preferences [#13302](https://github.com/mixxxdj/mixxx/pull/13302)
* Add/reorder tabstops in Library and Waveform preferences
  [#13846](https://github.com/mixxxdj/mixxx/pull/13846)
* Add missing spacer in interface preferences [#13094](https://github.com/mixxxdj/mixxx/pull/13094)
* Fix fetching of soundcard sample rate
  [#11951](https://github.com/mixxxdj/mixxx/pull/11951)
  [11949](https://github.com/mixxxdj/mixxx/issues/11949)

##### Controller Mappings

* Denon MC7000: Add optional jog wheel acceleration to the controller mapping [#4684](https://github.com/mixxxdj/mixxx/pull/4684)
* Denon MC7000: Unify parameter button logic and add customizable modes [#13589](https://github.com/mixxxdj/mixxx/pull/13589)
* Denon MC7000: Add sampler options to mapping settings [#13950](https://github.com/mixxxdj/mixxx/pull/13950)
* MIDI for light: Implement new Active deck heuristic [#13513](https://github.com/mixxxdj/mixxx/pull/13513)
* MIDI for light: Add settings GUI [#13721](https://github.com/mixxxdj/mixxx/pull/13721)
* Numark Scratch: Add controller settings  [#13404](https://github.com/mixxxdj/mixxx/pull/13404)
* Pioneer DDJ-FLX4: Mapping improvements [#12842](https://github.com/mixxxdj/mixxx/pull/12842)
* Traktor Kontrol S4 MK3: Add setting definition for  [#12995](https://github.com/mixxxdj/mixxx/pull/12995)
* Traktor Kontrol S4 MK3: Software mixer support and default pad layout customisation [#13059](https://github.com/mixxxdj/mixxx/pull/13059)
* Traktor Kontrol S4 Mk3: Rework jogwheel speed compute and motorized platter [#13393](https://github.com/mixxxdj/mixxx/pull/13393)
* Traktor Kontrol S4 Mk3: Revert QuickEffect preset offset [#13997](https://github.com/mixxxdj/mixxx/pull/13997)
* Traktor Kontrol S4 Mk3: Correct wheel timestamp wrap-around [#14016](https://github.com/mixxxdj/mixxx/pull/14016)

##### Controller Backend

* Send sysex to all handlers [#12827](https://github.com/mixxxdj/mixxx/pull/12827)
* Speed up midi sysex receive [#12843](https://github.com/mixxxdj/mixxx/pull/12843)
* Add control for showing a deck's track menu [#10825](https://github.com/mixxxdj/mixxx/pull/10825)
* Removed old examples HID keyboard and HID trackpad [#12977](https://github.com/mixxxdj/mixxx/pull/12977)
* Reduce log noise with HID device
  [#13010](https://github.com/mixxxdj/mixxx/pull/13010)
  [#13125](https://github.com/mixxxdj/mixxx/pull/13125)
* Allow controller mapping to discard polling [#12558](https://github.com/mixxxdj/mixxx/pull/12558)
* Add support for mapping user settings
  [#11300](https://github.com/mixxxdj/mixxx/pull/11300)
  [#13046](https://github.com/mixxxdj/mixxx/pull/13046)
  [#13057](https://github.com/mixxxdj/mixxx/pull/13057)
  [#13045](https://github.com/mixxxdj/mixxx/pull/13045)
  [#13656](https://github.com/mixxxdj/mixxx/pull/13656)
  [#13738](https://github.com/mixxxdj/mixxx/pull/13738)
  [#13979](https://github.com/mixxxdj/mixxx/pull/13979)
  [#13990](https://github.com/mixxxdj/mixxx/pull/13990)
* Registering MIDI Input Handlers From Javascript
  [#12781](https://github.com/mixxxdj/mixxx/pull/12781)
  [#13089](https://github.com/mixxxdj/mixxx/pull/13089)
* Controller IO table: Fix display text for Action/control delegate [#13188](https://github.com/mixxxdj/mixxx/pull/13188)
* Drop lodash dependency in ComponentJS [#12779](https://github.com/mixxxdj/mixxx/pull/12779)
* Support for bulk devices on Windows and Mac [#13008](https://github.com/mixxxdj/mixxx/pull/13008)
* Drop lodash dependency in ComponentJS
  [#12779](https://github.com/mixxxdj/mixxx/pull/12779)
* Fix pending reference to the old mapping after selecting 'No mapping' [#13907](https://github.com/mixxxdj/mixxx/pull/13907)
* Fix crash with GoToItem when no app windows has the focus [#13657](https://github.com/mixxxdj/mixxx/pull/13657)

##### Waveforms

* Visualize slip mode position by splitting waveform (RGB GLSL only)
  [#13002](https://github.com/mixxxdj/mixxx/pull/13002)
  [#13256](https://github.com/mixxxdj/mixxx/pull/13256)
  [#10063](https://github.com/mixxxdj/mixxx/issues/10063)
* Show beats and time until next marker in the waveform
  [#12994](https://github.com/mixxxdj/mixxx/pull/12994)
  [#13311](https://github.com/mixxxdj/mixxx/pull/13311)
  [#13953](https://github.com/mixxxdj/mixxx/pull/13953)
  [#13314](https://github.com/mixxxdj/mixxx/issues/13314)
* Don't elide hotcue labels
  [#13219](https://github.com/mixxxdj/mixxx/pull/13219)
  [#10722](https://github.com/mixxxdj/mixxx/issues/10722)
* Allshader RGB, Filtered and Stacked Waveforms using textures for waveform data
  [#13151](https://github.com/mixxxdj/mixxx/pull/13151)
  [#12641](https://github.com/mixxxdj/mixxx/issues/12641)
* Allow changing the waveform overview type without reloading the skin
  [#13273](https://github.com/mixxxdj/mixxx/pull/13273)
* Overview: Update immediately, when the normalize option or global gain changed
  [#13634](https://github.com/mixxxdj/mixxx/pull/13634)
* Overview: Clear pickup position display when opening cue menu
  [#13693](https://github.com/mixxxdj/mixxx/pull/13693)

##### Experimental Features

* QML Skin: Can be tested via the --qml command line option
  [#13152](https://github.com/mixxxdj/mixxx/pull/13152)
  [#12139](https://github.com/mixxxdj/mixxx/pull/12139)
  [#13152](https://github.com/mixxxdj/mixxx/pull/13152)
* QML Skin related changes
  [#11423](https://github.com/mixxxdj/mixxx/pull/11423)
  [#12559](https://github.com/mixxxdj/mixxx/pull/12559)
  [#12549](https://github.com/mixxxdj/mixxx/pull/12549)
  [#12541](https://github.com/mixxxdj/mixxx/pull/12541)
  [#12795](https://github.com/mixxxdj/mixxx/pull/12795)
  [#12844](https://github.com/mixxxdj/mixxx/pull/12844)
  [#12546](https://github.com/mixxxdj/mixxx/pull/12546)
  [#12794](https://github.com/mixxxdj/mixxx/pull/12794)
  [#12536](https://github.com/mixxxdj/mixxx/issues/12536)
  [#13058](https://github.com/mixxxdj/mixxx/pull/13058)
  [#12604](https://github.com/mixxxdj/mixxx/pull/12604)
  [#3967](https://github.com/mixxxdj/mixxx/pull/3967)
  [#13009](https://github.com/mixxxdj/mixxx/pull/13009)
  [#13009](https://github.com/mixxxdj/mixxx/pull/13009)
  [#13011](https://github.com/mixxxdj/mixxx/pull/13011)
  [#13506](https://github.com/mixxxdj/mixxx/pull/13506)
* iOS support: Mixxx can be built for iOS
  [#12672](https://github.com/mixxxdj/mixxx/pull/12672)
* iOS support related changes
  [#12689](https://github.com/mixxxdj/mixxx/pull/12689)
  [#12714](https://github.com/mixxxdj/mixxx/pull/12714)
  [#12716](https://github.com/mixxxdj/mixxx/pull/12716)
  [#12698](https://github.com/mixxxdj/mixxx/pull/12698)
  [#12676](https://github.com/mixxxdj/mixxx/pull/12676)
  [#12688](https://github.com/mixxxdj/mixxx/pull/12688)
  [#13379](https://github.com/mixxxdj/mixxx/pull/13379)
  [#13378](https://github.com/mixxxdj/mixxx/issues/13378)
  [#13383](https://github.com/mixxxdj/mixxx/pull/13383)
* Emscripten/WebAssembly support, to run Mixxx hardware independent in a browser
  [#12918](https://github.com/mixxxdj/mixxx/pull/12918)
* Emscripten/WebAssembly related changes
  [#12910](https://github.com/mixxxdj/mixxx/pull/12910)
  [#12913](https://github.com/mixxxdj/mixxx/pull/12913)
  [#12916](https://github.com/mixxxdj/mixxx/pull/12916)
  [#12915](https://github.com/mixxxdj/mixxx/pull/12915)
  [#12921](https://github.com/mixxxdj/mixxx/pull/12921)
  [#12922](https://github.com/mixxxdj/mixxx/pull/12922)
  [#12931](https://github.com/mixxxdj/mixxx/pull/12931)
  [#12940](https://github.com/mixxxdj/mixxx/pull/12940)
  [#12945](https://github.com/mixxxdj/mixxx/pull/12945)
  [#12952](https://github.com/mixxxdj/mixxx/pull/12952)
  [#12930](https://github.com/mixxxdj/mixxx/pull/12930)
  [#12917](https://github.com/mixxxdj/mixxx/pull/12917)

##### Target support

* Maintain GL ES support [#13485](https://github.com/mixxxdj/mixxx/pull/13485)
* Tools: Add `rpm_buildenv.sh` for building on Fedora [#13069](https://github.com/mixxxdj/mixxx/pull/13069)
* Lenient taglib 2.0 guard [#12793](https://github.com/mixxxdj/mixxx/pull/12793)
* MixxxApplication: Support linking Qt statically on Linux [#12284](https://github.com/mixxxdj/mixxx/pull/12284)
* FindSndFile: Link mpg123 in static builds [#13087](https://github.com/mixxxdj/mixxx/pull/13087)
* FindPortMidi: Link ALSA in static builds on Linux [#12292](https://github.com/mixxxdj/mixxx/pull/12292) [#12291](https://github.com/mixxxdj/mixxx/pull/12291)
* FindLibudev: Link hidapi and libusb with libudev in static builds on Linux [#12294](https://github.com/mixxxdj/mixxx/pull/12294)
* FindVorbis: Link ogg in static builds [#12297](https://github.com/mixxxdj/mixxx/pull/12297)
* FindSleef: Use OpenMP in static builds [#12295](https://github.com/mixxxdj/mixxx/pull/12295)
* macOS packaging: Enable app sandbox in ad-hoc-packaged (i.e. non-notarized) bundles too [#12101](https://github.com/mixxxdj/mixxx/pull/12101)
* CMakeLists: Match arbitrary `arm64-osx` triplets [#11933](https://github.com/mixxxdj/mixxx/pull/11933)
* Disable warning in lib/apple code [#13522](https://github.com/mixxxdj/mixxx/pull/13522)
* GitHub CI: Use retry loop for CPack to work around macOS issue [#13991](https://github.com/mixxxdj/mixxx/pull/13991)
* Github CI: Enable `WARNINGS_FATAL` on macOS, too [#11905](https://github.com/mixxxdj/mixxx/pull/11905)


### Quoted Christmas songs

* All I want for Christmas (Mariah Carey)
* Baby, It's Cold Outside (Ella Fitzgerald & Louis Armstrong)
* Cheer for the Elves (Gwen Stefani)
* Christmas Lights (Coldplay)
* Christmas Present (Andy Williams)
* Christmas Will Break Your Heart (LCD Soundsystem)
* Driving home for Christmas (Chris Rea)
* Fairytale of New York (The Pogues & Kirsty MacColl)
* Feliz Navidad (José Feliciano)
* Happy New Year (Abba)
* Have yourself a merry little Christmas (Frank Sinatra)
* I'll be home on Christmas day (Blue Blot)
* I'll Be Home For Christmas (Bing Crosby)
* Jingle Bells (version Diana Krall / version Johnny Cash )
* Last Christmas (Wham)
* Let it snow! Let it snow! Let it snow! (Dean Martin)
* Light the Candles All Around the World (traditional)
* Player’s Ball (Christmas Radio Mix, Outkast)
* Presents for Christmas (Solomon Burke)
* Rockin' Around the Christmas Tree (Brenda Lee)
* Rudolph, the Red-Nosed Reindeer (The Ray Conniff Singers)
* Santa Clause is Coming to Town (version Bruce Springsteen)
* Santa Tell Me’ (Ariana Grande)
* Sleigh Ride (The Ronettes)
* So this is Christmas (John Lennon)
* Thank You Santa (Phineas and Ferb)
* The Twelve Days of Christmas (traditional)
* Underneath the Mistletoe (Kelly Clarkson)
* Winter Wonderland (Bing Crosby)
* Wonderful Christmas Time (Paul McCartney)
* 8 Days Of Christmas (Destiny's Child)
