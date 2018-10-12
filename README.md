using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false, isGoback = false, isGoToStart = false;
        static string movementChoice, playerClass, classConfirm;
        static int randomItem = 0, HP = 100;
        static Random rng = new Random();
        static void Main(string[] args)
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
            Start();
            if (isGopnik == true)
            {
                House_Gopnik();
            }
            else if (isBarbarian == true)
            {
                House_Barbarian(); 
            }
            else if (isScientist)
            {
                House_scientist();
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
                "The goal with this game is to get to babushkas house.\n" +
                "Controls: 1, 2, 3, 4, 5 and enter");
            Console.ReadLine();
            Console.Clear();
        }

        static void NameSelect()//Här får spelaren "välja" namn
        {
            string playerName;
            Console.WriteLine("Before we begin. please enter name:");
            playerName = Console.ReadLine();
            Console.WriteLine(playerName + " is bad name. Your name is now Ivan.");
            Console.ReadLine();
            Console.Clear();
        }


        static void Class() //Här får användaren välja vilken klass de vill vara.
        {
            do
            {
                Console.Clear();
                Console.WriteLine("What is class, Ivan?\n1. Gopnik\n2. Slavic Barbarian\n3. Crazy Russian Sceintist");
                playerClass = Console.ReadLine();
                Console.Clear();

                if (playerClass == "1")
                {
                    Console.WriteLine("You are not be strong, or the big but you are move very fast.\n" +
                        "With Adidas tracksuityou have learn to steal and stealth.\n" +
                        "Strength: 4\nAgility: 10\nIntelligence: 6\n" 
                        "Are you sure you want to be Gopnik?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();

                    if (classConfirm == "1")
                    {
                        isGopnik = true;
                        HP = 35;
                    }
                    else
                    {
                        isGopnik = false;
                    }

                }
                else if (playerClass == "2")
                {
                    Console.WriteLine("Throughout your whole life, you have solve all problem with fighting.\n " +
                        "You are a very strong, very dumb, slavic barbarian.\n" +
                        "Strength: 10\nAgility: 2\nIntelligence: 3\n" +
                        "Are you sure you want to be a Barbarian?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();
                    if (classConfirm == "1")
                    {
                        isBarbarian = true;
                        HP = 60;
                    }
                    else
                    {
                        isBarbarian = false;
                    }
                }
                else if (playerClass == "3")
                {
                    Console.WriteLine("You were very good in school but you lost it all\n" +
                        "when you used your intelligence to create chemical weapon.\n" +
                        "Strength: 2\nAgility: 4\nIntelligence: 10\n" +
                        "Are you sure you want to be a Crazy Russian Scientist?\n" +
                        "1. Yes\n2. No\n");
                    classConfirm = Console.ReadLine();
                    Console.Clear();
                    if (classConfirm == "1")
                    {
                        isScientist = true;
                        HP = 20;
                    }
                    else
                    {
                        isScientist = false;
                    }
                }

            } while (isGopnik == false && isBarbarian == false && isScientist == false);
        }
        static void Start()//Oberoende av klass startar användaren på samma ställe, i huset. Här får man välja vart man ska gå.
        {
            Console.WriteLine("In the year 1921, Ivan wakes up in wreck of a house in Novosibirsk. It is very cold this winter.\n" +
                    "");

            movementChoice = Console.ReadLine();
            Console.Clear();

        }
        static void House_Gopnik()//Om spelaren har valt klassen Gopnik de dessa resultaten beroende på vad de valde att göra i House_Start.
        {
            if (isGopnik == true)
            {
                    Console.Clear();
                    if (movementChoice == "1")
                    {
                            Console.WriteLine("On your left, as you sit up in your bed is nightstand.\n");
                            Console.WriteLine("You search nightstand\n");
                            Console.WriteLine("You find:\nKnife");
                    }
                    else if (movementChoice == "2")
                    {
                        Console.WriteLine("You go to kitchen, and see vodka bottle.\n" +
                            "You all vodka, but you feel nothing because you are Russian");
                    }
                    else if (movementChoice == "3")
                    {
                         Console.WriteLine("You walk outside and feel cold december air.\n" +
                             "On your left you see bear. You become startle but worry not, is only Misha the bear.");
                    }

                
            }
        }
        static void House_Barbarian()//Om spelaren har valt klassen Slavic Barbarian får de dessa resultaten beroende på vad de valde att göra i House_Start.
        {
            Console.Clear();
            if (movementChoice == "1")
            {
                Console.WriteLine("You look at nightstand and break it\n");
                
            }
            else if (movementChoice == "2")
            {
                Console.WriteLine("You go to kitchen, and see vodka bottle.\n" +
                    "You all vodka, but you feel nothing because you are Russian");
            }
            else if (movementChoice == "3")
            {
                Console.WriteLine("You walk outside and feel cold december air.\n" +
                    "On your left you see bear. You become startle but worry not, is only Misha the bear.");
            }
        }
        static void House_scientist()//Om spelaren har valt klassen Crazy Russian Scientist får de dessa resultaten beroende på vad de valde att göra i House_Start.
        {
            Console.Clear();
            if (movementChoice == "1")
            {
                Console.WriteLine("On your left, as you sit up in your bed is nightstand.\n");
                Console.WriteLine("You search nightstand\n");
                Console.WriteLine("You find:\n2 Molotov");
            }
            else if (movementChoice == "2")
            {
                Console.WriteLine("You go to kitchen, and see vodka bottle.\n" +
                    "You all vodka, but you feel nothing because you are Russian");
            }
            else if (movementChoice == "3")
            {
                Console.WriteLine("You walk outside and feel cold december air.\n" +
                    "On your left you see bear. You become very scarebut worry not, is only Misha the bear.");
            }
        }       
    }
}
