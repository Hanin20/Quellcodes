# 
import java.util.*;

public class Umrechnung {

	/*
	 * Methode mit Rückgabewert (von der Datentyp int) und Parameterübergabe
	 * (Datentyp: String) zur Umrechnung von römischen Zahlen in Dezimalzahlen.
	 */
	public static int RomToDez(String rom) {

		int dez = 0;

		/*
		 * Die Zeile "for (int i = 0; rom.length() > i; i++)" initialisiert eine
		 * Schleifenvariable i mit 0 und führt die Schleife aus, solange i kleiner ist
		 * als die Länge des Strings rom. In jedem Schleifendurchlauf wird i um 1
		 * erhöht. Dies wird verwendet, um durch die Zeichen eines Strings rom zu
		 * iterieren (also jedes Zeichen im String wird einzeln betrachtet oder
		 * verarbeitet).
		 */
		for (int i = 0; rom.length() > i; i++) {

			char eingabe = rom.charAt(i); // einzelne String Zeichen ausselen
			char zeichen;

/*
// Dieser Abschnitt des Codes überprüft, ob die römische Ziffer an der aktuellen Position
// kleiner ist als die folgende Ziffer. Wenn ja, wird der entsprechende dezimale Wert subtrahiert,
// gemäß den Regeln der römischen Zahlen.
*/ 

			if (i + 1 != rom.length()) {

				zeichen = rom.charAt(i + 1);

				if (eingabe == 'I' && (zeichen == 'V' || zeichen == 'X' || zeichen == 'L' || zeichen == 'C'
						|| zeichen == 'D' || zeichen == 'M')) {

					dez = dez - 1;
					continue;
					// Wenn das zutrifft, wird die aktuelle Durchlauf der Schleife übersprungen und
					// der nächsten durchgeführt.
				}

				if (eingabe == 'V'
						&& (zeichen == 'X' || zeichen == 'L' || zeichen == 'C' || zeichen == 'D' || zeichen == 'M')) {
					dez = dez - 5;
					continue;
				}

				if (eingabe == 'X' && (zeichen == 'L' || zeichen == 'C' || zeichen == 'D' || zeichen == 'M')) {
					dez = dez - 10;
					continue;
				}

				if (eingabe == 'L' && (zeichen == 'C' || zeichen == 'D' || zeichen == 'M')) {
					dez = dez - 50;
					continue;
				}

				if (eingabe == 'C' && (zeichen == 'D' || zeichen == 'M')) {
					dez = dez - 100;
					continue;
				}

				if (eingabe == 'D' && zeichen == 'M') {
					dez = dez - 500;
					continue;
				}
			}

/* 
Der Code analysiert römische Zahlensymbole und berechnet den entsprechenden dezimalen Wert.
*/



			switch (eingabe) {

			case 'I':
				dez = dez + 1;
				break;

			case 'V':
				dez = dez + 5;
				break;
			case 'X':
				dez = dez + 10;
				break;
			case 'L':
				dez = dez + 50;
				break;
			case 'C':
				dez = dez + 100;
				break;
			case 'D':
				dez = dez + 500;
				break;
			case 'M':
				dez = dez + 1000;
				break;

			}
		}

		return dez; // Da die Methode mit Rückgabewert ist, muss sie mit ihre Rückgabewert beendet
					// werden.

	}

	/*
	 * Methode mit Rückgabewert (von der Datentyp String) und Parameterübergabe
	 * (Datentyp: int) zur Umrechnung von Dezimalzahlen in römischen Zahlen in .
	 */
	public static String DecInRom(int dez) {

		String newRom = "";

		while (dez > 0) {
/* 
überprüft in aufeinanderfolgenden if-Bedingungen, ob die Dezimalzahl größer 
oder gleich bestimmten Werten (z.B., 1000, 900, 500, usw.) ist, 
und fügt dann die entsprechenden römischen Ziffern zur newRom-Zeichenkette hinzu.
Dabei wird die Dezimalzahl entsprechend reduziert, bis sie schließlich den Wert 0 erreicht.
*/ 

			if (dez >= 1000) {

				newRom = newRom + "M";
				dez = dez - 1000;

			}

			else if (dez >= 900) {
				newRom = newRom + "CM";
				dez = dez - 900;
			}

			else if (dez >= 500) {

				dez = dez - 500;
				newRom = newRom + "D";
			}

			else if (dez >= 400) {
				newRom = newRom + "CD";
				dez = dez - 400;
			}

			else if (dez >= 100) {
				dez = dez - 100;
				newRom = newRom + "C";
			}

			else if (dez >= 90) {
				newRom = newRom + "XC";
				dez = dez - 90;
			}

			else if (dez >= 50) {
				dez = dez - 50;
				newRom = newRom + "L";
			}

			else if (dez >= 40) {
				newRom = newRom + "XL";
				dez = dez - 40;
			}

			else if (dez >= 10) {
				dez = dez - 10;
				newRom = newRom + "X";
			}

			else if (dez >= 9) {
				newRom = newRom + "IX";
				dez = dez - 9;
			}

			else if (dez >= 5) {
				dez = dez - 5;
				newRom = newRom + "V";
			}

			else if (dez >= 4) {
				newRom = newRom + "IV";
				dez = dez - 4;
			}

			else if (dez >= 1) {
				dez = dez - 1;
				newRom = newRom + "I";
			}

		}

		return newRom;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		String[] romNumber = { "I", "V", "X", "L", "C", "D", "M" };
		int[] dezNumber = { 1, 5, 10, 50, 100, 500, 1000 };

		Scanner sc = new Scanner(System.in);

		while (true) {

			System.out.println(
					"Geben Sie 1 oder 2: (1 für Römischzahl -> Dezimalzahl und 2 für Dezimalzahl -> Römischzahl)");
			String eingabe = sc.nextLine();

			if (eingabe.equals("1")) {

				System.out.println("Geben Sie ein römischen Zahl ein: ");
				String rom = sc.nextLine();

				int dez = RomToDez(rom);
				System.out.println("Der Dezimalzahl lautet: " + dez);
			}

			else {
				System.out.println("Geben Sie den Dezimalzahl ein:");
				int dez = sc.nextInt();
				sc.nextLine();

				String newRom = DecInRom(dez);

				System.out.println("Der Römischen Zahl lautet: " + newRom);

			}

			System.out.println("Möchten Sie andere Umrechnung durchführen? \nGeben Sie J/N: ");
			eingabe = sc.nextLine();
			if (!eingabe.equals("J")) {
				break;
			}
		}

		System.out.println("Ende des Programms!");
	}
}
