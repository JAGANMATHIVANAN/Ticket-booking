#include <stdio.h>
#include <string.h>
#define Area 5
#define Theatres 4
#define Movie 4
#define Timing 2
#define Rows 5
#define Cols 20

int placesname,theatresname,timing;
int seat[Rows][Cols];
int totalseats=0;

void nameofPlaces(),nameofTheatres(),nameofMovies(),seatdisplay(),bookedseat(),movietiming();
char AREA[Area][100] = {"","KARUR","ERODE","NAMAKKAL","SALEM"};
char THEATERS[Area][Theatres][100] = {{""},{"","ELANGO COMPLEX","KS THEATRE","JAI THEATRE"},{"","ANATH CINEMAS","MASS CINEMAS","FOOD THEATRE"},{"","PGP THEATRES","MKCE CINEMAS","THATHA CINEMAS"},{"","PG CINEMAS","UG CINEMAS","UGPG CINEMAS"}};
char MOVIES[Area][Theatres][Movie][100] =  {{""},{{""},{"","Joe-screen1-9.00am","Leo-screen2-1.00pm","Jawan-screen3-6.00pm"},{"","Salaar-screen1-8.00am","Joe-screen2-12.00pm","Leo-screen3-4.30pm"},{"","Jawan-screen1-10.0am","Salaar-screen2-1.30pm","Joe-screen3-7.30pm"}},{{""},{"","Joe-screen1-9.00am","Leo-screen2-12.00pm","Jawan-screen3-6.30pm"},{"","Salaar-screen1-10.00am","Joe-screen2-1.00pm","Leo-screen3-7.00pm"},{"","Jawan-screen1-10.00am","Salaar-screen2-1.00pm","Joe-screen3-6.30pm"}},{{""},{"","Joe-screen1-11.00am","Leo-screen2-3.00pm","Jawan-screen3-7.30pm"},{"","Salaar-screen1-9.30am","Joe-screen2-12.00pm","Leo-screen3-6.00pm"},{"","Jawan-screen1-9.00am","Salaar-screen2-1.00pm","Joe-screen3-5.30pm"}}};
char TIMING[Area][Theatres][Movie][Timing][100] =  {{""},{{""},{"","Joe-screen1-9.00am","Leo-screen2-1.00pm","Jawan-screen3-6.00pm"},{"","Salaar-screen1-8.00am","Joe-screen2-12.00pm","Leo-screen3-4.30pm"},{"","Jawan-screen1-10.0am","Salaar-screen2-1.30pm","Joe-screen3-7.30pm"}},{{""},{"","Joe-screen1-9.00am","Leo-screen2-12.00pm","Jawan-screen3-6.30pm"},{"","Salaar-screen1-10.00am","Joe-screen2-1.00pm","Leo-screen3-7.00pm"},{"","Jawan-screen1-10.00am","Salaar-screen2-1.00pm","Joe-screen3-6.30pm"}},{{""},{"","Joe-screen1-11.00am","Leo-screen2-3.00pm","Jawan-screen3-7.30pm"},{"","Salaar-screen1-9.30am","Joe-screen2-12.00pm","Leo-screen3-6.00pm"},{"","Jawan-screen1-9.00am","Salaar-screen2-1.00pm","Joe-screen3-5.30pm"}}};
int main ()
{
    printf("Movie Ticket Booking.\n");
    nameofPlaces();
    printf("\nselect the places : ");
    scanf("%d",&placesname);
    nameofTheatres(placesname);
    printf("\nselect the theatre : ");
    scanf("%d",&theatresname);
    nameofMovies(placesname,theatresname);
    printf("\nSelect the movie:");
    scanf("%d",&timing);
    movietiming(placesname,theatresname,timing);
    char name[50],gender[10];
    int age;
    printf("\nEnter the Name: ");
    scanf("%s",name);
    printf("\nEnter the Age: ");
    scanf("%d",&age);
    printf("\nEnter the Gender: ");
    scanf("%s",gender);
        for(int i=0;i<Rows;i++)
    {
     for(int j=0;j<Cols;j++){
      seat[i][j]=0;
     }
    }
    seatdisplay();
    bookedseat();
    seatdisplay();
    printf("\n\nEnjoy the movie have a nice day");
     }
void nameofPlaces()
{
    printf("Places : \n");
    for(int i=1;i<Area;i++)
    {
        printf("%d.%s\n",(i),AREA[i]);

        
    }
}
void nameofTheatres(int placesname)
{
  printf("theatres:\n");
  for(int i=1;i<Theatres;i++){
    printf("%d.%s\n",(i),THEATERS[placesname][i]);
  }
  
}
void nameofMovies(int placesname,int theatresname){
  printf("movies:\n");
  for(int i=1;i<Movie;i++){
    printf("%d.%s\n",(i),MOVIES[placesname][theatresname][i]);
  }
  
}
void movietiming(int placesname,int theatresname,int timing){
 for(int i=1;i<Timing;i++){
  printf("\nSelected Movie: %s\n", MOVIES[placesname][theatresname][timing]);
 }
}
void seatdisplay(){
 printf("\nseat arrangement:\n");
 for(int i=0;i<Rows;i++){
  for(int j=0;j<Cols;j++){
   printf("%c",seat[i][j]==0?'O':'X');
  }
  printf("\n");
 }
}
void bookedseat()
{    int numSeats;
    printf("Enter the number of seat: ");
    scanf("%d", &numSeats);
    for (int k = 0; k < numSeats; k++)
    {
        int row, colm;
        printf("Enter the row and colm to book seat %d: ", k + 1);
        scanf("%d", &row);
        scanf("%d", &colm);
        if (seat[row - 1][colm - 1] == 0){
            seat[row - 1][colm - 1] = 1;
            printf("seat %d booked \n", k + 1);
            totalseats++;
        }
        else{
            printf("Already seat booked\n");
            k--; 
        }
    }
    printf("Total No of booked seat: %d\n", totalseats);
}
