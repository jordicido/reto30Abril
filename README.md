# Reto 30 dias abril 2025

Repositorio con los enunciados y a posteriori, soluciones, del reto de 30 dias de abril en Prometeo

## Reto 1 abril - Redondeo

### Enunciado

En Grado Superior las notas se tienen que poner como un número entero, así que un día podrás ser el profe de entornos y podrás disfrutar del placer de poner un 7 a un estudiante con un 7,49 en el examen.

Desarrolla un algoritmo que, dado un número decimal, devuelve su resultado entero redondeado siguiendo estas normas:
Todos los números decimales por debajo de ,5 se redondean a la baja.
Los que tengan decimales desde ,5 a superior, se redondean al alza.

### Ejemplo

- Si el usuario introduce 4,49, el programa debe devolver un 4
- Si el usuario introduce 9,5 el programa debe devolver un 10

### Soluciones

#### Python

```python
numero = float(input("Introduce un número decimal: "))
if (numero - int(numero) >= 0.5):
    print(int(numero) + 1)
else: 
    print(int(numero))
```

#### Java

```java
import java.util.Scanner;

public class dia1 {
    public static void main(String[] args) {
        System.out.println("Introduce un número decimal:");
        Scanner scanner = new Scanner(System.in);
        float numero = scanner.nextFloat();

        if (numero - (int) numero >= 0.5) {
            System.out.println((int) numero + 1);
        } else
            System.out.println((int) numero);

        scanner.close();
    }
}
```

## Reto 2 abril - Calendario

### Enunciado

Tu misión es simple, soldado: crear un calendario que muestre todos los meses del año y sus semanas de forma clara y organizada. Nada de efectos especiales ni complicaciones innecesarias, solo un buen código que haga el trabajo. Crea un programa que:

- Itere los meses del año
- Itere las semanas del mes
- PISTA: Bucle for anidad.

### Ejemplo

Enero
Semana 1
Semana 2
Semana 3
…

### Soluciones

#### Python

```python
meses = ["Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio", "Julio", "Agosto", 
         "Septiembre", "Octubre", "Noviembre", "Diciembre"]

for mes in meses:
    dias = 0
    print(mes)
    if mes in ["Enero", "Marzo", "Mayo", "Julio", "Agosto", "Octubre", "Diciembre"]:
        dias = 31
    elif mes in ["Abril", "Junio", "Septiembre", "Noviembre"]:
        dias = 30
    else:
        dias = 28
        
    for i in range(1,dias+1):
        print(i, end="\t")
        if i % 7 == 0:
            print()
    print("\n\n")
```

#### Java

```java
public class dia2 {
    public static void main(String[] args) {
        String[] meses = new String[] { "Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio", "Julio", "Agosto",
                "Septiembre", "Octubre", "Noviembre", "Diciembre" };

        for (int i = 0; i < meses.length; i++) {
            int dias = 0;
            if (i == 0 || i == 2 || i == 4 || i == 6 || i == 7 || i == 9 || i == 11) {
                dias = 31;
            } else if (i == 3 || i == 5 || i == 8 || i == 10) {
                dias = 30;
            } else {
                dias = 28;
            }
            System.out.println(meses[i]);
            for (int j = 1; j <= dias; j++) {
                System.out.print(j + "\t");
                if (j % 7 == 0)
                    System.out.println();
            }
            System.out.print("\n\n");
        }
    }
}
```

## Reto 3 abril - El tiempo

### Enunciado

Crear dos variables utilizando los objetos fecha.

- En la primera se representa la fecha (día, mes, año) actual.
- En la segunda se representa la fecha de nacimiento.

Calcular cuántos años han transcurrido entre ambas fechas y muestra su resultado de maneras diferentes
Día, mes y año.
Hora, minuto y segundo.
Día de año.
Día de la semana.
Nombre del mes.

Pistas: buscar sobre el paquete java.time para para fechas y horas.

### Ejemplo

Entrada

- Fecha actual: 04/04/2025
- Fecha nacimiento: 04/06/1988

Salida

- Han pasado 36 años, 9 meses y 0 días.
- 4 de abril de 2025
- Son las 5:56 AM
- Han pasado 94 días desde el inicio del año.
- Es viernes
- El mes es abril

### Soluciones

#### Python

```python
from datetime import datetime

weekDays = {0 : "Lunes", 1 : "Martes", 2 : "Miercoles", 3 : "Jueves", 4 : "Viernes", 5 : "Sábado", 6 : "Domingo"}
monthsOfYear = {1 : "Enero", 2 : "Febrero", 3 : "Marzo", 4 : "Abril", 5 : "Mayo", 6 : "Junio", 7 : "Julio", 8 : "Agosto",
                9 : "Septiembre", 10 : "Octubre", 11 : "Novembre", 12 : "Desembre"}

birthDate = datetime.strptime(input("Introduce tu fecha de nacimiento (DD/MM/YYYY): "), "%d/%m/%Y")
currentDate = datetime.now()

years = currentDate.year - birthDate.year
months = currentDate.month - birthDate.month
days = currentDate.day - birthDate.day
daysOfYear = currentDate - datetime.strptime("01/01/2025","%d/%m/%Y")

if months < 0:
    years -= 1
    months += 12
    
if days < 0:
    months -= 1
    previous_month = (currentDate.month - 1) if currentDate.month > 1 else 12
    previous_year = currentDate.year if currentDate.month > 1 else currentDate.year - 1
    days_in_previous_month = (datetime(previous_year, previous_month + 1, 1) - datetime(previous_year, previous_month, 1)).days
    days += days_in_previous_month

print(f"Han pasado {years} años,  {months} meses y {days} días")
print(f"Hoy es {currentDate.day} de {currentDate.month} del {currentDate.year}")
print(f"Son las {currentDate.hour}:{currentDate.minute}:{currentDate.second}")
print(f"Han pasado {daysOfYear.days} días dede el inicio del año")
print(f"Es {weekDays[currentDate.weekday()]}")
print(f"El mes es {monthsOfYear[currentDate.month]}")
```

#### Java

```java
import java.time.LocalDate;
import java.time.LocalTime;
import java.time.Period;
import java.time.format.DateTimeFormatter;
import java.time.format.TextStyle;
import java.util.Locale;
import java.util.Scanner;

public class dia3 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("En qué fecha naciste? (DD/MM/AAAA):");
        LocalDate bornDate = LocalDate.parse(scanner.nextLine(), DateTimeFormatter.ofPattern("dd/MM/yyyy"));
        LocalDate currenDate = LocalDate.now();

        Period period = Period.between(bornDate, currenDate);
        System.out.println("Han pasado " + period.getYears() + " años, " + period.getMonths() + " meses y "
                + period.getDays() + " días.");
        System.out.println("Hoy es " + currenDate.getDayOfMonth() + " de "
                + currenDate.getMonth().getDisplayName(TextStyle.FULL, Locale.forLanguageTag("es-ES")) + " de "
                + currenDate.getYear());
        System.out.println("Son las " + LocalTime.now().getHour() + ":" + LocalTime.now().getMinute() + ":"
                + LocalTime.now().getSecond());
        System.out.println("Han pasado " + currenDate.getDayOfYear() + " días dede el inicio del año");
        System.out.println(
                "Es " + currenDate.getDayOfWeek().getDisplayName(TextStyle.FULL, Locale.forLanguageTag("es-ES")));
        System.out.println(
                "El mes es " + currenDate.getMonth().getDisplayName(TextStyle.FULL, Locale.forLanguageTag("es-ES")));

        scanner.close();
    }
}
```

## Reto 4 abril - Boom

### Enunciado

Como dice la señora del famoso meme ([link](https://www.youtube.com/watch?v=U7qESuhCqhg&ab_channel=AntonioJuanJim%C3%A9nezGonz%C3%A1lez)), un día estalló la guerra. Haz un programa que, dado un número que se pasa por entrada, haga una cuenta atrás y acabe con un ¡BOOM!.

### Ejemplo

Entrada

5

Salida

5
4
3
2
1
¡BOOM!

### Soluciones

#### Python

```python
counter = int(input("Introduce la cuenta atrás: "))

for i in range(counter, 0, -1):
    print(i)
    
print("¡BOOM!")
```

#### Java

```java
import java.util.Scanner;

public class dia4 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Introduce la cuenta atrás: ");
        for (int i = scanner.nextInt(); i > 0; i--) {
            System.out.println(i);
        }
        System.out.println("¡BOOM!");
        scanner.close();
    }
}
```

## Reto 5 abril -  ¡Exclamaciones

### Enunciado

Jordi nunca se acuerda de abrir las exclamaciones. Él dice que es porque en catalán no se abren las exclamaciones, pero yo creo que simplemente no sabe escribir.
Vamos a crear un programa que asegure que hay tantos abrir exclamación (¡) como cerrar exclamación (!) para flamearlo.

### Ejemplo

Entrada

¡¡¡Caramba!!!
Hola!

Salida

Si
No

### Solución

#### Python

```python
sentence = input("Introduce la frase: ")

counter = 0

for letter in sentence:
    if letter == "¡":
        counter += 1
    elif letter == "!":
        counter -= 1
        
    if counter < 0:
        break

if counter == 0:
    print("Si")
else:
    print("No")
```

#### Java

```java
import java.util.Scanner;

public class dia5 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Introduce la frase: ");
        String sentence = scanner.nextLine();
        int counter = 0;

        for (String letter : sentence.split("")) {
            if (letter.equals("¡"))
                counter++;
            else if (letter.equals("!"))
                counter--;

            if (counter < 0)
                break;
        }

        if (counter == 0)
            System.out.println("Si");
        else
            System.out.println("No");

        scanner.close();
    }
}
```

## Reto 6 abril -  Cajero del Mercadona

### Enunciado

Juan está trabajando en un mercadona en el que no hay cajero automático, él siempre calcula el cambio de los clientes de cabeza. ¿Se te ocurre alguna forma de hacerle la vida más sencilla al pobre chaval?

Crea un programa que:
Reciba la cantidad de dinero (double) que el usuario ha entregado para pagar.

Compare la cantidad entregada con el precio del producto y calcule la diferencia.

Súmale el IVA porque esto es españa, redondeado a dos décimas (+21%)

Devuelva el valor utilizando la menor cantidad de billetes y monedas posibles siendo estos billete de 500 €, billete de 200 €, billete de 100 €, billete de 50 €, billete de 20 €, billete de 10 €, billete de 5 €, moneda de 2 €, moneda de 1 €, moneda de 50 cnts, moneda de 20 cnts, moneda de 10 cnts, moneda de 2 cnts y moneda de 1 cnt.

Pero cuidado, si un cliente intenta pagar con menos dinero del necesario… ¡tendrás que avisarle antes de que se lleve el producto gratis!

### Solución

#### Python

```python
money = (500, 200, 100, 50, 20, 10, 2, 1, 0.5, 0.2, 0.1, 0.05, 0.02, 0.01)
cost = float(input("Define el precio del producto: "))
pay = float(input("Con cuanto dinero vas a pagar?: "))

cost += cost*0.21

change = pay - cost

for item in money:
    print(f"{item}: {int(change//item)}")
    if change//item > 0:
        change -= item * (change//item)  
```

#### Java

```java
import java.util.Scanner;

public class dia6 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double[] money = new double[] { 500, 200, 100, 50, 20, 10, 2, 1, 0.5, 0.2, 0.1, 0.05, 0.02, 0.01 };

        System.out.println("Define el precio del producto: ");
        double cost = scanner.nextDouble();
        System.out.println("Con cuanto dinero vas a pagar?: ");
        double pay = scanner.nextDouble();

        cost += cost * 0.21;

        double change = pay - cost;

        for (double item : money) {
            if (item >= 1.0) {
                System.out.println((int) item + ": " + (int) Math.floor(change / item));
            } else
                System.out.println(item + ": " + (int) Math.floor(change / item));

            if (change / item >= 1) {
                change -= item * ((int) (change / item));
            }
        }

        scanner.close();
    }
}
```

## Reto 7 abril -  Carrera de caracoles cibernéticos

### Enunciado

Imagina una emocionante carrera entre caracoles cibernéticos. Cada caracol tiene una velocidad aleatoria entre 1 y 5 (¡qué emoción!).

- Escribe un programa que simule una carrera de 20 "pasos" entre dos caracoles.
- En cada paso, la posición de cada caracol aumenta según su velocidad.
- Al final, ¡declara al caracol ganador (o si hay un emocionante empate)!

### Solución

#### Python

```python
import random

snail1 = random.randint(1,5)
snail2 = random.randint(1,5)

if snail1 == snail2: 
    print(f"La carrera ha acabado en empate en la posición {snail1*20}")
elif snail1 > snail2:
    print(f"El ganador ha sido el caracol 1 en la posición {snail1*20}")
else:
    print(f"El ganador ha sido el caracol 2 en la posición {snail2*20}")
```

#### Java

```java
public class dia7 {

    public static void main(String[] args) {
        int snail1 = 1 + (int) (Math.random() * 5);
        int snail2 = 1 + (int) (Math.random() * 5);

        if (snail1 == snail2) {
            System.out.println("La carrera ha acabado en empate en la posición " + snail1 * 20);
        } else if (snail1 > snail2) {
            System.out.println("El ganador ha sido el caracol 1 en la posición " + snail1 * 20);
        } else {
            System.out.println("El ganador ha sido el caracol 2 en la posición " + snail2 * 20);
        }
    }
}
```

## Reto 8 abril -  El Robot de Saludos Personalizados

### Enunciado

Escribe un programa que le pregunte al usuario su nombre.
Si el nombre comienza con la letra "A" (mayúscula o minúscula), el robot responderá con un saludo entusiasta como: ¡Hola, Asombroso/a "Nombre"!.
Si el nombre tiene más de 7 letras, el robot dirá: ¡Vaya, "Nombre", ¡qué nombre tan largo y sofisticado!.
Para cualquier otro nombre, el robot simplemente dirá: Saludos, "Nombre".

¡Prepara al robot para todo tipo de nombres! Como un saludo especial a un nombre que empiece por A y tenga 7 letras, o que cuente un chiste si saluda a Jaimito...

### Solución

#### Python

```python
name = input("Dime tu nombre, humano\n")

if len(name) > 7 and name[0].lower == 'a':
    print(f"¡Hola, Asombroso/a {name}, qué nombre tan largo y sofisticado!")
elif  len(name) > 7:
    print(f"¡Vaya, {name}, ¡qué nombre tan largo y sofisticado!")
elif name[0].lower == 'a':
    print(f"¡Hola, Asombroso/a {name}!")
else:
    print(f"Saludos, {name}")
```

#### Java

```java
import java.util.Scanner;

public class dia8 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Dime tu nombre, humano");
        String name = scanner.next();

        if (name.length() > 7 && name.toLowerCase().charAt(0) == 'a') {
            System.out.println("¡Hola, Asombroso/a " + name + ", qué nombre tan largo y sofisticado!");
        } else if (name.length() > 7) {
            System.out.println("¡Vaya, " + name + ", ¡qué nombre tan largo y sofisticado!");
        } else if (name.toLowerCase().charAt(0) == 'a') {
            System.out.println("¡Hola, Asombroso/a " + name + "!");
        } else
            System.out.println("Saludos, " + name);

        scanner.close();
    }
}
```

## Reto 9 abril -  Aglomeración de clases

### Enunciado

Los alumnos de Prometeo que cursan DAM/DAW + Master andan muy liados y no tienen claro cuando tienen clase y cuando no.

Haz un programa que les indique si tienen clase de FP, de Máster, o de las dos en un conjunto de fechas dado. El usuario introduce un número N, que indica el número de días que quiere ver, se deberá imprimir el número del día, si no tienen nada en esa fecha, FP si tiene clase de un módulo de DAM/DAW o Máster si ese día tiene clase de máster.

- Los días múltiplos de 3 tienen clase de FP.
- Los días múltiplos de 5, de máster.
- Los días que son múltiplos de 3 y 5 tienen clase de las dos.

### Ejemplo

Entrada

15

Salida

1
2
FP
4
Máster
FP
7
8
FP
Máster
11
FP
13
14
FP + Máster

### Solución

#### Python

```python
days = int(input("Número de días a visualizar:\n"))

for i in range(1,days+1):
    if i % 15 == 0:
        print("FP + Máster")
    elif i % 3 == 0:
        print("FP")
    elif i % 5 == 0:
        print("Máster")
    else:
        print(i)
```

#### Java

```java
import java.util.Scanner;

public class dia9 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Número de días a visualizar:");
        int days = scanner.nextInt();

        for (int i = 1; i <= days; i++) {
            if (i % 15 == 0) {
                System.out.println("FP + Máster");
            } else if (i % 3 == 0) {
                System.out.println("FP");
            } else if (i % 5 == 0) {
                System.out.println("Máster");
            } else
                System.out.println(i);
        }

        scanner.close();
    }
}
```
