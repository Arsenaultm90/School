
https://docs.godotengine.org/en/stable/
## Collision Objects

There are four kinds of collision objects:  
1. Area2D: Detects overlaps and emits signals  
	Useful for non-physics collision detections  
	Eg. End of level portals, event triggering, item pickups  

2. StaticBody2D: Participates in physics, unmoving  
	No dynamic behaviour, can not be moved  
	Eg. Walls, Floors, Boulders  

3. RigidBody2D: Simulates physics, indirect control  
	Apply forces instead of direct movement  
	Eg. Ragdoll characters, bouncy balls  

4. CharacterBody2D: Code-Controlled Collisions  
	No physics interactions, manually write collision response  
	Eg. Game characters (precise movement)

