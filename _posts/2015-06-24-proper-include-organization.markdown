---
layout: post
title: "Proper Include Organization"
date: 2015-06-24 23:18:44 +0200
comments: true
categories:
---

At work I'm was asked to take over the maintainer role of a larger C++ library.

This library is a key foundation of several other modules and programs.

The library comes with a top-level include file which pulls in all the features
for the end-user. I'm not a fan of this approach, but for now it is ok. However,
there is one thing that bothers me: the overall organization of the include files
between each other and the compile-units. Most, if not all header files, do not list
their dependent header files. Every compile unit pulls in almost all other header files
not only those it actually needs to compile. The previous maintainer created a top-level
header file for every sub-module (math functions, networking stuff, etc. ). The different
compile units include those module header-files.

For some reason the whole library is compiled with a "unity build" approach. A top-level
compile unit includes all the other compile-units into one big file. This file gets compiled
in one go.

When I setup my development environment, I changed this single-source file approach to
use separate compile units. A few days later my co-workers complained that the time
to run the nightly build went from 5 hours up to around 20 hours.

Due to the specific nature of my library's include file organization compiling it
with separate compile-units increased the time to build it from 5 minutes to around 20 minutes.

Compiling the different compile-units meant that most other header files (and many many
other system includes) had to be compiled over and over again. And not just once with the
single-source approach. With a rather slow compiler, like MSVC, this did not go unnoticed.

So I had to revert my change back to the single-source approach.

Keeping a sane include organization is key to lean and small compile units.
