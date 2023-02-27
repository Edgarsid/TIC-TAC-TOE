# TIC-TAC-TOE
C++ TIC TAC TOE


#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;



char X = 'X';   
char O = 'O';   
char lauk[10] = {'o','1','2','3','4','5','6','7','8','9'};  
int uzv =0;  

void laukums()   
{
   	cout<<"        |     |     "<< endl;
    cout<<"     "<<lauk[1]<<"  |  "<<lauk[2]<<"  |  "<<lauk[3]<<endl;
    cout<<"   _____|_____|_____"<< endl;
    cout<<"        |     |     "<< endl;
    cout<<"     "<<lauk[4]<<"  |  "<<lauk[5]<<"  |  "<<lauk[6]<<endl;
    cout<<"   _____|_____|_____"<< endl;
    cout<<"        |     |     "<< endl;
    cout<<"     "<<lauk[7]<<"  |  "<<lauk[8]<<"  |  "<<lauk[9]<<endl;
    cout<<"        |     |     "<<endl << endl;
}

void lauk_logikai(int *a, int *b, int N, int M)   
{
    for(int i=0; i<N*M+1; i++)
    {
    	*(a+i) = 0;
        *(b+i) = 0;
	}
}

void logika(int *a, int *b, int N, int M) 
{
	for(int i=0; i<N*M; i = i+M)  
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M; j++)
    	{
    		*(b+i) += *(a+j+i);		
		}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	
	for(int i=0; i<N; ++i)  
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M*N; j = j+M)
    	{
    		*(b+i) += *(a+j+i);			    		
		}
        cout << endl;
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	
	int j = 0; 
	*(b+j) = 0; 
	for(int i=0, j = 0; i<N*M; i = i+M+1)  
    	{
    		*(b+j) +=*(a+i);
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
		}
	
	*(b+j) = 0;  
    for(int i=M-1; i<N*M-2; i = i+M-1)
    	{
    		*(b+j) +=*(a+i);
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
		}
}

void logika_CPU(int *a, int *b, int N, int M)  
{
	int r_k_d = 0; 
	int check = 0; 


    for(int i=0; i<N*M; i = i+M) 
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M; j++)
    	{
    		*(b+i) += *(a+i+j);
			r_k_d = i;			
				if(*(b+i) == -2 && check == 0)
					for(int i=r_k_d; i<r_k_d+N; i++)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
		}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	for(int i=0; i<N; ++i) 
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M*N; j = j+M)
    	{
    		*(b+i) += *(a+j+i);
    		r_k_d = i;
				if(*(b+i) == -2 && check == 0)
					for(int i=r_k_d; i<N*M; i = i + N)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
		}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	int j = 0;
	*(b+j) = 0;  
	for(int i=0, j = 0; i<N*M; i = i+M+1)  
   			*(b+j) +=*(a+i);
				if(*(b+j) == -2 && check == 0)
					for(int i=0; i<N*M; i = i + M +1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;	
						}
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
	*(b+j) = 0;
    for(int i=M-1; i<N*M-2; i = i+M-1) 
    		*(b+j) +=*(a+i);
				if(*(b+j) == -2 && check == 0)
					for(int i=M-1; i<N*M; i = i + M -1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}	
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;


	for(int i=0; i<N*M; i = i+M)  
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M; j++)
    	{
    		*(b+i) += *(a+i+j);
			r_k_d = i;			
    		 	if(*(b+i) == 2 && check == 0)
					for(int i=r_k_d; i<r_k_d+N; i++)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
		}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	for(int i=0; i<N; ++i)  
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M*N; j = j+M)
    	{
    		*(b+i) += *(a+j+i);
    		r_k_d = i;
    		    if(*(b+i) == 2 && check == 0)
					for(int i=r_k_d; i<N*M; i = i + N)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
		}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	
	*(b+j) = 0;
	for(int i=0, j = 0; i<N*M; i = i+M+1)  
   			*(b+j) +=*(a+i);
    		    if(*(b+j) == 2 && check == 0)
					for(int i=0; i<N*M; i = i + M +1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
		
		
	*(b+j) = 0;
    for(int i=M-1; i<N*M-2; i = i+M-1)  
    		*(b+j) +=*(a+i);
    		    if(*(b+j) == 2 && check == 0)
					for(int i=M-1; i<N*M; i = i + M -1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;

			
	for(int i=0; i<N*M; i = i+M) 
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M; j++)
    		*(b+i) += *(a+i+j);
			r_k_d = i;			
				if(*(b+i) == -1 && check == 0)
					for(int i=r_k_d; i<r_k_d+N; i++)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	for(int i=0; i<N; ++i)
    {
    	*(b+i) = 0;
    	for(int j = 0; j<M*N; j = j+M)
    		*(b+i) += *(a+j+i);
    		r_k_d = i;
				if(*(b+i) == -1 && check == 0)
					for(int i=r_k_d; i<N*M; i = i + N)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}
            if(*(b+i) == 3)
				uzv = 1;
			else if(*(b+i) == -3)
				uzv = 2;
	}
	*(b+j) = 0;
	for(int i=0, j = 0; i<N*M; i = i+M+1)  
   			*(b+j) +=*(a+i);
				if(*(b+j) == -1 && check == 0)
					for(int i=0; i<N*M; i = i + M +1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;	
						}
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
	*(b+j) = 0;
    for(int i=M-1; i<N*M-2; i = i+M-1)
    		*(b+j) +=*(a+i);
				if(*(b+j) == -1 && check == 0)
					for(int i=M-1; i<N*M; i = i + M -1)
						if(*(a+i) == 0 && check == 0)
						{
							*(a+i) =-1;
							lauk[i+1] = O;
							check = 1;
						}	
    		if(*(b+j) == 3)
					uzv = 1;
			else if(*(b+j) == -3)
					uzv = 2;
					
	if(check == 0) 
	{
		int cits = rand()%8 + 1;
		if(lauk[cits] == X || lauk[cits] == O)
			{
			do
			{
				cits = rand()%8 + 1;
			}
			while(lauk[cits] == X || lauk[cits] == O); 
			}
		*(a+cits) = -1;
		lauk[cits] = O;
	}
}

void spele_Player(int *a, int *b, int N, int M) 
{
	int l = 0, SP_1, SP_2;
	do
	{
		cout << "Player 1 enter field: " << endl;
		cin >> SP_1;
		if(SP_1<1 || SP_1>9 || lauk[SP_1] == X || lauk[SP_1] == O) 
		{
			do
			{
				cout << "Enter not occupied field or from 1 - 9 " << endl;
				cin >> SP_1;
			}
			while(SP_1<1 || SP_1>9 || lauk[SP_1] == X || lauk[SP_1] == O); 
		}
    	*(a+SP_1-1) = 1;
    	lauk[SP_1] = X;
    	laukums();
		logika(a,b,N,M);
		l++;
		if(uzv ==1) 
			{
				cout << "Player 1 WON" << endl;
				break;
			}
		if(l ==9) 
			{
				cout << "Draw" << endl;
				break;
			}

		cout << "Player 2 enter field: " << endl;
		cin >> SP_2;
		if(SP_2<1 || SP_2>9 || lauk[SP_2] == X || lauk[SP_2] == O) 
		{
			do
			{
				cout << "Enter from 1 to 9 " << endl;
				cin >> SP_2;
			}
			while(SP_2<1 || SP_2>9 || lauk[SP_2] == X || lauk[SP_2] == O); 
			}

		*(a+SP_2-1) = -1;
		lauk[SP_2] = O;
		laukums();
		logika(a,b,N,M);
		if(uzv ==2)   
			{
				cout << "Player 1 WON" << endl;
				break;
			}
		l++;
	}
	while(l != 9);
}

void spele_CPU(int *a, int *b, int N, int M) 
{
	int l = 0, SP_1, CPU;
	do
		{
		cout << "Enter field: " << endl;
		cin >> SP_1;
		if(SP_1<1 || SP_1>9 || lauk[SP_1] == X || lauk[SP_1] == O) 
		{
			do
			{
				cout << "Enter not occupied field or from 1 - 9 " << endl;
				cin >> SP_1;
			}
			while(SP_1<1 || SP_1>9 || lauk[SP_1] == X || lauk[SP_1] == O); 
		}
    	*(a+SP_1-1) = 1;
    	lauk[SP_1] = X;
		logika(a,b,N,M);
		if(uzv ==1)
		{
			cout << "Player WON" << endl; 
			break;
		}

		l++;
		if(l ==9) 
		{
			cout << "Draw" << endl;
			break;
		}
		if(l == 1)  
		{
			CPU = 5;  
			if(lauk[CPU] == X)
			CPU = 1;  
			*(a+CPU-1) = -1;
		}
		else if(l == 3 && lauk[5] == X && lauk[9] == X) 
		{
			CPU = 3;
			*(a+CPU-1) = -1;
		}
		else  
			logika_CPU(a,b,N,M);
    	lauk[CPU] = O;
	
		laukums();
		if(uzv ==2) 
		{
			cout << "CPU WON" << endl;
			break;
		}
		l++;
		}
	while(l != 9 || uzv != 1 || uzv!=2);
}

int main()
{
	cout<<"      TIC TAC TOE  "<< endl << endl;
    time_t t;
    srand((unsigned) time(&t));
    const int N=3;
    const int M=3;
    int a[N][M];
    int b[N][M];
    int c[N][M];
    int izvele;
    int velreiz;  

    do
    {
    	cout <<"Game: Player vs Player   -   press 1"<< endl;
    	cout <<"Game: Player vs CPU      -   press 2"<< endl;
    	cin >> izvele;
    		if(izvele != 1 && izvele !=2)   // izveleties, kadu speli spelet
    		{
    			do
    			{
    				cout << "Enter 1 or 2" << endl;
    				cin >> izvele;
				}
				while(izvele != 1 && izvele !=2);
			}
    
    		if(izvele == 1)
    		{
   				cout<<"    Player No. 1:  X  "<<endl;
				cout<<"    Player No. 2:  O  "<<endl << endl;
	    		laukums();
    			lauk_logikai(*a,*b,N,M);
    			spele_Player(*a,*b,N,M);
			}
			if(izvele == 2)
    		{
   				cout<<"    Player No. 1:  X  "<<endl;
				cout<<"             CPU:  O  "<<endl << endl;
	    		laukums();
    			lauk_logikai(*a,*b,N,M);
    			spele_CPU(*a,*b,N,M);
			}
			
    	cout<<"    Play again?  "<<endl;
    	cout<<"    1: YES  "<<endl << "    2: NO  "<<endl;
    	cin >> velreiz;
    		if(velreiz < 1 || velreiz > 2)  
    		{
    			do
				{
				cout << "Enter 1 or 2" << endl;
				cin >> velreiz;
				}
				while(velreiz != 1 && velreiz != 2); 
			}
		lauk[1] = '1'; lauk[2] = '2'; lauk[3] = '3'; lauk[4] = '4'; lauk[5] = '5'; lauk[6] = '6'; lauk[7] = '7'; lauk[8] = '8'; lauk[9] = '9'; // laukuma atjaunoshana
		uzv =0;
	}
	while(velreiz == 1); 
	   
    system("pause");
    return 0;
}
