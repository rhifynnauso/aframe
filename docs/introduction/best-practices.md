---
title: Best Practices
type: introduction
layout: docs
parent_section: introduction
order: 11
---

## A-Frame

[ecs]: ./entity-component-system.md
[mixins]: ../core/mixins.md
[template]: https://github.com/ngokevin/kframe/tree/master/components/template/

Some best practices for the framework:

- The core structure of A-Frame is [entity-component (ECS)][ecs]. Place and
  structure application code within purely A-Frame components for reusability,
  modularity, composability, decoupling, encapsulation, declarativeness, and
  testability. It's okay to start out at first using content scripts
  (`<script>`), but look to move towards components.
- [Mixins][mixins] and [templating][template] are useful to reuse and reduce
  repeated HTML.

## Performance

[asm]: ../core/asset-management-system.md
[hardware]: ./vr-headsets-and-webvr-browsers.md
[merge]: ../components/geometry.md#mergeto
[stats]: ../components/stats.md

Performance is critical in VR. A high framerate must be maintained in order for
people to feel comfortable and as if they were in another place. Here are some
ways to help improve performance of an A-Frame scene:

- Use [recommended hardware specifications][hardware].
- Use the **[stats component][stats]** to keep an eye on various metrics (FPS,
  vertex and face count, geometry and material count, draw calls, number of entities). We
  want to maximize FPS and minimize everything else.
- Make use of the **[asset management system][asm]** to benefit from browser
  caching and preloading. Trying to fetch assets while rendering is slower than
  fetching all assets before rendering.
- If using models, look to bake your lights into textures rather than relying
  on real-time lighting and shadows.
- Generally, the fewer number of entities and lights in the scene, the better.
- Make sure your textures' resolutions are sized to powers of two (e.g.,
  256x256, 512x1024) in order to avoid the renderer having to resize the
  texture during runtime.
- Limit the number of faces and vertices on models.
- Some further techniques (not yet documented) include geometry instancing,
  geometry merging, level of detail (LOD).
- When using raycasters or colliders, select which entities are to be raycasted
  against rather than raycasting against every object in the scene.
- When adding continuously running behaviors, use A-Frame component `tick`
  handlers to hook into the global render loop. Use utilities such as
  `AFRAME.utils.throttleTick` to limit the number of times the `tick` handler
  is run if appropriate.

## VR Design

[leapmotion]: https://developer.leapmotion.com/assets/Leap%20Motion%20VR%20Best%20Practices%20Guidelines.pdf
[oculus]: https://developer.oculus.com/documentation/intro-vr/latest/concepts/bp_intro/

Designing for VR is different than designing for flat experiences. As a new
medium, there are new sets of best practices to follow, especially to maintain
user comfort and presence. This has been thoroughly written about so we defer
to these guides. Note that VR interaction design is fairly new, and nothing is
absolute:

- [Oculus Best Practices (for VR)][oculus]
- [Leap Motion VR Best Practices Guidelines][leapmotion]

Some things to note:

- The common golden rule is to never unexpectedly take control of the camera
  away from users.
- Units (such as for position) should be considered meters. This is because the
  WebVR API returns pose in meters which is fed into most camera controls. By
  considering units as meters, we achieve expected scale.
