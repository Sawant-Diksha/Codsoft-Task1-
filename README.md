# Codsoft-Task1-

import java.util.Random;
import java.util.Scanner;

public class GuessCorrectGame
{

    public static void main(String[] args) {
        Scanner obj1 = new Scanner(System.in);
        int no_of_rounds = 0;
        int no_of_wins = 0;

        System.out.println("WELCOME TO THE NEW WORLD!!!!!!.........");

        
        do {
            no_of_rounds++;
            boolean win = start_here(obj1);
            if (win) {
                no_of_wins++;
            }
        } while (try_againto_play(obj1));

        System.out.println("========================================================================");
        System.out.println("THANKS YOU TRIED WELL!!!!!!....");
        System.out.println("YOU PLAYED : \n\tROUNDS =" +" "+no_of_rounds+ "\tWON = " + no_of_wins + "");
        System.out.println("YOUR WIN RATE: " + ((double) no_of_wins / no_of_rounds * 100) + "%");
		System.out.println("========================================================================");

        obj1.close();
    }

    
    static int generate_num(int minimum, int maximum) {
        Random obj2= new Random();
        int var=obj2.nextInt(maximum - minimum + 1) +minimum;
        return var;
     }
    
    static boolean start_here(Scanner obj1) {
        int random_num = generate_num(1, 100);
        int no_of_attempts = 0;
        final int possible_attempts = 8;
        boolean it_is_right = false;

        System.out.println("ENTER THE NUMBER BETWEEN 1 TO 100 ");
        System.out.println("YOU HAVE ONLY" +" "+possible_attempts + " ATTEMPTS TO GUESS THE NUMBER.");
		System.out.println("========================================================================");

        
        while (no_of_attempts < possible_attempts) {
            no_of_attempts++;
            int user_input = user_thinking(obj1);
            if (user_input < random_num) {
                System.out.println("Too Low! Try Again.");
				System.out.println("  ");
            } else if (user_input > random_num) {
                System.out.println("Too High! Try Again.");
				System.out.println("  ");
            } else {

				System.out.println("========================================================================");
				System.out.println("WOHOO!!! YOU GUESSED IT RIGHT CONGRATES AND THE NUMBER IS :" + random_num);
                System.out.println("YOU TOOK " + no_of_attempts + " ATTEMPTS.");
				System.out.println("========================================================================");
                it_is_right = true;
                break;
            }
        }

        if (!it_is_right) {
            System.out.println("SORRY, YOU'VE USED ALL YOUR ATTEMPTS. THE CORRECT NUMBER WAS: " + random_num);
        }

        return it_is_right;
    }

    
    static int user_thinking(Scanner obj1) {
        System.out.print("THINK AND ENTER THE NUMBER: ");
        return obj1.nextInt();
    }

    
    static boolean try_againto_play(Scanner obj1) {
        System.out.print("DO YOU WANT TO PLAY ANOTHER ROUND??? [YES/NO] : ");
        String feedback = obj1.next().toUpperCase();
        return feedback.equals("YES");
    }
}
