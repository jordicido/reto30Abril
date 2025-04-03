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
