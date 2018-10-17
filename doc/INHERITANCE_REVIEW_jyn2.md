NetId: jyn2 my partner left before I could get his net id

# Part 1

1. My cell classes encapsulate decisions and the data relevant to those decisions. 
Once they are passed the information they need about the surrounding cells, the cells' update methods can be called by outside classes that know nothing about the cells themselves.

2. The cell inheritance hierarchy is a super class abstract cell which is extended by other particular cells.
In some cases, like water world with sharks and fish, there is an intermediary super class between cell and the final implemented cell.
This is due to similarities between shark and fish behavior. 
For the main cell super class, the behavior that it is built around is the the update method which determines what cell the current cell should be replaced with next round.

3. Some of the qualities that are closed is the types of data needed and used by cell classes.
They all use a map of their neighbors and need to be able to get access to their neighbors.
They also all need to be able to hold a javafx shape and store the cell that will replace them next round.
The open portion is the implementation of the class update method which changes for each subclass.
Also the construction of the map that holds the neighbors of each object changes based on each simulation.

4. My section shouldn't have to handle errors for the most part.
The user provided information should be checked before being used to initialize the simulation related objects.

5. My design is good because it is flexible. 
If the rules of the game are changed it is very easy to create a new cell subclass.
In that new class I would only need to change the update method to change the simulation.
If the rules of adjacency are changed, it would be easy to add new cells to the neighbors map.

# Part 2

1. My part relies upon the the data provided by the file reader class. 
My cell classes are used by the GUI and game loop portion of the project.

2. My classes are only really dependent upon behavior because all they need is to provided certain types of data.
As long as the reader class provides the necessary info, it doesn't matter how it is implemented.

3. The dependency is minimized by ensuring that everything possible is kept private.
This way there isn't dependency except between a few particular methods.
Also, information is passed through parameters where needed making the dependencies clear.

4. My super class cell and the game of life cells seem to structured well as possible. 
There isn't much more that can be done.

# Part 3

1. The cell classes don't really change based on user input. 
The only thing that changes is what cell class is used and how many cells to create.
I in some cases the parameters also change, like the chance of fire spreading. 

2. I'm most excited by implementing the cell logic for how to update cells.

3. I'm most worried about implementing the section that stores new cell assignments and updates them later.