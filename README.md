# PILA-Y-COLA
TAREA
1.	Crear un programa en java que permita Invertir una cadena usando una Pila. - Este programa leerá una cadena de texto ingresada por el usuario, utilizará una pila para invertir la cadena y luego mostrará la cadena invertida. Ejemplo Ingresa “ESTUDIANTES”, mostrará “SETNAIDUTSE”
/**
	Invertir una cadena en Java, método 1
*/
class Main {
	public static void main(String[] args) {
		String cadena = "ESTUDIANTES";
		// Esta será la cadena invertida, primero está vacía
		String invertida = "";
		// Recorremos la original del final al inicio
		for (int indice = cadena.length() - 1; indice >= 0; indice--) {
			// Y vamos concatenando cada carácter a la nueva cadena
			invertida += cadena.charAt(indice);
		}
		System.out.println("Cadena original: " + cadena);
		System.out.println("Cadena invertida: " + invertida);

	}
}
2.-	Crea un programa que permita ingresar 10 valores en una Cola y luego muestre la Cola ordenada en forma ascendente.
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Queue<Integer> cola = new LinkedList<>();

        Scanner sc = new Scanner(System.in);

        System.out.println("Ingresa 10 valores:");

        for (int i = 0; i < 10; i++) {
            int valor = sc.nextInt();
            cola.offer(valor);
        }

        ordenarCola(cola);

        System.out.println("Cola ordenada en forma ascendente:");
        for (int num : cola) {
            System.out.print(num + " ");
        }
    }

    public static void ordenarCola(Queue<Integer> cola) {
        int n = cola.size();

        for (int i = 0; i < n; i++) {
            int minIndex = minIndex(cola, n - i);
            insertMinToRear(cola, minIndex);
        }
    }

    public static int minIndex(Queue<Integer> cola, int sortIndex) {
        int minIndex = -1;
        int minValue = Integer.MAX_VALUE;
        int n = cola.size();

        for (int i = 0; i < n; i++) {
            int current = cola.poll();

            if (current <= minValue && i <= sortIndex) {
                minIndex = i;
                minValue = current;
            }

            cola.offer(current);
        }

        return minIndex;
    }

    public static void insertMinToRear(Queue<Integer> cola, int minIndex) {
        int minValue = 0;
        int n = cola.size();

        for (int i = 0; i < n; i++) {
            int current = cola.poll();

            if (i != minIndex) {
                cola.offer(current);
            } else {
                minValue = current;
            }
        }

        cola.offer(minValue);
    }
}

3.-	Crear un programa que permita ingresar dos Colas de enteros por separado, además deberá ordenarlas de menor a mayor y que devuelva una nueva Cola como unión de ambas con sus elementos ordenados de la misma forma.
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class UnionColas {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        Queue<Integer> cola1 = new LinkedList<>();
        Queue<Integer> cola2 = new LinkedList<>();
        
        System.out.println("Ingrese los elementos de la primera cola separados por espacios:");
        String[] elementos1 = sc.nextLine().split(" ");
        for(String elemento : elementos1) {
            cola1.add(Integer.parseInt(elemento));
        }
        
        System.out.println("Ingrese los elementos de la segunda cola separados por espacios:");
        String[] elementos2 = sc.nextLine().split(" ");
        for(String elemento : elementos2) {
            cola2.add(Integer.parseInt(elemento));
        }
        
        Queue<Integer> colaUnion = unirColasOrdenadas(cola1, cola2);
        
        System.out.println("Cola unida y ordenada: ");
        for(Integer elemento : colaUnion) {
            System.out.print(elemento + " ");
        }
    }

    public static Queue<Integer> unirColasOrdenadas(Queue<Integer> cola1, Queue<Integer> cola2) {
        Queue<Integer> colaUnion = new LinkedList<>();
        
        while(!cola1.isEmpty() && !cola2.isEmpty()) {
            if(cola1.peek() < cola2.peek()) {
                colaUnion.add(cola1.poll());
            } else {
                colaUnion.add(cola2.poll());
            }
        }
        
        while(!cola1.isEmpty()) {
            colaUnion.add(cola1.poll());
        }
        
        while(!cola2.isEmpty()) {
            colaUnion.add(cola2.poll());
        }
        
        return colaUnion;
    }
}

4.	Diseñe un programa en java que permita el ingreso de 10 números (entre cero y diez) de forma desordenada en una pila, luego el programa imprima en letra el número que contiene la pila, Ejemplo:

import java.util.Stack;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Stack<Integer> pila = new Stack<>();
        Scanner sc = new Scanner(System.in);

        System.out.println("Ingrese 10 números entre 0 y 10 de forma desordenada:");

        for (int i = 0; i < 10; i++) {
            int numero = sc.nextInt();
            if (numero >= 0 && numero <= 10) {
                pila.https://www.onlinegdb.com/online_java_compiler#push(numero);
            } else {
                System.out.println("Número fuera de rango, ingrese nuevamente.");
                i--;
            }
        }

        while (!pila.isEmpty()) {
            int numero = pila.pop();
            switch (numero) {
                case 1:
                    System.out.println("Uno");
                    break;
                case 2:
                    System.out.println("Dos");
                    break;
                case 3:
                    System.out.println("Tres");
                    break;
                case 4:
                    System.out.println("Cuatro");
                    break;
                case 5:
                    System.out.println("Cinco");
                    break;
                case 6:
                    System.out.println("Seis");
                    break;
                case 7:
                    System.out.println("Siete");
                    break;
                case 8:
                    System.out.println("Ocho");
                    break;
                case 9:
                    System.out.println("Nueve");
                    break;
                case 10:
                    System.out.println("Diez");
                    break;
                default:
                    System.out.println("Número no válido");
            }
        }
    }
}

   
