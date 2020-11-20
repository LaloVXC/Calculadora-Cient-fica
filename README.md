#include <iostream>
#include <cmath>
using namespace std;
#define pi 3.1416
int Select;
//Declaracion de clases
class operaciones {				               	//Clase principal
	public:
		int suma(int numero);
		int resta(int numero);
		int multiplicacion(int numero);
		float division(int x, int y);
		int potencia(int valor,int exp);
};
/////////////////////////////////////////////////////////////////////////////
class geometria : public operaciones{			//clase de herencia 1
	public:
		//perimetro
		int perimetro_triangulo(int a, int b, int c);
		int perimetro_rectangulo(int b, int a);
		float perimetro_circulo(int d);
		//area
		int area_rectangulo(int b, int a);
		int area_triangulo(int b, int a);
		float area_circulo(int r);
		//volumen
		int vol_rectangulo(int b, int a, int h);
		int vol_triangulo(int b, int a, int h);
		float cilindro(int h, int r);
};
////////////////////////////////////////////////////////////////////////////////
class matrices : public geometria {		    	//clase de herencia 2
	public:
		void victoria_secrets(int tamanio, int* matriz);
		void laserjet1018(int tamanio, int* matriz);
		void voltron(int tamanio, int* matresult, int* matriz1, int* matriz2);
		void karina(int tamanio, int* matresult, int* matriz1, int* matriz2);
		void dotto(int tamanio, int* matresult, int* matriz1, int* matriz2);
		void venom(int tamanio, int* matresult, int* matriz);
};
//////////////////////////////////////////////////////////////////////////////
class vectores : public matrices {		     	//Clase de herencia 3
	public:
		void constantine();
		void rellenar_vector(int* vector);
		float distancia_puntos(int vectores[3][3]);
		float magnitud_vector1(int vectores[3][3]);
		float magnitud_vector2(int vectores[3][3]);
		void suma_vectores(int* vector1);
};
//////////////////////////////////////////////////////////////////////////////
class estadistica : public vectores {			//Clase de herencia 4
	public:
		void rellenar_datos(int numdato, int A[50]);
		float moda(int numdato, int A[50]);
		float promedio(int numdato, int A[50]);
		float mediana(int numdato, int A[50]);
};
/////////////////////////////////////////////////////////////////////////////
class calc_completa : public estadistica {		//Clase de herencia 5
	public:
		void aritmetica();
		void figuras();
		void matriz();
		void vector();
		void estadisticas();
};
//////////////////////////////////////////////////////////////////////////////
							//Funcion Principal

int main() {
	int SelectP;
	calc_completa o;
	while (1) {
		cout << "---calculadora---" <<endl;
		cout << "1.-Operaciones Aritméticas básicas. " <<endl;
		cout << "2.-Operaciones geométricas." <<endl;
		cout << "3.-Operaciones matriciales." <<endl;
		cout << "4.-Operaciones algebraicas y vectores." <<endl;
		cout << "5.-Operaciones estadísticas." <<endl;
		cin >> SelectP;
		switch (SelectP)
		{
			case 1:
				cout << "---Operaciones aritméticas básicas---" <<endl;
				cout << "1.-Suma" <<endl;
				cout << "2.-Resta" <<endl;
				cout << "3.-Multiplicacion" <<endl;
				cout << "4.-Division" <<endl;
				cout << "5.-Potencia" <<endl;
				cin >> Select;
				o.aritmetica();
				break;
			case 2:
				cout << "---Operaciones geométricas---" <<endl;
				cout << "--AREA--" <<endl;
				cout << "1.-Rectangulo" <<endl;
				cout << "2.-Triangulo" <<endl;
				cout << "3.-Circulo" <<endl;
				cout << "--PERIMETRO--" <<endl;
				cout << "4.-Rectangulo" <<endl;
				cout << "5.-Triangulo" <<endl;
				cout << "6.-circulo" <<endl;
				cout << "--VOLUMEN--" <<endl;
				cout << "7.-Prisma rectangular" <<endl;
				cout << "8.-Prisma triangular" <<endl;
				cout << "9.-Cilindro" <<endl;
				cin >> Select;
				o.figuras();
				break;
			case 3:
				cout << "---Operaciones matriciales---" <<endl;
				cout << "1.-Suma" <<endl;
				cout << "2.-Resta" <<endl;
				cout << "3.-Multiplicacion" <<endl;
				cout << "4.- transpuesta dematriz 1" <<endl;
				cout << "5.- transpuesta dematriz 2" <<endl;
				cin >> Select;
				o.matriz();
				break;
			case 4:
				cout << "--Operaciones algebraicas y vectores--" <<endl;
				cout << "1.-Resolución de sistemas de ecuaciones simples, 2 incógnitas" <<endl;
				cout << "2.-Distancia entre dos puntos." <<endl;
				cout << "3.-Magnitud de vector 1" <<endl;
				cout << "4.-Magnitud de vector 2" <<endl;
				cout << "5.-Suma de dos vectores" <<endl;
				cin >> Select;
				o.vector();
				break;
			case 5:
				cout << "---Operaciones estadísticas---" <<endl;
				cout << "1.-Promedio" <<endl;
				cout << "2.-Mediana" <<endl;
				cout << "3.-Moda" <<endl;
				cin >> Select;
				o.estadisticas();
				break;
			default:
				break;
		}
	}
	return 0;
}
//////////////////////////////////////////////////////////////////////////////////////
//Funciones Estructura operaciones
int operaciones::suma(int numero) {
	int sumatoria=0;
	int dato;
	for (int i = 0; i < numero; i++) {
		cout << (i + 1) << ": ";
		cin >> dato;
		sumatoria = sumatoria + dato;
	}

	return sumatoria;
}
int operaciones::resta(int numero) {
	int dato;
	int rest = 0;
	for (int i = 0; i < numero; i++) {
		cout << (i + 1) << ": ";
		cin >> dato;
		if (rest == 0) {
			rest = dato;
		}
		else {
			rest = rest - dato;
		}
	}

	return rest;
}
int operaciones::multiplicacion(int numero) {
	int acumulacion = 1;
	int dato;
	for (int i = 0; i < numero; i++) {
		cout << (i + 1) << ": ";
		cin >> dato;
		acumulacion = acumulacion * dato;
	}

	return acumulacion;
}
float operaciones::division(int a, int b) {
	return a/ b;
}
int operaciones::potencia(int a,int exp) {
	int save=1;
	for (int i = 0; i < exp; i++) {
		save = save * a;
	}
	return save;
}
////////////////////////////////////////

//funciones geometricas
int geometria::perimetro_triangulo(int a, int b, int c) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	if (c < 0) {
		c = c * (-1);
	}
	return (a + b + c);
}
int geometria::perimetro_rectangulo(int b, int a) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	return((2 * b) + (2 * a));
}
float geometria::perimetro_circulo(int d) {
	if (d < 0) {
		d = d * (-1);
	}

	return pi * d;
}
int geometria::area_triangulo(int b, int a) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	return((b*a)/2);
}
int geometria::area_rectangulo(int b, int a) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	return(b*a);
}
float geometria::area_circulo(int r) {
	if (r < 0) {
		r = r * (-1);
	}
	return((r^2)*pi);
}
int geometria::vol_rectangulo(int b, int a, int h) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	if (h < 0) {
		h = h * (-1);
	}
	return b*a*h;
}
int geometria::vol_triangulo(int b, int a, int h) {
	if (a < 0) {
		a = a * (-1);
	}
	if (b < 0) {
		b = b * (-1);
	}
	if (h < 0) {
		h = h * (-1);
	}
	return (((b*a)/2)*h);
}
float geometria::cilindro(int h, int r) {
	if (r < 0) {
		r = r * (-1);
	}
	if (h < 0) {
		h = h * (-1);
	}
	return ((pi*(r^2)) * h);
}
///////////////////////////////////////////////////////
//funciones matriciales
void matrices::victoria_secrets(int longer, int* mat) {
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {
			cout << j + 1 << ", " << i + 1 << ": ";
			cin >> *(mat + (i * longer) + j);
		}
	}
}
void matrices::laserjet1018(int longer, int* mat) {
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {
			cout << *(mat + (i * longer) + j) << " ";
		}
		cout << endl;
	}
}
void matrices::voltron(int longer, int* matresult, int* mat1, int* mat2) {
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {

			(*(matresult + (i * longer) + j)) = (*(mat1 + (i * longer) + j)) + (*(mat2 + (i * longer) + j));

		}

	}
}
void matrices::karina(int longer, int* matresult, int* mat1, int* mat2) {
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {
			(*(matresult + (i * longer) + j)) = (*(mat1 + (i * longer) + j)) - (*(mat2 + (i * longer) + j));
		}
	}
}
void matrices::dotto(int longer, int* matresult, int* mat1, int* mat2) {
	int op = 0;
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {
			op = 0;
			for (int k = 0; k < longer; k++) {
				op = ((*(mat1 + (i * longer) + k)) * (*(mat2 + (k * longer) + j))) + op;
			}
			*(matresult + (i * longer) + j) = op;
		}
	}
}
void matrices::venom(int longer, int* matresult, int* mat) {
	for (int i = 0; i < longer; i++) {
		for (int j = 0; j < longer; j++) {
			*(matresult + (i * longer) + j) = *(mat + (j * longer) + i);
		}
	}
}
////////////////////////////////////////////////////////////////////////////////////////
//funciones algebraicas y vectoriales
void vectores::constantine() {
	int sisec[2][3];
	cout << "Dime los datos de la primera funcion de la ecuacion: " << endl;
	cout << "(Ax+By=C)" << endl;
	cout << "A= "; cin >> sisec[0][0];
	cout << "B= "; cin >> sisec[0][1];
	cout << "C= "; cin >> sisec[0][2];
	cout << "Dime los datos de la segunda funcion de la ecuacion: " << endl;
	cout << "(Ax+By=C)" << endl;
	cout << "A= "; cin >> sisec[1][0];
	cout << "B= "; cin >> sisec[1][1];
	cout << "C= "; cin >> sisec[1][2];
	cout << "ecuacion 1:  " << sisec[0][0] << "x +" << sisec[0][1] << "y =" << sisec[0][2] << endl;
	cout << "ecuacion 2:  " << sisec[1][0] << "x +" << sisec[1][1] << "y =" << sisec[1][2] << endl;
	int determinante;
	float x, y;
	determinante = (sisec[0][0] * sisec[1][1]) - (sisec[0][1] * sisec[1][0]);
	x = -((sisec[0][1] * sisec[1][2]) - (sisec[0][2] * sisec[1][1])) / determinante;
	y = ((sisec[0][0] * sisec[1][2]) - (sisec[0][2] * sisec[1][0])) / determinante;
	cout << "x= " << x << endl;
	cout << "y= " << y << endl;
}
void vectores::rellenar_vector(int* vectores) {
	for (int j = 0; j < 2; j++) {
		cout << "Vector " << j + 1 << ": " << endl;
		for (int i = 0; i < 3; i++) {
			cin >> *(vectores + i+(j*3));
		}
	}
}
float vectores::distancia_puntos(int vectores[3][3]) {
	int suma_cuadrados;
	for (int i = 0; i < 3; i++) {
		vectores[2][i] = vectores[0][i] -vectores[1][i];
	}
	suma_cuadrados = vectores[2][0] + vectores[2][1] + vectores[2][2];
	return (sqrt(suma_cuadrados));
}
float vectores::magnitud_vector1(int vectores[3][3]) {
	int suma_cuadrados = (vectores[0][0] * vectores[0][0]) + (vectores[0][1] * vectores[0][1]) + (vectores[0][2] * vectores[0][2]);
	return (sqrt(suma_cuadrados));
}
float vectores::magnitud_vector2(int vectores[3][3]) {
	int suma_cuadrados = (vectores[1][0] * vectores[1][0]) + (vectores[1][1] * vectores[1][1]) + (vectores[1][2] * vectores[1][2]);
	return (sqrt(suma_cuadrados));
}
void vectores::suma_vectores(int* vector1) {
	for (int i = 0; i < 3; i++) {
		*(vector1 + i + 6) = ((*(vector1 + i)) + (*(vector1 + i + 3)));
	}
}
//////////////////////////////////////////////////////////////////////
//Funciones estadisticas
void estadistica::rellenar_datos(int numdato, int A[50]) {
	cout << "Ingrese los datos : "<<endl;
	for (int i = 0; i < numdato; i++) {
		cout << "ingrese: ";
		cin >> A[i];
	}
}
//MODA
float estadistica::moda(int Numdatos, int datos[50]) {
	int s=0, m=s, a=1;

	for (int i = 0; i < Numdatos; i++) {
		s = 0;
		for (int j = 0; j < Numdatos; j++) {
			if (datos[i] == datos[j] && i != j) {
				s = (s + 1);
			}
		}
		if (s >= m) {
			m = s;
			a = i;
		}
	}
	return datos[a];
}
//PROMEDIO
float estadistica::promedio(int Numdatos, int datos[50]) {
	int sumatoria = 0;
	for (int i = 0; i < Numdatos; i++) {
		sumatoria = (sumatoria + datos[i]);
	}
	return (sumatoria/ Numdatos);
}
//MEDIANA
float estadistica::mediana(int Numdatos, int datos[50]) {
	int aux;
	for (int i = 0; i < Numdatos; i++) {
		for (int j = 0; j < Numdatos; j++) {
			if (datos[j] > datos[j + 1]) {
				aux = datos[j];
				datos[j] = datos[j + 1];
				datos[j + 1] = aux;
			}
		}
	}
	return datos[Numdatos /2];
}
///////////////////////////////////////////////////////////////////
//Funciones calculadora completa
//MENU DE ARITMETICA
void calc_completa::aritmetica() {
	int a, b;
	switch (Select){
		case 1://suma
			cout << "Cuantos datos quieres sumar?: " << endl;
			cin >> a;
			cout << "La suma total es: " << suma(a)<<endl;
			break;
		case 2://resta
			cout << "Cuantos datos quieres restar?: " << endl;
			cin >> a;
			cout << "La resta total es: " << resta(a) << endl;
			break;
		case 3://multiplicacion
			cout << "Cuantos datos quieres multiplicar?: " << endl;
			cin >> a;
			cout << "= " << multiplicacion(a) << endl;
			break;
		case 4:// division
			cout << "division: " << endl;
			cin >> a;
			cout << "/" << endl;
			cin >> b;
			cout << "= " << division(a, b) << endl;
			break;
		case 5://potencia
			cout << "potencia: " << endl;
			cin >> a;
			cout << "elevado a la: ";
			cin >> b;
			cout << "= " << potencia(a, b) << endl;
			break;
		default://salida
			break;
	}
}
//MENU DE GRAOMETRICA
void calc_completa::figuras() {
	int a, b, c;
	//Se separan los casos dependiendo la figura
	switch (Select){
		case 1:
			cout << "Cual es la altura del rectangulo: ";
			cin >> a;
			cout << "Cual es la base del rectangulo: ";
			cin >> b;
			cout << "El area es: " << area_rectangulo(a, b) << endl;
			break;
		case 2:
			cout << "Cual es la altura del triangulo: ";
			cin >> a;
			cout << "Cual es la base del triangulo: ";
			cin >> b;
			cout << "El area es: " << area_triangulo(a, b) << endl;
			break;
		case 3:
			cout << "Cual es el Radio del circulo: ";
			cin >> a;
			cout << "El area es: " << area_circulo(a) << endl;
			break;
		case 4:
			cout << "Cual es la altura del rectangulo: ";
			cin >> a;
			cout << "Cual es la base del rectangulo: ";
			cin >> b;
			cout << "El perimetro es: " << perimetro_rectangulo(a, b) << endl;
			break;
		case 5:
			cout << "Cual es el lado 'a' del triangulo: ";
			cin >> a;
			cout << "Cual es el lado 'b' del triangulo: ";
			cin >> b;
			cout << "Cual es el lado 'c' del triangulo: ";
			cin >> c;
			cout << "El perimetro es: " << perimetro_triangulo(a, b, c) << endl;
			break;
		case 6:
			cout << "Cual es el diametro del circulo: ";
			cin >> a;
			cout << "El perimetro es: " << perimetro_circulo(a) << endl;
			break;
		case 7:
			cout << "Cual es la Base del rectangulo: ";
			cin >> a;
			cout << "Cual es la altura(a) del rectangulo: ";
			cin >> b;
			cout << "Cual es la altura(h) del solido: ";
			cin >> c;
			cout << "El volumen es: " << vol_rectangulo(a, b, c) << endl;
			break;
		case 8:
			cout << "Cual es la Base del triangulo: ";
			cin >> a;
			cout << "Cual es la altura(a) del triangulo: ";
			cin >> b;
			cout << "Cual es la altura(h) del solido: ";
			cin >> c;
			cout << "El volumen es: " << vol_triangulo(a, b, c) << endl;
			break;
		case 9:
			cout << "Cual es el radio del circulo: ";
			cin >> a;
			cout << "Cual es la altura del cilindro: ";
			cin >> b;
			cout << "el volumen del cilindro es: " << cilindro(b, a) << endl;
			break;
		default:
			break;
	}
}
//MENU DE MATRICES
void calc_completa::matriz() {
	int sice=3;
	int Mat1[3], Mat2[3], Mat3[3];
	cout << "define las dimensiones de la matriz  " << endl;
	cin >> sice;
	cout << "DIme la matriz 1" << endl;
	victoria_secrets(sice, (int*)Mat2);
	laserjet1018(sice, (int*)Mat2);
	cout << endl;
	cout << "DIme la matriz 2" << endl;
	victoria_secrets(sice, (int*)Mat3);
	laserjet1018(sice, (int*)Mat3);
	cout << endl;
//Aqui se escoje el tipo de operacion y se utilizan nombres para identificarlos 
	switch (Select) {
	case 1:
		cout << "La suma de las matrices es: " << endl;
		voltron(sice, (int*)Mat1, (int*)Mat2, (int*)Mat3);
		laserjet1018(sice, (int*)Mat1);
		cout << endl;
		break;
	case 2:
		cout << "La resta de las matrices es: " << endl;
		karina(sice, (int*)Mat1, (int*)Mat2, (int*)Mat3);
		laserjet1018(sice, (int*)Mat1);
		cout << endl;
		break;
	case 3:
		cout << "La multiplicacion de las matrices es: " << endl;
		dotto(sice, (int*)Mat1, (int*)Mat2, (int*)Mat3);
		laserjet1018(sice, (int*)Mat1);
		cout << endl;
		break;
	case 4:
		cout << "La Transpuesta de la matriz 1 es: " << endl;
		venom(sice, (int*)Mat1, (int*)Mat2);
		laserjet1018(sice, (int*)Mat1);
		cout << endl;
		break;
	case 5:
		cout << "La Transpuesta de la matriz 2 es: " << endl;
		venom(sice, (int*)Mat1, (int*)Mat3);
			laserjet1018(sice, (int*)Mat1);
			cout << endl;
			break;
		default:
			break;
	}
}
//MENU DE VECTORES
void calc_completa::vector() {
	int vec1[3][3];
	switch (Select){
		case 1:
			constantine();
			break;
		case 2:
			cout << "ingresa los vectores" << endl;
			rellenar_vector((int*)vec1);
			cout << endl;
			cout << "la distancia entre los puntos es: " << distancia_puntos(vec1) << endl;
			break;
		case 3:
			cout << "ingresa los vectores" << endl;
			rellenar_vector((int*)vec1);
			cout << endl;
			cout << "la magnitud del vector es: " << magnitud_vector1(vec1);
			break;
		case 4:
			cout << "ingresa los vectores" << endl;
			rellenar_vector((int*)vec1);
			cout << endl;
			cout << "la magnitud del vector es: " << magnitud_vector1(vec1);
			break;
		case 5:
			cout << "ingresa los vectores" << endl;
			rellenar_vector((int*)vec1);
			cout << endl;
			cout << "la suma de vectores es: " << endl;
			suma_vectores((int*)vec1);
			cout << "(" << vec1[2][0] << ", " << vec1[2][1] << ", " << vec1[2][2] << ")" << endl;
			break;
		default:
			break;
	}
}
//MENU DE ESTADISTICA
void calc_completa::estadisticas() {
	int A[50];
	int Num;
	cout << "que cantidad de datos ingresaras?" << endl;
	cin >> Num;
	cout << "dame los datos" << endl;
	rellenar_datos(Num, A);
	switch (Select)
	{
		case 1:
			cout << "el promedio es: " << promedio(Num, A) << endl;
			break;
		case 2:
			cout << "la mediana es: " << mediana(Num, A) << endl;
			break;
		case 3:
			cout << "la moda es: " << moda(Num, A) << endl;
			break;
		default:
			break;
	}
}
