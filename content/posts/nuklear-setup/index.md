---
title: "Nuklear GUI Setup using CMake"
date: 2024-08-14
# weight: 1
# aliases: ["/first"]
tags: ["Nuklear", "CMake", "C", "C++"]
categories: ["blog"]
author: "behoovah"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
# cover:
  #  image: "<image path/url>" # image path/url
  #  alt: "<alt text>" # alt text
  #  caption: "<text>" # display caption under cover
  #  relative: false # when using page bundles set this to true
  #  hidden: true # only hide on current single page
# editPost:
  #  URL: "https://github.com/<path_to_repo>/content"
  #  Text: "Suggest Changes" # edit text
  #  appendFilePath: true # to append file path to Edit link
---
## Intro
[Nuklear](https://github.com/Immediate-Mode-UI/Nuklear) Is a really cool library for programing
Graphical User Interfaces (GUIs) using C or C++. The library itself is written in 'pure' C but,
the best part about it: *it's a single header file*. That means no installation, no weird dlls,
just copy the nuklear.h into your project and include it.

Unfortunately this simplicity is a bit deceptive, as you need to know a bit about the library and
what its doing before you can actually even get started with it. 

I thought I would make a quick post about how I was able to get an example from the 
[Nuklear demos folder](https://github.com/Immediate-Mode-UI/Nuklear/tree/master/demo) compiling and running
using cmake and in a linux environment. 

**You will need to have a couple of things set-up to follow along**:
- [SDL2](https://wiki.libsdl.org/SDL2/Installation) (SDL is usually included with most linux distros)
- [CMake](https://cmake.org/) (CMake will create a makefile for us. Most linux distros have a cmake package available)

**Why SDL??**

Nuklear is *back-end agnostic* meaning that it doesn't actually draw anything directly but uses whatever back-end
you tell it to. Examples of different Nuklear back-ends can be found on the
[Nuklear Github](https://github.com/Immediate-Mode-UI/Nuklear/tree/master/demo). OpenGL, SFML, SDL/opengl are
options but for simplicity in this post, I am just going to use the example for SDL2 using its built-in renderer. 
This way we can avoid adding more dependencies such as GLAD etc.


## Create Project Folder
You can really do this a lot of different ways. For this example I'm going to create the following
structure inside of a directory called `nuke-test`:

```
├── src
│   ├── main.c
├── include
│   ├── nuklear.h
│   ├── nuklear_sdl_renderer.h
│   
└── CMakeLists.txt
```

## Copy Files
Go to the [Nuklear sdl_renderer demo](https://github.com/Immediate-Mode-UI/Nuklear/tree/master/demo/sdl_renderer)
folder and copy the `main.c` file into the src directory.

Next copy the `nuklear_sdl_renderer.h` into the include directory.

Then go to [Nuklear main branch](https://github.com/Immediate-Mode-UI/Nuklear/tree/master)
and copy the `nuklear.h` file into the include directory.

## Modify Example Files
In `nuklear_sdl_renderer.h` you will need to include the Nuklear library so that it can find the definitions add:
```
#include "nuklear.h"
```
Also in `nulear_sdl_renderer.h` you will find a line:
```
#define NK_SDL_RENDERER_SDL_H <SDL.h>
```
(for me its on line 16). Depending on where SDL is installed on your system you may need to change this line.
for me I changed it to:
```
#define NK_SDL_RENDERER_SDL_H <SDL2/SDL.h>
```
In `main.c` you will find these two lines near line number 25:
```
#include "../../nuklear.h"
#include "nuklear_sdl_renderer.h"
```
We dont need to include `nuklear.h` again because it is included with `nuklear_sdl_renderer.h` so we can delete that line
and replace the second line with the proper path to our `nuklear_sdl_renderer.h`:
```
#include "../include/nuklear_sdl_renderer.h"
```
## Create CMakeLists
Now we need to make a CMakeLists.txt file in the top directory. This will tell CMake how to go about creating a makefile. This is 
a pretty straightforward config, we just need to make sure that SDL can be found and that the math library is included:
```
#minimum required cmake version
#cmake --version

cmake_minimum_required(VERSION 3.2)

#set project name
project (NUKE_TEST)

find_package(SDL2 REQUIRED)

#create sources variable
set(SOURCES
  src/main.c
)

#add excutable with sources
add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME} SDL2 m)

#directories included
target_include_directories(${PROJECT_NAME}
  PRIVATE
    ${PROJECT_SOURCE_DIR}/include
  )
```
## Test
First things first run `cmake .` in the top directory of the project to initialize cmake,
and have it create the makefile.

Next run `make`

If there are no errors then try running the excutable that is created by typing `./NUKE_TEST`

If something didn't work try this:
- go over paths/file modifications carefully.
- look for typos
- google compiler error messages and codes.

## Congrats
If everything worked *NICCEEEE* now you can play around in `main.c` and change up the example or create
your own using the provided backend.

Of course this is nothing but getting the backend running on a simple example. Part of the cool factor
of Nuklear is that it is so flexible and customizable. Once you get the hang of it there are countless
ways to incorporate it into a project.

[go back](../).
