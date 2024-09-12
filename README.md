import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int totalScore = 0;
        int rounds = 3; // Number of rounds

        for (int round = 1; round <= rounds; round++) {
            int numberToGuess = (int) (Math.random() * 100) + 1;
            int attempts = 5; // Limiting the number of attempts
            int points = 0;
            boolean guessed = false;

            System.out.println("Round " + round + ": Guess the number between 1 and 100");

            for (int attempt = 1; attempt <= attempts; attempt++) {
                System.out.print("Attempt " + attempt + ": ");
                int userGuess = scanner.nextInt();

                if (userGuess == numberToGuess) {
                    points = (attempts - attempt + 1) * 10; // Points based on attempts
                    totalScore += points;
                    guessed = true;
                    System.out.println("Congratulations! You guessed the number. Points earned: " + points);
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("The number is higher.");
                } else {
                    System.out.println("The number is lower.");
                }
            }

            if (!guessed) {
                System.out.println("Sorry, you've used all attempts. The number was: " + numberToGuess);
            }

            System.out.println("Total Score after round " + round + ": " + totalScore);
        }

        System.out.println("Game Over! Your final score is: " + totalScore);
        scanner.close();
    }
}
