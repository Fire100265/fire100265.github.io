---
layout: post
title: "Overview of Brightness Utility"
date: 2025-11-18 15:00:00 +0800
categories: general
---

About a week ago, I published my first boredom-induced project: [Brightness Utility](https://www.github.com/Fire100265/brightness-utility). This is a very simple wrapper for the ddcutil library and is built with Qt6.

## Motivation
Usually, I only have the will to write my own applications if they actually serve a need and a bearable alternative does not exist. This was the case with this utility. Most desktop environments on Linux, such as KDE and GNOME, have built-in brightness control utilities. However, my setup with Swaywm with Waybar on Arch. I really wanted a way to control the brightness of my monitor while being firmly planted on my chair. Hence, this project was born.

While GUIs for brightness control did exist, they all relied on the ACPI sysfs interfaces in `/sys/class/backlight/*`. This is useless for me because pretty much only laptops use it. External monitors use the Display Data Channel Command Interface (DDC/CI) protocol to interact with the operating system.

## Implementation
Thankfully, a library for handling most of the heavy-lifting already existed in the form of [ddcutil](https://www.ddcutil.com/). The developers even give us a nice API to work with in the form of `ddcutil_c_api.h`. They really did most of the hard work for me since the DDC/CI specification is long and complex and all I care about is the brightness.

I also wanted to add a simple Qt6 GUI with a slider and status tray icon of a sun, which when pressed open the GUI. Originally, I thought about using GTK4 as ddcutil is a C library and I would have language consistency. However, GTK has horrible support for status tray icons and I had to rely on community-maintained third-party libraries like [libayatana-appindicator-glib](https://github.com/AyatanaIndicators/libayatana-appindicator-glib). I also could not get my linker to find the library for some reason. Either way, Qt6 has way better support for app indicators and I ended up using that. Only drawback of Qt6 for me is that C++ is far from my favourite language. It is just way too complex.

The last part of my program was CMake. I wanted to practice using a modern build system for my program as these scale way better with many different dependencies and are the community-recommended ways to handle C and C++ builds. Originally, I wanted to try GNU Autotools for my build system, as every Linux system already comes with them. However, I quickly gave us as soon as I saw just how many different components there are in this build system, as well as the need to learn the frankly dated M4 programming language. Hence, I chose CMake as so many different open-source projects use it and has become the de-facto standard.

## Key Takeaways
This project exposed me to many dfferent programming skills that will certainly be useful for me in learning more about the field of computing.

First was the utilisation of a C library. Though it had a pretty decent API, I still learnt how they are utilised.

The most important skill here for me was Qt6. It is one of the leading frameworks in UI development and is going stronger than ever. It will certainly be useful for me in the future.

Lastly, CMake is an excellent tool to learn because of its prevalence in C projects and its invaluable versattility and compatibility.

## Conclusion
Overall, this was a pretty easy and useful project. I can build on the things I learnt here in the future.
