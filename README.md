tp7.c
```c
#include <stdio.h>
#define TAM 3
void mayor_menor(float precio[],int cod[]) {
	float min=999999999999999999,max=0;
	int algo;
	for(int i=0; i<TAM; i++) {
		if( precio[i]<min) {
			min=precio[i];
		}
		if(precio[i]>max) {
			max=precio[i];
		}
	}
	for(int i=0; i<TAM; i++) {
		if(max==precio[i]) {
			algo=cod[i];
			printf("\nMas caro:[%d] %f",algo,max);
		}
		if(min==precio[i]) {
			algo=cod[i];
			printf("\nMas barato:[%d] %f",algo,min);
		}
	}
}
void carga(int *p, float *f) {
	float min,max;
	for(int i=0; i<TAM; i++) {
		do {
			printf("\nIngrese el codigo de barras:");
			scanf("%d",p+i);
			if( (*p) <0 || (*p) > 999999999) {
				printf("\nERROR,no pueden ser numeros menores a 1 y mayores a 999999999");
			}
		} while( (*p) <0|| (*p) >999999999);
		do {
			printf("\nIngrese el precio del producto:");
			scanf("%f",f+i);
			if( (*f) <0) {
				printf("\nERROR,no pueden ser numeros negativos");
			}
		} while( (*f)<0);
	}
}
int main()
{
	int cod[TAM];
	int *p=cod;
	float precio[TAM],min,max;
	float *f=precio;
	printf("\nIngresa %d productos se solicitara el codigo y el precio:",TAM);
	carga(p,f);
	printf("\nCodigo    Precio:");
	for(int i=0; i<TAM; i++) {
		printf("\n%d      %f ",cod[i],precio[i]);
	}
	mayor_menor(precio,cod);
	return 0;
}
