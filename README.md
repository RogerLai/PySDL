PySDL
=====

Similar projects first:
-----------------------

* The equally named [PySDL on SourceForge](http://sourceforge.net/projects/pysdl). Last update was from 2000. Implemented in C.
* [Pygame](http://www.pygame.org/). Actively developed. Implemented in C. Is not a straight-forward 1:1 binding to SDL but has a different API.

How does this **PySDL** differ?
-------------------------------

* Purely implemented in Python.
* On-the-fly ctypes generation from the `SDL.h`.
* Straight-forward 1:1 binding to SDL.

How is it implemented?
----------------------

It uses [PyCParser](https://github.com/albertz/PyCParser) to automatically parse the SDL headers and to generate a ctypes interface to the library.

TODOs
-----

* I only tested it on MacOSX yet. There I needed some additional ObjC/Cocoa initializing code. Basically the stuff in `SDLmain.m`. Maybe similar stuff is needed on other architectures. Maybe it would also be possible to search for the `SDLmain.a` and just call the `main` in there. However, there is already a report that it also works on Linux.
* Some more testing. Some more complex example.
* The interface generated by PyCParser could be cached so it doesn't has to be recreated each time it is started. This has become less important though since the C parser already supports caching itself at least for the parsing part.
* Maybe it makes sense to provide an (possibly optional) additional wrapper around `SDL_Surface*` which calls `SDL_FreeSurface` in its `__del__` method.
* PyCParser could be extended. It works just enough so that it is able to fully parse the SDL headers.

--- [Albert Zeyer](https://github.com/albertz/)

