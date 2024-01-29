#include <omp.h> // Incluimos la biblioteca OpenMP
#include <iostream>

// Tamaño de los arreglos
#define N 1000 
// Tamaño del "chunk" para la paralelización
#define chunk 100
// Número de elementos a mostrar
#define mostrar 10

// Prototipo de la función para imprimir arreglos
void imprimeArreglo(float *d);

int main()
{
    std::cout << "Sumando Arreglos en Paralelo!\n"; 
    
    // Declarar arreglos a, b, y c
    float a[N], b[N], c[N]; 
    int i;
    
    srand(time(NULL)); // Inicializar la semilla del generador de números aleatorios

    // Inicialización de los arreglos a y b con números aleatorios
    for (i = 0; i < N; i++)
    {
        // Números aleatorios entre 1 y N-1
        a[i] = 1 + rand() % (N - 1); 
        b[i] = 1 + rand() % (N - 1);
    }
    // Tamaño del "chunk" para la paralelización
    int pedazos = chunk; 

    // Paralelización con OpenMP
    #pragma omp parallel for \
    shared(a, b, c, pedazos) private(i) \
    schedule(static, pedazos)

    // Operación de suma en paralelo
    for (i = 0; i < N; i++)
        c[i] = a[i] + b[i];

    // Impresión de los primeros elementos de los arreglos
    std::cout << "Imprimiendo los primeros " << mostrar << " valores del arreglo a: " << std::endl;
    imprimeArreglo(a);
    std::cout << "Imprimiendo los primeros " << mostrar << " valores del arreglo b: " << std::endl;
    imprimeArreglo(b);
    std::cout << "Imprimiendo los primeros " << mostrar << " valores del arreglo c: " << std::endl;
    imprimeArreglo(c);
}

// Definición de la función para imprimir arreglos
void imprimeArreglo(float *d)
{
    for (int x = 0; x < mostrar; x++) 
        std::cout << d[x] << " - ";
    std::cout << std::endl;
}
