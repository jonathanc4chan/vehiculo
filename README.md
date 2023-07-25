import java.util.Scanner;
public class Vehiculos {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Bienvenido a la aplicación para calcular la velocidad promedio de vehículos de carreras.");

        int numVehiculos;
        do {
            System.out.print("Ingrese el número de vehículos en la competencia (debe ser mayor a 0): ");
            numVehiculos = scanner.nextInt();
        } while (numVehiculos <= 0);

        double[] sumTiempos = new double[numVehiculos];
        int[] numVueltas = new int[numVehiculos];

        for (int i = 0; i < numVehiculos; i++) {
            System.out.println("\nVehículo " + (i + 1));
            int numVueltasVehiculo;
            do {
                System.out.print("Ingrese el número de vueltas recorridas por el vehículo (debe ser mayor a 0): ");
                numVueltasVehiculo = scanner.nextInt();
            } while (numVueltasVehiculo <= 0);

            int vuelta = 1;
            while (vuelta <= numVueltasVehiculo) {
                System.out.print("Ingrese el tiempo en segundos de la vuelta " + vuelta + ": ");
                double tiempoVuelta = scanner.nextDouble();
                sumTiempos[i] += tiempoVuelta;
                vuelta++;
            }

            numVueltas[i] = numVueltasVehiculo;
        }

        System.out.println("\nResultados:");
        for (int i = 0; i < numVehiculos; i++) {
            double velocidadPromedio = calcularVelocidadPromedio(sumTiempos[i], numVueltas[i]);
            System.out.println("Vehículo " + (i + 1) + ": Velocidad Promedio = " + velocidadPromedio + " m/s");
        }
    }

    private static double calcularVelocidadPromedio(double tiempoTotal, int numVueltas) {
        // Suponemos que la longitud del circuito es constante para todos los vehículos.
        double longitudCircuito = 4000; // Longitud del circuito en metros
        double tiempoTotalSegundos = tiempoTotal * 60; // Convertir a segundos
        return longitudCircuito / (tiempoTotalSegundos * numVueltas);}
}
