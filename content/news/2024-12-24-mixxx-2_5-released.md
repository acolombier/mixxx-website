title: Mixxx 2.5 Released
authors: Evelynne Veys
tags: 2.5, release announcement
comments: yes
date: 2024-12-24 15:25:19

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
Unwrap your gift, [the complete changelog 2.5.0](https://github.com/mixxxdj/mixxx/blob/2.5.0/CHANGELOG.md)
Here some sparkles:

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
* Looping/Beatjump: use seconds if track has no beats
  [#12961](https://github.com/mixxxdj/mixxx/pull/12961)
  [#11124](https://github.com/mixxxdj/mixxx/issues/11124)

##### Skins / Interface

* Toggle the menubar with single Alt key press (auto hide)
  [#11526](https://github.com/mixxxdj/mixxx/pull/11526)
  [#13301](https://github.com/mixxxdj/mixxx/pull/13301)
* Allow to edit track title and artist directly within the decks via a delayed double-click
  [#11755](https://github.com/mixxxdj/mixxx/pull/11755)
  [#13930](https://github.com/mixxxdj/mixxx/pull/13930)
* Add type toggle to cue popup [#13215](https://github.com/mixxxdj/mixxx/pull/13215)
* Effect Meta Knob: draws arc from default meta position
  [#12638](https://github.com/mixxxdj/mixxx/pull/12638)
  [#12634](https://github.com/mixxxdj/mixxx/issues/12634)
* Command line interface: Add option `--start-autodj` to start Auto DJ immediately after Mixxx start.
  [#13017](https://github.com/mixxxdj/mixxx/pull/13017)
  [#10189](https://github.com/mixxxdj/mixxx/issues/10189)

##### Effects

* Add Compressor effect [#12523](https://github.com/mixxxdj/mixxx/pull/12523)
* add Glitch effect [#11329](https://github.com/mixxxdj/mixxx/pull/11329)
* Add backend for Audio Unit (AU) plugins on macOS
  [#12112](https://github.com/mixxxdj/mixxx/pull/12112)
  [#13938](https://github.com/mixxxdj/mixxx/pull/13938)

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
* Add multi-track property editor / batch tag editor
  [#12548](https://github.com/mixxxdj/mixxx/pull/12548)
  [#9023](https://github.com/mixxxdj/mixxx/issues/9023)
  [#13299](https://github.com/mixxxdj/mixxx/pull/13299)
  [#13609](https://github.com/mixxxdj/mixxx/pull/13609)
  [#13597](https://github.com/mixxxdj/mixxx/issues/13597)
  [#13631](https://github.com/mixxxdj/mixxx/pull/13631)
* Computer feature: add sidebar action "Refresh directory tree" [#12908](https://github.com/mixxxdj/mixxx/pull/12908)
* Add 'Shuffle playlist' sidebar action
  [#12498](https://github.com/mixxxdj/mixxx/pull/12498)
  [#6988](https://github.com/mixxxdj/mixxx/issues/6988)
* Tracks: Custom color for missing tracks [#12895](https://github.com/mixxxdj/mixxx/pull/12895)
* Tracks: Custom text color for played tracks (qss)
  [#12744](https://github.com/mixxxdj/mixxx/pull/12744)
  [#5911](https://github.com/mixxxdj/mixxx/issues/5911)
  [#12912](https://github.com/mixxxdj/mixxx/pull/12912)
  [#13538](https://github.com/mixxxdj/mixxx/pull/13538)

##### Preferences

* Decks: Add load point option 'First hotcue'
  [#12869](https://github.com/mixxxdj/mixxx/pull/12869)
  [#12740](https://github.com/mixxxdj/mixxx/issues/12740)
* MIDI Input editor: allow selecting multiple Options [#12348](https://github.com/mixxxdj/mixxx/pull/12348)

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
* Allow changing the waveform overview type without reloading the skin
  [#13273](https://github.com/mixxxdj/mixxx/pull/13273)
* Overview: Update immediately, when the normalize option or global gain changed
  [#13634](https://github.com/mixxxdj/mixxx/pull/13634)

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
