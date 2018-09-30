using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        
        static void Main(string[] args)
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
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
            Console.WriteLine("The year is 1921. In the Soviet Union people are starving, and you are one of them.\n" +
                "Only the strongest Russians will survive...\n" +
                "Controls: 1, 2, 3, 4, 5 and enter");
        }

        static void NameSelect()
        {
            string playerName;
            Console.WriteLine("Before we begin. please enter you name:");
            playerName = Console.ReadLine();

            Console.WriteLine(playerName + " is a bad name. Your name is now Ivan.");
            Thread.Sleep(3000);
            Console.Clear();
        }


        static void Class()
        {
            string playerClass, classConfirm;
            bool isGopnik = false, isBarbarian = false, isScientist = false;

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
        

    }
}
