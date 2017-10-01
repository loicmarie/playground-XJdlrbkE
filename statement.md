# Welcome!

This C++ template lets you get started quickly with a simple one-page playground.

```C++ runnable
#include <iostream>

#define WIDTH 8
#define HEIGHT 8

using namespace std;

void displayBitboard(uint64_t position) {
	int i,j;
	uint64_t currPosition = position;
    for(i=0; i < HEIGHT; i++) {
        // printf("%lu\n", position);
        // currPosition = position >> i;
        for ( j = 0; j < WIDTH; j++) {
          if (currPosition & 0x01) {
        		   printf("1");
          } else {
        		   printf("0");
          }
          currPosition = currPosition >> 1;
        }
    }
    printf("\n");
}

void display(uint64_t board, uint64_t position) { // TODO: afficher le jeu a l'endroit
    char symb;
	int i,j;
	uint64_t boardTmp = board,
	         positionTmp = position;
	printf("   |");
	for (j = 0; j < WIDTH; j++)
		printf(" %d |", j);
	printf("\n");
	for (j=0; j<WIDTH+1; j++)
	    printf("----");
	printf("\n");
    for(i=0; i < HEIGHT; i++) {
        // boardTmp = board >> i;
        // positionTmp = position >> i;
        printf(" %d |", i);
        for ( j = 0; j < WIDTH; j++) {
          if (positionTmp & 0x01) {
        		   symb = 'X';
          } else {
        		   symb = '.';
          }
          printf(" %c |", symb);
          boardTmp = boardTmp >> 1;
          positionTmp = positionTmp >> 1;
        }
        printf("\n");
    	for (j=0; j<WIDTH+1; j++)
    	    printf("----");
    	printf("\n");
    }
}

uint64_t moveRight(uint64_t position) {
    return position >> 5;
}

int main()
{
    uint64_t position = 39685902827520;
    displayBitboard(position);
    display(0, position);
    position = moveRight(position);
    displayBitboard(position);
    printf("\n");
    display(0, position);
    // cout << test << endl;
    return 0;
}
```

# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced C++ template](https://tech.io/select-repo/598)
