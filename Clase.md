/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

package tpobligatorio;
/**
 *
 * @author Dante Giuliano Fai-2062 
 */
public class Arbol {
  //Atributos de la Arbol
 private String nombre;
 private int altura;
 private int profRaices;
 private boolean frutos;
 private int tempMinima;
 //Declaracion de parametros
 public Arbol(){
     nombre=" ";
     altura=0;
     profRaices=0;
     frutos=false;
     tempMinima=0;
 }
 public Arbol(String a){
     nombre=a;
 }
 public Arbol(String a,int alt,int pRaices,boolean b,int tMin){
     nombre=a;
     altura=alt;
     profRaices=pRaices;
     frutos=b;
     tempMinima=tMin;
 }
 public void setAltura(int a){
     altura=a;
 }
  public void setTemperaturaMinima(int a){
     tempMinima=a;
 }
 public void setProfundidadRaices(int a){
     profRaices=a;
 }
 public void setFrutos(boolean a){
     frutos=a;
 }
 public boolean getFrutos(){
     return frutos;
 }
 public int getTemperaturaMinima(){
     return tempMinima;
 } 
 public int getAltura(){
     return altura;
 }
  public String getNombre(){
     return nombre;
 }
  public int getProfundidadRaices(){
     return profRaices;
 }
 public String ToString1(){
     return "_______________________________________\n|Nombre de Arbol: "+nombre
     +"\n|Altura de Arbol: "+altura+"\n|Profundidad de Raices: "+profRaices+"\n|Arbol frutal: "+frutos+
     "\n|Temperatura minima Soportada: "+tempMinima+"\n_______________________________________";
 }
 public boolean equals(Arbol obj){
     return(nombre.equalsIgnoreCase(obj.getNombre()));
 }    
    }
