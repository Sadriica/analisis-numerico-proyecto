# Casos de uso y pruebas: Métodos numéricos

Cada caso se ejecutó en la aplicación (`metodos-numericos.html`, Chrome) el 2026-11-10.
✅ = se cumple · ❌ = no se cumple / pendiente.

Para repetir un caso: abra el HTML, elija el tema y la pestaña indicados y escriba la entrada.

---

## Capítulo 1 · Raíces de ecuaciones

### R1.1 Métodos: bisección, regla falsa, punto fijo, Newton, secante y raíces múltiples

Entrada común: f(x) = `x^3 - 2x - 5`, tolerancia 1e-7, error absoluto. Raíz esperada: **2.0945514815**.

| Método | Datos | Esperado | Estado |
|---|---|---|---|
| Bisección | a = 2, b = 3 | 2.0945514815, ~24 iteraciones | ✅ |
| Regla falsa | a = 2, b = 3 | 2.0945514815 | ✅ |
| Punto fijo | g(x) = `(2x + 5)^(1/3)`, x₀ = 2 | 2.0945514815, \|g′\| < 1 | ✅ |
| Secante | x₀ = 2, x₁ = 3 | 2.0945514815 | ✅ |
| Newton | x₀ = 2 | 2.0945514815, ~4 iteraciones | ✅ |
| Newton n1 | x₀ = 2, m = 1 | igual que Newton | ✅ |
| Newton n2 | x₀ = 2 | 2.0945514815 | ✅ |
| Raíz múltiple | ejemplo «(x − 1)³(x − 3)», x₀ = 0.5 | n1 (m = 3) y n2 llegan a 1 en menos iteraciones que Newton, que se vuelve lineal y avisa | ✅ |

### R1.2 Graficar e imprimir la tabla solución
| Caso | Esperado | Estado |
|---|---|---|
| Cualquier método con datos válidos | gráfica con f(x) y los pasos; tabla con n, xₙ, f(xₙ) y los 4 errores | ✅ |
| Botones ⏮ ◀ ▶ ⏭ | la gráfica muestra el paso elegido | ✅ |

### R1.3 Cualquier función algebraica
Cada función se resolvió con bisección y con Newton (derivada automática).

| f(x) | Intervalo | Raíz esperada | Estado |
|---|---|---|---|
| `sqrt(x) - 2` | [1, 9] | 4 | ✅ |
| `cbrt(x) + 1` | [−3, 0] | −1 | ✅ (corregido) |
| `ln(x) - 1` | [1, 4] | e ≈ 2.7182818 | ✅ |
| `exp(x) - 2` | [0, 1] | ln 2 ≈ 0.6931472 | ✅ |
| `1/x - 0.5` | [1, 3] | 2 | ✅ |
| `sen(x)` | [3, 4] | π | ✅ |
| `x^2 - 2x` | [1.5, 3] | 2 | ✅ |
| `abs(x) - 3` | [1, 5] | 3 | ✅ |
| `x*e^(-x) - 0.2` | [0, 1] | 0.2591711 | ✅ |
| `(x^2 + 1)/(x - 5) + 1` | [−2, 4] | (−1 + √17)/2 | ✅ |
| `x^(1/3) - 1.5` | [1, 5] | 3.375 | ✅ |
| `tan(x/4) - 1` | [2, 4] | π | ✅ |
| `x(x + 1) - 2` | [0, 3] | 1 | ✅ (corregido) |
| `arctan(x) - 1` | [0, 3] | tan 1 ≈ 1.5574077 | ✅ (corregido) |

### R1.4 Ayuda con la derivada
| Caso | Esperado | Estado |
|---|---|---|
| Newton con «Derivar automáticamente» | f′(x) aparece escrita y en notación matemática | ✅ |
| Desmarcar la casilla | se puede escribir f′(x) a mano (`3x^2 - 2` da la misma raíz); si está mal escrita, se avisa | ✅ |
| n1 y n2 | muestran f′ y f″ calculadas | ✅ |
| f′ no real en el punto (p. ej. cbrt en x < 0) | se usa la derivada numérica en ese punto | ✅ (corregido) |

### R1.5 Explicar cómo se ingresan los datos y prevenir errores
| Entrada | Mensaje esperado | Estado |
|---|---|---|
| f = `x^2 +` | «la expresión termina antes de tiempo» | ✅ |
| f = `y + 1` | «No se reconoce: y. La variable debe ser x.» | ✅ |
| a = 3, b = 1 | «Debe cumplirse a < b» | ✅ |
| f(a)·f(b) > 0 | avisa que no hay garantía de raíz en [a, b] | ✅ |
| tolerancia −1 | «debe ser mayor que 0» | ✅ |
| iteraciones 0 | «Use un entero entre 1 y 1000» | ✅ |
| Newton, f = x² + 1, x₀ = 0 | «f′(x₀) = 0: la tangente es horizontal» | ✅ |
| n1 con m = 0 | «m debe ser mayor que 0» | ✅ |
| n2 sin raíz real: f = `cos(x) - 2`, x₀ = 0 | «Revise la gráfica», no «Convergió» | ✅ (corregido) |
| Sección «Cómo escribir la función» | explica la sintaxis, las funciones y las constantes | ✅ |

### R1.6 Gráfica e informe de comparación ante diferentes errores
| Caso | Esperado | Estado |
|---|---|---|
| Pestaña Comparar | tabla de los 7 métodos y 4 gráficas (una por error) contra las iteraciones | ✅ |
| Cambiar el criterio: absoluto, relativo, relativo a xₙ₋₁, \|f(xₙ)\| | se recalcula y se marca el criterio | ✅ |
| Botón «Informe PDF» | informe con resumen, gráficas y un capítulo por método | ✅ |
| Error **de condición** | — | ❌ pendiente |

---

## Capítulo 2 · Sistemas de ecuaciones lineales

### R2.1 Métodos: Jacobi, Gauss-Seidel y SOR
Sistema 4 × 4: A = [[10, −1, 2, 0], [−1, 11, −1, 3], [2, −1, 10, −1], [0, 3, −1, 8]], b = (6, 25, −11, 15). Solución esperada: **(1, 2, −1, 1)**.

| Método | Esperado | Estado |
|---|---|---|
| Jacobi | (1, 2, −1, 1), ρ(T) ≈ 0.4265 | ✅ |
| Gauss-Seidel | (1, 2, −1, 1), ρ(T) ≈ 0.0899 | ✅ |
| SOR, ω = 1.1 | (1, 2, −1, 1) | ✅ |

### R2.2 Tabla, radio espectral y si converge según ρ
Sistema A = [[2, −1, 1], [2, 2, 2], [−1, −1, 2]], b = (−1, 4, −5).

| Método | Esperado | Estado |
|---|---|---|
| Jacobi | ρ(T) ≥ 1, «el método no converge» | ✅ |
| Gauss-Seidel | ρ(T) < 1, «el método converge», solución encontrada | ✅ |
| Cualquier método | tabla con x₁…xₙ y los 5 errores por iteración; matrices T y C | ✅ |

### R2.3 Matrices de hasta 8 × 8
| Caso | Esperado | Estado |
|---|---|---|
| Selector de tamaño | de 2 × 2 a 8 × 8 | ✅ |
| 8 × 8 no simétrica, diagonal dominante, solución (−3, −2, …, 4) | los 3 métodos la encuentran | ✅ |
| Pegar desde Excel (n × n o n × (n + 1)) | se ajusta el tamaño | ✅ |
| Pegar una sola fila en a₁₁ | se pega la fila | ✅ (corregido) |

### R2.4 Explicar cómo se ingresan los datos y prevenir errores
| Entrada | Mensaje esperado | Estado |
|---|---|---|
| Celda vacía | indica qué celda falta | ✅ |
| Celda con texto (`abc`) o `4,-1` | «No son números válidos» | ✅ (`4,-1` corregido) |
| Cero en la diagonal | avisa e indica que se intercambien filas | ✅ |
| ω = 2.5 en SOR | «debe cumplir 0 < ω < 2» | ✅ |
| Sistema mal escalado diag(10⁶, 10⁻⁷) | se resuelve, no se marca singular | ✅ (corregido) |
| Sección «Cómo ingresar el sistema» | explica el tamaño, el pegado y la diagonal | ✅ |

### R2.5 Gráfica e informe de comparación
| Caso | Esperado | Estado |
|---|---|---|
| Pestaña Comparar | tabla de 3 métodos y 5 gráficas de error contra las iteraciones | ✅ |
| Informe PDF | resumen, gráficas, T, C, ρ y tabla por método | ✅ |
| Error **de condición** κ(A) | — | ❌ pendiente |

---

## Capítulo 3 · Interpolación

### R3.1 Métodos: Vandermonde, Newton, Lagrange, spline lineal, cuadrático y cúbico
Puntos de p(x) = x³ − 2x + 1: (−1, 2), (0, 1), (1, 0), (2, 5).

| Caso | Esperado | Estado |
|---|---|---|
| Vandermonde, Newton y Lagrange | p(x) = x³ − 2x + 1 y p(3) = 22 en los tres | ✅ |
| Los tres splines | S(xᵢ) = yᵢ en los 4 nodos | ✅ |
| Spline lineal en x = 0.5 | 0.5, el promedio de y(0) y y(1) | ✅ |
| Spline cúbico | 3 tramos, sistema de 4(4 − 1) = 12 ecuaciones, S″ = 0 en los extremos | ✅ |

### R3.2 Graficar e imprimir el polinomio
| Caso | Esperado | Estado |
|---|---|---|
| Cualquier método | gráfica con la curva, los puntos usados y los reservados | ✅ |
| Vandermonde | p(x), la matriz [V \| y], el vector a y κ(V) | ✅ |
| Newton | forma de Newton, forma expandida y tabla de diferencias divididas | ✅ |
| Lagrange | Σ yᵢLᵢ(x), la forma expandida y cada Lᵢ(x) | ✅ |
| Splines | S(x) por tramos y tabla de coeficientes | ✅ |

### R3.3 Almacenar el 20 o 30 % de los datos
| Caso | Esperado | Estado |
|---|---|---|
| 10 puntos, 20 % | se reservan 2 puntos interiores, nunca los extremos | ✅ |
| 10 puntos, 30 % | se reservan 3 puntos interiores | ✅ |
| Marcar «reservar» a mano | pasa a «Elegidos a mano» | ✅ |
| Datos de y = 2x + 1, 30 % reservado | los 6 métodos dan error ≈ 0 (≤ 10⁻¹⁴) | ✅ |
| Función de Runge, 9 puntos, 30 % | el spline cuadrático tiene el menor error máximo (0.46, contra 0.55 del polinomio de grado 5) y aparece resaltado | ✅ |
| Comparar | tabla de errores máximos, gráfica con los 6 interpolantes y gráficas de error por dato | ✅ |

### R3.4 Hasta 10 datos
| Caso | Esperado | Estado |
|---|---|---|
| 10 puntos | el botón «Agregar punto» se desactiva | ✅ |
| Pegar 12 puntos | se usan los primeros 10 y se avisa | ✅ |
| 2 puntos | no deja quitar más | ✅ |

### R3.5 Explicar cómo se ingresan los datos y prevenir errores
| Entrada | Mensaje esperado | Estado |
|---|---|---|
| Celda vacía | «Faltan valores en la fila …» | ✅ |
| Texto en una celda | «no es un número válido» | ✅ |
| Dos puntos con el mismo x | «Las filas … tienen el mismo x» | ✅ |
| Reservar tantos que quedan < 2 | «se necesitan al menos 2: reserve menos puntos» | ✅ |
| «Evaluar en x» fuera del rango | avisa que es extrapolación | ✅ |
| Puntos desordenados | se ordenan y se avisa | ✅ |
| x grandes (1950…2020) | κ(V) ≈ 10³⁷ y aviso de mal condicionamiento | ✅ |
| Sección «Cómo ingresar los datos» | explica el formato, la reserva y el pegado | ✅ |

---

## General
| Caso | Esperado | Estado |
|---|---|---|
| Recargar la página | se conservan los datos de cada tema | ✅ |
| Cambiar de tema con los botones | se muestra solo el tema elegido; el enlace (#…) lo recuerda | ✅ |
| Sin internet | funciona: math.js y las fuentes están dentro del HTML | ✅ |
| Consola del navegador | sin errores de JavaScript en ninguna prueba | ✅ |

## Bugs encontrados y corregidos (2026-11-10)
1. Newton n2 decía «Convergió» en puntos que no son raíz, donde f′(x) = 0 (p. ej. cos(x) − 2 con x₀ = 0).
2. La derivada automática de `cbrt(x)` no era real para x < 0, así que Newton no arrancaba.
3. `x(x + 1)` y `2e(x − 1)` no se aceptaban como multiplicación.
4. `arctan`, `arcsin`, `arccos` y `ctg` no se reconocían.
5. Una celda con `4,-1` se leía como 3 en lugar de dar error.
6. Pegar una sola fila en la primera celda de A se bloqueaba.
7. Los sistemas mal escalados (p. ej. diag(10⁶, 10⁻⁷)) se marcaban como singulares.
8. Con b del orden de 10¹⁵, el sistema se declaraba divergente y el mensaje afirmaba ρ ≥ 1 aunque ρ = 0.25.

Pendiente conocido: Newton sobre f(x) = x − 2·10¹⁵ desde x₀ = 0 se declara divergente, porque el umbral de divergencia de raíces es fijo (10¹⁵). Es un caso extremo.
