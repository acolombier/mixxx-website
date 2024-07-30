title: GSoC 2024 Project Report - Harmonic Mixing Enhancements (Part 1)
authors: Daniel Fernandes
status: draft
tags: gsoc, harmonic mixing
comments: yes

## Introduction

This project levels up your Harmonic Mixing workflow in Mixxx by adding these new features to help you find compatible tracks at glance:

1. Color coding the Key column of the track list.
2. Highlights in the BPM column for tracks that have a tempo close to a target track.
3. New Track Similarity Column, which uses the Key and BPM to compute how well two tracks work together.

We just added the color code key column feature (1.). In this post, I will share what this process was like so far, and where you can try the feature out.

## Project Planning

We used Zulip to get feedback and find use cases from the community to better understand the needs of Mixxx' users, which was important for solving some open questions. We particularly wanted to find clarity for the Track Similarity Column. After some discussion I made a design doc which gave us a concrete plan and made it easier to decide on the finishing details.

[mixxxdj/proposals#5](https://github.com/mixxxdj/proposals/pull/5)

## Color Coding the Key Column

In this phase, we color the key column such that, keys that work well together have similar colors. We also wanted to provide alternative color palettes, for accessibility and personal preference.

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

[mixxx#13390](https://github.com/mixxxdj/mixxx/pull/13390)

## Key Color Palettes

We added several color palettes for the key column that you can choose from. This includes palettes from third party software, so you can keep using the colors you're used to, as well as accessible color palettes optimized for the three broad types of color blindness: [Protanopia](https://davidmathlogic.com/colorblind/#%232626D9-%237582D7-%23A7C2DD-%23B8E0E0-%23A7DDC2-%2375D782-%2326D926-%230DA522-%2302783D-%23006666-%23023D78-%230D22A5) (red-blind), [Deuteranopia](https://davidmathlogic.com/colorblind/#%23D92626-%23D77582-%23DDA7C2-%23E0B8E0-%23C2A7DD-%238275D7-%232626D9-%23220DA5-%233D0278-%23660066-%2378023D-%23A50D22) (green-blind), and [Tritanopia](https://davidmathlogic.com/colorblind/#%2326D926-%2382D775-%23C2DDA7-%23E0E0B8-%23DDC2A7-%23D78275-%23D92626-%23A5220D-%23783D02-%23666600-%233D7802-%2322A50D) (blue-blind).

![Accessible Key Colors]({static}/images/news/accessible_key_colors.png)

We used 1/3 of hues for each palette, changing the hue vertically and changing the brightness and saturation horizontally when the colors are arranged in a circle. This ensures that every region on the circle has a distinct color, and that the change in colors is nearly uniform.

You can find the code written to generate these palettes [here](https://svelte.dev/repl/b65bda7e6a53487880a08726bfb2da7e?version=4.2.18).

We have tested that these work well in simulators. However, we are not done until we get feedback / confirmation from the users who would benefit from these palettes. If that's you, please reach out!

[mixxx#13497](https://github.com/mixxxdj/mixxx/pull/13497)

## Where to try it out

This feature is now available in the [Alpha versions](https://mixxx.org/download/#testing) of Mixxx. We would greatly appreciate any testing, and if you find bugs, please do let us know in the GitHub Issues.
