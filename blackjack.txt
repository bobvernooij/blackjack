import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class blackjack {

	public static void main(String[] args) {
		 String kleur[] = {"harten", "ruiten", "schoppen", "klaver"};
		 String waarde[] = {"A", "heer","vrouw", "boer", "tien", "negen", "acht", "zeven", "zes", "vijf", "vier", "drie", "twee"};
		 Deck[] deck = new Deck[52]; //hierdoor worden 52 kaarten aangemaakt
		 int counter = 0;
		 for(int i = 0; i< kleur.length;i++) {
			 for(int j = 0; j< waarde.length;j++) {
				 deck[counter]= new Deck(kleur[i],waarde[j]);
				 counter++;
			 }
		 }
		 //Doelstelling 1: Alle kaarten zitten 1x in het overzicht in een random volgorde
		 Collections.shuffle(Arrays.asList(deck));//hierdoor zijn kaarten altijd random
		 
		 int gamecounter = 0;
		 int score = 0; {
		 while (score < 21) {
			 System.out.println("k = nieuwe kaart, p = passen, q = quit");
			 Scanner keuze = new Scanner(System.in);//Doelstelling 2: Verdeel kaarten adhv input
			 String input = keuze.nextLine();
			  if (input.equals("k")==true) {
				 if (gamecounter==0) { //Doelstelling 3: Twee kaarten bij de start
					System.out.println("Kaart 1:" + deck[gamecounter].naam);
					score += deck[gamecounter].punten;
				 	gamecounter++;
				 	System.out.println("Kaart 2:" + deck[gamecounter].naam);
				 	score += deck[gamecounter].punten;
				 	gamecounter++;
				 } else { //Doelstelling 3: A kan 11 punten of 1 punt waard zijn
				 System.out.println("Nieuwe kaart:"+ deck[gamecounter].naam);
				 	if (deck[gamecounter].punten==11 && score>=11) {
				 		score ++;
				 		gamecounter++;
				 	}	else {
				 		score += deck[gamecounter].punten;
				 		gamecounter++;
				 	}
				 }
		 	 } else if (input.equals("p")==true) {
		 		 break;
		 	 } else if (input.equals("q")==true) {
		 		 System.out.println("Einde");
		 		 System.exit(0);
		 	 } else { //Doelstelling 3: Foute input doet het programma niet vastlopen
		 		 System.out.println("Foute input, probeer opnieuw");
		 	 }
		 }	if (score ==21) {
			 System.out.println("21! U hebt gewonnen");
		 }	else if (score >= 22) {
			 System.out.println(score+ " punten, U hebt verloren");
		 }	else {
			 System.out.println("Eindscore: "+score);
		 }	
		 }
	}
}
class Deck {
	String kleur;
	String waarde;
	String naam;
	int punten;
		
	Deck(String kleur, String waarde) {
		this.naam = (kleur+" "+waarde);
		this.kleur = kleur;
		this.waarde = waarde;
		if (waarde.equals("twee")==true) {
			punten = 2;
		} else if (waarde.equals("drie")==true) {
			punten = 3;
		} else if (waarde.equals("vier")==true) {
			punten = 4;
		} else if (waarde.equals("vijf")==true) {
			punten = 5;
		} else if (waarde.equals("zes")==true) {
			punten = 6;
		} else if (waarde.equals("zeven")==true) {
			punten = 7;
		} else if (waarde.equals("acht")==true) {
			punten = 8;
		} else if (waarde.equals("negen")==true) {
			punten = 9;
		} else if (waarde.equals("tien")==true) {
			punten = 10;
		} else if (waarde.equals("boer")==true) {
			punten = 10;
		} else if (waarde.equals("vrouw")==true) {
			punten = 10;
		} else if (waarde.equals("heer")==true) {
			punten = 10;
		} else if (waarde.equals("A")==true) {
			punten = 11;
		}
	}
}