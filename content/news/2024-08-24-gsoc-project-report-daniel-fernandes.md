title: GSoC 2024 Project Report - Harmonic Mixing Enhancements
authors: Daniel Fernandes
tags: gsoc, gsoc-2024, harmonic mixing
comments: yes
date: 2024-08-24 07:50:11

## Introduction

Welcome to the GSoC report for the Harmonic Mixing Enhancements project, which aims to make finding compatible tracks a breeze with these new features:

1. Color coding the Key column of the track list.
2. New Track Similarity Column, which uses the Key and BPM to compute how well two tracks work together.

In this post, I will share what this process has been like, the current state of things, and where you can try the merged features out.

## Project Planning

We used Zulip to get feedback and find use cases from the community to better understand the needs of Mixxx' users, which was important for solving some open questions. We particularly wanted to find clarity for the Track Similarity Column. After some discussion I drafted a design doc which gave us a concrete plan to improve on and made it easier to decide the finishing details.

- [mixxxdj/proposals#5](https://github.com/mixxxdj/proposals/pull/5) (draft)

## Color Coding the Key Column

In this part, we color the key column such that, keys that work well together have similar colors. We also wanted to provide alternative color palettes, for accessibility and personal preference.

We started with designing how the key colors will be shown. It was a bit tricky, because the tracks also have their own 'Color' property, so we had to make sure that these colors don't clash.

Using feedback from the community, we iterated over a few designs, finding out what looked best but also met our needs. Here are some of these iterations:

![Key Column Design Iterations]({static}/images/news/mixxx-track-key-colors-design-iterations.png)

And here's how the final design looks in the app:

![Key Column Design Iterations]({static}/images/news/mixxx-track-key-colors-screenshot.png)

This design preserves the readability of the text, while being a subtle hint for compatibility without interfering much with the track color.

### Implementation

A `KeyDelegate` was created to override the default behavior for the key column. It retrieves the Key Color to draw a recentangle to the left of the text.

A *Mixxx Key Color Palette* was also created, based on the colors from the Mixxx Keywheel.

To allow users to turn the feature off, a checkbox was added to toggle the Key colors.

- [mixxx#13390](https://github.com/mixxxdj/mixxx/pull/13390) (merged)
- [mixxx#13475](https://github.com/mixxxdj/mixxx/pull/13475) (bugfix, merged)

## Key Color Palettes

We added several color palettes for the key column that you can choose from. This includes palettes from third party software, so you can keep using the colors you're used to, as well as accessible color palettes optimized for the three broad types of color blindness: [Protanopia](https://davidmathlogic.com/colorblind/#%232626D9-%237582D7-%23A7C2DD-%23B8E0E0-%23A7DDC2-%2375D782-%2326D926-%230DA522-%2302783D-%23006666-%23023D78-%230D22A5) (red-blind), [Deuteranopia](https://davidmathlogic.com/colorblind/#%23D92626-%23D77582-%23DDA7C2-%23E0B8E0-%23C2A7DD-%238275D7-%232626D9-%23220DA5-%233D0278-%23660066-%2378023D-%23A50D22) (green-blind), and [Tritanopia](https://davidmathlogic.com/colorblind/#%2326D926-%2382D775-%23C2DDA7-%23E0E0B8-%23DDC2A7-%23D78275-%23D92626-%23A5220D-%23783D02-%23666600-%233D7802-%2322A50D) (blue-blind).

![Accessible Key Colors]({static}/images/news/accessible_key_colors.png)

We used 1/3 of hues for each palette, changing the hue vertically and changing the brightness and saturation horizontally when the colors are arranged in a circle. This ensures that every region on the circle has a distinct color, and that the change in colors is nearly uniform.

You can find the code written to generate these palettes [here](https://svelte.dev/repl/b65bda7e6a53487880a08726bfb2da7e?version=4.2.18).

We have tested that these work well in simulators. However, we are not done until we get feedback / confirmation from the users who would benefit from these palettes. If that's you, please reach out!

### Implementation

The color palettes were added along with a dropdown to choose between them. Translation support was also added for all palette names.

- [mixxx#13497](https://github.com/mixxxdj/mixxx/pull/13497) (merged)
- [mixxx#13571](https://github.com/mixxxdj/mixxx/pull/13571) (bugfix, merged)

### Where to try it out

The Key Colors feature is available in the [Alpha versions](https://mixxx.org/download/#testing) of Mixxx. We would greatly appreciate any testing, and if you find bugs, please do let us know in the GitHub Issues.


## Track Similarity [WIP]

You've probably noticed that in your collection there are pairs of tracks, with seemingly incompatible keys and different BPMs, that still work beautifully when played together, without the need for Keylock. This is possible, because when we sync the tempo of both tracks, the pitch of one track is shifted relative to the other in just the right way, that they both end up in similar keys.

Wouldn't it be cool if Mixxx could show you exactly which tracks work nicely this way? As a first step to making that happen, we needed a method for computing such similarity between two tracks.

I decided to prototype the algorithm in Python, and then port it into C++ for Mixxx. Fortunately, Mixxx stores all its data in an SQLite file, so I was able to export my library with the sqlite CLI tool and test the prototype on it.

I iterated on the prototype by testing out the results in Mixxx, and making notes so I can understand what to tweak. The final version of the algorithm that I settled on, can be found as a [Jupyter notebook](https://gist.github.com/danferns/bb1c3ca326df64320ddb1da1afe72e5f). It takes in the Key and BPM of two tracks, and outputs a single similarity value for how well the tracks will work.

With the algorithm settled on, it was time to port it to Mixxx.

### Implementation

The function `trackSimilarity()` was implemented in `KeyUtils`. Some helper functions were added, including `trackSyncPitchDifference()` which returns the pitch difference between two tracks, when they're played at the same BPM.

To test that it's working, the similarity of each track is computed against a "dummy" track in C Major at 100BPM and is displayed as a tooltip on the Key column. The output from the prototype and the C++ implementation in Mixxx are identical.

This feature is behind a CMake flag as it is currently still in development.

- [mixxx#13563](https://github.com/mixxxdj/mixxx/pull/13563) (WIP, not merged)

## Next steps

After finishing the Similarity Algorithm, the output needs to be used in a new "Similarity Column". For this, a system for determining the target track to be used is needed. More details on the rules for choosing the target track are discussed in the proposal PR.

For the Key Colors feature, we need to color the Key label on the decks, disable the Key Palette setting if Key Colors are disabled, and have the key column update when also clicking "Apply" on the preferences and not just after closing the preferences window.

## My experience and the things I learnt

It was the Mixxx manual that introduced me to Harmonic Mixing a few years ago, and it got me excited about DJing. Since then, I started thinking about ideas like Track Similarity, but I never thought I'd get to actually work on making them real! I'm truly grateful for this experience.

Mixxx was the first real world C++ project I worked on, and I learnt a lot of things that will help me for years to come. I learnt how to make project plans, and keep myself on track. It was specially helpful to break tasks down into smaller tasks, and make "mini-deadlines" for each of them. I learnt to brainstorm with others, and saw how ideas can evolve. On the technical side, I got lots of opportunities to use and understand Git more deeply, and also to navigate through and work on a large codebase.

## Acknowledgements

Mixxx has an amazingly helpful and enthusiastic community behind it, and everyone I've worked with is so awesome!

Firstly, I'd like to thank my mentor [Daniel Schürmann]({author}daniel-schurmann) for guiding me right from the very initial planning and brainstorming stages, and all the way to reviewing and getting the PRs merged. He made sure that I was never stuck on anything, and took great care that things go smoothly. He has been very helpful and supportive!

I'd like to thank [ronso0](https://github.com/ronso0) for his valuable design ideas and for guiding me with helpful feedback and testing during the code review. I'd also like to thank [Swiftb0y]({author}nikolaus-einhauser) for his valuable feedback and suggestions and for helping me make my code easier to read and efficient.

A special thanks to everyone participating in the discussions and testing for these features, it has been a very essential part of the process and was also quite fun!

Finally, I'd like to thank Google and the GSoC team for this one of a kind opportunity which introduced me to the awesome and collaborative world of open source.
