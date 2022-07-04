# Estructura básica de archivos.

* **En C.**

```c
#include<stdio.h>
int main(int argc, char **argv){
	int numero = 12;
	int numero_2;
	char* string;
	
	return 0;//-> Siempre tiene que ir esto debido a que nuestra función main retorna un int, se retorna un 0 que le indica a nuestro computador que ya termino el codigo y sin problemas
}
```

En la parte superior siempre irán exportados los *headers*, es decir los `.h` es muy importante notar que si queremos importar un `.h` un *header* que nosotros hicimos, debemos hacerlo reemplazando los `<>` por `""`.

En otras palabras suponiendo que tenemos un archivo llamado`resumen.h` en nuestro código debemos llamarlo así `#include"resumen.h"`

---



* En **C++**

  ```c++
  #include<iostream>
  #include<string>
  using namespace std;
  
  int main(int argc, char** argv){
  	string s;
  	cout<<"Imprime en consola"<<endl;
  	cin>>string;
  	//guarda en variables
      return 0; //-> Siempre tiene que ir esto debido a que nuestra función main retorna un int, se retorna un 0 que le indica a nuestro computador que ya termino el codigo y sin problemas
  }
  
  ```

  ​	Realmente aquí hay poco que comentar debido a que  es la misma estructura, lo mismo sucede con los `.h` solo que las librerías fundamentales son `#include<iostream>` que permite usar la consola para mostrar y recibir entradas.

  * **cout** se *muestran* cosas en la terminal. 

  * **cin** se *reciben* entradas de consola .

    También hay que destacar el `using namespace std` que nos permite escribir solamente **cout** y **cin**, si no tendríamos que poner `std::cout` y `std::cin`.

---

# Strings.

* En **C**.

  Par entender las strings en C debemos tener en cuenta que una palabra es un conjunto de caracteres, es decir un ***arreglo*** de caracteres. Usualmente la forma en la que suele usar strings es la siguiente

  ```c
  #include<stdio.h>
  #include<string.h>//Nos permite manipular strings
  #include<stdlib.h> //con este podemos hacer mallocs y los free correspondientes para guarda nuestras strings de manera dinamica.
  
  int main(int argc, char** argv){
      char* linea;//aca definimos un arreglo de caracteres, por eso es char *
      linea = (char *)malloc(sizeof(char)*n);
      //aca lo que hacemos es reservarle memoria a este arreglo de caracteres, a esta string, donde lo pimero es "castear" lo que malloc nos de hacia el tipo de variable que  es linea. En nuestro caso es char* por eso al principo esta (char *). despues hacemos el malloc() que en el cual con el sizeof(char)*n le asignamos el tamaño que queremos, cabe destacar que n es un numero cualquiera que uno decida ocupar.
      free(linea);
      return 0;
  }
  ```

  Les dejo una tabla con los metodos mas importantes:
  
  <table class="alt">
  <tbody><tr><th>No.</th><th>Function</th><th>Description</th></tr>
  <tr><td>1)</td><td><a href="c-strlen">strlen(string_name)</a></td><td>returns the length of string name.</td></tr>
  <tr><td>2)</td><td><a href="c-strcpy">strcpy(destination, source)</a></td><td>copies the contents of source string to destination string.</td></tr>
  <tr><td>3)</td><td><a href="c-strcat">strcat(first_string, second_string)</a></td><td>concats or joins first string with second string. The result of the string is stored in first string.</td></tr>
  <tr><td>4)</td><td><a href="c-strcmp">strcmp(first_string, second_string)</a></td><td>compares the first string with second string. If both strings are same, it returns 0.</td></tr>
  <tr><td>5)</td><td><a href="c-strrev">strrev(string)</a></td><td>returns reverse string.</td></tr>
  <tr><td>6)</td><td><a href="c-strlwr">strlwr(string)</a></td><td>returns string characters in lowercase.</td></tr>
  <tr><td>7)</td><td><a href="c-strupr">strupr(string)</a></td><td>returns string characters in uppercase.</td></tr>
  </tbody></table>
  
  

---

* En **C++**.

  Acá realmente es mucho más sencillo he intuitivo su uso dado que existe una librería para estos llamado `#include<string>`

```c++
#include<iostream>
#include<string>
using namespace std;

int main(int argc, char** argv){
    string linea;
    cin>>linea;
    cout<<linea; //al hacer esto solo nos guardara la primera palabra, es decir hasta el espacio en blanco.
    
    linea = "wena compita"; //esta es otra forma de ocupar las strings y declararlas
    linea.lenght(); //retorna el largo de la string
    
    return 0;
}
```

Básicamente acá no tiene que hacer ni mallocs ni free, la librería `<string>` maneja todo lo que necesitan.

Les dejo una tabla que encontré bonita con los métodos mas importantes **uwu**

<table class="table table-bordered">
<tbody><tr>
<th>Sr.No</th>
<th style="text-align:center;">Function &amp; Purpose</th>
</tr>
<tr>
<td class="ts">1</td>
<td><p><b>strcpy(s1, s2);</b></p>
<p>Copies string s2 into string s1.</p>
</td>
</tr>
<tr>
<td class="ts">2</td>
<td><p><b>strcat(s1, s2);</b></p>
<p>Concatenates string s2 onto the end of string s1.</p>
</td>
</tr>
<tr>
<td class="ts">3</td>
<td><p><b>strlen(s1);</b></p>
<p>Returns the length of string s1.</p>
</td>
</tr>
<tr>
<td class="ts">4</td>
<td><p><b>strcmp(s1, s2);</b></p>
<p>Returns 0 if s1 and s2 are the same; less than 0 if s1&lt;s2; greater than 0 if s1&gt;s2.</p>
</td>
</tr>
<tr>
<td class="ts">5</td>
<td><p><b>strchr(s1, ch);</b></p>
<p>Returns a pointer to the first occurrence of character ch in string s1.</p>
</td>
</tr>
<tr>
<td class="ts">6</td>
<td><p><b>strstr(s1, s2);</b></p>
<p>Returns a pointer to the first occurrence of string s2 in string s1.</p>
</td>
</tr>
</tbody></table>

---
Tambien se puede hacer una concatenación de strings. Para esto primero tenemos que declarar la string

```c++
#include<string>
int main(){
    string palabra = "";
    //ahora si podemos ir agregando strings a esta variable
    string+= "hola" + " como" + " estas";
    return 0;
}
```



# Punteros

Ok la definición de toda la vida de punteros es que es donde almacenas direcciones de memoria, es decir donde esta *"Apuntado"* el valor de la variable, esto puede ser particularmente util al momento de **manejar memoria** de manera dinámica, tener **arreglos** de **clases** *(objetos)* o simplemente **retornar 2 valores** en ciertas funciones.

Funcionan de igual manera tanto en **C** como en **C++** 

```c
#include<stdio.h>
int main(){
    int a = 3;//->aca tenemos una variable común
    int* b; //->aca tenemos una varibale con una dirección de memoria para un int
    *b =5; //de esta forma estamos modificando el valor de guardado por el puntero, es el quivalente a decir a=5;
    printf("%d",a); //esto funciona y nos muestra un 3
    printf("%d",b); //esto no funciona ya que b es un hexadecimal con la direccion de memoria apuntada
    printf("%d",*b); //esto nos mostraria el valor apuntado por b que es 5 =D
    printf("%d",&a);  //esto no funciona ya que &a es un hexadecimal con la direccion de memoria apuntada
    return 0;
}
```

Gracias a esto se puede ver que cuando nosotros declaramos un string en Cd e la siguiente manera:

`char* palabra;` lo que estamos haciendo es crear un puntero hacia el inicio de nuestro arreglo por lo que después podríamos recorrerlo aumentando nuestro puntero en 1 para avanzar a la siguiente dirección.

Pequeña imagen que explica un poco lo que dije arriba. Para los strings siempre será importante notar que el ultimo carácter agregado es un"***\0***" ya que este le indica al programa que ahí termina el string.

![](https://dyclassroom.com/image/topic/c/pointers-string/str-ptr.jpg)

## Doble return en funciones 

para lograr esto haremos una función que me retorne el producto entre dos "*vectores*"

```c++
#include<iostream>
using namespace std;

void producto(int x1,int y1,int x2,int y2, int* r1,int *r2){
//Lo primero que tenemos que notar es que r1 y r2 son punteros de int, estos son los valores en lo que yo guardare la multiplicación de estos vectores.
    *r1 = x1*y2; //formulas supuestas de una imagen de internet :D
    *r2 = y2*y1;
    //se puede ver que guardamos los valores de estas multiplicaciónes en las direcciones apuntadas por r1 y r2, es decir que se modificaron los valores que inicialmente estaban ahi dentro de esta funcion.
}

int main(){
    int x1=3;
    int y1=5;
    int x2=1;
    int y2=7;
    int r1;//Notese que no lo definimos como punteros debido a que si lo hicieramos tendriamos que asginar el tamaño con un malloc o un new.
    int r2;
    cout<<"v1("<<x1<<","<<y1<<")"<<endl;
    cout<<"v2("<<x2<<","<<y2<<")"<<endl;
    cout<<"el nuevo vector es"<<endl;
    producto(x1,y1,x2,y2,&r1,&r2);//como nosotros le dijimos a nuestra funcion que r1 y r2 son int*, tenemos que pasarle la DIRECCIÓN de estas variables.
    cout<<"v3("<<r1<<","<<r2<<")"<<endl;
    return 0;
}
```

## Arreglos de punteros.

```c++
#include<iostream>
using namespace std;
int TAMAÑO = 5; //esto es una variable local por convencion va en mayuscula uwu
int main(){
    int numeros[] = {5,10,20,30,40};//declaramos un arreglo normal de int
    int * punteros[TAMAÑO];//declaramos un arreglo de PUNTEROS de INT
    for (int i =0;i<TAMAÑO;i++){
        punteros[i] = &numeros[i]//aca vamos recorriendo donde se guardar los punteros y guardamos en cada posición, la direccion de memoria de lo que este en el arreglo numeros, por eso usamos &
    }
    for (int i =0;i<TAMAÑO;i++){
        cout<<"numeros["<<i<<"]"<<"="<<*punteros[i]<<endl;
        //Finalmente aca leemos con un for las distintas direcciones apuntadas y mostramos el valor por pantalla, el output de esto deberia ser
        /* array_of_integers[0] = 5 
           array_of_integers[1] = 10 
           array_of_integers[2] = 20 
           array_of_integers[3] = 40 
           array_of_integers[4] = 80
            */
    }
    
    return 0;
}

```

Este caso se ve muy básico e inecesario pero esto mismo se puede aplicar para los structs y objetos.

---

# Structs

Principalmente los structs son una forma de almacenar datos de una forma estructurada

```c
#include <stdio.h>
typedef struct Persona{ //Persona es el nombre del struct
    int edad; // aca simplemente definimos las variables que queremos almacenar
    char nombre[20];
    char apellido[20];
}Persona;//nombre del struct de nuevo por que no recuerdo que era el typedef
int main(){
    Persona p1;//Lo creamos en primera instancia
    p1->edad = 21;//con el operado "->" puedes asginar y tambien obtener datos de dicho struct
    p1->nombre = "Matias";
    p1->apellido = "Muñoz";
    printf("la edad de %s %s es %d",p1->edad,p1->nombre,p1->apellido);
    return 0;
}    
```

---

# Headers

Ok los headers son archivos con una extención `.h` que nos permite declarar funciones fuera de nuestro código main y poder hacerlas en otros archivos, archivos específicos para este tipo de funciones, esta muy relacionado con las **clases** que veremos un poco más adelante por ejemplo:

### operaciones.h

---

```c++



int suma(int x,int y);
int resta(int x, int y);

```

### operaciones.cpp

---

```c++
#include"operaciones.h"
int suma(int x, int y){
    return x+y;
}
int resta(int x, int y){
    return x-y;
}
```

Con esto creado podemos hacer un ***main*** que utilice estas funciones importando nuestro `operaciones.h`

### main.cpp

---

```c++
#include<iostream>
#include"operaciones.h"
using namespace std;
int main(){
    int a = 4;
    int b = 5;
    cout<<suma(a,b)<<endl;//al momentos de llamarlas, el programa buscara si estas existen en el los imports, en el .h para ser precisos
    cout<<resta(a,b)<<endl;
    return 0;
}
```

Ahora, todo suena super pero necesitamos compilarlo y como sabemos, no se puede compilar algo sin main. para hacer esto tenemos que ocupar la flag *-o* en en nuestro compilador g++, creando asi un archivo .o que indicara que es un binario. para esto podemos hacer un ***Makefile***.

# Makefile

 Básicamente algo que corre comandos en nuestra consola, tiene 3 componentes importantes, **variables**, **reglas** y **dependencias**

## variables

Se pueden ver de la siguiente forma, a veces necesitase escribir rutas y bla bla bla, asi que las dejas puestas, lo más usados suele ser para las flags y el compilador además de algunas direcciones de programas.

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
```

## Reglas

Ahora veremos lo que son las reglas, son básicamente las indicaciones de distintos comandos que debe ejecutar el archivo makefile al llamarlo.

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
main.o: main.cpp operaciones.o
	$(cc) $(flag) main.cpp -o $(exe)
```

En este ejemplo la regla seria el main.o:

vamos a agregarle lo necesario para compilar lo de arriba:

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
main.o: main.cpp operaciones.o
	$(cc) $(flag) main.cpp -o $(exe)
operaciones.o: operaciones.cpp operaciones.h
	$(cc) $(flag) -c operaciones.cpp -o $(exe)
```

Acá es importante notar que usamos un -c debido a que operaciones no es un archivo que contenga un main, no es un ***ejecutable***.

## Dependencias 

Como su nombre lo indica, son las cosas de las que va a depender que se ejecuten las reglas, esta las mira y ve si es que han sido actualizadas o si existen o no. De no estar al dia o no estar creadas, llamara la regla correspondiente para que lo compile, tambien revisa si los archivos fueron modificados, en el makefile se logra ver esto con en el main con `main.o: main.cpp operaciones.o` donde se ve que la regla main.o depende del main.cpp y operaciones.o

## Reglas extras

Podemos definir unas reglas que son bien utiles para recompilar las cosas y para correrlos:

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
main.o: main.cpp operaciones.o
	$(cc) $(flag) main.cpp -o $(exe)
operaciones.o: operaciones.cpp operaciones.h
	$(cc) $(flag) -c operaciones.cpp -o $(exe)
clean:
	rm *.o *.out *.exe
```

Donde ***\*.out*** es para linux y ***\*.exe*** es para windows.

*Agregar también que para borrar cosas en windows, no es **rm** es **del***

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
main.o: main.cpp operaciones.o
	$(cc) $(flag) main.cpp -o $(exe)
operaciones.o: operaciones.cpp operaciones.h
	$(cc) $(flag) -c operaciones.cpp -o $(exe)
run: main.o
	./$(exe).out
clean:
	rm *.o *.out *.exe
```

Aplica lo mismo acá con el run, ***\*.out*** es para linux y ***\*.exe*** es para windows.



# Clases (objetos)

Mismo concepto que los structs solo que acá se pueden crear metodos(funciones) y tienen sus atributos (variables) Esto es solo en C++.

Para poder usar estos si o si necesitamos un archivo `.h` y un archivo `.cpp` para partir haciendo esto vamos a declarar nuestra clase.

## Persona.h

De primera mano crearemos un ***header*** donde declararemos nuesta clase, como ya hablamos antes, las clases tiene ***Metodos*** y ***Atributos***, estos pueden ser **publicos** o **privados**. cuando son publicos, cualquier persona, incluyendo el usuario puede modificarlos y/o usarlos, en cambio si son privados solo pueden modificarse dentro de la misma clase. **Por lo general yo dejo los atributos en private y los metodos en public**.

```c++
#include<string>
class Persona{
    private:
    string nombre;
    int edad;
    float altura;
    public:
    Persona(string nombre, int edad,float altura);//constructor con argumentos
    Persona();//constructor sin argumentos
    void saludar();//Como los atributos estan en private, tenemos que hacer los Setters
    			   //y los getters
    void setNombre(string nombre);
    void setEdad(int edad);
    void setAltura(float altura);
    //Y ahora hacemos los getters
    string getNombre();
    int getEdad();
    float getAltura();    
}
```

## Persona.cpp

Lo primero que tenemos que hacer es crear un **constructor**.

### Constructor con parametros.

----

El primero que haremos será uno con los atributos pasados directamente. Cabe recalcar que un constructo es algo que nos genera la clase (objeto).

```c++
#include"persona.h"//Añadimos los headers en el que declaramos la clase y adicionalmente
#include<iostream> //los que usaremos para el funcionamiento de la clase
#include<string>
using namespace std;
//Para poder crear los metodos de la clase se debe usar la notacion 
//NombreClase::NombreMetodo. 
//Aca como es el constructor le digo NombreClase::NombreConstructor
// En lo personal les pongo el mismo nombre a la clase y el constructor. y por convencion la primera letra en mayuscula
Persona::Persona(string nombre,float altura,int edad){
    this->nombre = nombre; //Con el this, le indicamos a el programa se esta haciendo referencia asi si mismo, para que no haya problemas con el repetir nombres al asignar
    this->altura = altura;
    this->edad = edad;
}
```



### Constructor sin parametros.

---

Aquí usaremos el concepto de ***sobrecarga*** es decir, llamaremos de igual forma otro constructor pero no le daremos parametros, para asi instanciar una persona **sin** nombre **ni** edad **ni** altura.

```c++
#include"persona.h" //Incluimos el header de nuestra clase y lo necesario para sus
#include<iostream>  //metodos
using namespace std;

Persona::Persona(){
    this->nombre="";
    this->edad=0;
    this->altura = 0.0;
}
```

### Setters.

---

Ahora haremos los setters, cabe destacar que como nuestros atributos son private, no podemos acceder directamente a estos ni para leerlos ni para escribirlos, es por eso que les creamos metodos que nos permitan hacer estas acciones y van dentro de nuestro archivo `.cpp`.

```c++
//recuerden que seguimos trabajando en persona.cpp
#include"persona.h" //Incluimos el header de nuestra clase y lo necesario para sus
#include<iostream>//metodos
#include<string>
using namespace std;
void Persona::setNombre(string nombre){
    this->nombre = nombre; // asi de sencillo asignamos el nombre con nuestro setter
}
void Persona::setEdad(int edad){
    this->edad = edad; // asi de sencillo asignamos la edad con nuestro setter
}
void Persona::setAltura(float altura){
    this->altura = altura; // asi de sencillo asignamos la altura con nuestro setter
}
```

Cabe destacar que como se esta **asignando** algo, nuestra funcion retorna ***void***. 

### Getters.

---

Mismo concepto, como son privados los atributos, no podemos leerlos, así que creamos los getters para poder mostrarlos cuando sean necesarios. también dentro de nuestro archivo `.cpp`.

```c++
//recuerden que seguimos trabajando en persona.cpp
#include"persona.h" //Incluimos el header de nuestra clase y lo necesario para sus
#include<iostream>//metodos
#include<string>
using namespace std;
string Persona::getNombre(){
    return this->nombre; //asi de simple, retornamos el atributo en cuestion
}
int Persona::getEdad(){
    return this->edad;
}
int Persona::getAltura(){
    return this->altura;
}
```

Es importante notar que dependiendo de el tipo de **atributo** que sea,  es lo que va a retornar la función, mucho ojo.

### Metodos.

---

Finalmente con esto ya podemos trabajar con el método especifico que habíamos creado para nuestro objeto que es ***`saludar()`***.

```c++
//recuerden que seguimos trabajando en persona.cpp
#include"persona.h" //Incluimos el header de nuestra clase y lo necesario para sus
#include<iostream>//metodos
#include<string>
using namespace std;
void Persona::saludar(){
    cout<<"Hola mi nombre es "<<this->nombre<<" mido "<<this->altura<<"m y tengo  "<<this->edad<<" años"<<endl;
}
```

### Finalmente.

---

Al final nuestro archivo `persona.cpp` quedaria asi:

```c++
#include"persona.h" //Incluimos el header de nuestra clase y lo necesario para sus
#include<iostream>//metodos
#include<string>
using namespace std;
//Constructor con parametros
Persona::Persona(string nombre,float altura,int edad){
    this->nombre = nombre; 
    this->altura = altura;
    this->edad = edad;
}
//constructor sin parametros
Persona::Persona(){
    this->nombre="";
    this->edad=0;
    this->altura = 0.0;
}
//Setters
void Persona::setNombre(string nombre){
    this->nombre = nombre; 
}
void Persona::setEdad(int edad){
    this->edad = edad; 
}
void Persona::setAltura(float altura){
    this->altura = altura;
}
//Getters
string Persona::getNombre(){
    return this->nombre; 
}
int Persona::getEdad(){
    return this->edad;
}
int Persona::getAltura(){
    return this->altura;
}
//metodo saludar
void Persona::saludar(){
    cout<<"Hola mi nombre es "<<this->nombre<<" mido "<<this->altura<<"m y tengo  "<<this->edad<<" años"<<endl;
}
```





## Main.cpp

Con todo esto por fin podemos crear nuestro `main.cpp` 

```c++
#include"persona.h"
using namespace std;
Persona p1("matias",21,1.87); //asi se instancia
p1.saludar();//Hola mi nombre es matias mido 1.87m y tengo 21;
Persona p2();
p2.saludar();//Hola mi nombre es mido 0.0m y tengo 0;
```

Esto seria clases, ahora, como compilamos esto?

## Compilar en binarios.

Aquí realmente no es necesario crear un makefile, podemos ingresar las comandos manualmente pero, en el examen si o si va un makefile asi que:

1. Siempre partan definiendo sus variables.

   ```makefile
   cc=g++
   flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
   exe=salida
   ```

2. Vamos por la compilación de nuestra clase primero, recuerden que esta **depende** de el *header* **persona.h y de persona.cpp**

   ```makefile
   cc=g++
   flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
   exe=salida
   
   persona.o: persona.cpp persona.h
   	$(cc) $(flag) -c persona.cpp -o persona.o
   ```

   Notemos adicionalmente que le agregue el **`-c`** esto es debido a que persona.cpp no contiene un main así que lo compilaremos como binario.

3. Finalmente con esto ya podemos agregar el main, que depende de **`persona.o`** y **`main.cpp`**. Esto debe ir arriba ya que es nuestra regla principal.

   ```makefile
   cc=g++
   flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
   exe=salida
   
   main: persona.o main.cpp
   	$(cc) $(flag) main.cpp persona.o -o $(exe)
   
   persona.o: persona.cpp persona.h
   	$(cc) $(flag) -c persona.cpp -o persona.o
   ```

   Con esto creamos el archivo que necesitamos para poder ejecutarlo.

4. Ahora podemos añadir la regla y clear para poder obtener algunos puntos como se ve en las pautas de examen.

   ```makefile
   cc=g++
   flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
   exe=salida
   
   main: persona.o main.cpp
   	$(cc) $(flag) main.cpp persona.o -o $(exe)
   
   persona.o: persona.cpp persona.h
   	$(cc) $(flag) -c persona.cpp -o persona.o
   run: main.o
   	./$(exe).out
   clean:
   	rm *.o *.out *.exe
   ```

   Donde ***\*.out*** es para linux y ***\*.exe*** es para windows.



# Librerías

## Compilación dinámica de Headers.

Ok esta es la parte que quizas menos entiendo pero hare mi mayor esfuerzo por explicarlo. 

### -fPIC.

---

Para lograr hacer una **librería** hay un concepto importante que tenemos que tener en cuenta, cuando nosotros compilamos con los comandos del g++, es decir hacemos `g++ main.cpp` estamos creando código ***Estático***.

La palabra estático hace referencia a que todos los **comandos de headers/librerias** **externas** que nosotros usemos, dígase por ejemplo nuestro `persona.h` tienen sus comandos en un **espacio especifico de la memoria de nuestro pc**. Claramente cuando tratamos de hacer librerías para que alguien más las utilice, **no** va a tener estos archivos en el mismo espacio de memoria que el nuestro.

Para lograr que esto no se así y nuestras librerías sean ***Dinámicas*** debemos agregar el siguiente comando al momento de compilar: `-fPIC`

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida

main: persona.o main.cpp
	$(cc) $(flag) main.cpp persona.o -o $(exe)

persona.o: persona.cpp persona.h
	$(cc) $(flag) -fPIC -c persona.cpp -o persona.o
run: main.o
	./$(exe).out
clean:
	rm *.o *.out *.exe
```

Es importante ver que solo le agregaremos esto a los binarios que estamos haciendo, en este caso particular solo es a **persona.o** `$(cc) $(flag) -fPIC -c persona.cpp -o persona.o`.

## Compilar Header a libreria.

Para hacer una librería deberemos agregar una regla nueva, que se **llamara igual que la libreria** **que queramos crear**, en este caso será ***persona*** y se le debe anteponer el **prefijo lib**, si no por alguna razón no función. Quedaría entonces como **libpersona.dll** `lib=libpersona.dll`

debemos notar que se usa la extensión ***.dll*** para las librerias en windows y *.**so*** en Linux.

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
lib=libpersona.dll

main: persona.o main.cpp
	$(cc) $(flag) main.cpp persona.o -o $(exe)

$(lib): persona.o
	$(cc) $(flags) -shared persona.o -o $(lib)
	
persona.o: persona.cpp persona.h
	$(cc) $(flag) -fPIC -c persona.cpp -o persona.o
	
run: main.o
	./$(exe).out
	
clean:
	rm *.o *.out *.exe
```

*Ok*, de buenas a primeras tenemos que ver que se creo la regla `$(lib)`

```makefile
$(lib): persona.o
	$(cc) $(flags) -shared persona.o -o $(lib)
```

Es importante ver que acá las dependencias seran todos los `.o` que tengamos, en este caso solo es uno, lo siguiente es que se le agrega la flag **`-shared`** realmente no se que significa pero es totalmente necesario

## Compilación del main como binario.

Por razones que desconozco realmente, el main debe compilarse como binario, es decir con una extensión `.o` asi que debemos cambiar su regla de compilación

```makefile
main.o: persona.o main.cpp
	$(cc) $(flag) -c main.cpp persona.o -o main.o
```

Notemos que cambiamos el nombre del archivo a main.o al igual que la regla.

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
lib=libpersona.dll

main.o: persona.o main.cpp
	$(cc) $(flag) -c main.cpp persona.o -o main.o

$(lib): persona.o
	$(cc) $(flags) -shared persona.o -o $(lib)
	
persona.o: persona.cpp persona.h
	$(cc) $(flag) -fPIC -c persona.cpp -o persona.o
	
run: main.o
	./$(exe).out
	
clean:
	rm *.o *.out *.exe
```



## Compilación del main usando libreria.

Ahora viene la parte final de las librerias, compilar el main binario para hacerlo un ejecutable, haciendo uso de estas. vamos a agregarle las siguientes 

* **-L.** : Lo que hace esta flag es que le dice al compilador que se usara una libreria que esta en esta misma carpeta. **El punto es importantísimo ya que este le indica que esta en la carpeta**.
* **-lnombreLibreria**: Con esto le estamos diciendo al compilador cual es el nombre de la libreria que debe buscar y usar para compilar. en nuestro caso seria ***-lpersona***.
* **-Wl, ** : Wl es el linker que se usa, no se mucho de este.
* **-rpath=.** : Esto lo que hace es decirle al linker que añada esta carpeta a donde debe buscar por librerias.

Estos cambios van en una nueva regla que llamaremos igual que la variable ***exe***.

```makefile
$(exe): main.o $(lib)
	$(cc) $(flags) main.o -o $(exe) -L. -lpersona -Wl, -rpath=. 
```

Las dependencias de este van a ser claramente nuestro `main.o` y tambien nuestra libreria que seria `libpersona.dll`.

Finalmente nuestro makefile se veria así:

```makefile
cc=g++
flag=-std=c++11 -Wall -Wextra -Wundef -Werror -Wuninitialized -Winit-self
exe=salida
lib=libpersona.dll

$(exe): main.o $(lib)
	$(cc) $(flags) main.o -o $(exe) -L. -lpersona -Wl, -rpath=. 

main.o: persona.o main.cpp
	$(cc) $(flag) -c main.cpp persona.o -o main.o

$(lib): persona.o
	$(cc) $(flags) -shared persona.o -o $(lib)
	
persona.o: persona.cpp persona.h
	$(cc) $(flag) -fPIC -c persona.cpp -o persona.o
	
run: $(exe)
	./$(exe).out
	
clean:
	rm *.o *.out *.exe *.dll
```

Hay que ver que se le agrego el a la regla **run**  la dependencia de la regla **exe** y se añadió al clean un ***.dll*** 

# Librerías con swig.

Literalmente ni me voy a meter con que es swig, solo se que genera mucho código para facilitar la creación de librerías para distintos lengujes.

## Creación de archivo.i

Lo primero que tenemos que hacer es generar un archivo.i, realmente es una estructura que debes aprender simplemente.

```swig
%module NombreDelModuloEnPython
%{
#include"Header.h"
%}
%include"Header.h"
```

Realmente esto lo podemos reducir a tres partes

### 1.- Nombre del modulo en Python.

Es la primera parte que se escribe y es bastante descriptivo, en función de esto será como nosotros llamaremos a la función desde Python.

**personas.i**

```swig
%module Personas
```

**Test.py**

```python
import Personas as Per
```

Bastante derechito.

### 2.-Headers.

Básicamente acá debes **agregar los headers** que hayas ocupado, también puedes hacer código en esta pequeña parte pero no es del todo recomendable.

```swig
%{
#include"persona.h"
%}
```

### 3.-Headers a importar, tambien de C++.

Acá debes **volver a agregar tus módulos** y en caso de hacer algo adicional como mostrar un ***cout*** directo a Python importar las librerías correspondientes.

```swig
%include"persona.h"
```

Con esto tienes tu archivo.i hecho, se vería así.

```swig
%module Personas

%{
#include"persona.h"
%}

%include"persona.h"
```

## Finalmente, creación del makefile

### Variables makefile.

---

De primera mano vamos a crear las variables necesarias para que el makefile funcione:

* CC = El compilador, algo clásico ya.

* rutaPython = La ruta de el python que tengamos.

* rutaSwig = La ruta donde tengamos instalados Swig.

* libreria: el nombre de la libreria pero con extensión ***.pyd***.

  Esto se veria así:

  ```makefile
  CC = g++
  rutaPython = en el examen lo dejamos vacio jaja
  rutaSwig = en el examen lo dejamos vacio jaja x2
  libreria = _persona.pyd // es importante poner el guión bajo.
  ```

  

### Back to basic.

Para  compilar una librería en Swig primero tenemos que hacer las reglas para c**ompilar en binarios nuestros headers**, es MUY importante recordar que t**odos los headers deben ser dependencias de los otros**, es decir que dependan de sus `.o` ya que los **queremos compilar a una librería**, en el ejemplo solo tengo un header, por eso hare una sola regla.

```makefile
CC = g++
rutaPython = en el examen lo dejamos vacio jaja
rutaSwig = en el examen lo dejamos vacio jaja x2
libreria = _persona.pyd // es importante poner el guión bajo.}

persona.o:persona.h persona.cpp
	$(CC) -fPIC -c persona.cpp -o persona.o
```

Destáquese que le agregue el `-fPIC` ya que es una Liberia.

### archivo lib_wrap.cxx

Para ahora armar nuestro archivo, debemos darle la indicación a swig de que nos compile la libreria, esto se hace de la siguiente forma.

```makefile
lib_wrap.cxx: dependencias.h masDependencias.h archivo.i
	$(rutaSwig)/swig -python -c++ archivo.i
	
```

Acá necesitamos le damos de regla los headers y adicionalmente nuestro `arhivo.i` le indicamos que será un modulo de `-python` escrito en `-c++` mediante las flags.

En el ejemplo de personas se veria así:

```makefile
persona_wrap.cxx: persona.h persona.i
	$(rutaSwig)/swig -python -c++ persona.i
```

### Finalmente la regla de la liberia.

Para terminar nos queda hacer una regla con el **nombre** de la variable que usamos para **lib**( `$(lib)` ) donde las dependencias serán `lib_wrap.cxx` y también los binarios de nuestros headers (`.o`).

```makefile
$(lib):lib_wrap.cxx dependencias.o masDependencias.o 
	$(cc) -fPIC -c lib_wrap.cxx -o lib_wrap.o -I$(rutaPython)/include
    $(cc) -shared lib_wrap.o dependencias.o masDependencias.o -o $(lib) -L$(rutaPython) -lpython39 #aca va la version que tengan
```

esto seria todo  para compilar, realemente no hay mucho que explicar mas que decir que de primera mano **no se ponen flags** por que si no, no compila y que cambien la version de python, en el examen dara igual la que pongan asumo.

Finalmente para rematar, el ejemplo de las personas.

```makefile
$(lib):persona_wrap.cxx persona.o
	$(cc) -fPIC -c persona_wrap.cxx -o persona_wrap.o -I$(rutaPython)/include
    $(cc) -shared persona_wrap.o persona.o -o $(lib) -L$(rutaPython) -lpython39
```



finalmente el makefile quedaría así:

```makefile
CC = g++
rutaPython = en el examen lo dejamos vacio jaja
rutaSwig = en el examen lo dejamos vacio jaja x2
libreria = _persona.pyd

$(lib):persona_wrap.cxx persona.o
	$(cc) -fPIC -c persona_wrap.cxx -o persona_wrap.o -I$(rutaPython)/include
    $(cc) -shared persona_wrap.o persona.o -o $(lib) -L$(rutaPython) -lpython39

lib_wrap.cxx: dependencias.h masDependencias.h archivo.i
	$(rutaSwig)/swig -python -c++ archivo.i

persona.o:persona.h persona.cpp
	$(CC) -fPIC -c persona.cpp -o persona.o
```

# Agradecimientos.

Muchas gracias al Matias ebrio que es incapaz de negarse sus promesas. Exito en el examén.

![](data:image/jpeg;base64,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)
