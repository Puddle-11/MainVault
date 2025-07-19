2025-07-15 20:52

Status: #alpha 

Tags: [[Programming]] [[Graphics]]

## Camera Stacking
Camera stacking is a method of setting a camera to overlay and stacking it on top of another camera to render out to the main screen.
While simple in concept, Unity's implementation can have some quirks. When building your project, if you are not on the correct render pipeline sometimes the [[Swap Chain]] will reject the overlay camera and just show a blank screen instead.

## References
[Camera Overlays](https://docs.unity3d.com/2023.2/Documentation/Manual/cameras-overlay.html)
[Camera Stacking](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@7.2/manual/camera-stacking.html)
