[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=9820682&assignment_repo_type=AssignmentRepo)

# Combat Chaos (Text-based RPG)
  
Authors: [Davis Kim](https://github.com/daviskimCS), [Lauren Tomasi](https://github.com/ltoma001), [Jahnavi Naik](https://github.com/jahnavi-naik), [Arun Chacko](https://github.com/arunchacko1)

## Project Description
In our proposed text-based strategic combat game, users will choose among different the character classes: rogue, tank, or fighter. Each of these character classes are associated with different sets of statistics: health, speed, strength. After choosing their class, the player is presented with some beginner level items that they choose from. At each turn of a given game, a narrative is presented and the user is thrown into battle and can select between the different options: attack, defend, and dodge. At the end of each battle, additional items will be presented for the user to choose from. These items provide the player with permanent statistical buffs that will help them take down future enemies.

Why is it important or interesting to you?
- This project is important to us because we are excited to learn about completing a project as a team using topics we are currently learning and have learned about. This project is interesting because, like many others, some of us group members enjoy playing video games during our pass time.

What languages/tools/technologies do you plan to use?
- The language we plan on using is mainly C++ to utilize Object Oriented Programming with things such as classes and inheritance to implement our characters.
- We used Valgrind as a way for us to debug our code.
- We used GTest to create unit tests.

What will be the input/output of your project?
- We will get user input from the command line and output text to prompt the player through fights and to continue the game.


What are the features that the project provides?
- Entertainment.
- Human-computer interaction.
- Inheritance & polymorphism.
- Encapsulation
- Abstraction

## Class Diagram 
![image](https://user-images.githubusercontent.com/93836665/222857677-5018d3fb-7f38-4673-9b84-96e33967bfbe.png)

**Class Diagram Description:**
For the game to start, an instance of the game class is created. The startGame() function will create an instance of the Player class, which inherits from the character class, and stage class. The main plot will be split up into multiple instances of the stage class with differing names, attributes, and following stage classes. When the Player moves to a new location, the stage class would update the current location of the Player and the Player would be able to use the displayInfo() function to show the new location's name and description as well as the current experience and inventory.

Progressing in the game is shown through an instance of the stage class. Certain stages will create an instance of the combat class, which inherits from the stage class. Each combat will create an instance of exactly one enemy, which inherits from the character class. There will be multiple enemies that the Player has to battle against as they progress through the game with certain items allocated to the Player’s inventory after each battle. In combat, different statistics of the Player and enemy, such as their respective health, strength, speed, attack, and used item type, will be considered to find the outcome of each turn of the battle. The combat class has methods for managing the different mechanics, such as calculateDmg() and Outcome() to process the final result of the combat instance. 

The character base class has methods like attack() and defend() for the Player and enemy class that are only used during combat. The battle has finished once either the layer or enemy’s character health statistic is below 0, triggering the combat instance to conclude. Depending on which character’s health was lowered below zero, will progress to the game to the next stage or end the game. The player class also has method showInventory() to display all the available items that a player has. 

The Player class will have a private pointer to an Inventory class when instantiated. The Inventory class will have the functions that allow the Player class to interact with the Inventory, such as addItem(Item) and useItem(). The Inventory class will have a vector of the Item class which will hold the Items that will be given and gained from the Player progressing. These items will have different names, descriptions, types, and magnitudes that will vary depending on which is used and can be displayed upon call from the Player class.

For every stage, there is a possibility of the player encountering items. To handle which items the player has, we create an instance of the Inventory class to hold the instances of the Item class. The item class interacts with the player class, using the method useItem() to apply the effects of an item when used. This will be used outside of combat and will have permanent effects on the player’s character health, strength, speed, and attack stats. 
 
 ## New Class Diagram (Considering Solid Design Principles)
 ![Milestone #2_ UML Class Diagram](https://user-images.githubusercontent.com/93836665/222854063-f1855771-0e6c-4a36-af1a-a51c24241f56.png)
 
Single Responsibility Principle: Added a vector of type Item to organize the items within the Inventory class. Added method isEmpty() to check if a player doesn’t have any items within the Inventory class. This was almost implemented into what was previously removeItem() to useItem() to account for a player having more than one of the same type of item within the Inventory class.
The Combat class has a single responsibility of handling combat between two characters. It does not handle any other responsibilities such as managing game state or interacting with the user. This makes the class easier to maintain and test. Each of the private functions in the combat class has a single responsibility: compareSpeed() compares the speed of two characters, calculateDmg() calculates the damage dealt by a character, and setParticipants() sets the participants of a combat encounter. These functions don't try to do anything more than what their name suggests.

Dependency Inversion Principle: Changed parameter for useItem() from type Item to string to account for user input within the Player class. This helps prevent the method from relying too heavily on properly interacting with the Inventory and Item classes, which are lower in level. The handling for matching happens down the stream by functions that are already built to handle a parameter of type string, allowing for looser coupling between the classes.

Open/Closed Principle: Added a vector of type Item to represent what items a player could potentially pick up from a stage within the Stage class. Allows a developer to update what items are available on a certain stage, extending upon what is already written. The developer is able to do so without modifying the class directly, allowing for the possibility of another developer to update what items are available on a different stage while maintaining the code’s stability.

Interface Segregation Principle 
The Combat class has a simple and clear interface that only includes the necessary public methods for handling combat. We didn’t include any unnecessary methods or properties that were not directly related to combat. By using the ISP, we can make the class more focused and easier to use in game. 

 ## V1.0.0 Class Diagram
 ![image](https://user-images.githubusercontent.com/93836665/225830734-ed5b155f-ea3a-4a10-9945-0d20df873a8d.png)
 
 ## Screenshots
![image](https://user-images.githubusercontent.com/93836665/225844541-09eb1e95-1c9e-460d-b687-e06611731e22.png)
![image](https://user-images.githubusercontent.com/93836665/225844549-262f7031-6b05-45d1-8dcf-898cadc68a59.png)

 ## Installation/Usage
To install our project, you would need to download the project as a zip file or use git. To download as a ZIP file, select "Download ZIP" and save the file to their computer. Once the file is saved, extract the contents of the ZIP file to a folder of your choice. To download using git, copy the repository's URL from the dropdown menu and use git commands to clone the repository to their computer. For example, you use the command "git clone https://github.com/cs100/final-project-cs100-pg.git" to download the repository. Once you have done that, you can run "cmake ." and "make" in your terminal to create the executable needed. Then run "./BuildV1.0.0" to start playing!
 ## Testing
 Our project was tested and validated using GoogleTest and Valgrind. These two tools used in combination allowed for us to get our desired output, data management, and execution. Below are screenshots of are test suites and Valgrind report after running our Build V1.0.0 executbale.
 
![image](https://user-images.githubusercontent.com/93836665/225844243-d4272c13-e2bb-4b28-bdb1-a0ff7c0076c3.png)
![image](https://user-images.githubusercontent.com/93836665/225844286-3eecae37-e721-41db-9858-74ece9c6ccc7.png)
![image](https://user-images.githubusercontent.com/93836665/225844302-5c5f4af6-596c-4830-ba3b-1373d63f8549.png)
![image](https://user-images.githubusercontent.com/93836665/225844319-d979e230-6f01-4615-a919-bde5050b9b23.png)
![image](https://user-images.githubusercontent.com/93836665/225844340-5d83f354-0b1a-48ed-9228-dc00a5bf244b.png)
![image](https://user-images.githubusercontent.com/93836665/225844371-295ccacb-c497-4503-baa0-2010f224e345.png)
![image](https://user-images.githubusercontent.com/93836665/225844390-39bbb5a2-aa35-490a-968f-1f7f8f9d263f.png)
