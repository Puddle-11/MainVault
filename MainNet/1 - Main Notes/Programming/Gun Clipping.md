2025-07-15 20:46

Status: #alpha 

Tags: [[Programming]]

## Gun Clipping
Gun clipping is an issue that happens a lot in early development for FPS games. While less prevalent in 3rd person. The gun extends from the player model and collider so when the player is up against a wall the gun will *clip* into the wall. 

A common solution for this is to have 2 cameras, one to render the scene, the "base" camera. and one to render the gun and other things that should be always on top. In unity there's something called an overlay camera. which will render a scene and overlay its output + alpha onto another cameras output, which then gets rendered to the screen, or [[Swap Chain]]. 


## References
