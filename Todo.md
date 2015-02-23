
#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
//#include "words.h"

using std::cout;
using std::cin;
using std::endl;
using std::vector;

void imperr(vector<char> , vector<char> );
const char* getWord();

int main(int argc, char *argv[]){
	srand(time(0));
	char resp='s';
		while(resp=='s'||resp=='S'){	
		int cont=0;
		//words p;
		const char* palabra=getWord();
		vector<char> aciertos;
		vector<char> todo;
		vector<char> errores;
		char lives[7]="OOOOOO";
		bool ganperd=false;
			cout<<"¡Bienvenido Usuario a Ahorcado!"<<endl;
			cout<<"Tiene 6 intentos para adivinar la palabra"<<endl;
				int contador=0;
					for(int i=0;i<30;i++){
						if(palabra[i]=='\0'){
							break;
						}else{
							contador++;
						}
					}
				char* progreso=new char[contador+1];
					for(int i=0;i<contador;i++){
						progreso[i]='_';
					}	
				while(cont<6){
					char letra;
					bool quesiga=false;
						cout<<"Vidas: "<<lives<<endl;
						while(quesiga==false){
							cout<<"Ingrese la letra: ";
							cin>>letra;
							quesiga=true;
								for(int i=0; i<todo.size();i++){
									if(todo.at(i)==letra){
										quesiga=false;
										cout<<"¡Ya ingreso esta letra!"<<endl;
										break;
									}
								}
						if(quesiga){
							todo.push_back(letra);
						}
				}//end while
		bool dio=false;		
			for(int i=0; i<contador+1; i++){
				if(palabra[i]==letra){
					aciertos.push_back(letra);
					dio=true;
					break;
				}	
			}
			cout<<"Progreso: "<<endl;
			for(int i=0;i<aciertos.size();i++){
				for(int j=0; j<contador;j++){
					if(aciertos.at(i)==palabra[j]){
						progreso[j]=palabra[j];
					}
				}
			}	
		cout<<progreso;			
		cout<<endl;
		if(dio==false){
			errores.push_back(letra);
		}
		cout<<"Errores: ";
		for(int i=0; i<errores.size();i++){
			cout<<errores.at(i)<<" , ";
		}
		cout<<endl;
		for(int i=0;i<contador;i++){
				if(progreso[i]==palabra[i]){
					ganperd=true;
				}else{
					ganperd=false;
					break;
				}
		}
			if(dio==false){
				if(lives[5]=='X'){
						ganperd=false;
						break;
				}
			lives[cont]='X';
			cont++;
			continue;
		}
		if(ganperd){
			break;
		}			
				}	 
	if(ganperd){
		cout<<"¡Felicidades! Usted ha Ganado"<<endl;
		cout<<"La palabra era: "<<palabra<<endl;
	}else{
		cout<<"GAME OVER"<<endl;
		cout<<"La palabra era: "<<palabra<<endl;
		cout<<"Letras Acertadas: ";
			for(int i=0;i<aciertos.size();i++){
				cout<<aciertos.at(i)<<" , ";
			}
		cout<<endl;
			
	}
	cout<<"¿Desa volver a jugar?[S/N]"<<endl;
	cin>>resp;		
	delete[] progreso;	
}  //fin while grande 
			                           
	return 0;
}


const char* getWord(){
	
	/*
	char* line;
	vector<char*> palabras;
	ifstream file("verbos-espanol.txt");
	if(file.is_open()){
		while(file.good()){
			file.getline(line,20);
			palabras.push_back(line);	
				if(palabras.size()==45){
					break;
				}
		}	
		file.close();
	}*/
	
	const char* palabras[70]={"enrayar","enrazar","enreciar","enredar","enrehojar","enrejalar","misturar","mitificar",
		"mitigar","mitinear","mitrar","mixtificar","mixturar","mocar","mocear","mochar","mochilear",
		"mocionar","modelar","modelizar","moderar","modernizar","modificar","modorrar","modular",
		"mofar","moflearse","mohatrar","mohecer","mojar","mojonar","molar","enrejar","enresmar","enriar","ababillarse","abachar","abacorar","abejonear","abejorrear",
"abeldar","abellacar","abemolar","aberrar","abicharse",
"abigarrar","abinar","abisagrar","abundar","abuñolar",
"abuñuelar","descogotar","descojonarse","descolar","descolchar",
"descolgar","descollar","descolmar","descolmillar","descolocar"
,"descolonizar","descolorar","descolorir","descombrar",
"descomer","descompadrar","descompaginar","descompasarse",
"descompensar"};
	const char* retorno;
	int x=rand() % 70; 
	retorno=palabras[x];
	return retorno;
}
