using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false, isGoback = false, isGoToStart = false, hasKnife = false, hasFist = false, hasMolotov = false, Win = false;
        static string MovementChoice, PlayerClass, ClassConfirm, EnemyName = " ", Weapon;
        static int RandomItem = 0, PlayerHP = 0, PlayerDMG = 0, EnemyDMG = 0, EnemyHP, FullHP;
        static Random rng = new Random();
        static void Main(string[] args)
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
            do
            {
                Start();
            } while (isGoToStart == true);
            Outside_Start();

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
                PlayerClass = Console.ReadLine();
                Console.Clear();

                if (PlayerClass == "1")
                {
                    Console.WriteLine("You are not be strong, or the big but you are move very fast.\n" +
                        "With Adidas tracksuityou have learn to steal and stealth.\n" +
                        "Strength: 4\nAgility: 10\nIntelligence: 6\n" +
                        "Are you sure you want to be Gopnik?\n" +
                        "1. Yes\n2. No\n");
                    ClassConfirm = Console.ReadLine();
                    Console.Clear();

                    if (ClassConfirm == "1")
                    {
                        isGopnik = true;
                        FullHP = 35;
                        PlayerHP = 35;
                    }
                    else
                    {
                        isGopnik = false;
                    }

                }
                else if (PlayerClass == "2")
                {
                    Console.WriteLine("Throughout your whole life, you have solve all problem with fighting.\n " +
                        "You are a very strong, very dumb, slavic barbarian.\n" +
                        "Strength: 10\nAgility: 2\nIntelligence: 3\n" +
                        "Are you sure you want to be a Barbarian?\n" +
                        "1. Yes\n2. No\n");
                    ClassConfirm = Console.ReadLine();
                    Console.Clear();
                    if (ClassConfirm == "1")
                    {
                        isBarbarian = true;
                        FullHP = 60;
                        PlayerHP = 60;
                    }
                    else
                    {
                        isBarbarian = false;
                    }
                }
                else if (PlayerClass == "3")
                {
                    Console.WriteLine("You were very good in school but you lost it all\n" +
                        "when you used your intelligence to create chemical weapon.\n" +
                        "Strength: 2\nAgility: 4\nIntelligence: 10\n" +
                        "Are you sure you want to be a Crazy Russian Scientist?\n" +
                        "1. Yes\n2. No\n");
                    ClassConfirm = Console.ReadLine();
                    Console.Clear();
                    if (ClassConfirm == "1")
                    {
                        isScientist = true;
                        FullHP = 20;
                        PlayerHP = 20;
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
                "You realise babushka(grandmother) is maybe cold. You have to check up on her.\n" +
                    "1. Check your nightstand\n2. Check the kitchen\n3. Go outside");

            MovementChoice = Console.ReadLine();        
            if (isGopnik == true)
            {
                Console.Clear();
                if (MovementChoice == "1")
                {
                    Console.WriteLine("On your left, as you sit up in your bed is nightstand.\n");
                    Console.WriteLine("You search nightstand\n");
                    if (isGopnik == true)
                    {
                        Console.WriteLine("You find:\nKnife");
                        hasKnife = true;
                        Weapon = "knife";
                        PlayerDMG = 14;
                        Console.ReadKey();
                        Console.Clear();
                        isGoToStart = true;
                    }
                    else if (isBarbarian == true)
                    {
                        Console.WriteLine("You search the nightstand, but find nothing so you break it\n");
                        Console.ReadKey();
                        hasFist = true;
                        Weapon = "fists";
                        PlayerDMG = 12;
                        Console.Clear();
                        isGoToStart = true;
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("You find:\n2 Molotov");
                        hasMolotov = true;
                        Weapon = "molotov";
                        PlayerDMG = 14;
                        Console.ReadKey();
                        Console.Clear();
                        isGoToStart = true;
                    }
                }
                else if (MovementChoice == "2")
                {
                    Console.WriteLine("You go to kitchen, and see vodka bottle.\n" +
                        "You all vodka, but you feel nothing because you are Russian");
                    Console.ReadKey();
                    Console.Clear();

                }
                else if (MovementChoice == "3")
                {
                    Console.WriteLine("You walk outside and feel cold december air.\n" +
                        "On your left you see bear. You become startle but worry not, is only Misha the bear.");
                    Console.ReadLine();
                }
            }
        }
        static void Outside_Start()
        {
            do
            {
                Console.WriteLine("You see two paths.\n" +
                    "1. Dark dense forest\n" +
                    "2. Regular forest");
                
                MovementChoice = Console.ReadLine();
                if (MovementChoice == "1")
                {
                    Console.Clear();
                    Console.WriteLine("You start sneaking through the forest, in the bushes.\n" +
                        "Suddenly you hear noise. It is childhood bully Vanya.\n" +
                        "What do you want to do?\n" +
                        "1. Attack him for all the time he bullied you.\n" +
                        "2.Keep moving");
                    MovementChoice = Console.ReadLine();
                    if(MovementChoice == "1")
                    {
                        EnemyName = "Vanya";
                        EnemyHP = rng.Next(35, 45);
                        EnemyDMG = rng.Next(5, 8);
                        if(isGopnik == true)
                        {
                            if(hasKnife == true)
                            {
                                Console.WriteLine("You gather the courage to go up to him sneakily, in the shadows.\n");

                                BattleSystem();
                                
                            }
                            else if(hasKnife == false)
                            {
                                Console.WriteLine("You run at Vanya and start to attack him.");
                                Console.Clear();
                                BattleSystem();
                            }
                        }
                        else if (isBarbarian == true)
                        {
                            Console.WriteLine("You remember that you didn't have a bully, so you go to bully him instead.\n" +
                                "You run up to him to attack him.");
                            BattleSystem();
                        }
                        else if(isScientist == true)
                        {
                            if (hasMolotov == true)
                            {

                            }
                            else if (hasMolotov == true)
                            {

                            }
                        }
                    }
                }
                else if (MovementChoice == "2")
                {
                    Console.WriteLine("You get flashback to childhood and move on, past Vanya.");
                    Field();
                }
                else
                {
                    isGoback = true;
                }
            } while (isGoback == true);
        }
        static void Field()
        {
            Console.WriteLine("You finally walk out of the forest, and come to a big field.");
        }
        static void BattleSystem()
        {
            for (int i = 0; i < 10; i++)
            {
                if (EnemyHP <= 0)
                {

                }
                else if (PlayerHP <= 0)
                {

                }
                Console.WriteLine("What do you want to do?                                                                                      HP: " + PlayerHP + "/" + FullHP + "\n" +
                    "1. Attack\n2. Run away");
                
                
                
            }
        }
        
    }
}
