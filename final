#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <time.h>
#include <windows.h>

void Clear_Console();
void Maze_Generate(int size,char maze[size][size], char travelled[size][size]);
void Prims(int size,char maze[size][size], char travelled[size][size], int x_coordinate, int y_coordinate);
void Update_Loading(int loading, int totalCells);
void displayMaze(int size, char maze[size][size],int x_coordinate,int y_coordinate);
void space(int number);
void waiting(char array[]);
void displayMenu();

int main() {

    int size;

    displayMenu();

    printf("\033[1mEnter size of the maze: ");
    scanf("%d",&size);

    if(size<=0){
        Clear_Console();
        printf("!! Please enter a Valid Size !!\n");
        printf("Enter size of the maze: ");
        scanf("%d",&size);
    }

    if(size%2==0){
        size--;
    }
    
    printf("\n");
    
    char maze[size][size];
    char travelled[size][size];

    for(int i=0;i<size;i++){
        for(int j=0;j<size;j++){
            if(i==0 || i==size-1 || j==0 || j==size-1){
                maze[i][j]='*';
            }
            else if(j%2==1 && i%2==1){
                maze[i][j]=' ';
            }
            else{
                maze[i][j]='*';
            }
            if(i==1 && j==1){
                maze[i][j]='S';
            }
            if(i==size-2 && j==size-2){
                maze[i][j]='E';
            }
        }
    }

    for(int i=0;i<size;i++){
        for(int j=0;j<size;j++){
            if(i==0 || i==size-1 || j==0 || j==size-1){
                travelled[i][j]='*';
            }
            else if(i%2==1 || i%2==0 && j%2==1){
                travelled[i][j]='t';
            }
            else{
                travelled[i][j]='*';
            }
            if(i==1 && j==1){
                travelled[i][j]='S';
            }
        }
    }

    Maze_Generate(size,maze,travelled);

    char input;
    
    printf("\n\n\033[1mDo you want to Solve this maze?(Y/N) ");
    scanf(" %c",&input);
    getchar();

    if(input=='y' || input=='Y'){

        int x_coordinate = 1;
        int y_coordinate = 1;

        maze[x_coordinate][y_coordinate] = 'S';

        Prims(size, maze, travelled, x_coordinate, y_coordinate);

        maze[size - 2][size - 2] = 'E';

        displayMaze(size, maze,x_coordinate, y_coordinate); // Display initial maze

        // Maze solving loop
        char move;
        while (maze[x_coordinate][y_coordinate] != 'E') {
            printf("\n\033[1mEnter move (W/A/S/D to move, Q to quit): ");
            scanf(" %c", &move);

            switch (move) {
                case 'W':
                case 'w':
                    if (maze[x_coordinate - 1][y_coordinate] != '*') {
                        maze[x_coordinate][y_coordinate] = ' ';
                        x_coordinate--;
                    }
                    break;
                case 'A':
                case 'a':
                    if (maze[x_coordinate][y_coordinate - 1] != '*') {
                        maze[x_coordinate][y_coordinate] = ' ';
                        y_coordinate--;
                    }
                    break;
                case 'S':
                case 's':
                    if (maze[x_coordinate + 1][y_coordinate] != '*') {
                        maze[x_coordinate][y_coordinate] = ' ';
                        x_coordinate++;
                    }
                    break;
                case 'D':
                case 'd':
                    if (maze[x_coordinate][y_coordinate + 1] != '*') {
                        maze[x_coordinate][y_coordinate] = ' ';
                        y_coordinate++;
                    }
                    break;
                case 'Q':
                case 'q':
                    
                    waiting("Quitting");
                    printf("\033[1K");
                    printf("\r\nGame Quitted Successfully !\n");
                    return 0;
                default:
                    printf("Invalid move. Please enter W/A/S/D to move, or Q to quit.\n");
                    break;
            }

            displayMaze(size, maze,x_coordinate, y_coordinate); // Display updated maze
        }
        printf("\n\033[1mCongratulations! You reached the exit!\n");
    }
    else if(input=='n' || input=='N'){
        return 0;
    }
}


void Maze_Generate(int size,char maze[size][size], char travelled[size][size]){

    srand(time(NULL));

    int hold,loading=0;

    if(size<10){
        hold=5;
    }
    else if(size>10 && size<30){
        hold=3;
    }
    else if(size>30 && size<50){
        hold=2;
    }
    else{
        hold=1;
    }
    
    int x_coordinate = 1;
    int y_coordinate = 1;
    
    maze[x_coordinate][y_coordinate] = 'S';
    
    Prims(size,maze, travelled, x_coordinate, y_coordinate);
    
    maze[size-2][size-2] = 'E';

    waiting(" Please wait while your maze is generating");
    printf("\n\n");
    
    for(int n = 0; n<size; n++)
    {
        for(int k = 0; k<size; k++)
        {   
            if(n==0 && k==0){
                printf(" ");
            }
            printf("%c ", maze[n][k]);
            loading++;
            Update_Loading(loading, size*size);
            Sleep(hold);
        }

        printf("%c ", '\n');
    }

    printf("\033[3;K");
    printf("\nMaze generated successfully!\n\n");
    waiting("\rWait.....We got something interesting for you");
    Sleep(1000);
    displayMaze(size,maze,x_coordinate,y_coordinate);

}

void waiting(char array[]) {
    int i=0,j=1;
    while(j!=0){
        if(i==0){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s..",array);
            i=1;
        }
        Sleep(400);
        if(i==1){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s....",array);
            i=2;
        }
        Sleep(400);
        if(i==2){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s......",array);
            i=3;
        }
        Sleep(400);
        if(i==3){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s.........",array);
            i++;
        }
        Sleep(400);
        if(i==4){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s...........",array);
            i++;
        }
        Sleep(400);
        if(i==5){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s..............",array);
            i++;
        }
        Sleep(400);
        if(i==6){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s..............",array);
            i++;
        }
        Sleep(400);
        if(i==7){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s...........",array);
            i++;
        }
        Sleep(400);
        if(i==8){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s.........",array);
            i++;
        }
        Sleep(400);
        if(i==9){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s......",array);
            i++;
        }
        Sleep(400);
        if(i==10){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s....",array);
            i++;
        }
        Sleep(400);
        if(i==11){
            // Clear_Console();
            printf("\033[1K");
            printf("\r%s..",array);
            i=0;
        }
        Sleep(400);
        j--;
    }
}

void Update_Loading(int loading, int totalCells){

    printf("\033[s");
    printf("\033[3;45H");
    printf("\rMaze Completion (%.2f %%)                        \n\n", (loading / (float)totalCells) * 100);
    // if((loading / (float)totalCells) * 100==100.00){
    //     printf("\033[3;H");
    //     printf("Maze generated successfully!                                                ");
    // }
    printf("\033[u");

    fflush(stdout);

}

void displayMaze(int size, char maze[size][size], int x_coordinate, int y_coordinate) {
    Clear_Console();
    printf("\n\n\n");
    if(maze[x_coordinate][y_coordinate]=='E'){
        for (int n = 0; n < size; n++) {
            space(50);
            for (int k = 0; k < size; k++) {
                if(n==0 && k==0){
                    
                    printf(" ");
                }
                if (n == x_coordinate && k == y_coordinate) {
                    
                    printf("\x1b[32m");
                    printf("X ");
                    printf("\x1b[0m");

                } 
                else {
                    
                    if(maze[n][k]=='E'){
                        
                        printf("\x1b[32m");
                        printf("%c ", maze[n][k]);
                        printf("\x1b[0m");
                    }
                    else{
                        if(maze[n][k]=='*'){
                            if(n==size-2 && k==size-1){
                                printf("\033[1;32m%c \033[0m",254);
                            }
                            else{
                                printf("%c ",254);
                            }
                        }
                        else{
                            
                            printf("%c ", maze[n][k]);
                        }
                    }
                }
            }
            
            printf("%c ", '\n');
        }
        return;
    }
    for (int n = 0; n < size; n++) {
        space(50);
        for (int k = 0; k < size; k++) {
            if(n==0 && k==0){
                printf(" ");
            }
            if (n == x_coordinate && k == y_coordinate) {
                
                printf("\x1b[31m");
                printf("X ");
                printf("\x1b[0m");

            } 
            else {

                if(maze[n][k]=='E'){
                    
                    printf("\x1b[32m");
                    printf("%c ", maze[n][k]);
                    printf("\x1b[0m");
                }
                else{

                    if(maze[n][k]=='*'){
                        if(n==size-2 && k==size-1 || n==1 && k==0){
                            if(n==1 && k==0){
                                printf("\033[33m%c \033[0m",254);
                            }
                            else{
                                printf("\033[32m%c \033[0m",254);
                            }
                        }
                        else{
                            printf("%c ",254);
                        }
                    }

                    else{
                       
                        printf("%c ", maze[n][k]);
                    }
                }                
            }
        }
        printf("%c ", '\n');
    }
}

void space(int number){
    for(int i=0;i<number;i++){
        printf("%c",32);
    }
}

void Clear_Console(){

    system("cls");

}

void Prims(int size,char maze[size][size], char travelled[size][size], int x_coordinate, int y_coordinate) {
    
    int randomnumber = rand()%4;

    while(travelled[x_coordinate-1][y_coordinate-1] == 't'  || travelled[x_coordinate][y_coordinate-1] == 't'  || travelled[x_coordinate+1][y_coordinate-1] == 't'  || travelled[x_coordinate-1][y_coordinate] == 't'  || travelled[x_coordinate][y_coordinate] == 't'  || travelled[x_coordinate+1][y_coordinate] == 't'  || travelled[x_coordinate-1][y_coordinate+1] == 't'  || travelled[x_coordinate][y_coordinate+1] == 't'  || travelled[x_coordinate+1][y_coordinate+1] == 't' ){
    
        randomnumber = rand()%4;
        
        if(randomnumber == 0){

            if((x_coordinate >1) && (travelled[x_coordinate-2][y_coordinate] == 't' )){
                
                x_coordinate--;
                maze[x_coordinate][y_coordinate] = ' ';
                travelled[x_coordinate][y_coordinate]= ' ';
                x_coordinate--;
                travelled[x_coordinate][y_coordinate]= ' ';
                Prims(size,maze,travelled, x_coordinate, y_coordinate);
                x_coordinate+=2;
            }

            else if(travelled[x_coordinate-2][y_coordinate] != 't' ){

                travelled[x_coordinate-1][y_coordinate] = '*';

            }
        }
        
        else if(randomnumber == 1) {

            if((x_coordinate <size-2) && (travelled[x_coordinate+2][y_coordinate] == 't' )) {

                x_coordinate++;
                maze[x_coordinate][y_coordinate] = ' ';
                travelled[x_coordinate][y_coordinate]= ' ';
                x_coordinate++;
                travelled[x_coordinate][y_coordinate]= ' ';
                Prims(size,maze,travelled, x_coordinate, y_coordinate);
                x_coordinate-=2;

            }
            
            else if(travelled[x_coordinate+2][y_coordinate] != 't' ){

                travelled[x_coordinate+1][y_coordinate] = '*';

            }
        }

        else if(randomnumber == 2) {

            if((y_coordinate >1) && (travelled[x_coordinate][y_coordinate-2] == 't' )) {

                y_coordinate--;
                maze[x_coordinate][y_coordinate] = ' ';
                travelled[x_coordinate][y_coordinate]= ' ';
                y_coordinate--;
                travelled[x_coordinate][y_coordinate]= ' ';
                Prims(size,maze,travelled, x_coordinate, y_coordinate);
                y_coordinate+=2;

            }

            else if(travelled[x_coordinate][y_coordinate-2] != 't' ) {

                travelled[x_coordinate][y_coordinate-1] = '*';

            }
        }

        else {

            if((y_coordinate <size-2) && (travelled[x_coordinate][y_coordinate+2] == 't' )) {

                y_coordinate++;
                maze[x_coordinate][y_coordinate] = ' ';
                travelled[x_coordinate][y_coordinate]= ' ';
                y_coordinate++;
                travelled[x_coordinate][y_coordinate]= ' ';
                Prims(size,maze,travelled, x_coordinate, y_coordinate);
                y_coordinate-=2;

            }

            else if(travelled[x_coordinate][y_coordinate+2] != 't' ) {

                travelled[x_coordinate][y_coordinate+1] = '*';

            }
        }
    }
}

void displayMenu(){

    Clear_Console();
printf("\t");
printf("\t");
printf("\t");
printf("\t");
printf("\t");
printf("\t");
printf("\t");
    printf("\t%c %c %c  MENU  %c %c %c\n",4, 4, 4, 4, 4, 4);

    printf("\n");
    printf("\n");
    printf("1) Play\n");
    printf("\n");
    printf("2) Instructions\n");
    printf("\n");
    printf("3) About\n");
    printf("\n");
    printf("\n");
printf("Choose from above to proceed!  ");
int a;
int b=1;
int c=1;
int d=1;
scanf("%d", &a);
    switch (a)
    {
    case 1:
    Clear_Console();
     break;

    case 2:
    Clear_Console();
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t%c %c %c  INSTRUCTIONS  %c %c %c\n",4, 4, 4, 4, 4, 4);

    printf("\n");
    printf("\n");
    printf("The player first needs to choose the Size of the maze which he/she would like to solve.\n");
    printf("In order to Solve the maze, the player has to find a way to Exit the Maze.\nIntially, the player is present at Starting position Represented by S.");
    printf("The end point of Maze is represented by E. The current position of the player is represented by X\n");
    printf("The player can use the following keys to navigate through the Maze.\n");
    printf("\tw - To move up\n");
    printf("\td - To move right\n");
    printf("\ta - To move left\n");
    printf("\ts - To move down\n");
    printf("\n");
    printf("\n");
    printf("Enter 0 to return to the menu ");
    scanf("%d", &b);
if(b==0){
    displayMenu();
}
        break;

    case 3:
    Clear_Console();
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t");
    printf("\t%c %c %c  ABOUT  %c %c %c\n",4, 4, 4, 4, 4, 4);

    printf("\n");
    printf("\n");
    printf("This is a random generator and solver which has been made by using the Prims Algorithm.\n");
    printf("\n");
    printf("\t");
    printf("\t");
    printf("\tOur Team\n");
    printf("\t1) Jenish Thakkar\n \t2) Rudra Thakar\n \t3) Sahilpreet Singh\n \t4) Ameen \n");
    printf("\n");
    printf("Enter 0 the return to menu ");
    scanf("%d", &c);
    if(c==0){
        displayMenu();
    }
        break;

    default:
    printf("Enter valid value!!");
    printf("Enter 0 the return to menu ");
    scanf("%d", &d);
    if(d==0){
        displayMenu();
    }
        break;
    }
}
