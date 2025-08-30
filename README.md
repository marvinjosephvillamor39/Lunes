INTERFACE ning Dave, Joseph, Taguba, Villamor

package Interfeeze;

public interface Dave<Double> {
	
	double add(int x, int y);
	double min(int x, int y);
	double mul(int x, int y);
	double div(int x, int y);
	
	

}

package Interfeeze;

public interface Joseph<Integer> {
	
	void add(int x);
	void red(int x);
	void size();
	boolean isFull();

}

package Interfeeze;

public class Taguba<Double> implements Dave<Double> {

	public double add(int x, int y) {
		return x+y;
	}

	public double min(int x, int y) {
		return x-y;
	}

	public double mul(int x, int y) {
		return x*y;
	}

	public double div(int x, int y) {
		return x/y;
	}

}

package Interfeeze;

public class Villamor<Integer> implements Joseph<Integer> {
	
	private int amount = 0;
	

	public void add(int x) {
		amount += x;
		System.out.println("You have added "+x+" Liter/s");
		check(x);
	}

	public void red(int x) {
		amount -= x;
		System.out.println("You have drained "+x+" Liter/s");
		check(x);
	}

	public void size() {
		System.out.println("The amount of water is " + amount + " Liter/s");
	}

	public boolean isFull() {
		return amount == 100;
	}
	
	private void check(int x) {
		if(amount > 100) {
			System.out.println("The water tank is overflowing. You died due to drowning.");
			System.exit(0);
		}
		if(amount < 0) {
			System.out.println("There's no water left. You died due to drought.");
			System.exit(0);
		}
	}

}


MAIN NI KARL


package Main;

import java.util.Scanner;
import Interfeeze.Villamor;
import Interfeeze.Taguba;

public class Carl {
	
	static Scanner scn = new Scanner(System.in);
	static Villamor wat = new Villamor<Integer>();
	static Taguba calc = new Taguba<Double>();
	
		
	static void water(){
		
		System.out.println("\n\n\nWater Tank:\n1 Fill\n2 Drain\n3 Size\n4 Tank is full\n5 Return");
		int a = scn.nextInt();
		
		switch(a) {
		case 1: 
			System.out.print("How much liters? ");
			wat.add(scn.nextInt());
			break;
		case 2: 
			System.out.print("How much liters? ");
			wat.red(scn.nextInt());
			break;
		case 3: 
			wat.size();
			break;
		case 4: 
			System.out.println(wat.isFull());;
			break;
		case 5: 
			menu();
			break;
		default:
			System.out.println("Invalid choice!");
		}
		
		water();
	}
	
	static void calculator() {
		System.out.println("\n\n\nCalculator:\n1 +\n2 -\n3 *\n4 /\n5 Return");
		int a = scn.nextInt();
		
		
		switch(a) {
		case 1:
			System.out.print("Num1: ");
			int num1 = scn.nextInt();
			System.out.print("Num2: ");
			int num2 = scn.nextInt();
			System.out.println(num1 + " + " + num2 + " = " + calc.add(num1,num2));
			break;
		case 2:
			System.out.print("Num1: ");
			num1 = scn.nextInt();
			System.out.print("Num2: ");
			num2 = scn.nextInt();
			System.out.println(num1 + " - " + num2 + " = " + calc.min(num1,num2));
			break;
		case 3:
			System.out.print("Num1: ");
			num1 = scn.nextInt();
			System.out.print("Num2: ");
			num2 = scn.nextInt();
			System.out.println(num1 + " * " + num2 + " = " + calc.mul(num1,num2));
			break;
		case 4:
			System.out.print("Num1: ");
			num1 = scn.nextInt();
			System.out.print("Num2: ");
			num2 = scn.nextInt();
			System.out.println(num1 + " / " + num2 + " = " + calc.div(num1,num2));
			break;
		case 5:
			menu();
			break;
		default:
			System.out.println("Invalid choice!");
		}
		calculator();
	}

	static void menu() {
		
		System.out.println("Test:\n1 Water Tank\n2 Calculator\n3 Exit");
		int a = scn.nextInt();
		
		switch(a){
		case 1: 
			water();
			break;
		case 2: 
			calculator();
			break;
		case 3:
			System.out.println("Ok bye-bye!");
			System.exit(0);
			break;
		default:
			System.out.println("Invalid choice!");
			menu();
		}
	}
		
	public static void main(String[] args) {
		menu();
	}

}
