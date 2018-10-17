Instead of focusing on the smaller refactoring errors, I focused on fixing a larger structural error.
Previously, all the cells contained the knowledge of what Nodes neighbored the Node holding themselves.
This is problematic from a two way dependency standpoint and also made the game classes very messy to write.

So this lab I worked on moving some of the logic regarding the position of cells and nodes from the cell classes into the node classes.
In order to do this I am implementing a super node class and sub node classes for different types of behavior.
For example, static nodes only update themselves internally. 
Moving nodes hold cells that move to other positions throughout the simulation.
AlgoNodes move based on some kind of algorithm. 
The other benefit of this change is that the game classes don't need to have any knowledge of cells anymore.
All they need to look at are the nodes that they are passed. 

These changes are quite fundamental and difficult to change.
However, once they are I think it should make my code much better structured. 