Help
=============================================================================

Mabioned provides an easy to use UI to modify region and area files,
but has only few features that go beyond editing raw values at this
point in time. This file gives you some basic information necessary
to utilize this application.

Take a look at the other documentation files as well to learn more
about Mabioned.

Terminology
-----------------------------------------------------------------------------

### Region

Mabinogi's world is made up of regions, which are in turn made up of
Areas. The region files in themselve contain only general information
about a region, such as lighting, and a list of area files that are
part of it.

### Area

Areas contain the more substantial information about a Region,
such as props, events, and the terrain. They can be edited on their
own, but need to be placed in a Region.

### Entity

Entities are things that are placed in an Area. They include Props
(such as trees), Events that make something happen when a player
enters them for example, and even players themselves.

### Prop

Every object in the world is a Prop. Examples are trees, houses, statues,
chairs, and so on. Many props can be interacted with, allowing players
to punch or touch them. Officially their behavior is controlled by
parameters in the area files, but server emulators such as Aura
might not actually use this information.

### Event

An event is an area in a region where something happens under
certain circumstances, for example when entering or leaving it.

They typically consist of only one rectangular Shape and are used
to control the background music, show notices telling players where they
are, provide warp locations for the official servers, and more.

### Shape

Shapes give props and events their form, controlling their collision
or in which section of a Region an Event should be triggered. Any prop
and event can be made up of several shapes, which are always rectangular.

Some props don't have shapes, which means you can walk through them.
Due to the application currently basing all rendering on those
shapes such entities are represented by circles.

### Parameter

Props and events often times contain information in form of parameters
that tell the official clients and servers what to do with them.
These paramaters usually have a type descriping what type of parameter
it is, a signal type that controls when something should happen, and an
XML object for additional information, such as which track to play
when entering a town.

### Area Plane/Plane/Sqare

Area planes, planes, and squares are the part of the area that contains
the terrain information. To put it another way, the height map and
texture information are saved here. This part of the region files
hasn't been fully researched yet.

Application Window
-----------------------------------------------------------------------------

```
-----------------------------------------------------------
|                           1                             |
|---------------------------------------------------------|
|                  |                                      |
|                  |                                      |
|        2         |                                      |
|                  |                                      |
|                  |                  4                   |
|                  |                                      |
|------------------|                                      |
|                  |                                      |
|        3         |                                      |
|                  |                                      |
|---------------------------------------------------------|
|                           5                             |
-----------------------------------------------------------
```

- 1: Main Menu and Toolbar.
- 2: Tree, displays Region, Areas, Props, and Events in a tree structure.
- 3: Property Window, displays properties of the currently selected
  object in the Tree and allows editing them.
- 4: Map, displays the currently open Region or Area.
- 5: Status Bar, provides information like coordinates the mouse points
  at or the current scale the map is displayed with.

Unknown properties
-----------------------------------------------------------------------------

When opening a region or area file you will likely notice some properties
with names like "Unk3", "Unk4", etc. These are values in the files which's
purpose is currently unknown. They are displayed only to give full access
to the file's information, and modifying them might have unexpected
consequences.

Auto-updating properties
-----------------------------------------------------------------------------

In its current form Mabioned provides easy access to all of a region's
data and properties, and technically *everything* about a region can
be modified, but comfort features are still being added.
For example, you could modify the terrain and its textures, but you'd
have to modify all values by hand.

Here's some things the application currently does automatically for you.

### Position and Rotation

If you modify an entity's position or rotation, its shapes' positions,
rotations, and bounding boxes are updated as well, as you would expect.

### Ids

If you modify a region's or area's ids the change is reflected in all
areas and it's entities, updating region, area, and entity ids.

Reloading Regions
-----------------------------------------------------------------------------

Since the client is loading the regions on demand when you enter them
it's possible to modify and reload a region during run-time. To do this
you need to put the region you want to edit into your data folder and
modify your client to load the region from there. If you edit it now,
leave the region, and enter it again, the client will load your changes.
In a server emulator like Aura you might also have access to a refresh
command that makes this process easier.

Beware that reloading small changes works great, but bigger changes
sometimes crash the client when you re-enter the region. Simply start
the client again in that case, you should be able to enter the region
without problems after the restart.

Data Folder
-----------------------------------------------------------------------------

Mabioned optionally uses information from Mabinogi's client to display
prop names, provide advanced search and filtering, render minimap background
images, and more. To use these features you need to specify the location
of an extracted data folder, which you can set under
"Edit > Settings > Folders".
