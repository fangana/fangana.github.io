---
title: AMO lab techniques
excerpt: Something I plan to put in my thesis
tags: [physics]
---

I realized recently that there many tips, tricks, and techniques to working with optics and lasers in an AMO lab that are taught only in lab via advisors/older grad students. These aren't things that need to be or even can be taught in normal (lab) classes, but I found it weird that it's hard to find them online too. So, I've decided to include a section in my (upcoming) thesis dedicated to these techniques which may be general to AMO labs... or specific to the equipment in my lab.

---
## Table of Contents
0. Basic laser safety
1. Aligning a laser to a straight line
2. Fiber coupling: how to couple laser light into a single-mode optical fiber
3. Cleaning optics
4. Tightening posts
5. Coupling a tapered amplifier
6. Making a double-pass/cat's eye AOM setup


---
## Basic laser safety

Laser safety can be summed up into one rule: *never look at a laser* (don't shine a laser into an eye). This seems like the most obvious thing, but I and other people very often accidentally skirt this number one rule, because there are so many ways eyes can contact laser beams. Some sub-rules that cover most of the safety are:

* *Wear laser goggles* (of the right wavelength/optical density).
* *Don't put optics at eye level*. *Don't put eyes at laser level*.
* *Keep track of (block) stray reflections*. Often easier to *build an enclosure*.
* *Be careful when placing optics*. Place optics straight down, so that a beam can't deflect vertically into an eye.
* *Look away from the laser/table* when bending down to pick things off the ground.

---
## Aligning a laser to a straight line

This is a basic technique for steering laser beams, and is most often used to make a beam parallel to the table or to overlap two beams. It's documented pretty well by EdmundOptics [here](https://www.edmundoptics.com/resources/application-notes/lasers/simplifying-laser-alignment/) ([youtube vid](https://www.youtube.com/watch?v=A1LIcQTktGU)) and other optics companies.

[PIC PIC PIC]

As shown in the sketch above, we need two degrees of freedom to match a laser beam to a line, so we use two mirrors on adjustable mirror mounts (x and y tilt). This can be thought of as using one mirror ("far mirror") to define the position of the laser, and one mirror ("near mirror") to determine the angle. Typically we put these mounts at 45 degrees to the laser to get the most range of motion from the mirrors.

We then need two targets to aim the laser at: one placed near to the mirrors and one placed far away. When overlapping two beams, the target is just the other beam. Otherwise, I've used a piece of paper taped to a mount, which I move back and forth between near and far positions which I define with screws in the table.

Then, **use the near mirror to align the laser to the near target**, then **the far mirror to the far target** and repeat until the laser is aligned to both targets. I typically do this coarsely (moving the mirror mounts) before doing it finely (clamping down the mounts and moving the knobs on the mounts).

[PIC PIC PIC]

As a final note, the "ideal" version of laser alignment uses two mirrors that are separated very far away, such that the "near mirror" controls the position of the beam (red, dashed) and the "far mirror" controls the angle (blue, dotted).

---

## Fiber coupling

To couple laser light into a single mode fiber, you need two adjustable mirrors (x and y axes) and a fiber adapter with an aspheric lens in a "[z axis mount](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=188)" that can adjust the distance between the two. (In optics, the z axis is along the propagation of the laser beam.)

The idea is to match the mode of the laser beam with the mode that the fiber accepts, meaning that the angle and position of the laser must be exactly right (the two mirrors), and the asphere must be positioned exactly to focus the light into the fiber (z-axis mount). As a first pass, we roughly place the mirrors such that the laser hits the center of the fiber coupler straight on (not at a large angle).

### Coarse alignment: a fiber pen back through

Since our goal is to mode match, we look at the mode of the fiber by shining light back through the fiber. We hook up a "fiber pen", a low powered handheld laser with a fiber input, to the fiber in reverse.

With the fiber pen light coming out, we collimate the light by adjusting the z axis knob on the fiber coupler/asphere mount. This roughly ensures that a collimated beam aligned in x and y will go into the fiber.

To align x and y, we need to overlap the incoming laser beam and the reverse fiber pen beam. To overlap two beams in general, they must be matched horizontally and vertically at two points (ideally separated by a large distance) along their propagation, and we use one mirror to align each point.

### Fine alignment: walking the knobs

For fine alignment, we look at the power going through the fiber as we "walk" corresponding pairs of knobs (horizontal/horizontal or vertical/vertical) on the mirror mounts.

[PICTURE]
In the "ideal" limit of fiber coupling, one mirror is placed (infinitely) far from the fiber adapter, and one is near. Tilting the far mirror effectively controls the position of the beam on the coupler, and tilting the near mirror controls the angle of the beam going into the coupler. In practice, the mirrors are much closer, but are still placed 45 degrees to the beam - otherwise, the angle/position get more coupled and the procedure becomes harder.

We are trying to find a global maximum in the output power in the 2D parameter space of knobs 1 and 2. In practice, this means maximizing the power with knob 1 at different values of knob 2, in a procedure like:
1. Maximize power by twisting knob 1.
2. Twist knob 2 a little.
3. Maximize power by twisting knob 1.
4. If the power here is larger than at the previous knob 2 position, repeat steps 2-3. If it's smaller, twist knob 2 in the other direction and repeat step 3. Practice can make this go very quickly.

Eventually, this gets you pretty close to the maximum power with these two knobs. We do this with pairs of horizontal knobs and pairs of vertical knobs, and with the z knob and some of the other knobs. By iterating on several pairs of knobs, eventually we get to the global maximum of the 5D (!!!) parameter space.

For collimated, gaussian beams, we typically get around 70-80\% fiber coupling efficiency (output power from fiber/input power). For more non-ideal beams (e.g., a weird mode from a tapered amplifier), 50\% is pretty good. Sometimes long-focal-length cylindrical and spherical lenses placed before the fiber coupler can increase the efficiency with better mode matching.

---

## Cleaning optics

Optics (lenses, mirrors, beam splitters...) are often covered in dust and occasional fingerprints, and it's important to keep them clean to prevent stray reflections and keep up performance. There are many techniques that are [documented online through optics companies](https://www.newport.com/n/how-to-clean-optics), but this is what I do:

1. FIRST, use compressed air to blow off any large debris/dust from the optic.
2. Use methanol/solvent with lens tissue to clean the optic.
3. Repeat with methanol if it's still dirty.

There are different ways to use methanol to clean an optic:
1. Lay the lens tissue on top of the optic, put a few drops of methanol on top, and drag the wet part of the tissue across the entire optic. This works well if the optic is unmounted and the surface is flat. If any residue remains, you've put on too much methanol.
2. Wad up some lens tissue and grab it with forceps, without touching the part of the tissue that will contact the optic. Drop some methanol on the tissue. Wipe from the center towards the outside, and don't touch the optic twice with the same part of the tissue. This way, you don't drag any dust across the entire optic and create a scratch.

Ideally, this should all be done above some lens tissue and directly above a table so the optic doesn't get dirty or damaged if you happen to drop it.

---

# Tightening posts

Optics placed in mounts must be extremely secure, and failing to tighten one part of one mount can cause instability in alignment, laser power, and fiber coupling efficiency. It's not obvious what to tighten, how to tighten it, and how much to tighten what. Here are two examples of mounts in my setup, and how I've tightened them.

The rule of thumb is: *tighten with an allen wrench or a long lever arm*. Using just a hex screwdriver is not tight enough.

1/2 inch post+BE1 with 90 degree angle holder, one screw is thumb screw.

Things to tighten (labeled, and in order):
1. 1/2 inch post to lens holder.
2. Lens inside lens holder.
3. 1/2 inch post to 1/2 inch post.
4. 1/2 inch post to 90 degree angle adapter. (x2)
5. 1/2 inch post holder to post holder base.
6. 1/2 inch post holder to 1/2 inch post.
7. Post holder base to table with fork clamp.

Other things to tighten:
* Mirrors to mirror mounts: Be careful. Tightening too much can crack the mirror.
* Cage hardware: The small 0.050-size screws are notoriously easy to strip, especially with a screwdriver. Use allen wrenches for this, and don't over-tighten.
* Tightening in small spaces: If it's hard to squeeze in an allen wrench, I sometimes use the forbidden technique:
[forbidden technique picture]

---

## Coupling a tapered amplifier

A tapered amplifier

---

## Making a double-pass (cat's eye) AOM setup
