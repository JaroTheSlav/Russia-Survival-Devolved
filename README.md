using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false;
        static void Main(string[] args)
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
            House();
            Console.ReadLine();
        }


        static void StartScreen()
        {
            Console.ForegroundColor = ConsoleColor.Yellow;
            Console.BackgroundColor = ConsoleColor.DarkRed;
            Console.Clear();
            Console.WriteLine("------------------------------------------------------------------------------------------------------------------------");
            Console.SetCursorPosition(1, 8);
            Console.WriteLine
               ("                                     [][][]   []  []   [][][]   [][][]  []    []  \n" +
                "                                      []   []  []  []  []       []       []   [][] \n" +
                "                                      []   []  []  []  []       []       []  []  []\n" +
                "                                      [][][]   []  []   [][]     [][]    []  []  []\n" +
                "                                      [] []    []  []       []       []  []  [][][]\n" +
                "                                      []  []   []  []       []       []  []  []  []\n" +
                "                                      []   []   [][]   [][][]   [][][]   []  []  []\n");

            Console.WriteLine
                ("                                                    Survival Devolved");
            Console.SetCursorPosition(0, 23);
            Console.WriteLine("------------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("                                                <Press enter to continue>");
            Console.ReadLine();
            Console.Clear();
        }

        static void Introduction()
        {
            Console.WriteLine("In the Soviet Union people are starving, and you are one of them.\n" +
                "Only the strongest Russians will survive...\n" +
                "The goal with this game is to survive 10 days by any means.\n" +
                "Controls: 1, 2, 3, 4, 5 and enter");
        }

        static void NameSelect()
        {
            string playerName;
            Console.WriteLine("Before we begin. please enter you name:");
            playerName = Console.ReadLine();
            Console.Clear();

            Console.WriteLine(playerName + " is a bad name. Your name is now Ivan.");
            Console.Clear();
        }


        static void Class()
        {
            string playerClass, classConfirm;
            

            do
            {
                Console.Clear();
            Console.WriteLine("What is your class, Ivan?\n1. Gopnik\n2. Slavic Barbarian\n3. Crazy Russian Sceintist");
            playerClass = Console.ReadLine();
                Console.Clear();

                if (playerClass == "1")
                {
                    Console.WriteLine("You may not be the strongest, or the biggest but you sure are the most agile.\n" +
                        "You have mastered the art of stealth and stealing, all through the power of your Abibos Tracksuit.\n" +
                        "Strength: 4\nAgility: 10\nIntelligence: 6\n" +
                        "Are you sure you want to be a Gopnik?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();
                    
                    if (classConfirm == "1")
                    {
                        isGopnik = true;
                    }
                    else
                    {
                        isGopnik = false;
                    }

                }
                else if (playerClass == "2")
                {
                    Console.WriteLine("Throughout your whole life, you have solved every problem with violence.\n " +
                        "Simply put, you are an extremely strong, dumb, slavic barbarian.\n" +
                        "Strength: 10\nAgility: 2\nIntelligence: 3\n" +
                        "Are you sure you want to be a Barbarian?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();
                    if (classConfirm == "1")
                    {
                        isBarbarian = true;
                    }
                    else
                    {
                        isBarbarian = false;
                    }
                }
                else if (playerClass == "3")
                {
                    Console.WriteLine("You used to be the top of your class, but you lost everything\n" +
                        "when you used your intelligence to create chemical weapons.\n" +
                        "Strength: 2\nAgility: 4\nIntelligence: 10\n" +
                        "Are you sure you want to be a Crazy Russian Scientist?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();
                    if (classConfirm == "1")
                    {
                        isScientist = true;
                    }
                    else
                    {
                        isScientist = false;
                    }
                }

            } while (isGopnik == false && isBarbarian == false && isScientist == false); 
        }
        
        static void House()
        {
            string actionChoice;
            Random rng = new Random();
            int randomItem = 0;

            Console.WriteLine("In the year 1921, Ivan wakes up in a wreck of a house in Novosibirsk. It's very cold this winter.\n" +
                "What do you want to do?\n" +
                "1.Stay in your bedroom\n" +
                "2.Go to the kitchen\n" +
                "3.Go to the living room\n" +
                "4.Go outside");
            
            string movementChoice = Console.ReadLine();
            Console.Clear();
            if (movementChoice == "1")
            {
                Console.WriteLine("Your bedroom is very simple and conatins only a bed, a nightstand and a closet.");
                if (isGopnik == true)
                {
                    Console.WriteLine("What would you like to do?\n" +
                        "1.Check your bed\n" +
                        "2.Check your nightstand\n" +
                        "3.Check you closet\n" +
                        "4.Go back");
                    actionChoice = Console.ReadLine();
                    Console.Clear();
                    if (actionChoice == "1")
                    {
                        Console.WriteLine("You find:" +
                            "s" +randomItem);

                            
                        randomItem = rng.Next(1, 4);
                        switch (randomItem)
                        {
                            case 1:
                                Console.WriteLine("One almost empty bottle of vodka");
                                break;
                            case 2:
                                Console.WriteLine("Half a can of tuna");
                                break;
                            case 3:
                                Console.WriteLine("Half a ball of yarn");
                                break;
                        }
                    }
                    else if (actionChoice == "1")
                    {
                        Console.WriteLine("You find:" +
                            "s" + randomItem);


                        randomItem = rng.Next(1, 4);
                        switch (randomItem)
                        {
                            case 1:
                                Console.WriteLine("One almost empty bottle of vodka");
                                break;
                            case 2:
                                Console.WriteLine("Half a can of tuna");
                                break;
                            case 3:
                                Console.WriteLine("Half a ball of yarn");
                                break;
                        }
                    }
                    else if (actionChoice == "1")
                    {
                        Console.WriteLine("You find:" +
                            "s" + randomItem);


                        randomItem = rng.Next(1, 4);
                        switch (randomItem)
                        {
                            case 1:
                                Console.WriteLine("One almost empty bottle of vodka");
                                break;
                            case 2:
                                Console.WriteLine("Half a can of tuna");
                                break;
                            case 3:
                                Console.WriteLine("Half a ball of yarn");
                                break;
                        }
                    }

                }
            }
        }
    }
}
