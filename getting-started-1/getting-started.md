# History and Philosophy of Chataigne

## The History

### Why making Chataigne ?

Along the years, I've worked in a lot of different projects and had to create a lot of tools again and again. While those tools were functional, they weren't optimized nor easy to use and once the creation is done, I couldn't let those tools to the artists I worked with for them to continue working on the project as they were not quite user-friendly.

Few years ago, i decided to create once and for all a tool that would fit most of my purposes as both a technician and digital artist. After few years of private use and tests, i decided to rewrite it completely from scratch in C++/JUCE and give it to the community as a free, open-source software, now known as Chataigne.

### Why this unpronounceable name ?

Chataigne means "Chestnut" in french, the real story behind this name involves a love story and wanting to remember this time in my life. Also it's funny.

## The Philosophy

### What exactly is Chataigne ?

In most of artistic projects involving technology, creators are going to use multiple softwares and devices for different purposes : one to control audio, one to generate video, another to handle the video mapping and maybe one to control lights, or Arduino boards to control motors, who knows..

In these setups, the communication and synchronization between those softwares can be challenging and therefore rapidly escalate to an overly complex setup. Also, those softwares and devices may require technical experience to be able to understand how they work and what's their best practices.

Chataigne aims to be the "conductor" of this technologic orchestra : while it will barely do anything visible to the public on it's own, it will be the one seeing the big picture and make sure that everyone gets what it needs. I'm trying hard to make the interface understandable for both technician and artists, so hopefully Chataigne would be the common workplace for artists and technician to work together.

### Why and when should i use it ?

First of all, because Chataigne is a conductor and doesn't "play an instrument", you won't have much use of it unless you have an "orchestra", meaning you it will make sense if you actually have a project and want to control other softwares and devices.

#### Chataigne is mainly a show and interactive installation creation tool

If you have a project involving multiple softwares and / or devices, you may want to synchronize everything from a unique place dedicated to that and not have intricate relationship between all your tools.

#### Chataigne is both "interactive" real-time and timeline based

Chataigne is working around two core concepts : the[ State Machine ](../the-state-machine/introduction-to-the-state-machine.md)and the [Time Machine.](../the-time-machine-sequences/introduction-to-the-time-machine.md)

The State Machine will handle all real-time interaction with rules that can be very basic but can get fairly complex if needed.

The Time Machine will handle all time based control, with classic timelines that can trigger controls at precise moments, or animate parameters and colors along time. It features a basic audio timeline if you need to play audio in sync, but if you need complex audio handling, you should definitely use a dedicated software for that, and control it from Chataigne.

#### Chataigne features a lot of side tools for fast testing and researching

Chataigne contains a lot of "hidden gems" and tools that integrate with the global workflow, but also can be used separately such as the [Router ](../modules/the-module-router.md)which will basically route any input to different outputs and convert the signal at the same time. You'll discover them as you wander around the docs and the software.

## Next

Now that you have some context, let's dive into it ! Learn all about [The Interface](the-interface.md)

