# DroneWars

I will give information about my main project named “Drone Wars” during the internship I made in Beren Studio.
Drone Wars is a 3D-VR first person shooter game made in Unity. 

# Main Idea

Firstly, the idea was, for a PC player to shoot the drones that attack in various ways with a gun while hiding behind the walls. 
We, me and my team mate, first created a PC player and built 5 different guns, 5 different drones, 3 explosion effects, environment, enemy guns, and various UI components. 
In the last 2 weeks, we tried to convert a PC player project into a VR project.

# PC Player

While creating pc player we first made the main camera become the child of the PC player. This enabled us to create a first-person view. After that, we added a character controller, capsule collider, and rigid-body component to the PC player. We arranged the character controller attributes accurately; slope limit, step offset, skin width, min move distance, center, radius, and height. These are for the movement of the pc player. Then, we added a player movement script for arranging the relation between the input and the movement, which are right-left movement and crouching movement. 

For arranging looking around to the direction of the mouse, we added a look-around script. We also limited the vertical and horizontal rotation of looking around movement.

# Weapons

We built 5 different guns: an M1911 handgun, grenade launcher, machine gun, rocket launcher, and shotgun. We implemented 5 different shooting mechanisms for each of them.  
We also built a weapon-switching mechanism and inventory system that shows the order of the guns.  

Before creating the weapons, we needed to add a crosshair to know where we were aiming. We added canvas and arranged its scale as “scale with screen size” to make the crosshair centered.  Then we added a crosshair image to the canvas pivoted in the center. 

After we chose which approach to use, we created a bullet prefab and added a rigid body, sphere collider, and line renderer to it. We removed the gravity and arranged Interpolate as interpolate and collision detection as continuous dynamic. To achieve greater accuracy when simulating fast-traveling bullets, we have implemented these fine adjustments to our solution. After these arrangements, we added a gun script to our handgun and a bullet projectile script to the bullet prefab. However, while writing our script we used Instantiate and Destroy methods very frequently as we used prefabs. This usage was very costly. Because of that we used the pool mechanism instead of Destroy and Instantiate. 

We also implemented a reload mechanism and a simple animation of it. We used the Lean Tween package of Unity to make a simple animation of the reload operation. 
If “R” is pressed, then the coroutine Reload function would be called.  

# Drones

We have implemented 5 different kinds of drones having 3 movement features: standing, running, and rotating. Drones are health drones, enemy drones, bomb drones, normal drones, and AI drones.  Health and enemy drones are both standing and rotating. The bomb drone is running, and the normal drone is both rotating and running. AI drone is not doing a specific movement, its movement is random. We have prepared the drones to appear at regular intervals, and standing drones also appear at various locations at specific time intervals. AI and enemy drones also shoot the player using their bullets.  
While implementing these drones we did not use prefabs, we used a pool mechanism.  

The bullet mechanism of the enemy and AI drones are like the guns. In addition to these features, shooting a drone increases the score by 5, and shooting the health drone increases also the health of the player. We wanted to give the player the feeling of gaining health, so we added a simple animation when we shot the health drone. A huge plus-signed object is approaching the PC player, when we shoot the health drone.  

Finally, when we shoot the bomb drone, it can destroy objects located within a specified radius. The points of the destroyed objects are calculated together and added to the total score. If the health drone is in the specified radius, the health of the player also increases.  

# UI And Extras

In our game, the player, enemy drone, and AI drone have a health bar of their own. According to the player’s damage, the health of the drones is decreased. The damage of the drones is the same. 

We also created canvas for score text which counts the points you get by destroying the drones, combo text which increases the score point you get by destroying the drones if you hit 5 drones repeatedly without missing and ammo text which shows how much ammo you have left, for every weapon it has different value. We arranged these in the game manager-script. 

In addition to those features, we have also implemented an explosion effect which differs for some drones. For example, if you destroy AI, enemy, or normal drones it has a default explosion effect. If you destroy a health drone, a green explosion effect will be seen, and a bomb drone has a blue explosion effect. The explosion effect is also made using a pool mechanism.  

# Efficient Coding

For efficiency, we made a game manager a singleton and in the game manager, we implemented the set and got functions of the combo, health, and the score of the player. In the context of the Singleton design pattern, only one instance of the class is created and shared throughout the application. 

In addition to that, we have created a game parameter script. We created it as public static and all the variables as public const. Hence, the script can be reached by every other script. We had stored the literals and some constant numbers as a variable for refrainment from using them directly.  

We also created a Tag holder script for storing the tag names. The reason and the implementation are the same as the game parameter script. 


# VR Player

In the last 2 weeks, we added some extra features to our PC player but, our focus was to convey the game to the VR player. We had created another drone wars project and installed a VR extension to it. We transformed our assets into the VR player project and pressed the build and run button. After changing some inputs to make our game playable in the VR, our job was over. For example, instead of checking whether we pressed the left click of the mouse or not, we checked the input according to the VR console. 

![drone_wars](https://github.com/beyzacapraz/DroneWars/blob/main/image%20(1).png?raw=true)
