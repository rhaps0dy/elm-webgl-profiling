# elm-music-viz
Particle-based music visualizer. Used to profile and maybe optimize elm-webgl.

If you use my elm-webgl fork, this small app maxes out 1 core of a 3.4GHz CPU when
running at 30fps (so it does not run at 30fps) and creates so much garbage the
collector can't keep up with it and it eventually eats up all the memory. This
version can be seen running [here](http://rhaps0dy.bananabo.xyz/v1/). I am not
posting it since it's not worth much, but it's a straight port of this repo to
make use of my fork of elm-webgl.

jdavidberger made a much better version of webgl, also implemnting points,
lines, etc. so I ported the application to it to try. Now, at 60fps, the same
CPU core stays at ~80%. The memory is also eaten up, but much, much slower.

I'm not sure how much memory usage comes from the app itself and how much from
the library being tested here. Profiling the app again shows a 78% library CPU
usage vs 22% application CPU usage. There is a part using 72% which is marked
with comments in the library code. If we can improve the performance of that
with a couple tricks (likely, but I do not know which now), elm-webgl will be
that much better. If we could know why the meory leaks too it'd be great.

## How to install elm-webaudio

1- Remove it from elm-package.json

2- elm package install the rest of dependencies

3- Clone
[https://github.com/bmatcuk/elm-webaudio](https://github.com/bmatcuk/elm-webaudio)
to `elm-stuff/packages/bmatcuk/elm-webaudio/1.0.0/`. To be clear, don't clone
it _under_ that directory, clone it such that WebAudio.elm's path is
`elm-stuff/packages/bmatcuk/elm-webaudio/1.0.0/WebAudio.elm`

4- Add the line to elm-package.json again

## How to run
`elm reactor` at the root of this repo and navigate with its web interface to
`src/Main.elm`
