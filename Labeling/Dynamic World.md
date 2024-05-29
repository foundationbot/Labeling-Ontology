# Labeling Ontology: Dynamic World
Dynamic World covers labeling for either self-animated objects, or objects that can be manipulated by the bot.

## Label Types
- Segmentation: Highly detailed outlining of both environmental features and objects, with the annotation interior representing the object’s volume.

- Cuboids: 3 dimensional bounding boxes enclosing objects, with XYZ rotation. May be tracked across multiple frames in video data.

## Labeling Guidelines
### Dynamic Labeling Principles
In Dynamic Labeling workflows, you will label clips involving motion through 3-D scenes. These may involve complex environmental geometry, interaction with objects in the scene and other moving objects such as people.
In this labeling ontology, we will cover the principles used to label each of these various objects.

### Labels
#### **Walkable Space**
Walkable space refers to the ground floor that ego is either currently walking through in the clip, or appears to be physically able to access during the duration of the clip.
##### *Geometry Guidelines*
- Do not label floorspace that is occupied by an object above it, such as floorspace directly underneath an object like a desk, table or shelf. This will be considered to be occluded, and *not* walkable space.
- Do label floorspace that is covered in small objects that a human being would be capable of moving, such as garbage bins, bags, loose wires, water bottles, etc...
- Do not label floorspace that is blocked from access by ego in the duration of the clip. For instance, if we can see floor behind a gate or a door with a window, we will not label this as Walkable Space, as ego cannot access this floorspace within the duration of the clip.
- Always attempt to snap the geometry to the most extreme edge possible, err on the side of going over the boundary to capture the most walkable space possible. 
- In cases where floating objects make partial contact (such as table legs, chair wheels, etc..), draw the line straight between the points that touch the floor. Do not trace the underside of these objects.


#### **Person**
Non-Ego human beings who are present in the scene.
##### *Geometry Guidelines*
Persons should be labeled with tracked cuboid annotation. Drop the initial label on the first frame that the person appears, and the tracked label will persist. From this point, you may adjust the cuboid to fit the person, and move with them around the scene.
- Crop the edges of the cuboid as tightly as possible against their outer-most extremities. For instance, if their arm is outstretched far beyond their body, then the furthest most point of that arm should be the boundary for the cuboid in that direction. As the person moves their posture, the cuboid should expand and contract its dimensions to match.
- Persons whose legs are occluded should have the bottom of the cuboid approximated to the location that their feet are most likely to make contact with the floor. While there is some leeway for guesswork, this location must remain consistent over the course of the clip. If there are frames where their feet are visible, match your guess with these visible frames as closely as possible.
