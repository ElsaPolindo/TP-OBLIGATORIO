/*
 */
package tpobligatorio;
import java.util.Scanner;
/**
 * @author Dante Giulianno Fai 2062 Desarrollo de Algoritmos 2018 
 EL programa costa de una longitud inicial pedida al usuario
 junto con una carga inicial de 10 espacios de memoria del arreglo 
 para acceder al menu. 
 * El usuario debe estar en el menu para finalizar el programa
 
 nombre de la clase sera "Arbol" la referencia sera Arreglo
 Programado en Netbeants 8.2 
 * //Correcciones de Ingrid-Godoy:
 *Correcciones:
La clase Arbol debe llamarse Arbol, no Clase.
El diagrama UML no tiene contructor sin parametros.
El método setNombre no figura en el UML.
Faltan métodos equals y toString.
Los métodos deben estar ordenados por tipo para mayor claridad. El diagama UML debe respetarse.
En el test, los métodos que muestran datos deben usar el método toString.
 * 
 * 
 * //
 */
public class TpObligatorio {
    /**
     * @param args the command line arguments
     */
public static void main(String[] args) {
      //declaracion de las clases usadas en el programa
     Scanner lectura=new Scanner(System.in);
     Arbol arregloPre[]=new Arbol[10];
     arregloPre[0]=new Arbol("manzano",12,4,true,45);
     arregloPre[1]=new Arbol("jatalapa",8,3,true,50);
     arregloPre[2]=new Arbol("banano",3,2,false,25);
     arregloPre[3]=new Arbol("castaño",4,5,true,-50);
     arregloPre[4]=new Arbol("xhiamo",16,6,false,-5);
     arregloPre[5]=new Arbol("eucalipto",32,12,true,78);
     arregloPre[6]=new Arbol("pino",80,45,false,-15);
     arregloPre[7]=new Arbol("duraznero",3,1,true,48);
     arregloPre[8]=new Arbol("roble",34,17,false,130);
     arregloPre[9]=new Arbol("higuera",2,1,true,60);
      //Paametrizacion y declaracion de Variables;
      int longitud;
      //inicio de Algoritmo
       System.out.println("cuantos arboles desea ingresar el usuario?");
       longitud=lectura.nextInt()+10;
      Arbol arreglo[] = new Arbol[longitud];
    combinacion(arregloPre,arreglo);       
    }
public static void menu(Arbol arreglo[],int ciclos,boolean ordenado){
    int aux=0;
    Arbol  arrayAux[]; 
    //declaracion de clase para la lectura
        Scanner lectura =new Scanner(System.in);
    //declaracion de variables para este modulo
        int opcion;
    //interaccion con el usuario
    System.out.println("*_________________________________________________________________");
        System.out.println("|bienvenido al menu                                               | ");
        System.out.println("|1-Carga datos del arreglo                                        | ");
        System.out.println("|2-mostrar los arboles de mas de 10 mts de altura                 | ");
        System.out.println("|3-los arboles que soportan tempearaturas por debajo de los 0°    | ");
        System.out.println("|4-mostrar el nombre de los arboles frutales                      | ");
        System.out.println("|5-mostrar todos los Arboles                                      | ");
        System.out.println("|6-Buscar por altura                                              | ");
        System.out.println("|7-Ordenar arreglo                                                | ");
        System.out.println("|8-Ordenar Arreglo Metodo QuickSort                               | ");
        System.out.println("|9-Busqueda de Arboles Metodo Binario                             | ");
        System.out.println("|10-Finalzar el programa                                          | ");
        System.out.println("|**************************                                       | ");
        System.out.println("|0-desordenar arreglo                                             | ");
        System.out.println("|_________________________________________________________________|");
    //lectura para ejecutar las opciones disponibles
       opcion=lectura.nextInt();
        switch(opcion){
            //caso especial desordenar arreglo
            case 0:
            if(ciclos<=arreglo.length-1){
                  desordenarArray(arreglo,ciclos,ordenado);}
            else{
                System.out.println("error iminente");
                menu(arreglo,ciclos,ordenado);
            }
            break;
            //Carga nunevos Arboles
            case 1: ciclos++;
            if(ciclos<arreglo.length){
                cargaArboles(arreglo,ciclos,ordenado);}
            else{
                ciclos--;
                System.out.println("supero el arreglo :( debe pedir un nuevo lote de Arboles");
                System.out.println("nuevo lote de arboles");
                aux=lectura.nextInt();
                arrayAux=new Arbol[arreglo.length+aux];
                combinacion(arreglo,arrayAux); 
            }
                break;
                //Muestra los arboles de mas de 10 mts
            case 2:arbolesDeMasDe10mts(arreglo,ciclos,ordenado);
                break;
                //muestra los arboles con temperaturas bajas
            case 3:arbolesQueSoportanMenosDe0(arreglo,ciclos,ordenado);
                break;
                //muestra el nombre de los arboles frutales
            case 4:arbolesFrutales(arreglo,ciclos,ordenado);
                break; 
//segunda parte--------------------------------------------------------------
             //muestra todos los nombres de los Arboles
            case 5:mostrarArboles(arreglo,ciclos,ordenado);
            break;
            //busca los arboles de X altura
            case 6:int recorrido=0,numero,acum=0;
                System.out.println("ingrese la altura para buscar ");
                numero=lectura.nextInt();
                acum=busquedaPorAlturaRecursiva(arreglo,ciclos,recorrido,numero,acum);
                System.out.println("los arboles con la altura: "+numero+" son: "+acum);
                menu(arreglo,ciclos,ordenado);
            break;
            //metodos para ordenar Arrays
            case 7:if(ordenado==false){
                 ordenarArray(arreglo,ciclos,ordenado);}
            else{
                System.out.println("Arreglo Ordenado (: pruebe usando la opcion 0 para desordenarlo");
                menu(arreglo,ciclos,ordenado);
            }
            break;
            //metodo avanzado de Ordenamiento
            case 8:if(ordenado==true){
                System.out.println(" el arreglo esta ordenado pruebe a desordenarlo con la opcion"
                        + " 0 (:");
                menu(arreglo,ciclos,ordenado);
            }
                else{
                        int der=ciclos;
                        int izq=0;
                        quickSort(arreglo,izq,der,ciclos,ordenado);
                        }
            break;
            //metodo de busqueda binaria SIN RECURSION
            case 9 :if(ordenado==true){
                System.out.println("ingrese el nombre de un arbol para buscar");
                String nombre=lectura.next();
               busquedaBinaria(arreglo,nombre,ciclos,ordenado);          
            }
            else{
                System.out.println("arreglo no ordenado con el metodo 7, ordene el arreglo "
                        + " mediante un metodo de ordenamiento de la opcion 7");
                menu(arreglo,ciclos,ordenado);
            }
            break; 
            case 10:Finalizacion();
                break;
            default : System.out.println("numero incorrecto");
                menu(arreglo,ciclos,ordenado);
                break;
        }
        }
//primera parte del tp
public static void arbolesFrutales(Arbol arreglo[],int ciclos,boolean ordenado){
    int acum=0;
    System.out.println("-------------------------------------------");
        for (int i = 0; i<ciclos; i++) {
            if(arreglo[i].getFrutos()==true){
                System.out.println("Arbol frutal n°: "+(i+1));
                System.out.println(arreglo[i].getNombre());
            } 
    }
        System.out.println("-------------------------------------------");
        menu(arreglo,ciclos,ordenado);
}
public static void arbolesQueSoportanMenosDe0(Arbol arreglo[],int ciclos,boolean ordenado){
    int acum=0;
    for (int i = 0; i <ciclos; i++) {
        if(arreglo[i].getTemperaturaMinima()<0){
            acum++;
        }
    }
    System.out.println("los arboles que soportan T° por debajo de los 0° son "+acum);
    System.out.println(" \n________________________________________________________________");
    menu(arreglo,ciclos,ordenado);  
}
public static void arbolesDeMasDe10mts(Arbol arreglo[],int ciclos,boolean ordenado){
    for (int i = 0; i<ciclos; i++) {
        if(arreglo[i].getAltura()>10){
            System.out.println("-------------Arbol n° "+(i+1));
            System.out.println(arreglo[i].ToString1());
        } 
    }
    System.out.println("___________________________________________________________");
    menu(arreglo,ciclos,ordenado);
}
public static void cargaArboles(Arbol arreglo[],int ciclos,boolean ordenado){
    //variables locales y llamados
    Scanner lectura = new Scanner(System.in);
    String nombre;
    arreglo[ciclos]=new Arbol();
    System.out.println("debe ingresar un nombre para la debida comparacion");
    nombre=lectura.next();
    //guardo el nombre para comparrar que no exista en las clases
    if(comparacion(arreglo,nombre,ciclos)){
         System.out.println("ingrese la altura del arbol: "+nombre);
           int altura=lectura.nextInt();
           System.out.println("ingrese la profundidad de las raices: ");
           int profundidad=lectura.nextInt();
           System.out.println("posee frutos? true/fals");
           boolean frutos = lectura.nextBoolean();
           System.out.println("que temperatura soporta?");
           int temperatura=lectura.nextInt();
          arreglo[ciclos]=new Arbol(nombre,altura,profundidad,frutos,temperatura);
           System.out.println("carga finalizada");
           System.out.println("_______________________________________________");
        menu(arreglo,ciclos,ordenado=false);
    }
    else{
        System.out.println("nombre repetido, ingrese otro nombre");
        cargaArboles(arreglo,ciclos,ordenado);
    }
}
public static boolean comparacion(Arbol arreglo[],String nombre,int ciclos){
    //ingresa la Arbol Arbol y se realiza una busqueda parcial con el String 
    //de la opcion 1
    boolean nombreEncontrado=true;
    boolean retorno=true;
    int i=0;
    //inicio de la busqueda parcial
    while(nombreEncontrado==true&&i<=ciclos){
        if(arreglo[i].getNombre().equals(nombre)){
           retorno=false;
           nombreEncontrado=false;
        }
        i++;
    }
    return retorno;
}
public static void Finalizacion(){
    System.err.println("Finalizacion de algoritmo");
}
// Segunda Parte del trabajo practico
public static void mostrarArboles(Arbol arreglo[],int ciclos,boolean ordenado){
    for (int i = 0; i <= ciclos; i++) {
        System.out.print(arreglo[i].getNombre()+"||");
    }
    System.out.println(" ");
    menu(arreglo,ciclos,ordenado);
}
public static int busquedaPorAlturaRecursiva(Arbol arreglo[],int ciclos,int recorrido,int numeroX,int acum){
    if(recorrido==ciclos){
        if(arreglo[recorrido].getProfundidadRaices()>numeroX){
            acum++;
        }
    }
    else{
        if(arreglo[recorrido].getProfundidadRaices()>numeroX){
            acum++;
    }
        acum=busquedaPorAlturaRecursiva(arreglo,ciclos,recorrido+1,numeroX,acum);
        }
    return acum;
}
public static void quickSort(Arbol arreglo[],int izq,int der,int ciclos,boolean ordenado){
    Arbol pivote=arreglo[izq];
    Arbol auxiliar;
    int j=izq;
    int i=der;
    while(j<i){
        while(arreglo[j].getAltura()<=pivote.getAltura()&&j<i)j++;
        while(arreglo[i].getAltura()>pivote.getAltura())i--;
        if(j<i){
            auxiliar=arreglo[j];
            arreglo[j]=arreglo[i];
            arreglo[i]=auxiliar;
        }
    }
    arreglo[izq]=arreglo[i];
    arreglo[i]=pivote;
    if(izq<i-1){
        quickSort(arreglo,izq,i-1,ciclos,ordenado);
    }
    if(i+1<der){
        quickSort(arreglo,j+1,der,ciclos,ordenado);
    }
    System.out.println("Areglo Ordenado POR ALTURAS");
    menu(arreglo,ciclos,ordenado=false);
}
 public static void busquedaBinaria(Arbol  arreglo[], String nombre,int ciclos,boolean ordenado){
  int centro=0,inf=0,sup=ciclos;
 int encontrado=-1;
   while(inf<=sup){
       centro=(inf+sup)/2;
       if(nombre.compareToIgnoreCase(arreglo[centro].getNombre())==0){
           encontrado=centro;
           inf=sup+1;
       }
       else{
           if(nombre.compareToIgnoreCase(arreglo[centro].getNombre())<0){
               sup=centro-1;
           }
           else{
               inf=centro+1;
           }
       }
   }
    if(encontrado!=-1){
        System.out.println("el nombre coincidente es "+arreglo[centro].getNombre());
        System.out.println("En la posicion nª: "+(centro+1));
        menu(arreglo,ciclos,ordenado);
    }
    else{
        System.out.println("Nombre no encontrado");
        menu(arreglo,ciclos,ordenado);
    }
 }
//punto b
public static void ordenarArray(Arbol arreglo[],int ciclos,boolean ordenado){
    Scanner lectura = new Scanner(System.in);
    System.out.println("elija el metodo de ordenamiento a eleccion");
    System.out.println("1 Metodo de Burbuja mejorado");
    System.out.println("2 Metodo de Seleccion");
    System.out.println("3 Metodo de Insercion");
    System.out.println("4 volver a menu");
    int opcion = lectura.nextInt();
    switch(opcion){
        case 1: metodoBurbujaMejorado(arreglo,ciclos,ordenado);
            break;
        case 2:metodoSeleccion(arreglo,ciclos,ordenado);
            break;
        case 3:metodoInserccion(arreglo,ciclos,ordenado);
            break;
        case 4:menu(arreglo,ciclos,ordenado);
        break;
        default :System.out.println("numero incorrecto");
            ordenarArray(arreglo,ciclos,ordenado);
        break;
    }
}
public static void metodoBurbujaMejorado(Arbol arreglo[],int ciclos,boolean ordenado){
    boolean flag=true;
    for (int i = 0; i <= ciclos-1&&flag; i++) {
        flag=false;
        for (int j = 0; j <= ciclos-1-i; j++) {
            if (arreglo[j].getNombre().compareToIgnoreCase(arreglo[j+1].getNombre())>0) {
                flag=true;
                Arbol auxiliar =arreglo[j];
                arreglo[j]=arreglo[j+1];
                arreglo[j+1]= auxiliar;
            }
        }  
    }
  ordenado=true;
    System.out.println("Arreglo Ordenado");
  menu(arreglo,ciclos,ordenado);
}
public static void metodoInserccion(Arbol arreglo[],int ciclos,boolean ordenado){
    for (int i = 0; i <= ciclos; i++) {
        Arbol temp = arreglo[i];
        int j=i;
        while(j>0&&temp.getNombre().compareToIgnoreCase(arreglo[j-1].getNombre())<0){
            arreglo[j]=arreglo[j-1];
            j= j-1;
        }
        arreglo[j]=temp;
    }
   ordenado=true;
    System.out.println("Arreglo Ordenado");
   menu(arreglo,ciclos,ordenado);
}
public static void metodoSeleccion(Arbol arreglo[],int ciclos,boolean ordenado){
    int pos;
        Arbol menor;
        Arbol temp;
    for (int i = 0; i <= ciclos; i++) {
        menor=arreglo[i];
        pos = i;
        for (int j =i+1; j <= ciclos; j++) {
            if (arreglo[j].getNombre().compareToIgnoreCase(menor.getNombre())<0) {
                menor=arreglo[j];
                pos=j;
            }
            if(pos !=1){
               temp=arreglo[i];
               arreglo[i]=arreglo[pos];
               arreglo[pos]=temp;
            }
        }
    }
   ordenado=true;
    System.out.println("Arreglo Ordenado");
   menu(arreglo,ciclos,ordenado);
}
//metodos auxiliares no pedidos 
public static void combinacion(Arbol []arregloPre,Arbol []arreglo){
    int ciclos=arregloPre.length-1;
    boolean ordenado=false;
    for (int i = 0; i <arregloPre.length; i++) {
        arreglo[i]=arregloPre[i];
    }
    menu(arreglo,ciclos,ordenado);
}
public static void desordenarArray(Arbol arreglo[],int ciclos,boolean ordenado){
    Arbol aux;
    double a;
    int cambio;
    boolean eleccion;
    for (int j = 0; j <= ciclos; j++) {
    for (int i = 0; i <= ciclos; i++) {
        a=Math.random()*(ciclos-0)+0;
        cambio=(int)a;
        aux = arreglo[i];
        arreglo[i]=arreglo[cambio];
        arreglo[cambio]=aux;
    }
    }
   ordenado=false;
    System.out.println("Arreglo desordenado");
   menu(arreglo,ciclos,ordenado);
}
}
