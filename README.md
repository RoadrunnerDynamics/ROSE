# ROSE🌹

*A beautiful interface to robotics.*

![rose](images/rose.jpg)

## ROSE: ROS made Easy

Robot Operating System (ROS(2)) has become the *de facto* standard for entry-level robots in universities and companies. The researchers who contribute to it have produced many programs and libraries capable of performing small tasks in complex robotic systems. Unfortunately, through a lack of focus and effort, the public ROS ecosystem has been allowed to deteriorate. Tutorials remain outdated, visualization and introspection tools remain slow and segfault-ey, ABI-breaking changes are introduced needlessly, and the one chance to fix it all was blown on a multi-year escapade into ivory-tower architecture and DDS vendor marketing fluff, without any feedback from real users of real robotic systems.

However, we must not remain stuck in this nightmarish past. There are new robots to build, new generations of roboticists to train, and new scales of problems we will have to tackle with our automated systems. To overcome contemporary challenges and prepare ourselves for the future, the critical infrastructure that lies at the heart of our profession must be repaired and maintained:

1. Interfaces and visualization utilities must be redesigned and rewritten for usability.

2. Simplicity, reliability, and performance must be introduced into core programs and libraries.

3. Accessibility to the tools used for building ROS systems must be improved by removing complex dependencies.

ROSE is an attempt to create beautiful, human-friendly interfaces to the world of ROS and robotic systems.

## The Plan

There are several things to complete in order to create a robotic ecosystem that is truly usable by all humans.

#### Interfaces

1. Make a static C library for ROS2 and dependencies
2. Create beautiful C bindings
3. Makefile for ROS2 C projects
   1. Bonus points: also make one for Windows
4. Set up code analysis tools for ROS projects
5. Build an Alpine (musl) container for ROS2
6. Create beautiful low-level-language bindings to the C library (Go, Rust, Ada, Hare, C++)
7. Create a good GUI for setting up ROS2 packages and systems
8. Create a good GUI for visualizing connections between nodes of ROS2 systems and viewing message data
   1. Bonus points: Automatically attach to GDB and Valgrind, easy view of resource utilization (Memory, CPU, GPU, network) of all processes at a glance.
9. Fix the init / launch system.
   1. Monitor process start time, use good lifecycle management, set process priorities, etc.
10. Fix the build system (CLI/GUI design? Teach people how to use Make? Enable static library generation?)
11. Create beautiful high-level language bindings (Node, Python, Julia, Mathematica)
12. Create libraries for interfacing with operating systems to monitor processes, manage heartbeats, implement process monitoring trees, monitor resource utilization, define failure behavior, etc.

#### Communication

1. Implement a fast and robust self-describing binary message format
2. Implement a shared memory message ring buffer for many-to-many communication
3. Implement UDP forwarding to/from ring buffers with retransmission and exponential backoff
   1. Bonus points: implement TLS reverse proxy
4. Implement serial communication forwarding
5. Create a new ROS2 backend that only uses this messaging system
6. Make ROS2 work on microcontrollers with this minimal messaging system

#### Simulation

1. Create a nice, permissively-distributable simulator for ROS2 (MuJoCo, Unity)
2. Make your own simulation engine (MuJoCo backend, Nuklear display, custom sensor models, Modelica FMU plugins for custom dynamics)

#### Core Packages

1. Localization: Work on simplifying and improving RTAB-Map and ORBSlam, packaging them up in a container
2. GTF - make a "Graph Transform" library using message passing, allowing kinematic loops
3. MPC - make an MPC and control optimization library using MuJoCo and BLIS
   1. Multiple vehicle kinematic models and plugins by default
   2. Bonus points: use ML to speed up optimization with NNC
4. Nav Stack: Make a very fast motion planning library that uses sampling methods
   1. Multiple vehicle kinematic models and plugins by default
   2. Bonus points: Use ML (NNC) to speed it up
5. Behavior trees: Create a simple library for defining robotics behavior trees
6. Create example applications using all of our libraries.

## Libraries for Robotics

> Simplicity is a prerequisite for reliability. - Edsger W. Dijkstra

Try to not pull in massive libraries. Use good, reliable libraries that run the instructions you want without introducing a bunch of incidental complexity. Also, try to use libraries that compile very quickly.

* **GUI** - [Nuklear](https://github.com/Immediate-Mode-UI/Nuklear)
* **TUI** - [Notcurses](https://github.com/dankamongmen/notcurses), [termbox](https://github.com/termbox/termbox)
* **Math** - [BLIS](https://github.com/flame/blis), [libzahl](https://git.suckless.org/libzahl/)
* **Text** - [libgrapheme](https://git.suckless.org/libgrapheme/)
* **Computer vision** - [CCV](https://libccv.org/)
* **Neural networks** - [NNC](https://libnnc.org/)
* **Barcodes** - [ZBar](https://zbar.sourceforge.net/)
* **Physics** - [MuJoCo](https://mujoco.org/)
* **Webservers** - [darkhttpd (static)](https://github.com/emikulic/darkhttpd), [mini_httpd](http://acme.com/software/mini_httpd/)
* **Image compression** - [QOK](https://qoiformat.org/)
* **Compression** - [liblzf](http://oldhome.schmorp.de/marc/liblzf.html)
* **Cryptography** - [LibreSSL](https://www.libressl.org/)

## Languages for Robotics

> Systems are asynchronous, distributed, and event-driven in nature, and this should be reflected inherently in the language used to define them and the tools used to build them. - Margaret Hamilton

This project aims at making robotics accessible for new generations of roboticists. To accomplish this, we need performance, some level of reliability, and ease of use.

ROSE should use the following languages for these purposes:

* Core functionality - fast, simple, and reliable languages: C, Hare, Ada
* Accessibility - high-level languages: Mathematica, JavaScript, Julia, Python, Go
* Compatibility - interfaces to established languages: C++, Java, Swift, Rust, Matlab

## Concluding Remarks

**Audience:** 👨‍👩‍👧‍👦This is a fun project meant to bring sophisticated robotics capabilities to beginners and researchers that need to get things done fast and need their tools to just work. This effort is part of a plan to use ROS on high-speed humanoid robotic systems.

**Reliability:** 🪨This project is solidly aimed at highly experimental research and robotics applications which are so complicated that the added effort of formal methods would prevent success in the first place. However, the simplicity of the software used in this project is paramount to enable such applications - and that simplicity does deliver some increased level of reliability. This project also intends to implement several tools to enhance some notions of reliability (tools like process monitoring and priority setting, system resource monitoring, and creation of fallback behaviors), but a full regeneration of the functionality of ROS in some combination of a robotics DSL and SPARK would be the best for final implementations.

**Practicality:** 🛠️ This is indeed a large project, but it is made possible given recent advances in software development. Namely, generative machine learning models, mob programming techniques, and an embrace of simplicity will enable a small group consisting of many beginners to make significant progress on this project in under a year.

**License:** ⚖️ The software of this project is licensed under the Unlicense since it provides the most accessibility to future generations of roboticists.

**Funding:** 💵 Saving the world from human centuries of wasted effort is a surprisingly unlucrative task. If you wish to support our noble and valiant cause, consider donating to the Roadrunner Dynamics or IEEE Robotics and Automation Society student organizations at [UTSA](https://www.utsa.edu/).
