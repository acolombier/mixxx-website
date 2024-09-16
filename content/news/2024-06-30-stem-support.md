title: "GSoC 2024: Adding STEM mixing support"
authors: Antoine Colombier
tags: gsoc, gsoc-2024, stems
slug: STEM-Mixing
date: 2024-08-26 12:00:00

Disclaimer: *The blog post primarily serves as the documentation for the [Google Summer of Code](https://summerofcode.withgoogle.com/) 2024 project: "Multi channel mixing support (STEMS)".*

## Explore New Creative Horizons with Mixxx's Latest Feature: Stem Mixing

We're excited to bring a powerful new feature to Mixxx: Stem Mixing. While the concept of stems — separate audio tracks for different elements of a song — has been a staple in digital audio workstations (DAWs) for years, it’s now making its way into live DJing. Typically, a song is divided into stems like drums, bassline, harmony, and vocals. In a DAW, these individual tracks allow producers to have granular control during the production process.

Now, with Stem Mixing in Mixxx, you can take that same level of control into your DJ sets. Built on top of [Native Instrument' Open Specification](https://www.stems-music.com) This feature enables you to isolate and manipulate these elements in real-time, allowing for live remixing, mashups, and creative edits on the fly. Whether you’re blending two tracks together or creating entirely new soundscapes, Stem Mixing offers a new dimension of flexibility and creativity for your performances.

Mixxx now supports Native Instruments stem files, the current public specification for this format. Whether you're an amateur DJ eager to experiment with new techniques or a professional looking to enhance your performances, Stem Mixing in Mixxx offers powerful new capabilities to elevate your mixes.

For example, it becomes piece of cake to mixxx the vocals of track with another instrumental version.
[![Stem Mixxing]({static}/images/news/stem_mixing.png)]({static}/images/news/stem_mixing.png)

It is also possible to load a single stem or set of them into sampler.
[![Stem Mixxing]({static}/images/news/stem_sampler_loading.png)]({static}/images/news/stem_sampler_loading.png)

Coupled with saved loop, it makes it pretty trivial to isolate that catchy voice line or a great saxophone sample!
[![Stem Mixxing]({static}/images/news/stem_sample_with_saved_loop.png)]({static}/images/news/stem_sample_with_saved_loop.png)

Please note that although we worked on improving the engine performance, stem mixing is still very resource-greedy, so do make sure your machine has enough CPU power to perform live stems mixing.

## Empowering open standards

Over the past few years, many DJing solutions have introduced their own proprietary standards for stems. While most of these formats can be reverse-engineered with relative ease, we wanted to support and encourage the open-source approach introduced by Native Instruments. We've extended the scope of that standard in Mixxx, allowing for more flexibility in audio formats. Unlike the original specification, which only supported AAC and ALAC, Mixxx now supports a broader range of codecs. These include all the formats already compatible with Mixxx, such as AIFF, MP3, Opus, WAV, and WV. The only requirement is to use the same codec across all stems, keep the sample rate consistent parameter and use stereo.

However, there are still some issues and limitations with the current standard, such as the lack of internationalization for labels. Rather than creating [yet another standard](https://imgs.xkcd.com/comics/standards_2x.png), we would prefer to contribute to improving the existing open specification from Native Instruments. If you are part of the NI team and are open to collaboration, we would love to help refine and expand this standard. Please feel free to [get in touch](https://mixxx.org/contact/) with us.

## Paving the Way for AI-Generated Stems

The introduction of Stem Mixing in Mixxx is just the beginning of a revolutionary journey in DJing technology. This feature not only enhances your current capabilities but also sets the stage for future innovations, particularly in the realm of AI-generated stems. The Mixxx community is actively exploring ways to integrate artificial intelligence to create stems on the fly, pushing the boundaries of what’s possible in live DJ performances.

Competitors like Virtual DJ and Algoriddim’s djay Pro AI have already implemented AI-driven stem separation, allowing DJs to extract individual elements from any track in real-time. These advancements highlight the potential and ambition we have for Mixxx. Our goal is to provide DJs with the most cutting-edge tools to unlock new levels of creativity and performance.

Imagine being able to instantly isolate vocals, drums, or other components from any track in your library, regardless of its original format. This capability would not only streamline the preparation process but also open up endless possibilities for live remixing and mashups. As the Mixxx community continues to develop and refine AI-driven features, we are committed to bringing these powerful tools to our users, ensuring that Mixxx remains at the forefront of DJing technology.

However, there is still a long journey for it to be ready, especially because of the challenge with supporting hardware acceleration, needed to perform stem separation in real-time. This topic is currently very active and hotly debated in our community chat on Zulip. If you are interested in contributing to this effort or just want to stay updated on the latest developments, we invite you to [join the discussion](https://mixxx.zulipchat.com/#narrow/stream/109171-development/topic/stem.20separation/near/439520527). Your input and enthusiasm can help shape the future of Mixxx.

## How to quickly get started

Currently, Mixxx does not yet support generating stems on the fly. However, there are ongoing discussions about enabling real-time stem creation or adding functionality to generate stem tracks directly within Mixxx.

For now, you will need to create the NI stem files yourself. Fortunately, there are several ways to do this. If you're an audio producer, you can build the stems directly. Native Instruments provides [a tool](https://www.stems-music.com/stem-creator-tool/) for generating Stem files from a pre-mastered track along with the four stems that compose it. Note that while Native Instruments allows exporting unmastered stems with embedded mastering (limiter and compressor) applied on the fly, Mixxx does not yet support this feature. For better results in Mixxx, it is recommended to export your stems pre-mastered and disable the embedded mastering option.

If you would like to convert your existing library, there are various options available online, often built around Meta's [demucs](https://github.com/facebookresearch/demucs) model. Unfortunately, many of these projects have licensing issues or significant limitations. While developing the stem feature, I created [a small command-line tool for generating stem tracks](https://github.com/acolombier/stemgen). It currently works on Linux and should also function with Linux containers on other platforms. I plan to continue maintaining it, with future goals of developing a more complete solution with a user interface and native support for Mac and Windows.

### Generate stems from stereo tracks using stemgen and Docker

> [Docker](https://www.docker.com/) is a platform that allows you to run applications in isolation from your system. Note that [stemgen](https://hub.docker.com/r/aclmb/stemgen) is available only as a Linux container. Linux containers are the default on Mac and Linux, but you will need to enable them on Windows.

#### Step 1: Download the Container

First, you’ll need to download the stemgen container to your machine. Open your terminal and run the following command:

```sh
docker pull aclmb/stemgen:latest
```

Please note that this container includes PyTorch for running Meta's model, as well as NVIDIA's CUDA libraries for GPU support. As a result, the container is quite large, so ensure you have at least 4 GiB of free space on your machine.

> **Info:**  
> If you are using a Linux machine with an NVIDIA graphics card, make sure to install the [NVIDIA container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).

#### Step 2: Run the Stem Generation Process

Once the container is downloaded, you can generate the stem file with the following command:

```sh
docker run -v /path/to/music/folder/:/path/to/music/folder/ -it --rm aclmb/stemgen:latest stemgen "/path/to/music/folder/My Music - Title.ext" /path/to/music/folder
```

*If you are using the NVIDIA container toolkit, you can add the `--gpus all` option after `--rm` like this:*

```sh
docker run -v /path/to/music/folder/:/path/to/music/folder/ -it --rm --gpus all aclmb/stemgen:latest stemgen "/path/to/music/folder/My Music - Title.ext" /path/to/music/folder
```

> **Tip:**  
> You can customize the generated stem file using various command-line options. To see a list of available options, run the following command:
> ```sh
> docker run -it --rm aclmb/stemgen:latest stemgen --help
> ```

#### Step 3: Enjoy Your New Stem File

That’s it! You should now have a file named `/path/to/music/folder/My Music - Title.stem.mp4` on your machine, ready to be played in Mixxx. If you encounter any issues, feel free to [start a new discussion on the project](https://github.com/acolombier/stemgen/discussions/categories/q-a).

## What features are supported already?

Here is a table that summarize the new stem features. Note that you may find more details and also get involved with the work in the [Github epic](https://github.com/mixxxdj/mixxx/issues/13116) dedicated to stem mixing.

|                       |                     |                                                          |
|-----------------------|---------------------|----------------------------------------------------------|
| File   support        | *Releasing in 2.6*  | [PR #13044](https://github.com/mixxxdj/mixxx/pull/13044) |
| Engine support        | *Releasing in 2.6*  | [PR #13070](https://github.com/mixxxdj/mixxx/pull/13070) |
| Multithreaded scaling | *Releasing in 2.6*  | [PR #13143](https://github.com/mixxxdj/mixxx/pull/13143) |
| Analyser support      | *Releasing in 2.6*  | [PR #13106](https://github.com/mixxxdj/mixxx/pull/13106) |
| Gain control          | *Releasing in 2.6*  | [PR #13086](https://github.com/mixxxdj/mixxx/pull/13086) |
| Quick FX              | *Releasing in 2.6*  | [PR #13123](https://github.com/mixxxdj/mixxx/pull/13123) |
| Loading as sampler    | *Scheduled in 2.6*  | [PR #13268](https://github.com/mixxxdj/mixxx/pull/13268) |
| UI                    | *Scheduled for 2.6* | [PR #13537](https://github.com/mixxxdj/mixxx/pull/13537) |
| Deck splitting        | *Planned*           |                                                          |

*`Releasing` implies that the PR is merged, `Scheduled` implies work in progress, near completion and `Planned` implies that this still left to do.*

If you wish to try the stem capabilities before the 2.6 beta gets released, you may [build Mixxx](https://github.com/mixxxdj/mixxx?tab=readme-ov-file#building-mixxx) using the CMake option `FFMPEG` and `STEM`.
