# week2player
package exercises;

import java.util.Scanner;

import static java.lang.System.in;
import static java.lang.System.out;

/*
 *  Utilities to input/output player data for a command line game
 *
 *  See:
 *  - UseAConstructor
 *  - ObjectArrMeth
 *
 */
public class Ex1ReadPlayers {
    public static void main(String[] args) {
        new Ex1ReadPlayers().program();
    }

    final Scanner sc = new Scanner(in);

    void program() {
        Player[] players = inputPlayers();
        outPlayers(players);
        Player player = new Player("Linnea", 3000);
        out.println(player.name);
        out.println(player.points);
        for (int i = 0; i < players.length; i++) {
            out.println("Name " + players[i].name + " points " + players[i].points);  // Print selected variables
        }
    }

    // This class captures the concept of a Player
    class Player {
        String name;   // A Player has a name and...
        int points;    // ... and points

        // TODO
        Player(String name, int points) {
            this.name = name;
            this.points = points;
        }

        Player(){

        }
    }

    // ---------- Methods -------------------

     Player[] inputPlayers() {
       // TODO
         out.print("How many players? > ");
         int nPlayers = sc.nextInt();
         sc.nextLine();                 // Read away enter code last in input
         Player[] players = new Player[nPlayers];    // Create array for dog objects (no objects so far, just the array)
         for (int i = 0; i < nPlayers; i++) {
             Player p = new Player();
             out.print("What's the name of the player? > ");  // Fill in data
             p.name = sc.nextLine();
             out.print("How many points? > ");
             p.points = sc.nextInt();
             players[i] = p;                   // Store object in array
             sc.nextLine();                 // Read away enter code
         }
         return players;

    }

    void outPlayers(Player[] players){
       // TODO
        int index = 0;
        int maxAge = players[index].points;  // Assume first is oldest ...
        for (int i = 0; i < players.length; i++) {
            if (players[i].points > maxAge) {  // ... if not store index of elder
                index = i;
                maxAge = players[i].points;   // .. and age.
            }
        }
        out.println(players[index]);
    }


}
