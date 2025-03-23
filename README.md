# Number-guess-game-by-java
import java.util.Random;
import java.util.Scanner;

public class NumberGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int totalRounds = 0;
        int totalWins = 0;
        
        while (true) {
            totalRounds++;
            int attemptsLeft = 5;  // Limit of attempts per round
            int targetNumber = random.nextInt(100) + 1; // Generate a number between 1 and 100
            boolean guessedCorrectly = false;
            
            System.out.println("Round " + totalRounds + ": Guess the number between 1 and 100!");
            
            // Start the game loop for each round
            while (attemptsLeft > 0) {
                System.out.println("You have " + attemptsLeft + " attempts left.");
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                
                // Compare the guess with the target number
                if (userGuess == targetNumber) {
                    System.out.println("Congratulations! You guessed the number correctly!");
                    guessedCorrectly = true;
                    totalWins++;
                    break;
                } else if (userGuess < targetNumber) {
                    System.out.println("Your guess is too low. Try again!");
                } else {
                    System.out.println("Your guess is too high. Try again!");
                }
                
                attemptsLeft--;
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry! You've used all attempts. The correct number was: " + targetNumber);
            }
            
            System.out.println("Your current score: " + totalWins + " wins out of " + totalRounds + " rounds.");
            System.out.print("Do you want to play another round? (y/n): ");
            String playAgain = scanner.next();
            
            if (playAgain.equalsIgnoreCase("n")) {
                System.out.println("Thanks for playing! Final score: " + totalWins + " wins out of " + totalRounds + " rounds.");
                break;
            }
        }
        
        scanner.close();
    }
}
