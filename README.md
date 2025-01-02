# raiz_cuadrada

```markdown
# Square Root Bisection Method

Este repositorio contiene una implementación del método de bisección para calcular la raíz cuadrada de un número dado.

## Descripción

El método de bisección es una técnica numérica para encontrar raíces de funciones. En este caso, se utiliza para calcular la raíz cuadrada de un número objetivo (`square_target`) con una tolerancia específica (`tolerance`) y un número máximo de iteraciones (`max_iterations`).

## Uso

La función `square_root_bisection` toma los siguientes parámetros:

- `square_target`: El número del cual se desea calcular la raíz cuadrada.
- `tolerance`: La tolerancia permitida para el error en el cálculo de la raíz cuadrada (por defecto es `1e-7`).
- `max_iterations`: El número máximo de iteraciones permitidas para el algoritmo (por defecto es `100`).

### Ejemplo

```python
def square_root_bisection(square_target, tolerance=1e-7, max_iterations=100):
    if square_target < 0:
        raise ValueError('Square root of negative number is not defined in real numbers')
    if square_target == 1:
        root = 1
        print(f'The square root of {square_target} is 1')
    elif square_target == 0:
        root = 0
        print(f'The square root of {square_target} is 0')

    else:
        low = 0
        high = max(1, square_target)
        root = None

        for _ in range(max_iterations):
            mid = (low + high) / 2
            square_mid = mid**2

            if abs(square_mid - square_target) < tolerance:
                root = mid
                break

            elif square_mid < square_target:
                low = mid
            else:
                high = mid

        if root is None:
            print(f"Failed to converge within {max_iterations} iterations.")

        else:   
            print(f'The square root of {square_target} is approximately {root}')

    return root

N = 16
square_root_bisection(N)
```

### Ejecución

Para ejecutar el código, simplemente llama a la función `square_root_bisection` con el número objetivo. Por ejemplo:

```python
N = 16
square_root_bisection(N)
```
