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

* ## Doble return en funciones 

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

* ## Arreglos de punteros.

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
