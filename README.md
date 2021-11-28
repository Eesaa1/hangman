namespace Hangman
{
    class Program
    {
        static void Main(string[] args)
        {
            /* Variables / Arrays */
            int livesRemaining = 6;
            string[] guessWord = new string[] { "e", "e", "s", "a", "a" };
            string[] currWord = new string[] { "_", "_", "_", "_", "_" };
            /* Variable "a" established to stop loop when word is guessed*/
            int a = 0;
            /* Ask user for input (Need condition do while) */
            do
            {
                /* Variable x used as I had a logic error with my loop*/
                int x = 0;
                Console.WriteLine("Enter a letter to guess: ");
                string guess = Console.ReadLine();
                /* Check if input is in guess word */
                for (int i = 0; i < 5; i++)
                {
                    /* If statement to determine if letter is correct or not (livesRemaining--)*/
                    if (guess == guessWord[i])
                    {
                        currWord[i] = guess;
                        x++;

                    }

                }
                /*another if with x used to determine lives outside of for loop to work around error*/
                if (x < 1)
                {
                    livesRemaining--;
                }
                else
                {
                    a = a + x;
                    Console.WriteLine("Well done you guessed correctly!");
                }
                Console.WriteLine("You have {0} lives remaining, good luck!", livesRemaining);
                Console.WriteLine("Your current word is: ");
                /*Prints current word*/
                for (int j = 0; j<5; j++)
                {
                    Console.Write(currWord[j]);
                }
                Console.WriteLine("");
            } while (a < 5 && livesRemaining > 0);
            /*If loop to see if they have got no lives or guessed currectly*/
            if (a >= 5)
            {
                Console.WriteLine("Congratulations, you guessed the word!");
            }
            else
            {
                Console.WriteLine("Unlucky, you ran out of lives, better luck next time!");
            }
        }
    }
}
