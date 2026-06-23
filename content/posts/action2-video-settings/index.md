---
title: My video settings on the DJI Action 2 for proximity FPV in the Andes
date: 2026-06-23
draft: false
tags:
  - camera
  - action2
  - settings
  - motion blur
  - fpv
summary: To capture the speed of the flight and the beauty of the landscape, my goal was to get a deep motion blur, decent exposure and wide FOV. To achieve that, my main decisions were breaking the 180° shutter rule and drastically reducing stabilization settings.
---
To capture the speed of the flight and the beauty of the landscape, my goal was to get a bold motion blur, decent exposure and wide FOV. Getting there took me some iterations.

This post is a record of what settings I use to achieve that with the DJI Action 2. My main decisions were breaking the 180° shutter rule and drastically reducing stabilization settings.

## Base settings

- **Resolution:** 4K 60fps, 4:3 format.
- **FOV:** Wide (not Ultra Wide). This preserves gyroscope data for stabilization.
- **Color profile:** D-Cinelike.
- **White balance:** AWB for now (I am still experimenting here).
- **Stabilization:** Turn OFF in-camera stabilization. Everything happens in Gyroflow.

![RAW Footage](images/motion-blur.gif)


## The exposure problem:

Auto exposure was inconsistent and didn't got me the results I wanted for this proximity flight style. Because the camera is constantly moving between bright sky and dark terrain, Auto settings result in minimal motion blur, blown highlights, and dark areas mid-flight.

My current approach is:

- **Shutter speed:** Fixed at 1/60 or 1/80.
- **ISO:** Range locked between 100 and 400 (not fixed, not full auto).
- **ND filters:** Essential (and chosen before each flight or session).

![Action 2 + TBS ND filters](images/action2_filter.jpg)

### Picking the ND filter

Before every flight or session I run a short test:

1. Choose an ND filter and configure the camera with your base settings.
2. Point at the sky and check the exposure meter.
3. Point at the ground or a dark surface and check the meter again.
4. Goal: meter at or near 0 in both extremes.
5. If it overexposes at the sky → higher ND.
6. If it underexposes in the shadows → lower ND.
7. If both happen → adjust ISO or shutter first, then repeat.

When the exposure meter is at or near 0 in both extremes, that's your ND.

It takes two minutes and saves the whole flight.

##  Deep motion blur

According to the 180° rule, the recommended standard for 60fps is 1/120 shutter speed. For most video work, that might work. But it didn't get me the results I wanted for FPV.

At 1/120, close-up terrain still looks crispy and detailed rather than fluid. 
Between 1/60 and 1/80, you get enough motion blur to make fast passes look natural, while still maintaining detail on slower shots and landscapes.

**This only works if your ND selection is correct.** A slower shutter with the 
wrong ND just blows the image. The test method above becomes critical 
here.

## Almost no stabilization

I stabilize in Gyroflow, never in-camera. But the more important lesson was 
how much stabilization to apply.

Default settings are set at 50% smoothness. For proximity FPV flying that's too much: you remove the sense of movement and hide the pilot's response that makes this type of footage unique. While trying other settings, I found that 5–15% smoothness was the sweet spot:

  - 5%: corrects the worst wobble and quad vibrations. Keeps the flying feel and stick input visible.
  - 15%: smoother for less aggressive flights. Works for landscapes and suits better a general audience.

![Gyroflow settings at 5% smoothness](images/gyroflow.png)

**My current settings:**

| Parameter          | Value         |
| ------------------ | ------------- |
| Smoothness         | 5.0% - 15.0%  |
| Lock horizon       | Off           |
| Dynamic zooming    | On            |
| Zoom limit         | 115%          |
| Zooming speed      | 4.0s          |
| Lens correction    | 100%          |
| Low pass filter*   | On — 50.00 Hz |
| IMU orientation    | XYZ           |
| Integration method | None          |
| Export codec       | H.265/HEVC    |
| Output size        | 4096 × 2304   |
| Bitrate            | 95 Mbps       |
| GPU encoding       | On            |
|                    |               |
*\*Low pass filter is optional to remove some electric or mechanical noise the camera's gyro captures at some throttle levels

*Everything else remains in default settings.*

## Color grading in DaVinci Resolve

Not much to suggest here yet. I use D-Cinelike in the camera and DaVinci Resolve for color grading. This is still an area I'm actively developing and learning. I'll document this separately once I have something replicable.

## Results

Here's a clip from the Peruvian Pacific coast with these settings applied (ND 16, 1/60 shutter speed, 5% stabilization, color grade in DaVinci):

![Result](images/output.gif)

{{< youtube MYRd_c3luvw >}}

---

*These settings were developed flying the Peruvian Pacific coast:
bright midday sun, high contrast terrain, sea level altitude. 
Other conditions will require different ND choices, 
but the logic is the same.*