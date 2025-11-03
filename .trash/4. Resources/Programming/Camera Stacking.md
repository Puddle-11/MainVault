---
tags:
  - resource
Area: "[[Programming]]"
---
[[Graphics Programming]]
# Camera Stacking
Camera stacking is a method of setting a camera to overlay and stacking it on top of another camera to render out to the main screen.
While simple in concept, Unity's implementation can have some quirks. When building your project, if you are not on the correct render pipeline sometimes the [[Swap Chain]] will reject the overlay camera and just show a blank screen instead.
## Resources
