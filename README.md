# Sistema de Facturación
### Fecha: 28/06/2023

## Tabla de contenidos
1. [Introducción](#introducción)
2. [Objetivo](#objetivo)
3. [Desarrollo del programa](#desarrollo-del-programa)
4. [Funcionalidades del programa](#funcionalidades-del-programa)
5. [Integración con el dispositivo externo](#integración-con-el-dispositivo-externo)
6. [Resultados y Beneficios](#resultados-y-beneficios)
7. [Presentación de avance de código](#presentación-de-avance-de-código)

## Introducción
La automatización y la mejora de la eficiencia de diversos procesos es indispensable en la actualidad. En este contexto, el desarrollo de un programa de sistema de facturación en C++ se presenta como una solución innovadora y beneficiosa para empresas y comercios. El programa permite a los usuarios realizar el proceso de facturación de manera ágil y precisa, simplificando tareas como cálculo y transacción. Además, se integra con una impresora de facturas para generar e imprimir automáticamente las facturas.

## Objetivo
### Objetivo Principal
Crear un sistema de facturación completo y eficiente, que proporcione una experiencia fluida al usuario al seleccionar productos, calcular precios y realizar transacciones, además de garantizar la correcta impresión de facturas a través de la conexión con la impresora externa.
### Objetivos Específicos
- Crear la lógica de cálculo necesaria para determinar el precio total de compra, considerando los productos seleccionados y sus respectivos precios.
- Investigar y seleccionar una solución de conexión entre el programa y la impresora de facturas, considerando los requisitos técnicos y las capacidades del dispositivo.
- Realizar pruebas del programa para verificar su funcionalidad, tanto en términos de la generación correcta de facturas como la conexión de impresora.

## Desarrollo del programa
El desarrollo del programa de facturación sigue un proceso metódico y estructurado para garantizar la implementación exitosa de todas las funcionalidades requeridas. A continuación, se detalla el proceso de desarrollo a seguir durante la creación del programa.
1. Análisis de requisitos: Realizar una fase de análisis exhaustiva para comprender completamente los requisitos del programa de facturación. Evaluar las operaciones claves a realizarse, como selección de productos, cálculo de precios y manejo de pagos, junto con la integración de la impresora de facturas.
2. Diseño de la interfaz de usuario: Diseñar una interfaz de usuario intuitiva y fácil de usar que permita a los usuarios interactuar eficientemente con el programa. Prestar especial atención a la navegación fluida y proporcionar retroalimentación visual para facilitar la comprensión de las operaciones realizadas.
3. Implementación de funciones y lógica de cálculo: Implementar las funciones y la lógica de cálculo necesaria para el funcionamiento del programa. Crear funciones en C++ para realizar tareas como la selección de productos, el cálculo del precio total de la compra, el inventario de productos, la gestión de pagos y la determinación del cambio a devolver. Diseñar una estructura de datos adecuada para almacenar y organizar la información de los productos y las facturas generadas.

## Funcionalidades del programa
Las principales funcionalidades del programa propuesto incluyen:
- Cálculo de precios: Permite calcular el precio total de la compra en base a los productos seleccionados.
- Gestión de pagos: Facilita el proceso de pago y determina el cambio a devolver en caso de pagos en efectivo.
- Generación de facturas automáticas: Genera e imprime automáticamente las facturas correspondientes a cada transacción realizada.

## Integración con el dispositivo externo
Para lograr la integración con la impresora de facturas, se investigaron opciones disponibles y se seleccionó la más adecuada. El método de conexión se establecerá mediante el uso de un puerto USB, se instalan los controladores necesarios y se configura el sistema para establecer una comunicación efectiva entre el programa y la impresora. Este proceso implica la utilización de bibliotecas o APIs específicas que permitan enviar comandos de impresión al dispositivo. Se realizan pruebas rigurosas para garantizar que los datos de las facturas se envíen correctamente y que la impresión se realice de manera precisa y legible.

## Resultados y Beneficios
La mejora en la eficiencia del proceso de facturación resulta importante para agilizar el proceso de facturación, además del almacenamiento automático de facturas, eliminando la necesidad de generarlas manualmente. El programa realiza cálculos precisos y exactos, evitando errores de redondeo y garantizando que los clientes reciban el cambio correcto al realizar pagos en efectivo.

## Presentación de avance de código


## Código para seleccionar y calcular el precio de productos

Este código permite al usuario seleccionar productos de una tienda de galletas llamada "Galletas Angulo", calcular el precio total de la compra y el cambio.

## Requisitos

- Se requiere un compilador de C++ para compilar y ejecutar este código.
- Se deben tener instaladas las bibliotecas estándar de C++.

## Estructura del código

El código tiene la siguiente estructura:

- `BASE.cpp`: Contiene la función `main` que inicia la ejecución del programa.

```cpp
#include "iostream"
#include "stdlib.h"
#include "unistd.h"
#include "strings.h"
#include "../lib/menuhelperomegadeluxe.h"
using namespace std;

int main()
{
    menuepico();
    return 0;
}
```

- `menuhelperomegadeluxe.h`: Contiene declaraciones de funciones auxiliares utilizadas en el programa.

```cpp
#include "iostream"
#include "string"
#include "string.h"
#include "algorithm"
#include <random>
#include "unistd.h"
#include "stdlib.h"
#include "../lib/patColor.h"
using namespace std;
#define DELAY 10000
enum items {GAL=1,PAS,TOR,HEL,BEB };//variables enumeradas para el swicth..
enum items1 {CHI=1,AVE,POL};
enum items2 {MIL=1,ORE,PAT};
enum items3 {CHOC=1,TRE,RED};
enum items4 {CHOCO=1,SAL,FRE};
enum items5 {COCA=1,CAF,LEC};

int getnumeromas01()//obtiene un numero de dinero obtenido
{
    int numero=0;
    char opc[1000];
    do{
        setTextColor(textColorMagenta);
        printf("\ningrese el dinero recibido: ");
        gets(opc);
        sscanf(opc,"%i",&numero);
    } while (numero<=0);
    fflush(stdin);
    fflush(stdout);
    return numero;
}
int getnumeromas00()// obtiene la cantidad de producto deseada
{
    int numero=0;
    char opc[1000];
    do{
        setTextColor(textColorRed);
        printf("\nQue cantidad del producto desea?: ");
        gets(opc);
        sscanf(opc,"%i",&numero);
    } while (numero<=0);
    fflush(stdin);
    fflush(stdout);
    return numero;
}
void enter() //detiene el programa hasta dar en enter
{
    cout << "Presiona Enter para continuar...";
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
}
int getnumeromasp2() //elige el segundo menu de productos
{
    int numero=0;
    char opc[10000];
    printf("\n\telige el producto:");
    do{
        
        gets(opc);
        sscanf(opc,"%i",&numero);
    } while (numero<=0 || numero>=5);
    fflush(stdin);
    fflush(stdout);
    return numero;
}
int getnumeromasp1() //menu principal
{
    int numero=0;
    char opc[10000];
    setTextColor(textColorGreen);
    printf("=====BIENVENIDO A GALLETAS ANGULO=====");
    setTextColor(textColorWhite);
    printf("\n1.-Galletas                           \n2.-Pastas                             \n3.-Tortas                             \n4.-Helados                             \n5.-Bebidas                            \n\telige el producto: ");
    do{
        
        gets(opc);
        sscanf(opc,"%i",&numero);
    } while (numero<=0 || numero>5);
    fflush(stdin);
    fflush(stdout);
    return numero;
}

int multiplicar(float precio) //realiza las operaciones para obtener el gasto final ,el cambio y se despide
{
   float total=0;
   float vuelto=0;
   int cantidad=getnumeromas00();
   

   total=cantidad*precio;
   setTextColor(textColorWhite);
   cout <<"\n El valor a pagar es: "<< total<< "$$" << endl;

   int plata = getnumeromas01();
   float cambio =plata-total;

   if (cambio<=0)
   {
    cambio=0;
   }
   setTextColor(textColorWhite);
   cout <<"\n Cambio: \n"<< cambio<< "$$" << endl;

   enter();
   setTextColor(textColorRed);
   cout <<"\n======GRACIAS POR SU COMPRA====== " << endl;
   
return 0;



}


void menuepico() //switch entre todos los menus
{
switch (getnumeromasp1())
{
case GAL: cout << " 1.-Chispas   $0.50\n 2.-avena   $0.50\n 3.-polvorosas   $0.75" << endl ;
          switch ( getnumeromasp2())
          {
          case CHI: multiplicar(0.5);

                    break;
          case AVE: multiplicar(0.5);
                    break;
          case POL: multiplicar(0.75);
                    break;
          default:
                    break;
          }
         break;
case PAS: cout <<" 1.-Milhojas   $0.50\n 2.-Orejitas   $0.50\n 3.-Paticas    $0.75" << endl ;
switch ( getnumeromasp2())
          {
          case MIL: multiplicar(0.5);
                    break;
          case ORE: multiplicar(0.5);
                    break;
          case PAT: multiplicar(1.2);
                    break;
          default:
                    break;
          }
            break;
case TOR: cout << " 1.-Chocolate   $0.50\n 2.-Tresleches  $0.50\n 3.-RedVelvet   $0.75" << endl ;
switch ( getnumeromasp2())
          {
          case CHOC: multiplicar(0.5);
                    break;
          case TRE: multiplicar(0.5);
                    break;
          case RED: multiplicar(1.2);
                    break;
          default:
            break;
          }

         break;
case HEL: cout << " 1.-Chocolate   $0.50\n 2.-Salcedo   $0.50\n 3.-Fresa   $0.75" << endl ;
switch ( getnumeromasp2())
          {
          case CHOCO: multiplicar(0.5);
                    break;
          case SAL: multiplicar(0.5);
                    break;
          case FRE: multiplicar(1.2);
                    break;
          default:
                    break;
          }

         break;
case BEB: cout << " 1.-Coca cola   $0.50\n 2.-Cafe        $0.50\n 3.-Leche       $0.75" << endl ;
switch ( getnumeromasp2())
          {
          case COCA: multiplicar(0.5);
                    break;
          case CAF: multiplicar(0.5);
                    break;
          case LEC: multiplicar(1.2);
                    break;
          default:
            break;
          }

         break;
default:
    break;
}

}
```

- `patColor.h`: Contiene declaraciones para cambiar el color del texto en la terminal.

```cpp
//===Color font ===/
#define COLOR_BLACK   "\x1B[30m"
#define COLOR_RED     "\x1b[31m"
#define COLOR_GREEN   "\x1b[32m"
#define COLOR_YELLOW  "\x1b[33m"
#define COLOR_BLUE    "\x1b[34m"
#define COLOR_MAGENTA "\x1b[35m"
#define COLOR_CYAN    "\x1b[36m"
#define COLOR_WHITE   "\x1B[37m"
#define COLOR_ORANGE  "\x1B[38;2;255;128;0m"
#define COLOR_ROSE    "\x1B[38;2;255;151;203m"
#define COLOR_LBLUE   "\x1B[38;2;53;149;240m"
#define COLOR_LGREEN  "\x1B[38;2;17;245;120m"
#define COLOR_GRAY    "\x1B[38;2;176;174;174m"
#define COLOR_RESET   "\x1b[0m"

//===Color background ===/
#define BG_BLACK   "\x1B[40m"
#define BG_RED     "\x1B[41m"
#define BG_GREEN   "\x1B[42m"
#define BG_YELLOW  "\x1B[43m"
#define BG_BLUE    "\x1B[44m"
#define BG_MAGENTA "\x1B[45m"
#define BG_CYAN    "\x1B[46m"
#define BG_WHITE   "\x1B[47m"
#define BG_ORANGE  "\x1B[48;2;255;128;0m"
#define BG_LBLUE   "\x1B[48;2;53;149;240m"
#define BG_LGREEN  "\x1B[48;2;17;245;120m"
#define BG_GRAY    "\x1B[48;2;176;174;174m"
#define BG_ROSE    "\x1B[48;2;255;151;203m"

//Colores de texto
#define textColorBlack 30
#define textColorRed 31
#define textColorGreen 32
#define textColorYellow 33
#define textColorBlue 34
#define textColorMagenta 35
#define textColorCyan 36
#define textColorWhite 37

//colores de fondo
#define fnBgBlack 40
#define fnBgRed 41
#define fnBgGreen 42
#define fnBgYellow 43
#define fnBgBlue 44
#define fnBgMagenta 45
#define fnBgCyan 46
#define fnBgWhite 47
```

El programa utiliza las siguientes bibliotecas estándar de C++:

- `iostream`: Proporciona funciones de entrada/salida estándar.
- `string`: Proporciona funciones y objetos para trabajar con cadenas de caracteres.
- `string.h`: Proporciona funciones para trabajar con cadenas de caracteres.
- `algorithm`: Proporciona funciones para realizar operaciones en rangos de elementos.
- `random`: Proporciona generadores de números aleatorios.
- `unistd.h`: Proporciona funciones para la interfaz con el sistema operativo.
- `stdlib.h`: Proporciona funciones y tipos de datos generales.
- `strings.h`: Proporciona funciones para trabajar con cadenas de caracteres.

## Uso del programa

1. Al iniciar el programa, se mostrará un menú principal con las siguientes opciones:
    
   ```cpp
   =====BIENVENIDO A GALLETAS ANGULO=====
   1.-Galletas
   2.-Pastas
   3.-Tortas
   4.-Helados
   5.-Bebidas
   Elige el producto:
   ```

2. El usuario debe ingresar el número correspondiente al tipo de producto que desea comprar y presionar Enter.
3. A continuación, se mostrará un submenú con las variantes disponibles para el producto seleccionado y sus precios:

   ```cpp
   1.-Chispas   $0.50
   2.-avena     $0.50
   3.-polvorosas $0.75
   Elige el producto:
   ```

4. El usuario debe ingresar el número correspondiente a la variante que desea comprar y presionar Enter.
5. El programa calculará el precio total de la compra multiplicando la cantidad seleccionada por el precio de la variante elegida.
6. Se mostrará el precio total de la compra en la pantalla:

   ```cpp
   El valor a pagar es: $X.XX
   ```
7. Se solicitará al usuario ingresar la cantidad de dinero recibido y se mostrará la cantidad de vuelto a devolver.

    ```cpp
   Ingrese el dinero recibido:

   Cambio: $X.XX
   ```
   
8. El programa finaliza su ejecución.