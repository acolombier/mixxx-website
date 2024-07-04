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

Before diving into the coding, my mentor recommended that we create a plan for the project and solve any open questions that were remaining.

We used Zulip to get feedback and find use cases from the community to better understand the needs of Mixxx' users. We particularly wanted to find clarity for the Track Similarity Column. After some discussion I made a design doc which gave us a concrete plan and made it easier to decide on the finishing details.

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

## Where to try it out

This feature is now available in the [Alpha versions](https://mixxx.org/download/#testing) of Mixxx. We would greatly appreciate any testing, and if you find bugs, please do let us know in the GitHub Issues. 