using System;
using System.Threading;

namespace Russia_Survival_Devolved
{
    class Program
    {
        static bool isGopnik = false, isBarbarian = false, isScientist = false, isGoBack = false, isGoToStart = false, enemy2GoBack = false, isE1Dead = false, isE2Dead = false, isPathBlocked = false;
        static string MovementChoice, ActionChoice, PlayerClass, ClassConfirm;
        static int KeyPiece = 0;
        static Random rng = new Random();
        static int Chance = rng.Next(0, 3);
        static void Main()
        {
            StartScreen();
            Introduction();
            NameSelect();
            Class();
            do
            {
                isGoToStart = false;
                Start();
                do
                {
                    isGoBack = false;
                    Outside_Start();
                } while (isGoBack == true);
            } while (isGoToStart == true);


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
            KeyPiece = 0;
            isGoToStart = false;
            Console.WriteLine("In the year 1921, Ivan wakes up in wreck of a house in Novosibirsk. It is very cold this winter.\n" +
                "You realise babushka(grandmother) is maybe cold. You have to check up on her. She lives in house far away.\n" +
                "But babushka has very complicated verification process.\nTo be allowed in her house you need to find all of the pieces to her key.\n" +
                "She has trusted 2 people with this key. You have to get the key pieces from them in any way possible.\n");
            Console.ReadKey();
            Console.Clear();
            Console.WriteLine("1.Check the kitchen\n2. Go outside");
            MovementChoice = Console.ReadLine();
            
            
            Console.Clear();
            if (MovementChoice == "1")
            {
                Console.WriteLine("You go to kitchen, and see vodka bottle.\n" +
                    "You drink all vodka, but you feel nothing because you are Russian");
                Console.ReadLine();
                Console.Clear();
                isGoToStart = true;
            }
            else if (MovementChoice == "2")
            {
                Console.WriteLine("You walk outside and feel cold december air.\n" +
                    "On your left you see bear. You become startle but worry not, is only Misha the bear.");
                Console.ReadLine();
            }
            

        }
        static void Outside_Start()//Outside_Start är som en "hub". När spelaren vinner över en fiende eller inte blir insläppt av babushka kommer man hit.
        {
            do
            {
                isPathBlocked = false;
                Console.Clear();
                Console.WriteLine("You see three paths. Which one do you follow?\n" +
                    "1. Left\n" +
                    "2. Right\n" +
                    "3. Babushkas house");
                MovementChoice = Console.ReadLine();
                if (MovementChoice == "1")
                {
                    if (isE1Dead == true)
                    {
                        Console.WriteLine("You enter a field, but it's so empty and boring that you go back.");
                        Console.ReadLine();
                        isPathBlocked = true;
                    }
                    else
                    {
                        Enemy1();
                    }
                }
                else if (MovementChoice == "2")
                {
                    if (isE2Dead == true)
                    {
                        Console.WriteLine("You enter a forest, but there's nothing there, so you go back.");
                        Console.ReadLine();
                        isPathBlocked = true;
                    }
                    else
                    {
                        Enemy2();
                    }
                }
                else if (MovementChoice == "3")
                {
                    BabushkaHouse();
                }
                
            } while (isPathBlocked == true);
        }
        static void Enemy1()//Detta är en av fienderna som spelaren möter.
        {

            Console.WriteLine("You enter a field, that is completely empty. Suddenly, out of ground comes a Molemanman.\n");
            Console.ReadLine();
            Console.Clear();
            Console.WriteLine("Moleman: Hello, traveler. What is your business in my field?\n" +
                "1. Fight(strength)\n2. Sneak(agility)\n3. Talk(intelligence)");
            ActionChoice = Console.ReadLine();

            if (ActionChoice == "1")
            {
                if (isGopnik == true)
                {
                    Console.WriteLine("Ivan: I want key!\n" +
                            "Moleman: Well then come and get it!");
                    Console.Clear();
                    Chance = rng.Next(0, 10);//Jag använde mig av en slumpgenerator för att bestämma om splearen lyckas med sina val eller inte, där chansen bestäms av splarens klass.
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6)
                    {
                        Console.WriteLine("You fight the Moleman with all your might and manage to come out victorious.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Moleman: Have mercy blyat! You can have key piece just leave me alone!");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("The Moleman crawls back in it's hole.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("You try to fight it, but it is stronger than you.\n" +
                            "Moleman: You thought you could just kill me, weakling?");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Game Over...\n");
                        isGoToStart = true;
                    }
                }
                else if (isBarbarian == true)
                {
                    Console.WriteLine("Ivan: I want key!\n" +
                            "Moleman: Well then come and get it!");

                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8 || Chance == 9 || Chance == 10)
                    {
                        Console.WriteLine("You fight the Moleman with all your might and manage to come out victorious.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Moleman: Have mercy blyat! You can have key piece just leave me alone!");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("The Moleman crawls back it's hole.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    
                }
                else if (isScientist == true)
                {
                    Console.WriteLine("Ivan: I want key!\n" +
                            "Moleman: Well then come and get it!");

                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4)
                    {
                        Console.WriteLine("You fight the Moleman with all your might and manage to come out victorious.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Moleman: Have mercy blyat! You can have key piece just leave me alone!");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("The Moleman crawls back it's hole.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("You try to fight it, but it is stronger than you.\n" +
                            "Moleman: You thought you could just kill me?");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Game Over...\n");
                        isGoToStart = true;
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
                        Console.WriteLine("You hide behind some rocks so the Moleman does not see you, then you sneak up behing him to grab key piece.\n" +
                            "Your thief skills kick in and you grab it without him noticing it.");
                        Console.ReadLine();
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                }
                else if (isBarbarian == true)
                {
                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5)
                    {
                        Console.WriteLine("You curl up, because if you can't see him, he can't see you.\n" +
                            "He doesn't see you because when curled up, you look like a rock.\n" +
                            "When he looks away you run as fast as you can toward him, grab the key piece and run away.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("You try to hide behind a rock, but you are bigger than it.\n" +
                            "He sees you, but before he can do anything you hit him in the head and grab the key piece");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                }
                else if (isScientist == true)
                {
                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7)
                    {
                        Console.WriteLine("You see a thick bush. You run inside the bush and run up behind the Moleman.\n" +
                            "The Moleman, being almost blind due to a life underground, doesn't see you and you steal the key piece.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("You try to hide, but you're not very good at improvising and then Moleman spots you.\n");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Moleman: You thought you could trick me\n" +
                            "The Moleman dissapears into it's hole for a second and then appears behind you.\n" +
                            "Moleman: Nothing personal, kiddo.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("The Moleman strikes you, instantly killing you.\n" +
                            "Game Over...\n");
                        isGoToStart = true;
                    }
                }
            }
            else if (ActionChoice == "3")
            {
                if (isGopnik == true)
                {
                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6)
                    {
                        Console.WriteLine("Ivan: Look over there!\n" +
                        "The Moleman looks back and before he can notice you grab the key piece");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("Ivan: Look over there!\n" +
                            "Moleman: No, you look over THERE!\n" +
                            "You look behind you, and the Moleman strikes you while you are distracted, killing you.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Game Over...");
                        isGoToStart = true;
                    }
                }

                else if (isBarbarian == true)
                {
                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4)
                    {
                        Console.WriteLine("Ivan: Give me key!");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: No.");
                        Console.ReadLine();
                        Console.WriteLine("Ivan: Please blyat I need key!");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: Ok here you go.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("The Moleman gives you the key because you were really polite and said please.");
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                        Console.WriteLine("Ivan: Give me key!");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: No blyat");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Game Over...");
                        Console.ReadLine();
                        isGoToStart = true;
                    }
                }
                else if (isScientist == true)
                {
                    Chance = rng.Next(0, 10);
                    if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8 || Chance == 9 || Chance == 10)
                    {
                        Console.WriteLine("Ivan: Can I perhaps interest you in some wares?");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: Depends. What kind of wares are we talking here?");
                        Console.ReadLine();
                        Console.WriteLine("Ivan: Well I have some vodka, some kvas and adidas pants.");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: Can I have all?");
                        Console.ReadLine();
                        Console.WriteLine("Ivan: Depends, will you give me you piece of key?");
                        Console.ReadLine();
                        Console.WriteLine("Moleman: Yes, just give me all things.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("You take the key piece, drop all of the things on his head, and walk away.");
                        Console.ReadLine();
                        KeyPiece = KeyPiece + 1;
                        isE1Dead = true;
                        isGoBack = true;
                    }
                    else
                    {
                         
                    }
                        
                }
            }

        }
        static void Enemy2()//Detta är fiende 2, Dedushka(farfar)
        {
            do
            {
                enemy2GoBack = false;
                isGoBack = false;
                Console.WriteLine("You enter a forest. Suddenly all of the bushes clear up, and you see dedushka(grandpa) sitting in a rocking chair.\n");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Dedushka: Ah, Ivan. What are you doing in this forest?");
                Console.WriteLine("1.Fight(strength)\n2.Sneak(agility)\n3.Talk(intelligence)");
                ActionChoice = Console.ReadLine();

                if (ActionChoice == "1")
                {
                    if (isGopnik == true)
                    {
                        Console.WriteLine("Ivan: Give me the key!\n" +
                                "Dedushka: What are you going to do, fight me?");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("He's right, you're not about to fight your dedushka");
                        Console.ReadLine();
                        Console.Clear();
                        enemy2GoBack = true;
                    }
                    else if (isBarbarian == true)
                    {
                        Console.WriteLine("Ivan: Give me the key!\n" +
                                "Dedushka: What are you going to do, fight me?");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("He's right, you're not about to fight your dedushka");
                        Console.ReadLine();
                        Console.Clear();
                        enemy2GoBack = true;
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("Ivan: Give me the key!\n" +
                                "Dedushka: What are you going to do, fight me?");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("He's right, you're not about to fight your dedushka");
                        Console.ReadLine();
                        Console.Clear();
                        enemy2GoBack = true;
                    }
                }
                else if (ActionChoice == "2")
                {
                    if (isGopnik == true)
                    {

                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7 || Chance == 8 || Chance == 9 || Chance == 10)
                        {
                            Console.WriteLine("You immediately hide behind a tree so dedushka doesn't see you. You hear him humming along, rocking in his chair.\n" +
                                "Quickly you circle around his chair behind some bushes, go up behind him, and take the key piece from around his neck.");
                            Console.ReadLine();
                            KeyPiece = KeyPiece + 1;
                            isE2Dead = true;
                            enemy2GoBack = true;
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
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Dedushka: BLYAT IVAN! GIVE ME BACK MY KEY!\n");
                            Console.ReadLine();
                            Console.Clear();
                            KeyPiece = KeyPiece + 1;
                            isE2Dead = true;
                            enemy2GoBack = true;
                        }
                        else
                        {
                            Console.WriteLine("You try to hide behind a rock, but you are bigger than it.\n");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Dedushka: Ivan, are you idiot or drunk? Probably both. Go home Ivan.");
                            Console.ReadLine();
                            isGoBack = true;
                        }
                    }
                    else if (isScientist == true)
                    {
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7)
                        {
                            Console.WriteLine("You remember dedushka has bad eyesight, so you get inside a bush and walk up to him.\n" +
                                "He doesn't notice because he is almost blind, so you grab the necklace and leave.\n");
                            Console.ReadLine();
                            KeyPiece = KeyPiece + 1;
                            isE2Dead = true;
                            enemy2GoBack = true;
                        }
                        else
                        {
                            Console.WriteLine("You try to hide, but you're not very good at improvising and then dedushka spots you.\n");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Dedushka: I am not THAT blind, Ivan. Go home idiot.\n");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("You go back, feeling very stupid.");
                            isGoBack = true;
                        }
                    }
                }
                else if (ActionChoice == "3")
                {
                    if (isGopnik == true)
                    {
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6 || Chance == 7)
                        {
                            Console.WriteLine("Ivan: Look over there!\n" +
                            "Dedushka looks back, but he just keeps looking.\n" +
                            "Eventually, you notice he just fell asleep in that position, so you grab the key and go");
                            Console.ReadLine();
                            KeyPiece = KeyPiece + 1;
                            isE2Dead = true;
                            enemy2GoBack = true;
                        }
                        else
                        {
                            Console.WriteLine("Ivan: Look over there!\n" +
                                "Dedushka: Do you think I am 5 years old? I am not idiot blyat. YOU look over there.\n" +
                                "You look behind you, and the dedushka throws his walking stick in your head so hard that you black out.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("You wake up in another part of the forest, and your head really hurts.");
                            isGoBack = true;
                        }
                    }

                    else if (isBarbarian == true)
                    {
                        Chance = rng.Next(0, 10);
                        if (Chance == 1 || Chance == 2 || Chance == 3 || Chance == 4 || Chance == 5 || Chance == 6)
                        {
                            Console.WriteLine("Ivan: Give me key!");
                            Console.ReadLine();
                            Console.WriteLine("Dedushka: No.");
                            Console.ReadLine();
                            Console.WriteLine("Ivan: Please blyat I need key!");
                            Console.ReadLine();
                            Console.WriteLine("Dedushka: Ok here you go.");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("Dedushka gives you the key because you are his grandson and you actually asked nicely.");
                            KeyPiece = KeyPiece + 1;
                            isE2Dead = true;
                            isGoBack = true;
                        }
                        else
                        {
                            Console.WriteLine("Ivan: Give me key!");
                            Console.ReadLine();
                            Console.WriteLine("Dedushka: No.");
                            Console.ReadLine();
                            Console.WriteLine("Ivan: BLYAT GIVE ME KEY!");
                            Console.ReadLine();
                            Console.WriteLine("NO!");
                            Console.ReadLine();
                            Console.Clear();
                            Console.WriteLine("You walk back, defeated by dedushkas clearly superior argumentative skills.");
                            enemy2GoBack = true;
                        }
                    }
                    else if (isScientist == true)
                    {
                        Console.WriteLine("Ivan: What would it take for you to give me the key piece you have?");
                        Console.ReadLine();
                        Console.WriteLine("Dedushka: Oh I don't know, what can you give me?");
                        Console.ReadLine();
                        Console.WriteLine("Ivan: I can give you vodka, potato, or kvas.");
                        Console.ReadLine();
                        Console.WriteLine("Dedushka: I am hungry as BLYAT! GIVE ME POTATO BLYAT.");
                        Console.ReadLine();
                        Console.Clear();
                        Console.WriteLine("Almost scared, you throw the potato at him, and he throws the key at you.");
                        KeyPiece = KeyPiece + 1;
                        isE2Dead = true;
                        isGoBack = true;
                    }
                }


            } while (enemy2GoBack == true);
        }
        static void BabushkaHouse()//Beroende på hur många nyckeldelar du har kommer du får olika "encounters" med Babushka(farmor)
        {
            if (KeyPiece == 0)
            {
                Console.WriteLine("You come to babushkas house. It's a very big house, but also very secure.\n" +
                    "Babushka is very serious about security. As you come up to the house you hear babushka yelling through the window.\n");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Babushka: Oh blyat, it's Ivan! What do you want blyat?\n");
                Console.WriteLine("Ivan: I just want to come in, and see how you are doing. It's very cold you know.");
                Console.ReadLine();
                Console.WriteLine("Babushka: How do I know it is real Ivan? Maybe it is wolf in mask, blyat.\n" +
                    "Come back when you have key piece. Only my family could be able to get them both.");
                Console.ReadLine();
                Console.WriteLine("Ivan: But babushka, it's me Ivan! Let me in blyat!");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Before you can say anything else, babushka slams the windows shut.");
                Console.ReadLine();
                isGoBack = true;
            }
            else if (KeyPiece == 1)
            {
                Console.WriteLine("You walk up to babushkas house, after one victory.\n");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Ivan: Babushka! I have piece of key now! Let me in blyat!");
                Console.ReadLine();
                Console.WriteLine("Babushka: How many key piece do you have blyat?\n");
                Console.ReadLine();
                Console.WriteLine("Ivan: I have one piece, isn't that enough blyat?\n");
                Console.ReadLine();
                Console.WriteLine("Babushka: Are you debil(dumb)? It was two piece of key, idiot blyat!");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Babushka slams the windows again, cracking them.");
                isGoBack = true;
            }
            else if (KeyPiece == 2)
            {
                Console.WriteLine("Babushka: What you want blyat?");
                Console.ReadLine();
                Console.WriteLine("Ivan: I have key now let me in.");
                Console.ReadLine();
                Console.WriteLine("The door flies open and you enter.");
                Console.ReadLine();
                Console.Clear();
                Console.WriteLine("Babushka: So, what did you want?");
                Console.ReadLine();
                Console.WriteLine("Ivan: I just want to see if you are the okay.");
                Console.ReadLine();
                Console.WriteLine("Babushka: HAH! Of course I am ok, I am Russian babushka blyat. Now leave.");
                Console.ReadLine();
                Console.SetCursorPosition(53, 15);
                Console.WriteLine("Conglaturations!");
                Console.SetCursorPosition(53, 16);
                Console.WriteLine("You are winner!");
            }
        }
    }
}

