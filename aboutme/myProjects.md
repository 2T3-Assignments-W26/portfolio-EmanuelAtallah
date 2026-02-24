# Project 1: Pacman-Style Survival Game in C#

### Project Description
This project is a console-based Pacman-Style survival game developed in C#. The player navigates around the map while being chased by monsters. The objective is to collect coins while avoiding monsters and surviving with three lives.

Special mechanics in this game include:
* The player has **3 lives**
* Monsters actively chase the player
* Stepping on a **key** eliminates one monster
* After each round, **3 new monsters** spawn
* A maximum of **10 monsters** can exist on the field at once

The game increases in difficulty as more monsters are added after each round, creating a progressive challenge system.

### Techologies Used
* C#
* Visual Studio
* .NET Console Application
  
### Code Snippets from the project
```C#
static void KillRandomMonster(int plateIndex)
{
    if (currentMonsterCount <= 0) return;

    // pick a random active monster index
    int found = rng.Next(0, currentMonsterCount);

    // remember the tile to clear (the monster being removed)
    int removedX = monsterX[found];
    int removedY = monsterY[found];

    // remove monster at index 'found' by swapping with last active monster
    int last = currentMonsterCount - 1;
    if (found != last)
    {
        monsterX[found] = monsterX[last];
        monsterY[found] = monsterY[last];
        oldmonsterX[found] = oldmonsterX[last];
        oldmonsterY[found] = oldmonsterY[last];
        monsterMoveInterval[found] = monsterMoveInterval[last];
        monsterMoveCounter[found] = monsterMoveCounter[last];
    }

    // clear last slot
    monsterX[last] = -1;
    monsterY[last] = -1;
    oldmonsterX[last] = -1;
    oldmonsterY[last] = -1;
    monsterMoveInterval[last] = 0;
    monsterMoveCounter[last] = 0;

    currentMonsterCount = Math.Max(0, currentMonsterCount - 1);

    // ensure the removed monster's glyph is erased from the console (only if not dashboard)
    if (removedY != dashboardY && removedX >= 0 && removedX < Console.WindowWidth && removedY >= 0 && removedY < Console.WindowHeight)
    {
        Console.SetCursorPosition(removedX, removedY);
        Console.Write(" ");
    }
}
```
```C#
static void cleanupmonsterposition()
{
    for (int i = 0; i < currentMonsterCount; i++)
    {
        if (oldmonsterX[i] >= 0 && oldmonsterX[i] < Console.WindowWidth && oldmonsterY[i] >= dashboardY + 1 && oldmonsterY[i] < Console.WindowHeight)
        {
        Console.SetCursorPosition(oldmonsterX[i], oldmonsterY[i]);
        Console.Write(" ");
        }
        if (monsterX[i] >= 0 && monsterX[i] < Console.WindowWidth && monsterY[i] >= dashboardY + 1 && monsterY[i] < Console.WindowHeight)
        {
                    Console.SetCursorPosition(monsterX[i], monsterY[i]);
                    Console.Write(monsterchar);
        }
    }
}
```
### Screenshots from the project

![Image](.\Startupscreen.png)
![Image](.\Gameplay.png)

### What I learned
Through this project, I learned how to build game mechanics using loops and conditional logic. I improved my understanding of object-oriented programming by managing monsters, player mouvement, and game states seperately.

I also learned how to:
* Handle real-time input using keyboard controls
* Manage collision detection
* Implement increasing difficulty through enemy spawning logic
* Control game flow with rounds and life systems

# Project 2: Business website (fictional) built from WordPress

### Project Description
This project is a fully functional business website using WordPress. The website was created using built-in themes and plugins without writing custom HTML or CSS

The site includes:
* Home page
* About page
* Services page
* Contact form
* Navigation menu

The objective of this project was to understand how content managment systems work and how to build and manage a professional website.