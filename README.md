using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false, isGoback = false, isGoToStart = false, hasKnife = false, hasFist = true, hasMolotov = false;
        static string MovementChoice, ActionChoice, PlayerClass, ClassConfirm, Weapon;
        static int RandomItem = 0, PlayerHP = 0, PlayerDMG = 0, EnemyDMG = 0, EnemyHP, FullHP, Encounter, KeyPiece = 0;
        static Random rng = new Random();
        static int Chance = rng.Next(0, 3);
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
            isGoToStart = false;
            Console.WriteLine("In the year 1921, Ivan wakes up in wreck of a house in Novosibirsk. It is very cold this winter.\n" +
                "You realise babushka(grandmother) is maybe cold. You have to check up on her. She lives in house far away.\n" +
                "But babushka has very complicated verification process. To be allowed in her house you need to find all of the pieces to her key.\n" +
                "She has trusted 4 people with this key. You have to get the key pieces from them in any way possible.\n");
            Console.ReadKey();
            Console.Clear();
            Console.WriteLine("1. Check your nightstand\n2. Check the kitchen\n3. Go outside");
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
                        
                        
                        Console.ReadKey();
                        Console.Clear();
                        isGoToStart = true;
                    }
                    else if (isBarbarian == true)
                    {
                        Console.WriteLine("You search the nightstand, but find nothing so you break it\n");
                        Console.ReadKey();
                        hasFist = true;
                        
                        
                        Console.Clear();
                        isGoToStart = true;
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("You find:\n2 Molotov");
                        hasMolotov = true;
                        

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
                    isGoToStart = true;
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
            Console.Clear();
            Console.WriteLine("You see two paths. Which one do you follow?\n" +
                "1. Left\n" +
                "2. Right");
            MovementChoice = Console.ReadLine();
            if (MovementChoice == "1")
            {
                Enemy1();
            }
            else if (MovementChoice == "2")
            {
                Enemy2();
            }
        }
        static void Enemy1()
        {
            do
            {
                Console.WriteLine("You enter a field, that is completely empty. Suddenly, out of ground comes big mole.\n");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Mole: Hello, traveler. What is your business in my field?\n" +
                    "1. Fight(strength)\n2. Sneak(agility)\n3. Talk(intelligence)");
                ActionChoice = Console.ReadLine();

                if (ActionChoice == "1")
                {
                    if (isGopnik == true)
                    {
                        Console.WriteLine("Ivan: I want key!\n" +
                                "Mole: Well then come and get it!");
                        Console.Clear();
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8)
                        {
                            Console.WriteLine("You fight the mole with all your might and manage to come out victorious.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Mole: Have mercy blyat! You can have key piece just leave me alone!");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("The mole crawls back in it's hole.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                        else
                        {
                            Console.WriteLine("You try to fight it, but it is stronger than you.\n" +
                                "Mole: You thought you could just kill me, weakling?");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Returning to last enemy...\n");
                            isGoback = true;
                        }
                    }
                    else if (isBarbarian == true)
                    {
                        Console.WriteLine("Ivan: I want key!\n" +
                                "Mole: Well then come and get it!");

                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8 || Chance == 9 || Chance == 10)
                        {
                            Console.WriteLine("You fight the mole with all your might and manage to come out victorious.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Mole: Have mercy blyat! You can have key piece just leave me alone!");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("The mole crawls back it's hole.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                        else
                        {
                            Console.WriteLine("You try to fight it, but it is stronger than you.\n" +
                                "Mole: You thought you could just kill me?");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Returning to last enemy...\n");
                            isGoback = true;
                        }
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("Ivan: I want key!\n" +
                                "Mole: Well then come and get it!");

                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6)
                        {
                            Console.WriteLine("You fight the mole with all your might and manage to come out victorious.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Mole: Have mercy blyat! You can have key piece just leave me alone!");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("The mole crawls back it's hole.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                        else
                        {
                            Console.WriteLine("You try to fight it, but it is stronger than you.\n" +
                                "Mole: You thought you could just kill me?");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Returning to last enemy...\n");
                            isGoback = true;
                        }
                    }
                }
                else if (ActionChoice == "2")
                {
                    if (isGopnik == true)
                    {

                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8 || Chance == 9 || Chance == 10)
                        {
                            Console.WriteLine("You hide behind some rocks so the mole does not see you, then you sneak up behing him to grab key piece.\n" +
                                "Your thief skills kick in and you grab it without him noticing it.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                    }
                    else if (isBarbarian == true)
                    {
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6)
                        {
                            Console.WriteLine("You curl up, because if you can't see him, he can't see you.\n" +
                                "He doesn't see you because when curled up, you look like a rock.\n" +
                                "When he looks away you run as fast as you can toward him, grab the key piece and run away.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                        else
                        {
                            Console.WriteLine("You try to hide behind a rock, but you are bigger than it.\n" +
                                "He sees you, but before he can do anything you hit him in the head and grab the key piece");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                    }
                    else if (isScientist == true)
                    {
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8)
                        {
                            Console.WriteLine("You see a thick bush. You run inside the bush and run up behind the mole.\n" +
                                "The mole, being almost blind due to a life underground, doesn't see you and you steal the key piece.");
                            KeyPiece = KeyPiece + 1;
                            break;
                        }
                        else
                        {
                            Console.WriteLine("You try to hide, but you're not very good at improvising and then mole spots you.\n");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Mole: You thought you could trick me\n" +
                                "The mole dissapears into it's hole for a second and then appears behind you.\n" +
                                "Mole: Nothing personal, kiddo.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("The mole strikes you, instantly killing you.\n" +
                                "Returning to last enemy...\n");
                            isGoback = true;
                        }
                    }
                }
                else if (ActionChoice == "3")
                {
                    if (isGopnik == true)
                    {
                        Console.WriteLine("1. \n2. \n3. ");
                        ActionChoice = Console.ReadLine();

                        if(ActionChoice == "1")
                        {

                        }
                        else if (ActionChoice == "2")
                        {

                        }
                        else if (ActionChoice == "3")
                        {

                        }
                    }
                    else if (isBarbarian == true)
                    {
                        Console.WriteLine("1. \n2. \n3. ");
                        ActionChoice = Console.ReadLine();

                        if (ActionChoice == "1")
                        {

                        }
                        else if (ActionChoice == "2")
                        {

                        }
                        else if (ActionChoice == "3")
                        {

                        }
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("1. \n2. \n3. ");
                        ActionChoice = Console.ReadLine();

                        if (ActionChoice == "1")
                        {

                        }
                        else if (ActionChoice == "2")
                        {

                        }
                        else if (ActionChoice == "3")
                        {

                        }
                    }
                }
            } while (isGoback == true);
        }
        static void Enemy2()
        {

        }
        static void Enemy3()
        {

        }
        static void Enemy4()
        {

        }
    }
}
