# triclojure-hoplon-2016

This is a starter project and reference for attendees of
the [ClojureScript with Hoplon Workshop](http://www.meetup.com/TriClojure/events/234304229/),
conducted on November 9th, 2016.  Its canonical location is https://github.com/hoplon/triclojure-hoplon-2016

This README document contains instructions for setting up your computer to run Clojure
and ClojureScript, and links to references and additional resources that you
might find helpful.

## Overview of directories and files
```
├── assets           # CSS for the starter project
├── boot.properties  # Pins the version of boot for this project 
├── build.boot       # Boot build file
├── README.md        # This document: setup, resources
└── src              # Starter project source files
```

## Table of Contents

* [One-time computer setup](#one-time-computer-setup)
* [Project develpoment](#project-development)
* [References](#references)
* [Glossary of Terms](#glossary-of-terms)

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

## References

### Community

* [#hoplon on Clojurians Slack](http://clojurians.net/)
* [Discourse community](http://hoplon.discoursehosting.net/)

### Talks and tutorials on Youtube

* [Hoplon and Javelin, WebDev Alternate Reality](https://www.youtube.com/watch?v=UoZyyo2Bwr8)
* [Building a reactive web frontend with Hoplon - Singapore Clojure Meetup](https://www.youtube.com/watch?v=zsAch5aqXmc)
* [Reactive web apps with Hoplon and Datascript](https://skillsmatter.com/skillscasts/5380-reactive-web-apps-with-hoplon-and-datascript)

## Glossary of Terms, Functions, Macros, Acronyms

| Term | Definition |
| --- | --- |
| `boot` | The [Boot](http://boot-clj.com/) command-line build tool, necessary to use Hoplon |
|`boot.properties`| Used to pin the versions of Clojure and Boot used on a per-project basis|
| `build.boot`| Clojure file loaded by `boot` automatically if present in the current directory unless the `-B` flag is passed.  Used to describe the build process for a particular project.|
| `cell` | `javelin.core/cell`, function, creates a new input cell: `(def n (cell 0))` |
| `cell=` | `javelin.core/cell=`, macro, creates a new formula cell `(def n+1 (cell= (inc n)))` |
| component | A ClojureScript function that returns an HTML element that can be embedded in a page.  Used to extend HTML by modularizing behaviors and abstracting over other components and HTML elements. |
| `.cljs.hl` | The file extension used by Hoplon-syntax ClojureScript files.  May use the `page` macro instead of the `ns` macro at the top, and Javelin and HLisp functions are automatically referred and so don't need to be qualified.  e.g. `(h1 (p "foo"))` can be written instead of `(hoplon.core/h1 (hoplon.core/p "foo"))` and `(cell 1)` can be writte instead of `(javelin.core/cell 1)`.  Hoplon apps tend to start as a single `.cljs.hl` file for convenience, but evolve into one or more `.cljs.hl` files that depend on the functions in many more `.cljs` files.  The `hoplon` Boot task compiles `.cljs.hl` files into `.cljs` files suitable for consumption by the ClojureScript compiler.|
| ClojureScript | The [ClojureScript](http://clojurescript.org/) language and compiler, a dialect of [Clojure](http://clojure.org/) that targets the JavaScript platform. `.cljs.hl` files are compiled by the `hoplon` task into `.cljs` files that are converted into JavaScript by the ClojureScript compiler.|
|`defelem`|`hoplon.core/defelem`, macro, convenience macro for creating components, or functions that return HTML objects.  Handles "boxing" attributes and children.  e.g. `(defelem example [attrs kids] {:attrs attrs, :kids kids})` when called like `(example :foo 1 :bar 2 (p "lol"))` returns `{:attrs {:foo 1, :bar 2}, :kids [#<[object HTMLParagraphElement]>]}`|
| `defc` | `javelin.core/defc`, macro, creates a new input cell `(defc n 0)` |
| `defc=` | `javelin.core/defc=`, macro, creates a new formula cell `(defc= n+1 (inc n))` |
| `formula`| `javelin.core/formula`, function, converts "normal" functions into functions of cells that participate in Javelin's graph of cells.  e.g. `(cell= (println x))` is equivalent to `((formula println) x)`.  `cell=` compiles into ClojureScript code that calls the `formula` function.  `formula` can be [used from JavaScript](http://adzerk.com/blog/2015/06/splint-functional-first-aid-jquery/).|
| Hoplon | The [Hoplon](http://hoplon.io/) Clojure and ClojureScript web framework |
| Javelin | The [Javelin](https://github.com/hoplon/javelin) ClojureScript library bundled with Hoplon |
| `page` | `hoplon.core/page`, macro, used at the top of `.cljs.hl` pages like `ns`, except declares HTML file to output instead of namespace |
| SPA | "Single-page Application", a browser-based application such as GMail that leverages the web browser as a rich client instead of as a hyperlinked document viewer.  Popular alternative to desktop apps since around when XMLHttpRequest/Ajax techniques entered the mainstream in 2007.  Hoplon was built specifically to build SPAs.|
| task | Or [Boot task](https://github.com/boot-clj/boot/wiki/Tasks), adds some capability to a boot-based project.  Tasks can be consumed as Clojure libraries, or tasks can be written and used in a single project's `build.boot` file.  The Hoplon "compiler" that converts `.cljs.hl` files to `.cljs` files is implemented and distributed as a Clojure library containing a boot task, the `hoplon` task.|

