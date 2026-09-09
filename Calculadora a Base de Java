import java.util.InputMismatchException;
import java.util.Locale;
import java.util.Scanner;
 
public class Calculadora {
 
    public static void main(String[] args) {
        // useLocale(Locale.US) fuerza el punto como separador decimal (3.5 y no 3,5)
        Scanner sc = new Scanner(System.in).useLocale(Locale.US);
        boolean seguir = true;
 
        System.out.println("=== Calculadora ===");
        System.out.println("Operaciones: +  -  *  /   (escribe 'salir' para terminar)");
 
        while (seguir) {
            double a = leerNumero(sc, "\nPrimer numero: ");
            String op = leerOperador(sc);
 
            if (op.equalsIgnoreCase("salir")) {
                seguir = false;
                continue;
            }
 
            double b = leerNumero(sc, "Segundo numero: ");
 
            try {
                double resultado = calcular(a, op, b);
                System.out.printf(Locale.US, "Resultado: %.4f%n", resultado);
            } catch (ArithmeticException e) {
                System.out.println("Error: " + e.getMessage());
            } catch (IllegalArgumentException e) {
                System.out.println("Error: " + e.getMessage());
            }
        }
 
        System.out.println("Chao.");
        sc.close();
    }
 
    /** Hace la operacion. Separada del main para poder probarla sola. */
    public static double calcular(double a, String op, double b) {
        return switch (op) {
            case "+" -> a + b;
            case "-" -> a - b;
            case "*" -> a * b;
            case "/" -> {
                if (b == 0) {
                    throw new ArithmeticException("no se puede dividir por cero");
                }
                yield a / b;
            }
            default -> throw new IllegalArgumentException("operador desconocido: " + op);
        };
    }
 
    /** Pide un numero hasta que el usuario escriba uno valido. */
    private static double leerNumero(Scanner sc, String mensaje) {
        while (true) {
            System.out.print(mensaje);
            try {
                return sc.nextDouble();
            } catch (InputMismatchException e) {
                sc.next(); // descarta la basura, si no queda en un loop infinito
                System.out.println("Eso no es un numero. Usa punto para decimales (ej: 3.5)");
            }
        }
    }
 
    private static String leerOperador(Scanner sc) {
        System.out.print("Operacion (+ - * / o 'salir'): ");
        return sc.next();
    }
}
