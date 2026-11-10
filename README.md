# Métodos numéricos: proyecto final de Análisis Numérico

**Integrantes:** Santiago Rodríguez y Daniel Cruz

Aplicación para ejecutar los métodos vistos en el curso, organizada por capítulos.

## Cómo usarla

Descargue `metodos-numericos.html` y ábralo con doble clic en cualquier navegador (Chrome, Firefox o Edge). No hace falta instalar nada ni tener conexión a internet: todo está incluido en el archivo.

Cada capítulo tiene ejemplos listos en «Cargar ejemplo…» y una sección desplegable que explica cómo ingresar los datos. El botón «Informe PDF» genera el informe de comparación del capítulo abierto (en el diálogo de impresión, elija «Guardar como PDF»).

## Contenido

| Capítulo | Métodos | Salidas |
|---|---|---|
| 1. Raíces de ecuaciones | Bisección, regla falsa, punto fijo, secante, Newton, Newton para raíces múltiples (n1 con multiplicidad m y n2 con f″) | Gráfica paso a paso, tabla de iteraciones, derivada automática, comparación de los métodos con los errores absoluto, relativo, relativo a xₙ₋₁ y \|f(xₙ)\| |
| 2. Sistemas lineales | Jacobi, Gauss-Seidel, SOR (matrices de 2 × 2 a 8 × 8) | Tabla de iteraciones, matrices T y C, radio espectral ρ(T) y si el método converge, comparación con 5 medidas de error |
| 3. Interpolación | Vandermonde, Newton (diferencias divididas), Lagrange, spline lineal, cuadrático y cúbico (hasta 10 datos) | Gráfica, polinomio solución y desarrollo (matriz, tabla o coeficientes), validación con el 20 % o el 30 % de los datos reservados, comparación de errores |

## Implementación

- Un solo archivo HTML con JavaScript. Los cálculos se hacen en el navegador con números de punto flotante de doble precisión (IEEE 754), el mismo formato que usan Python y R.
- Los métodos numéricos están programados a mano. Están en los bloques `Core` (raíces), `Sis` (sistemas) e `Interp` (interpolación) del archivo.
- Solo se usa la librería [math.js](https://mathjs.org) (Apache-2.0) para leer las expresiones que escribe el usuario y derivarlas de forma simbólica.

## Pruebas

`casos-de-uso.md` contiene los casos de uso de cada requisito, con la entrada, el resultado esperado y el resultado obtenido.
