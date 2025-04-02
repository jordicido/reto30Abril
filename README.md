# Reto 30 dias abril 2025

Repositorio con los enunciados y a posteriori, soluciones, del reto de 30 dias de abril en Prometeo

## Reto 1 abril

### Enunciado

En Grado Superior las notas se tienen que poner como un número entero, así que un día podrás ser el profe de entornos y podrás disfrutar del placer de poner un 7 a un estudiante con un 7,49 en el examen.

Desarrolla un algoritmo que, dado un número decimal, devuelve su resultado entero redondeado siguiendo estas normas:
Todos los números decimales por debajo de ,5 se redondean a la baja.
Los que tengan decimales desde ,5 a superior, se redondean al alza.

**Ejemplo**

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
