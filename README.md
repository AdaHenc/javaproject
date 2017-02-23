# javaproject
package grupowy;

import java.util.Scanner;

public class Program {

	public static Scanner userInput1 = new Scanner(System.in);
	public static Scanner userInput2 = new Scanner(System.in);
	public static Scanner userInput3 = new Scanner(System.in);
	public static Scanner userInput4 = new Scanner(System.in);
	public static Scanner userInput5 = new Scanner(System.in);
	public static Scanner userInput6 = new Scanner(System.in);
	public static Scanner userInput7 = new Scanner(System.in);
	public static Scanner userInput8 = new Scanner(System.in);

	public static void main(String[] arg){

		System.out.println("Do you already have an account (1) or would you like to register (2)?");
		int choiceLogOrReg = userInput1.nextInt();

		if (choiceLogOrReg == 1){
			System.out.println("Are you a user (1) or an admin (2)");
			int choiceUserOrAdmin = userInput2.nextInt();

			if (choiceUserOrAdmin == 1){
				runLoginUser();
			} else if (choiceUserOrAdmin == 2){
				runLoginAdmin();
			}
		} else if (choiceLogOrReg == 2){
			runRegister();
		}

	}

	public static void runRegister(){
		System.out.println("Type in your username: ");
		String newUserName = userInput3.nextLine();
		System.out.println("Type in your password: ");
		String newPassword = userInput4.nextLine();

		User newUser = new User(newUserName, newPassword);
		//write in file Users

		System.out.println("Your registration was succesfull.");
		runUser();

	}

	public static void runLoginAdmin(){
		while (true) {
			String userName = "admin";
			System.out.print("Password:");
			String password = userInput5.nextLine();
			if (ReadFile.checkPasswordByUsername(userName, password) == false){
				System.out.println("Invalid password. Try again.");
			} else {
				runUser();
				break;
			}
		}
	}

	public static void runAdmin(){
		printAdminMenu();
		while (true) {
			System.out.println("What do you want to do?");
			char adminChoice = userInput6.charAt(0);

			switch (adminChoice) {
			case 'A': 
				addRecipe();
				break;
			case 'B':
				removeRecipe();
				break;
			case 'C':
				editRecipe();
				break;
			case 'D':
				viewRanking();
				break;
			case 'E':
				changeUserInfo();
				break;
			case 'F':
				viewUserInfo();
				break;
			case 'G':
				System.out.println("Bye bye!");
				break;
			default:
				System.out.println("Invalid input.");
			}
		}

		public static void runLoginUser(){
			while (true) {
				System.out.println("What's your username?");
				String userName = userInput7.nextLine();

				if (ReadFile.checkIfUserExists(userName) == false){
					System.out.println("User does not exist. Try again.");
				} else {
					break;
				}
			} 

			while (true) {
				System.out.print("Password:");
				String password = userInput4.nextLine();
				if (ReadFile.checkPasswordByUsername(userName, password) == false){
					System.out.println("Invalid password. Try again.");
				} else {
					runUser();
					break;
				}
			}

		}


		public static void runUser(){
			printUserMenu();
			while (true) {
				System.out.println("What do you want to do?");
				char userChoice = userInput8.charAt(0);

				switch (userChoice) {
				case 'A': 
					searchForRecipe();
					break;
				case 'B':
					viewFavoriteRecipes();
					break;
				case 'C':
					changePassword();
					break;
				case 'D':
					System.out.println("Bye bye!");
					break;
				default:
					System.out.println("Invalid input.");
				}
			}
		}

		public static void printUserMenu(){
			System.out.println("A - search for a recipe");
			System.out.println("B - view favorite recipes");
			System.out.println("C - change user information");
			System.out.println("D - quit program");
		}

		public static void printAdminMenu(){
			System.out.println("A - add a new recipe");
			System.out.println("B - remove existing recipe");
			System.out.println("C - edit existing recipe");
			System.out.println("D - view ranking of favorite recipes");
			System.out.println("E - change user information");
			System.out.println("F - view user information");
			System.out.println("G - quit program");
		}

	}
