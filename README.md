# Ballz 3D RTX

This project upgrades the visuals of Ballz 3D with the power of raytracing.

## Setup

- Acquire the Ballz3D rom dump with md5 sum `339a8c9a96fcdedb2922b04bcc34f0d2`. (Other versions of the game not yet tested.)

## NOTES:

The `blastem` directory contains a copy of the source code of https://www.retrodev.com/blastem/ , modified (eventually) to support raytracing (?).

Could either:
(1) in-engine (have background layers handy)
(2) 

How do frames get to the screen?

Frames copied to `render_sdl.c` by `render_framebuffer_updated` (or copied to internal buffer?)

One place to grab memory would be in `advance_output_line` (vdp.c)
Another would be in `render_framebuffer_updated` (render_sdl.c)

Where to sneak in extra ballz-y data?
Could just allocate thicker framebuffer buffers and copy data in there(!)

Where is main memory? `m68k_context` appears to perhaps be the thing (nope!)
`genesis_context.work_ram` (genesis.h)

Okay, so can we grab work ram when vdp advances line? (prolly! threads? who knows!)

---

Current things:
 - flipped depth test and y axis because that gets closer to what we expect; might be more elegant to do ... anything else (also: need to test with demo camera pivot)
 - scale factor for center offset seems to be 1.0 but maybe I'm doing something wrong (thought: what if it's in post-transform space?)
 - character rotations are weird; maybe the local facing directions are in camera space?

 - what is the canvas size?
 - what is the focal length actually doing?
