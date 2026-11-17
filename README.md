
    private int contador;
    private Mision[] misiones;

    
    public RegistroMision(int capacidad) {
        this.contador = 0;
        this.misiones = new Mision[capacidad];
    }

    public boolean agregar(Mision m) {

        if (this.contador == this.misiones.length) {
            return false;
           
        }

         this.misiones[this.contador] = m;
            this.contador++;
            return true;
    }

 
    public static String generarReporte(Mision[] lista) {

        
    StringBuilder reporte = new StringBuilder();

    reporte.append("--- REPORTE DE MISIONES ---\n");

    reporte.append(String.format(
        "%-10s | %-15s | %-5s | %-20s | %-15s%n",
        "CÓDIGO", "DESTINO", "AÑO", "COMANDANTE", "NAVE"
    ));


    reporte.append("-".repeat(77)).append("\n");

    int total = 0;

    if (lista != null) {
        for (Mision m : lista) {

            if (m != null) {
                reporte.append(String.format(
                    "%-10s | %-15s | %-5d | %-20s | %-15s%n",
                    m.getCodigo(),
                    m.getDestino(),
                    m.getAnio(),
                    m.getComandante(),
                    m.getNave()
                ));

                total++;
            }
        }
    }

  
    reporte.append("-".repeat(77)).append("\n");

    reporte.append("Total de misiones: ").append(total);

    return reporte.toString();
    }

   
    public Mision[] obtenerTodas() {

        return Arrays.copyOf(this.misiones, this.contador);
    }
