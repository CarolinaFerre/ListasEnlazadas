ejercicios_listas_Enlazadas_Genericas
LISTAS ENLAZADAS GENÉRICAS

Ofrece una alternativa a la representación secuencial para la gestión de un grupo de Objetos. Evita que se produzca un desplazamiento de datos como ocurre en los ArrayList cuando se elimina un elemento. En este caso se van modificando enlaces con lo cual no se realiza desplazamiento de datos.

Objetos principales: Reducir el coste de las operaciones de inserción y borrado de un Objeto del grupo. Eliminar la necesidad de reserva inicial de memoria.

La lista Enlazada (nodos conectados por enlace) consta de una secuencia enlazada de nodos situados en la memoria dinámica. Cada nodo representa a un elemento del grupo y por tanto se compone de:

. Un dato del tipo base del grupo . Una referencia al siguiente nodo de la lista .El último nodo representa null

primero-->4-->8-->15-->16-->23-->42-->null

LA CLASE DE LOS NODOS DE UNA LISTA: método lista

class lista{

E dato;

lista siguiente; //Tenemos el dato y tenemos una referencia al nodo siguiente

lista(E dato){

this(dato,null);

}

lista(E dato,NodoLegsiguiente){

this.dato=dato;

this.siguiente=siguiente;

}

}

En el constructor debemos de dar valor a los atributos del objeto. El atributo primero es una referencia al primer nodo de la lista y es el único punto de entrada para recorrerla. Inicialmente, la lista está vacía y no hay ningún nodo inicial. Por ello, primero apunta a null.

public Lista(){

primero=null;

talla=0;
La inserción siempre se realiza en la cabeza de la lista:

Lista nuevo=new Lista(x);

El siguiente nodo es:

nuevo.siguiente=primero;

primero=nuevo;

public void insertar (E x){

Listanuevo=new Lista(x);

nuevo.siguiente=primero;

primero=nuevo;

talla++;

}

Inserción al Final:

Creo un nodo auxiliar que recorre la lista, el nodo inicial no puede desplazarse.

public void insertarEnFin (E x){

Lista nl=new Lista(x);

this.talla++;

if(aux==null) primero=nl;

else{

while(aux.siguiente!=null) aux=aux.siguiente;

//aux referencia al último nodo de la lista

aux.siguiente=nl;

}
}

Me desplazo por la estructura con aux.siguiente, eso hace que me desplace de nodos.

Finalmente hay que enganchar el nodo último aux con nl que es null y es el último. Esto se hace con: aux.siguiente=nl;

Para mostrar los datos de la Lista usaremos un bucle for y el método toString para mostrar los datos, aux comenzará con el nodo primero y la condición es que llegue a null, irá pasando de nodos con aux.siguiente:

public String toString(){

String res="";

for(Listaaux=primero;aux!=null;aux=aux.siguiente){

res+=aux.dato.toString()+"\n";

return res;
}

(Recorrido descendente no se puede hacer)

BORRADO DE UN NODO EN UNA LISTA ENLAZADA:

Borrar requiere buscar un elemento.

Hace falta la referencia al nodo anterior, ejemplo creamos la variable ant que referencia al nodo anterior.

ant.siguiente=aux.siguiente;

Así estaremos enlazando el nodo anterior con el siguiente

En el caso de que queramos borrar el primer nodo habría que modificar la variable primero a aux.siguiente:

primero=aux.siguiente;

public boolean eliminar(E x ){

Lista aux=primero,ant=null;boolean res=false;

while(aux!=null && !aux.dato.equals(x)){

ant=aux;aux=aux.aiguiente;

} if(aux!=null){

res=true; this.talla--;

if(ant==null) primero=aux.siguiente;

else ant.siguiente=aux.siguiente;

}return res;

}

USO DE LA LISTA

public class TestListaInteger{

public static void main (String args[){

  LEG<Integer>I=new LEG<Integer>();
I.insertar(new Integer(9));

I.insertar(new Integer(12));

System.out.println("Lista de Integer actual:\n"+I.toString());

System.out.println("Borrando de la lista el 10: ");

if(I.eliminar(new Integer(10))) System.out.println("Elemento inexistente."); } }

La lista puede crecer de forma dinámica, y tiene una sobrecarga de memoria. En una lista siempre tengo que acceder por el primer elemento y recorrer la estructura. En una lista siempre hay que cambiar enlaces, en ese caso siempre es más rentable una lista.
