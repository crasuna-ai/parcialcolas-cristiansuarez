public class Articulo {
    private String nombre;
    private double precio;
    private int cantidad;

    public Articulo(String nombre, double precio, int cantidad) {
        this.nombre = nombre;
        this.precio = precio;
        this.cantidad = cantidad;
    }

    public String getNombre() {
        return nombre;
    }

    public double getPrecio() {
        return precio;
    }

    public void setPrecio(double precio) {
        this.precio = precio;
    }

    public int getCantidad() {
        return cantidad;
    }

    public void setCantidad(int cantidad) {
        this.cantidad = cantidad;
    }

    @Override
    public String toString() {
        return "Nombre: " + nombre + ", Precio: $" + precio + ", import javax.swing.*;
import java.util.LinkedList;
import java.util.Queue;

public class SistemaVentas {
    private Queue<Articulo> cola = new LinkedList<>();

    public void iniciar() {
        while (true) {
            String opcion = JOptionPane.showInputDialog("""
                    1. Ingresar artículo
                    2. Vender artículo
                    3. Modificar artículo
                    4. Eliminar artículo
                    5. Mostrar artículos
                    6. Salir""");

            if (opcion == null) break;

            switch (opcion) {
                case "1" -> ingresarArticulo();
                case "2" -> venderArticulo();
                case "3" -> modificarArticulo();
                case "4" -> eliminarArticulo();
                case "5" -> mostrarArticulos();
                case "6" -> System.exit(0);
                default -> JOptionPane.showMessageDialog(null, "Opción no válida.");
            }
        }
    }

    private void ingresarArticulo() {
        try {
            String nombre = JOptionPane.showInputDialog("Nombre del artículo:");
            if (nombre == null || nombre.trim().isEmpty())
                throw new Exception("Nombre inválido");

            double precio = Double.parseDouble(JOptionPane.showInputDialog("Precio:"));
            if (precio <= 0) throw new Exception("Precio debe ser mayor a 0");

            int cantidad = Integer.parseInt(JOptionPane.showInputDialog("Cantidad:"));
            if (cantidad <= 0) throw new Exception("Cantidad debe ser mayor a 0");

            cola.add(new Articulo(nombre.trim(), precio, cantidad));
            JOptionPane.showMessageDialog(null, "Artículo agregado correctamente.");
        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, "Error: " + e.getMessage());
        }
    }

    private void venderArticulo() {
        if (cola.isEmpty()) {
            JOptionPane.showMessageDialog(null, "No hay artículos para vender.");
            return;
        }

        try {
            double ventaPromedio = Double.parseDouble(JOptionPane.showInputDialog("Ingrese la venta promedio:"));
            if (ventaPromedio <= 0) throw new Exception("Debe ser mayor a 0");

            String nombre = JOptionPane.showInputDialog("Nombre del artículo a vender:");
            if (nombre == null || nombre.trim().isEmpty())
                throw new Exception("Nombre inválido");

            boolean encontrado = false;
            for (Articulo art : cola) {
                if (art.getNombre().equalsIgnoreCase(nombre.trim())) {
                    double precioFinal = art.getPrecio();
                    if (precioFinal > ventaPromedio) {
                        precioFinal *= 0.9;
                    }
                    JOptionPane.showMessageDialog(null, "Artículo vendido\nPrecio final: $" + precioFinal);
                    encontrado = true;
                    break;
                }
            }

            if (!encontrado) {
                JOptionPane.showMessageDialog(null, "Artículo no encontrado.");
            }

        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, "Error: " + e.getMessage());
        }
    }

    private void modificarArticulo() {
        if (cola.isEmpty()) {
            JOptionPane.showMessageDialog(null, "No hay artículos para modificar.");
            return;
        }

        try {
            double ventaPromedio = Double.parseDouble(JOptionPane.showInputDialog("Ingrese la venta promedio:"));
            if (ventaPromedio <= 0) throw new Exception("Debe ser mayor a 0");

            String nombre = JOptionPane.showInputDialog("Nombre del artículo a modificar:");
            if (nombre == null || nombre.trim().isEmpty())
                throw new Exception("Nombre inválido");

            boolean modificado = false;
            for (Articulo art : cola) {
                if (art.getNombre().equalsIgnoreCase(nombre.trim())) {
                    double nuevoPrecio = Double.parseDouble(JOptionPane.showInputDialog("Nuevo precio:"));
                    if (nuevoPrecio <= 0) throw new Exception("Precio inválido");

                    if (nuevoPrecio > ventaPromedio) {
                        nuevoPrecio *= 0.9;
                    }

                    int nuevaCantidad = Integer.parseInt(JOptionPane.showInputDialog("Nueva cantidad:"));
                    if (nuevaCantidad <= 0) throw new Exception("Cantidad inválida");

                    art.setPrecio(nuevoPrecio);
                    art.setCantidad(nuevaCantidad);

                    JOptionPane.showMessageDialog(null, "Artículo modificado.");
                    modificado = true;
                    break;
                }
            }

            if (!modificado) {
                JOptionPane.showMessageDialog(null, "Artículo no encontrado.");
            }

        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, "Error: " + e.getMessage());
        }
    }

    private void eliminarArticulo() {
        if (cola.isEmpty()) {
            JOptionPane.showMessageDialog(null, "No hay artículos para eliminar.");
            return;
        }

        String nombre = JOptionPane.showInputDialog("Nombre del artículo a eliminar:");
        if (nombre == null || nombre.trim().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Nombre inválido");
            return;
        }

        boolean eliminado = false;
        int tamaño = cola.size();
        for (int i = 0; i < tamaño; i++) {
            Articulo actual = cola.poll();
            if (actual.getNombre().equalsIgnoreCase(nombre.trim())) {
                eliminado = true;
                JOptionPane.showMessageDialog(null, "Artículo eliminado correctamente.");
            } else {
                cola.add(actual);
            }
        }

        if (!eliminado) {
            JOptionPane.showMessageDialog(null, "Artículo no encontrado.");
        }
    }

    private void mostrarArticulos() {
        if (cola.isEmpty()) {
            JOptionPane.showMessageDialog(null, "No hay artículos en el inventario.");
            return;
        }

        StringBuilder sb = new StringBuilder("Artículos en inventario:\n");
        for (Articulo art : cola) {
            sb.append(art.toString()).append("\n");
        }
        JOptionPane.showMessageDialog(public class Main {
    public static void main(String[] args) {
        SistemaVentas sistema = new SistemaVentas();
        sistema.iniciar();
    }
}      
