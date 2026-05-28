---
title: "Compass"
date: 2026-05-28T17:30:49-04:00
draft: false
---

When I studied graphic design in college, we were taught structure.

We learned proportion, grid systems, alignment, hierarchy, and intentionality.

Then we opened the software, and all of that disappeared.

Whether it’s Illustrator, Figma, or open-source alternatives like Inkscape, traditional 2D vector software does not actually understand design principles. It hands you an unopinionated Bézier spline and treats you like a digital painter. You spend hours manually nudging handles and anchor points, trying to force precision out of tools that were never structurally aware to begin with.

A point is always slightly off. Complex booleans become destructive. The workflow slowly collapses into hacks and cleanup.

To compensate for this, modern design software relies heavily on Smart Guides, snapping systems, and temporary canvas guides. But these are not actual structural relationships. They are visual training wheels.

A guide is not a relationship.

Most guides only help align shapes relative to the canvas itself. They do not establish persistent rules between the objects in your design. If two shapes should remain tangent, concentric, proportionally linked, or mathematically dependent on one another, the software has no real understanding of that relationship. The designer is expected to manually maintain it forever.

The revelation for me did not come from 2D design.

It came from learning Autodesk Maya.

In 3D, working with NURBS (Non-Uniform Rational B-Splines) introduces a completely different philosophy. 3D software understands construction history and parented relationships. If you generate a surface from a curve, the software remembers the connection. Modify the curve later, and the surface updates automatically.

The relationship persists.

So why did 3D software figure out relational workflows decades ago while 2D graphic design remained trapped in the digital painting era?

## Introducing Compass

Compass brings the philosophy of 3D rigging and construction history into 2D vector design.

I am not building this because I am obsessed with pure mathematics. I am building it because I want design tools where structure exists by default instead of being simulated through manual adjustment.

In Compass, you do not just draw disconnected paths.

You establish relationships.

Drop two points. Anchor a circle to them. Move one point, and the circle recalculates perfectly. Attach a curve to a proportional scaffold, and the geometry updates automatically as the scaffold changes. The design behaves less like illustration and more like a live rig.

This enables a fully parented boolean workflow.

Instead of destructively cutting shapes apart with tools like Shape Builder, where the original curves are permanently lost,Compass treats boolean operations as live relationships. Shapes belong to procedural groups performing Union, Subtract, or Intersect operations continuously in real time. The visible result is always generated dynamically from the structure beneath it.

{{< figure src="compass2.png" title="Early UI: A complex shape built using a parented boolean workflow. Notice the constructor shapes." width="750px" >}}

To support this workflow, Compass introduces Constructor Shapes.

Instead of eyeballing curves or dragging temporary guides across the canvas, designers can place structural systems directly into the document itself,Golden Spirals, proportional scaffolds, radial systems, and constraint paths. These act more like rigs than visual overlays. They do not need to appear in the final export; they exist purely as invisible governing structures that drive the visible geometry attached to them.

Once the structure is complete, the scaffolding can simply be hidden.

{{< figure src="compass.png" title="The exact same setup with the scaffolding toggled off. A clean final form generated entirely from relationships and constraints." width="750px" >}}

## Rethinking the Engine

The interface shown above is still an early developer preview. The engine underneath it is what actually matters.

Building Compass requires abandoning how traditional 2D software handles geometry and memory.

In standard vector editors, deleting a shape simply removes a path. In Compass, deleting a shape is closer to deleting a node in Maya. The engine has to traverse a dependency graph, determine whether underlying points are still acting as load-bearing anchors for other geometry, and safely untangle those relationships before anything can be removed.

The document is no longer a flat collection of paths.

It is a live relational rig.

What we learn in design school, structure, proportion, intent, and systems, should exist inside the software itself.

Compass is an attempt to build a vector engine that finally understands that.