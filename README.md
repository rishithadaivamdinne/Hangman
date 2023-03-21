# Hangman
Hangman game using C
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
int main()
{

srand(time(NULL));

char words[][14]={"abruptly","randkluft","jazz",
                "ytterbium","axiom","absurd","sly"};
int guessindex=rand()%7;
int lives=5;
int correctguesses=0;
int old=0;
int length=strlen(words[guessindex]);
int letterguess[14]={0,0,0,0,0,0,0,0,0,0,0,0,0,0};
int quit=0;
char guess[14];char x;int i;

while(correctguesses<length)
{  printf("\n");
    for(i=0;i<length;i++)
    {
        if(letterguess[i]==0)printf("_ ");
        else printf("%c ",words[guessindex][i]);
    }
    printf("\nCorrect guesses so far=%d",correctguesses);
    printf("\nEnter a character ");
    fgets(guess,10,stdin);
    if(strncmp(guess,"quit",4)==0)
    {
        quit=1;
        break;
    }
    x=guess[0];old=correctguesses;

    for(i=0;i<length;i++)
    {
        if(letterguess[i]==1)
            continue;
        if(x==words[guessindex][i])
        {
            letterguess[i]=1;
            correctguesses++;
        }
    }
    if(old==correctguesses)
    {
        printf("\nSorry,wrong guess");
        lives--;
        printf("\nlives left=%d",lives);
        if(lives==0)
        {
            break;
        }

    }
    else printf("\nCorrect guess");int o;
    if(lives==5)
    {
        printf("\n        _____");
        for(o=0;o<9;o++)
        printf("\n        |");
        printf("\n________|________");
    }
    else if(lives==4)
    {


        printf("\n         _____");
        for(o=1;o<10;o++)
        {

        printf("\n        |");
        if(o<3)printf("     |");
                      }
        printf("\n________|________");
    }
    else if(lives==3)
    {
        printf("\n         _____");
        for(o=1;o<10;o++)
        {

        printf("\n        |");
        if(o<2)printf("     |");
        else if(o==2)
            printf("    _|_");
        else if(o==3)
            printf("   |   |");
        else if(o==4)
            printf("   |_ _|");
                      }
        printf("\n________|________");
    }
    else if(lives==2)
    {

        printf("\n         _____");
        for(o=1;o<10;o++)
        {

        printf("\n        |");
        if(o<2)printf("     |");
        else if(o==2)
            printf("    _|_");
        else if(o==3)
            printf("   |   |");
        else if(o==4)
            printf("   |_ _|");
            else if(o>4 && o<9)
                printf("     |");
                      }
        printf("\n________|________");
    }
    else if(lives==1)
    {

        printf("\n         _____");
        for(o=1;o<10;o++)
        {

        printf("\n        |");
        if(o<2)printf("     |");
        else if(o==2)
            printf("    _|_");
        else if(o==3)
            printf("   |   |");
        else if(o==4)
            printf("   |_ _|");
            else if(o==6)
                printf("    /|/ ");
            else if(o==5 || o==7 || o==8)
                printf("     |");

                      }
        printf("\n________|________");
    }

}int o;
if(quit==1)
    printf("\nThe user has quit early\n");
  else if(lives==0)
        {

        printf("\n         _____");
        for(o=1;o<10;o++)
        {

        printf("\n        |");
        if(o<2)printf("     |");
        else if(o==2)
            printf("    _|_");
        else if(o==3)
            printf("   |   |");
        else if(o==4)
            printf("   |_ _|");
            else if(o==6 || o==8)
                printf("    /|/ ");
            else if(o==5 || o==7)
                printf("     |");

                      }
        printf("\n________|________");


            printf("\nSorry,out of lives\nthe word = %s",words[guessindex]);}
    else printf("\nYOU WIN!!!\n word=%s",words[guessindex]);
    getch();
return 0;
}


