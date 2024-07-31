title: Midsummer Mixxx
authors: Evelynne Veys
tags: summer, info, news, update, harmonic, key, stem
comments: yes
status: draft

#### Let the Mixxx shine

Summertime, partytime. In the middle of the festival season you are maybe playing a sunny vibes gig somewhere.
Or you are relaxing on the beach or at the pool with a cocktail in the hand checking the long list of music you had to discover.
Both ways will give you inspiration and energy.
Who thinks Mixxx-devs are laying in the sun can't be more wrong, we're having a crowded github-festival ourselves.

#### Let the Mixxx in

A lot of new contributors found their way to our mapping parties on the discourse forum, our coding raves at github, 
and the development zulip dancehall. You are all welcome and we'd like to thank you for all kind of input.
With your feedback on the 2.5 beta version the coding team is on track for gold, the bugs and errors teams are already defeated.

#### I'm going on a holiday and …

While you're enjoying a well deserved vacation the Mixxx team is preparing new features.
Not all new features are already for bundling in an official release but you can find everything about them in the partie venues. 

The new visual aids for key and bpm will be astonishing, it needed quite some adaptations but the project is in pole position for gold.

The color integration will give you intuitive directions of matching tracks for harmonic mixing, also for people who suffer off color-blindness.
Soon you wil be able to discover a 'heat column' in the library which will give you hints on tracks that are compatible with the current playing track,
based on the Key and BPM. And BPM coloring will be added to show tracks with a BPM close to the current tempo.
This will be our first step in Intelligent Assistance, it can inspire you to make surprising Mixxx-es with tracks that slipped your mind.
And these features will later be used later for some QOL features, like an improved suggestions algorithm, search ranking based on similarity,
and adding key color ticks on the rate sliders.
Fill the floors!

Our marathon stem project is fantastic, a peek behind the curtain:
Playing with stems changes the whole idea of DJ-ing. If stems are new for you I would like to invite you to do some research. 
In brief: stems are regular music files that are separated in 4 stem-tracks by the original producer or with the aid of AI.
Mostly those tracks are drums, bass, melody and vocals. Together with the original track are those 4 new tracks
combined in a new container, a *.Stem.MP4 or *.Stem.M4A file, lossy or lossless (depends also on source).
While other DJ software will only support lossy stem files, we choose to support both.
These combined files can be 'remixed' on the fly, with other words: the volume of the tracks can be individual controlled,
a track can also be muted e.g. if you mute all tracks except the vocals you are actually playing an a capella.

Without stems you need the beats to be synced, even if the intermediate beat would fit better to cover bass/drum sounds,
you need to work hard with the eq's to camouflage bass left-overs. With stems you can just completely hide the unwanted tracks.

Remark: The quality of the stems is of course very important, a lot of stem creators are showing up everywhere. 
Some need you to upload your original file, some can use your GPU, some use well trained AI models, others don't.
On Zulip I wrote a report about my quest for stems.

In development Mixxx is already at the point that lossy and lossless stems can be played and controlled as stems, stem controls are already 
working an can be experimental mapped in controller mappings. 

DJ-ing with stems is a gamechanger, it takes away limitations, gives your creativity a boost.
A hint: controlling stems with the mouse is rather difficult, some controllers are already stems-ready which means they incormporated
volume encoders and mute buttons for the different stem tracks. But don't throw away you're valuable controller. 
I have experimented successfull creating a OSC midi controller to control stems (and samplers) from a tablet, when finished the files will be available.
Or you can start looking for an extra midi-controller that has enough encoders to control the volume and mute buttons of the stems (advice: 4 encoders, 4 mute buttons maybe encoders for the effect on the stem-track and buttons to select the deck).

If you're waiting for an official release with stem support, you'll have to be more patient.

#### Ceremonie protocollaire

A golden medal will be awarded to everyone who contributes to Mixxx.
Have a crazy Mixxxy summer.
