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
