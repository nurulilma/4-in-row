#include <iostream>
#include <cstdlib>
#include <ctime>
#include <unistd.h>
using namespace std;

// percobaan dari yuri 
char map[8][9] = {

	' ','|',' ','|',' ','|',' ','|',' ',

	'-','|','-','|','-','|','-','|','-',

	' ','|',' ','|',' ','|',' ','|',' ',

	'-','|','-','|','-','|','-','|','-',

	' ','|',' ','|',' ','|',' ','|',' ',

	'-','|','-','|','-','|','-','|','-',

	' ','|',' ','|',' ','|',' ','|',' ',
	
	'-','|','-','|','-','|','-','|','-',			
};

bool win=false;
bool playerturn=true;
int baris;

//=============================================================================

//Fungsi ini mecetak seluruh isi dari array map
void print(){
	system("CLS");
	for(int x=0; x<8; x++){
		for(int y=0; y<9; y++){
			cout << map[x][y];
		}
		cout << endl;
	}
	
}

//Fungsi ini menentukan bidak player dengan menggunakan boolean "playerturn"
char player(){
	if(playerturn){
		return 'B';
	}
	else{
		return 'M';
	}
}

//Fungsi ini mengecek apa kotak dibawah di baris yang di pilih, kosong. jika iya, maka akan ganti dengan bidak player
int insert(int barisKeBerapa){
	int check = -2;
	//cout << map[check][barisKeBerapa];
	while(map[check+2][barisKeBerapa]==' '){
		map[check+2][barisKeBerapa] = player();
		map[check][barisKeBerapa] = ' ';
		check = check + 2;
		print();
	}
}


int main(){

	do{
		//system("CLS");
		print();
		cout << endl << endl << "Sekarang giliran: " << player() << endl << "Ingin di baris ke berapa? ";
		cin >> baris;
		switch(baris){
			case 1:
				insert(0);
				break;
			case 2:
				insert(2);
				break;
			case 3:
				insert(4);
				break;
			case 4:
				insert(6);
				break;
			case 5:
				insert(8);
				break;
			default:
				cout << endl << "ERROR, bukan angka baris";
				sleep(1);
				break;
		}
		playerturn = !playerturn;
		
		
		
		
	}while(win == false);
	
}
