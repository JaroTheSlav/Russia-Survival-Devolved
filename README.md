using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false, isGoback = false, isGoToStart = false;
        static string movementChoice, playerClass, classConfirm;
        static int randomItem = 0;
        static Random rng = new Random();
        static void Main(string[] args)
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
            House_Start();
            if (isGopnik == true)
            {
                House_Gopnik();
            }
            else if (isBarbarian == true)
            {

            }
            
            Console.ReadLine();
        }


        static void StartScreen() //Ritar ut en startskärm.
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

        static void Introduction()//Här får spelaren en liten introduktion till spelet samt vilka knappar som behövs för spelet.
        {
            Console.WriteLine("In the Soviet Union people are starving, and you are one of them.\n" +
                "Only the strongest Russians will survive...\n" +
                "The goal with this game is to survive 10 days by any means.\n" +
                "Controls: 1, 2, 3, 4, 5 and enter");
            Console.ReadLine();
            Console.Clear();
        }

        static void NameSelect()//Här får spelaren "välja" namn
        {
            string playerName;
            Console.WriteLine("Before we begin. please enter you name:");
            playerName = Console.ReadLine();
            Console.WriteLine(playerName + " is a bad name. Your name is now Ivan.");
            Console.ReadLine();
            Console.Clear();
        }


        static void Class() //Här får användaren välja vilken klass de vill vara.
        {
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
        static void House_Start()//Oberoende av klass startar användaren på samma ställe, i huset. Här får man välja vart man ska gå.
        {
            Console.WriteLine("In the year 1921, Ivan wakes up in a wreck of a house in Novosibirsk. It's very cold this winter.\n" +
                    "What do you want to do?\n" +
                    "1.Check your nightstand\n" +
                    "2.Go to the kitchen\n" +
                    "3.Go outside");

            movementChoice = Console.ReadLine();
            Console.Clear();
            
        }
        static void House_Gopnik()//Om spelaren har valt klassen Gopnik de dessa resultaten beroende på vad de valde att göra i House_Start.
        {
            if (isGopnik == true)
            {

            
                
                Random rng = new Random();
            
                do
                {
                    Console.Clear();
                    if (movementChoice == "1")
                    {
                        do
                        {
                            Console.WriteLine("You on your left, as you sit up in your bed is a nightstand.\n");
                            Console.WriteLine("You search the nightstand\n");
                            Console.WriteLine("You find: ");
                            LowTierItem();
                            
                        } while (isGoback == true);

                    }
                    else if (movementChoice == "2")
                    {

                    }

                } while (isGoback == true);
            }
        }
        static void House_Barbarian()//Om spelaren har valt klassen Slavic Barbarian får de dessa resultaten beroende på vad de valde att göra i House_Start.
        {

        }
        static void House_Mage()//Om spelaren har valt klassen Crazy Russian Scientist får de dessa resultaten beroende på vad de valde att göra i House_Start.
        {

        }
        static void LowTierItem()//Denna metoden slumpar fram 
        {
            randomItem = rng.Next(1, 6);
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
                case 4:
                    Console.WriteLine("A bent fork");
                    break;
                case 5:
                    Console.WriteLine("One single feather");
                    break;
            }
        }
        static void MidTierItem()
        {
            randomItem = rng.Next(1, 6);
            switch (randomItem)
            {
                case 1:
                    Console.WriteLine("One full bottle of vodka");
                    break;
                case 2:
                    Console.WriteLine("A beet sandwich");
                    break;
                case 3:
                    Console.WriteLine("A jar of babushkas best cookies");
                    break;
                case 4:
                    Console.WriteLine("A rusty military knife");
                    break;
                case 5:
                    Console.WriteLine("A live chicken");
                    break;
            }

        }
        static void HighTierItem()
        {
            randomItem = rng.Next(1, 6);
            switch (randomItem)
            {
                case 1:
                    Console.WriteLine("Two full bottles of vodka");
                    break;
                case 2:
                    Console.WriteLine("A full pot of Borscht");
                    break;
                case 3:
                    Console.WriteLine("");
                    break;
                case 4:
                    Console.WriteLine("An AK-47");
                    break;
                case 5:
                    Console.WriteLine("");
                    break;
            }
        }
    }

   
}
