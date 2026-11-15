#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 5
int contpro = 0;

void ingresar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);
void mostrar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);
void buscar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);
void editar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);
void eliminar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);
void evaluar_viabilidad(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]);


int main() {
    char nombres[MAX][50];
    int demanda[MAX];
    float tiempo_unitario[MAX];
    float recursos_unitarios[MAX];
    int op;

    do {
        system("cls");
        printf("====== GESTION DE PRODUCCION  ELECTRONICA ======\n");
        printf("=================================================\n");
        printf(" 1. Agregar productos (Max 5)                    \n");
        printf(" 2. Mostrar productos                            \n");
        printf(" 3. Buscar productos                             \n");
        printf(" 4. Editar producto                              \n");
        printf(" 5. Eliminar producto                            \n");
        printf(" 6. Evaluar tiempo, recursos y viabilidad        \n");
        printf(" 7. Salir                                        \n");
        printf("=================================================\n");
        printf(" Ingrese una opcion del 1-7: ");
        scanf("%d", &op);

        switch (op) {
        case 1:
            system("cls");
            ingresar_productos(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 2:
            system("cls");
            mostrar_productos(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 3:
            system("cls");
            buscar_productos(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 4:
            system("cls");
            editar_productos(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 5:
            system("cls");
            eliminar_productos(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 6:
            system("cls");
            evaluar_viabilidad(nombres, demanda, tiempo_unitario, recursos_unitarios);
            system("pause");
            break;
        case 7:
            system("cls");
            printf("==== Saliendo del sistema de produccion ====\n");
            system("pause");
            break;
        default:
            printf("Opcion invalida. Intente nuevamente.\n");
            system("pause");
            break;
        }
    } while (op != 7);

    return 0;
}


void ingresar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    if (contpro < MAX) {
        printf("--- REGISTRO DE PRODUCTO [%d/%d] ---\n", contpro + 1, MAX);
        printf("Ingrese el nombre del componente: ");
        scanf(" %[^\n]", nombres[contpro]);
        printf("Ingrese la cantidad demandada: ");
        scanf("%d", &demanda[contpro]);
        printf("Ingrese el tiempo de fabricacion por unidad (horas): ");
        scanf("%f", &tiempo_unitario[contpro]);
        printf("Ingrese la cantidad de recursos por unidad: ");
        scanf("%f", &recursos_unitarios[contpro]);
        contpro++;
        printf("\n¡Producto registrado exitosamente!\n");
    } else {
        printf("¡Capacidad maxima alcanzada! Ya no hay espacio para mas productos.\n");
    }
}


void mostrar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    if (contpro == 0) {
        printf("No hay productos registrados en el sistema.\n");
        return;
    }
    
    printf("=========================================================================\n");
    printf("NOMBRE         DEMANDA     TIEMPO U.      RECURSOS U.\n");
    printf("=========================================================================\n");
    for (int i = 0; i < contpro; i++) {
        printf("%s           %d          %.2f           %.2f\n", 
               nombres[i], demanda[i], tiempo_unitario[i], recursos_unitarios[i]);
    }
    printf("=========================================================================\n");
}


void buscar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    char nombuscar[50];
    int encontrar = 0;

    if (contpro == 0) {
        printf("No hay productos ingresados para buscar.\n");
        return;
    }
    
    printf("Ingrese el nombre del producto a buscar: ");
    scanf(" %[^\n]", nombuscar);

    for (int i = 0; i < contpro; i++) {
        if (strcmp(nombres[i], nombuscar) == 0) {
            printf("\n¡Producto encontrado!\n");
            printf(" - Nombre: %s\n", nombres[i]);
            printf(" - Demanda: %d unidades\n", demanda[i]);
            printf(" - Tiempo unitario: %.2f horas\n", tiempo_unitario[i]);
            printf(" - Recursos unitarios: %.2f unidades\n", recursos_unitarios[i]);
            encontrar = 1;
            break;
        }
    }
    if (encontrar == 0) {
        printf("El producto '%s' no existe en el sistema.\n", nombuscar);
    }
}


void editar_productos(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    char nombuscar[50];
    int encontrar = 0;

    if (contpro == 0) {
        printf("No hay productos registrados para editar.\n");
        return;
    }

    printf("Ingrese el nombre del producto que desea editar: ");
    scanf(" %[^\n]", nombuscar);

    for (int i = 0; i < contpro; i++) {
        if (strcmp(nombres[i], nombuscar) == 0) {
            printf("\nProducto encontrado. Ingrese los nuevos datos:\n");
            printf("Nuevo nombre: ");
            scanf(" %[^\n]", nombres[i]);
            printf("Nueva demanda: ");
            scanf("%d", &demanda[i]);
            printf("Nuevo tiempo unitario (horas): ");
            scanf("%f", &tiempo_unitario[i]);
            printf("Nuevos recursos unitarios: ");
            scanf("%f", &recursos_unitarios[i]);
            
            printf("\n¡Producto actualizado correctamente!\n");
            encontrar = 1;
            break;
        }
    }[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    char nombuscar[50];
    int encontrar = 0;

    if (contpro == 0) {
        printf("No hay productos registrados para eliminar.\n");
        return;
    if (encontrar == 0) {
        printf("No se encontro el producto para editar.\n");
    }
}


void eliminar_productos(char nombres[MAX][50], int demanda
    }

    printf("Ingrese el nombre del producto que desea eliminar: ");
    scanf(" %[^\n]", nombuscar);

    for (int i = 0; i < contpro; i++) {
        if (strcmp(nombres[i], nombuscar) == 0) {
            
            for (int j = i; j < contpro - 1; j++) {
                strcpy(nombres[j], nombres[j + 1]);
                demanda[j] = demanda[j + 1];
                tiempo_unitario[j] = tiempo_unitario[j + 1];
                recursos_unitarios[j] = recursos_unitarios[j + 1];
            }
            contpro--;
            printf("\n¡Producto eliminado exitosamente del sistema!\n");
            encontrar = 1;
            break;
        }
    }
    if (encontrar == 0) {
        printf("El producto no fue encontrado para eliminar.\n");
    }
}


void evaluar_viabilidad(char nombres[MAX][50], int demanda[MAX], float tiempo_unitario[MAX], float recursos_unitarios[MAX]) {
    if (contpro == 0) {
        printf("No hay productos registrados para realizar la evaluacion.\n");
        return;
    }

    float tiempo_disponible, recursos_disponibles;
    float tiempo_total_req = 0;
    float recursos_totales_req = 0;

    printf("--- EVALUACION DE VIABILIDAD DE LA FABRICA ---\n");
    printf("Ingrese el tiempo total disponible en la planta (horas): ");
    scanf("%f", &tiempo_disponible);
    printf("Ingrese la cantidad total de recursos disponibles: ");
    scanf("%f", &recursos_disponibles);

    
    for (int i = 0; i < contpro; i++) {
        tiempo_total_req += (demanda[i] * tiempo_unitario[i]);
        recursos_totales_req += (demanda[i] * recursos_unitarios[i]);
    }

    printf("\n=========================================================\n");
    printf("                  RESULTADOS DE ANALISIS                 \n");
    printf("=========================================================\n");
    printf(" Tiempo Total Requerido:      %.2f horas\n", tiempo_total_req);
    printf(" Tiempo Disponible en Planta: %.2f horas\n", tiempo_disponible);
    printf(" Recursos Totales Requeridos: %.2f unidades\n", recursos_totales_req);
    printf(" Recursos Disponibles Planta: %.2f unidades\n", recursos_disponibles);
    printf("---------------------------------------------------------\n");

    if (tiempo_total_req <= tiempo_disponible && recursos_totales_req <= recursos_disponibles) {
        printf(" ESTADO: ¡VIABLE! La fabrica PUEDE cumplir con toda la demanda.\n");
    } else {
        printf(" ESTADO: ¡NO VIABLE! La fabrica NO puede cumplir con la demanda.\n");
        if (tiempo_total_req > tiempo_disponible) {
            printf(" -> Motivo: Exceso de tiempo requerido por %.2f horas.\n", (tiempo_total_req - tiempo_disponible));
        }
        if (recursos_totales_req > recursos_disponibles) {
            printf(" -> Motivo: Insuficiencia de recursos por %.2f unidades.\n", (recursos_totales_req - recursos_disponibles));
        }
    }
    printf("=========================================================\n");
}
