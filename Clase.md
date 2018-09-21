# TP-OBLIGATORIO
package tpobligatorio;
/**
 *
 * @author Dante Giuliano Fai-2062 
 */
public class Clase {
  //Atributos de la Clase
 private String nombre;
 private int altura;
 private int profRaices;
 private boolean frutos;
 private int tempMinima;
 //Declaracion de parametros
 public Clase(){
     nombre=" ";
     altura=0;
     profRaices=0;
     frutos=false;
     tempMinima=0;
 }
 public Clase(String a){
     nombre=a;
 }
 public Clase(String a,int alt,int pRaices,boolean b,int tMin){
     nombre=a;
     altura=alt;
     profRaices=pRaices;
     frutos=b;
     tempMinima=tMin;
 }
 //Observadores y constructores
 //Modificador-observador nombre
 public void setNombre(String a){
     nombre=a;
 }
 public String getNombre(){
     return nombre;
 }
 //Modificador-observador altura
 public void setAltura(int a){
     altura=a;
 }
 public int getAltura(){
     return altura;
 }
 //Modificador-observador profundidad de las raices
 public void setProfundidadRaices(int a){
     profRaices=a;
 }
 public int getProfundidadRaices(){
     return profRaices;
 }
 //Modificador-observador frutos
 public void setFrutos(boolean a){
     frutos=a;
 }
 public boolean getFrutos(){
     return frutos;
 }
 //Modificador-observador temperatura minima
 public void setTemperaturaMinima(int a){
     tempMinima=a;
 }
 public int getTemperaturaMinima(){
     return tempMinima;
 }
    }
