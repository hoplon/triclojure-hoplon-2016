# triclojure-hoplon-2016

This is a starter project and reference for attendees of
the [ClojureScript with Hoplon Workshop](http://www.meetup.com/TriClojure/events/234304229/),
conducted on November 9th, 2016.

This document contains instructions for setting up your computer to run Clojure
and ClojureScript, and links to references and additional resources that you
might find helpful.

It also contains instructions for developing the starter project once your
computer is set up.

## Table of Contents

* [One-time computer setup](#one-time-computer-setup)
* [Project develpoment](#project-development)
* [References](#references)

## One-time computer setup

Follow the instructions below to set up your computer to develop on the start project contained in this repository.  Windows 10, recent versions of OS X, and most distributions of GNU/Linux are suitable operating systems.  Windows 7 may or may not work.  If you are on Windows 7, you should consider developing on an [Ubuntu VM](http://askubuntu.com/a/153098).

### Install the Java Development Kit

First, you'll need to install the "Java Development Kit" or JDK on your
computer. You need version 8 or higher, so even if you have version 8 or
below already installed, you should install the latest version.

You can check which version of the JDK you have installed by trying `javac -version` in a terminal or console.  If it reports 1.8, you can skip this section.

> Note: JDK version 8 is also referred to in some places as JDK version 1.8.  They are the same version.

Among other things, the JDK includes the `java` and `javac` commands. `java`
starts the "Java Virtual Machine" or JVM, which is the platform that Clojure
code runs in. `javac` compiles `.java` files.

The workshop is oriented around the web browser platform and ClojureScript, but
the tools we'll be using (boot, the ClojureScript compiler) are
JVM/Clojure-based.

#### Windows and Mac

JDKs for various platforms can be downloaded here:
http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html If
you are on Windows or Mac, this is where you should obtain the JDK.

#### GNU/Linux

OpenJDK, an open-source version of Oracle's "official" JDK, might also be
available for your platform. It is also suitable. If you are using GNU/Linux, it
might be easier for you to install OpenJDK through your package manager than to
download and install the Oracle JDK.

### Install Boot

Follow the instructions for installing `boot` for your platform here:
https://github.com/boot-clj/boot#install

## Project development

After you've installed the JDK and `boot`, you can start continuous compilation of this project with the following command:

    boot dev



