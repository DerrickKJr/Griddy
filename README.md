# Griddy
Top-Down Tile Manager Script:
Open-Source Project Documentation
This document serves as the official guide for the open-source Unity Grid Manager project. It details the functionalities, usage, and key parts of the Grid Manager system, which allows for placing and removing objects on a grid in Unity. Developers can use, modify, and expand upon this system freely.
1.	Overview of Classes and Variables
The two main classes in this script are the `Element` and `GridManager` classes.
•	`Element`: Represents a single position on the grid. It contains a 2D position (Vector2) and a reference to the `GameObject` placed at that position.
•	`GridManager`: Manages the entire grid system, including placement, removal, and checking boundaries of objects on the grid. It tracks the dimensions of the grid and stores all placed elements.
2.	GridManager Variables Breakdown
The following are key variables in the `GridManager` class:
•	`width` and `height`: Represent the grid's dimensions, calculated from the BoxCollider2D size.
•	`origin`: Stores the bottom-left corner of the grid, ensuring objects are placed relative to the grid's center.
•	`gridOccupancy`: List of `Element` objects representing which cells on the grid are occupied.
•	`bounds`: Refers to the BoxCollider2D, which helps determine the grid's boundary and size.
3.	Grid Initialization in Start Method
In the `Start()` method, the following initialization happens:
•	The grid dimensions are derived from the BoxCollider2D's size.
•	The grid's origin is calculated based on the grid's width and height. This ensures that the grid is centered.
•	The grid's background (`SpriteRenderer`) is resized to match the calculated grid size, providing a visual indication of the grid area.
4.	Adding Structures to the Grid
The `AddToGrid()` method handles placing structures on the grid. Here's how it works:
•	It first checks if the mouse's world position (`wmp`) is within grid bounds using the `InBounds()`method.
•	It then checks whether the grid cell (based on the rounded world mouse position `rwmp`) is already occupied.
•	If the cell is unoccupied, it instantiates the selected structure at `rwmp` and adds this structure to the `gridOccupancy` list.
5.	Removing Structures from the Grid
The `RemoveFromGrid()` method manages structure removal. It works by:
•	Locating the structure at the grid cell corresponding to the rounded world mouse position (`rwmp`). 
•	If a structure exists at that position, it is destroyed, and the corresponding `Element` is removed from the `gridOccupancy` list.
•	If no structure is found, a message is printed to the console.
6.	Checking Bounds with InBounds Method
The `InBounds()` method is responsible for determining if the world mouse position (`wmp`) falls within the grid's boundaries. This ensures that players cannot place structures outside the grid, maintaining the system's integrity.
7.	Player Script Overview
The Player script is how the user interacts with the grid system. Key aspects:
•	`mp`: Mouse position in screen space. While this was used initially, the rounded world mouse position (`rwmp`) is enough for grid operations.
•	`wmp`: World mouse position derived from the screen position. This is converted into world space coordinates for grid placement.
•	`rwmp`: The rounded world mouse position, used to snap structures to the nearest grid cell.
•	The `AddToGrid()` and `RemoveFromGrid()` methods are called based on user input (mouse clicks).
 
8.	Next Steps and Enhancements
Possible enhancements to this system include:
•	Grid Visualization: Add grid lines to help players visualize the grid layout.
•	Snapping Feedback: Implement visual feedback that shows where a structure will be placed before clicking.
•	Customizable Grid Sizes: Allow developers or players to modify the grid's size and origin point dynamically.
•	Undo/Redo System: Implement an undo/redo system to give players flexibility in placing and removing objects.
![image](https://github.com/user-attachments/assets/91bac3b0-163e-4471-9ec5-46858adb51f5)

