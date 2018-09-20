# TP-OBLIGATORIO
import java.util.Scanner;

/**
 *
 * @author dante.giuliano
 */
public class DanteGiuliano {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
           Scanner lectura=new Scanner(System.in);
      Clase arbol = new Clase();
      int longitud;
        System.out.println("cuantos arboles desea ingresar el usuario?");
       longitud=lectura.nextInt();
      Clase Arbol[] = new Clase [longitud];
       
           System.out.println("");
        menu(Arbol,longitud);
    }
    public static void menu(Clase Arbol[],int largo){
        int opcion,acumulador=-1;
        Scanner lectura=new Scanner(System.in);
        System.out.println("bienvenido al menu ");
        System.out.println("1-Carga datos del arreglo");
        System.out.println("\"2-los arboles que miden mas de 10 mts\"");
        System.out.println("\"3-contar los arboles que soportan menos de 0 grados");
        System.out.println("\"4- mostrar todos los arboles\"");     
        System.out.println("ingrese una opcion");
        opcion=lectura.nextInt();
        switch(opcion){
            case 1:acumulador++;
                Opcion1(Arbol,largo,acumulador);
                break;
            case 2:
                break;
            case 3:
                break;
            case 4: 
                break;
            default : System.out.println("numero incorrecto");
                menu(Arbol,largo);
        }
        }
    
public static void Opcion1(Clase Arbol[],int largo,int acumulador){
    System.out.println("Su arreglo restante  es de "+largo);
    Scanner lectura = new Scanner(System.in);
    boolean carga=false;
    int acum=0;
   String validacion;
   int a=acumulador;
    do{
        for (int i = 0; i < Arbol.length; i++){
           Arbol[a]=new Clase();
            System.out.println("ingrese el nombre del arbol");
            Arbol[a].setNombre(lectura.next());
            //inicio la validacion del arreglo
            validacion=Arbol[a].getNombre();
            //llamo al modulo para verificar si esta o no repetido
            if(Verificacion(validacion,Arbol)){
            System.out.println("ingrese la altura del arbol");
           Arbol[a].setAltura(lectura.nextInt());
                System.out.println("ingrese la profundidad de raices");
           Arbol[a].setProfundidadRaices(lectura.nextInt());
                System.out.println("tiene frutos?");
           Arbol[a].setFrutos(lectura.hasNextBoolean());
                System.out.println("que temperatura soporta");
           Arbol[a].setTemperaturaMinima(lectura.nextInt());
           acum++;
            }
                    }
        
    }
    while(carga==true);
    
}    
        public static boolean Verificacion(String comparacion,Clase Arbol[]){
           boolean repetido=false,recorrido=true;
           int acum=0;
           do{
               if(Arbol[acum].getNombre().equals(comparacion)){
                   repetido=false;
               }
               acum++;
                 }
           while(acum<Arbol.length);
           return repetido;   
        }
      
            
        
}
