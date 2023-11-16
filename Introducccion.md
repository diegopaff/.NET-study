# Intruducción a C#

### Comandos útiles de la consola.

Entradas y salidas por consola

```c#
Console.WriteLine("datos"); // => Imprime en la consola y salta de línea.
Console.Write("datos"); // => Imprime en la consola sin saltar a una nueva línea.
Console.ReadLine(); //=> Pide un input desde la consola.

```

### Variables y tipos de datos

- int -> Guarda números enteros (4 bytes) (desde -2147483648 a 2147483647)
- long -> Guarda números enteros más grandes (8 bytes)
- float -> Guarda numeros con fraccion (4 bytes)
- double -> Guarda numeros con más números después de la coma (8 bytes)
- bool -> Valor booleano (1 bit)
- char -> Guarda el simbolo del sistema dentro de ' ' comillas simples (2 bytes)
- string -> Guarda una secuancia caracteres (2 bytes por caracter)

```c#
// se inicializan utilizando el tipo de variable antes del nombre que le vamos a asignar

int precios = 700; // creamos la variable precios

long l = 10;

float precio = 1.555f; // en los float hay que agregar una "f" al final del número para que sepa que es un flotante.

char h = 'ae523';

bool login = true; // solo puede ser true o false

string nombre = "diego" // el string se guarda dentro de comillas dobles.

```

### Conversión de datos

**Implícita:**

- Automática
- De menores a mayores tamaños
- char -> int -> long -> float -> double

**Explícita:**

- Manual
- De mayores a menores
- double -> float -> long -> int -> char

**Manual**
Ejemplo para convertir string to int, de manera similar para el resto de tipos.

```c#
// string to int
Convert.ToInt32(valor); //ToInt32 convierte de string a entero

```

### Constantes

utilizando la palabra reservada const antes de declarar la variable.
Es un valor que no se puede cambiar o resasignar durante el resto del código. Sólo lectura.

```c#

const string var = "Diego"; // fijo como constante la declaración.

```

### Null

Es un tipo de valor que le puedo asignar a una variable.
Sirve mucho para inicializar variables en null, porque no sabemos que valor va a tener esa variable.

```c#
// se pone un símbolo de pregunta despúes del tipo que queremos guardar como null
string? a = null;

```

### Operadores

**Arigméticos**

```c#
+ // suma
- // resta
* // multiplicación
/ // división
% // resto de la división
++ // auto incremento
-- // auto decremento

++i // se incrementa antes de imprimir
i++ // se imprime y después se incrementa.
```

**De asignación**

```c#
+= // le suma la cantidad ej: x += 3  -> x = x + 3
-=
*=
/=
%=
&=
|=
^= // elevado a la potencia
>>=
<<=
```

**De comparación**
Devuelve true or false

```c#
== // igual a
!= // distinto de
> // mayor que
> // menor que
>= // mayor o igual
<= // menor o igual

```

**Operadores Lógicos**
Devuelve true or false

```c#
&& // devuelve true si ambas declaraciones son true
|| // devuelve true si al menos una de las declaraciones es true
! // not -> devuelve el resultado opuesto

```

**Plantilla Literal**
Para escribir variables dentro de comillas de string

```c#
Console.WriteLine($"Resultado: {nombreVariable}");

```

### Estructura de Datos en C#

**Definición:**

- Se pueden agrupar los datos del mismo tipo en colecciones.
- En estas colecciones podemos utilizar métodos que nos ayuden a hacer operaciones de manera más simple.
- Evitamos errores y ahorramos tiempo

**Struct - Datos con utilidad**

```c#
// Struct - Datos con utilidad
// Cuando dice public quiere decir que cualquier parte del código puede acceder a ese elemento.

public struct Coords //crea un tipo de clase Coords
{

    public Coords (Coords(double x, double y))
    {
        X = x;
        Y = y;
    }

    public double X { get; }
    public double Y { get; }

    public override string ToString() => $"({X}, {Y})";
}

```

**readonly**

No se puede modificar, es como crear una constante pero en el entorno de clases

```c#
public readonly double Sum()
{
    return X + Y;
}

```

```c#
public readonly struct Coords
{
    public Coords(double x, double y)
    {
        X = x;
        Y = y;
    }

    public double X { get; init; }
    public double Y { get; init; }

    public override string ToString() => $"({X}, {Y})";
}
```

** Mutación no destructiva **

Se utiliza la expresión with para generar una copia de una instancia de tipo estructura y modificar algún campo.

```c#
public static void Main()
{
    var p1 = new Coords(0, 0);
    Console.WriteLine(p1);  // output: (0, 0)

    var p2 = p1 with { X = 3 };
    Console.WriteLine(p2);  // output: (3, 0)

    var p3 = p1 with { X = 1, Y = 4 };
    Console.WriteLine(p3);  // output: (1, 4)
}

```

### CONDICIONALES

**_ if - else _**

```c#

int test = 5;

if (test < 10)
{
    //body of if
}
else
{
    //body of else
}

```

**_ switch _**

```c#
bool c = true;
switch(c)
{
    case true:
        Console.WriteLine("true");
        break;
    case false:
        break;
    default:
        Console.WriteLine("false");
}
```

**_ break y continue _**

- break: Termina la sección de iteración del bucle más próxima.
- continue: Empieza una nueva interación del bucle más próximo.

### BUCLES

**_ Bucles, While, Do While, For _**

- Son estructuras para implementar lógica
- Permiten bifurcar el flujo del4 programa de acuerdo a diversos escenarios.
- Reducen las líneas de código que necesitamos ante tareas repetitivas.

**_ while _**

```c#
// WHILE
int j = 0;
while (j < 10)
{
    Console.Write(j);
    j++;
}
//---> 0123456789

```

** for **

```c#
// FOR
for (i = 0; i <10; i++)
{
    Console.Write(i);

}
//---> 0123456789

```

** Do..while **
La diferencia con while es que el do..while por lo menos ejecuta siempre una vez el código de adentro porque chequea la condición después.

```c#
// DO-WHILE
int j = 11;
do
{
    Console.Write(j);
    j++;
}
while (j < 10);
//---> 11

```

** Foreach **

Nos permite iterar facilmente en colecciones.
Ventajas:

- No es necesario pasarle el largo de la lista

```c#
// FOREACH -
var names = new List<string> { "Pepe", "Ana", "Felipe"}
foreach (var elemento in names)
{
    Console.WriteLine(elemento);
}

```

Math

```c#

Math.Max(x,y); // -> devuelve el máximo de dos números;
Math.Min(x,y); // -> devuelve el mínimo de dos números;
Math.Sqrt(x); // -> raiz cuadrada
Math.Abs(x); // -> valor absoluto
Math.Round(); // -> redondea el número al entero más cercano
Math.Ceiling() // -> redondea hacia arriba
Math.Floor() // -> redondea hacia abajo

```
