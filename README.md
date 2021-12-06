#include <stdio.h>
#include <string.h>
struct data
{
    char name[20];
    int age;
    char country[20];
    int category, odi, t_20, wicket,runs;
    float av_score;
} d[10];

void batsman_country(int a)
{
    char nation[20];
    printf("Enter the country name :\n");
    scanf("%s", nation);
    printf("The batsman from %s country are as follows :\n ", nation);
    int count = 0;
    for (int i = 0; i < a; i++)
    {

        if (strcmp(d[i].country, nation) == 0)
        {
            if (d[i].category == 1||d[i].category==3)
            {
                printf(" \n %d) %s \n", count + 1, d[i].name);
                count++;
            }
        }
    }
}
void average(int a)
{
    struct data swap;  
    int count = 0;
    printf("\n**** Sorted Average Score ***\n");
   
    printf("Player name   Average Score \n");
    for (int i = 0; i < a-1; i++)
    {
        for (int j = 0; j < a-1-i; j++)
        {
            if(d[j].av_score<d[j+1].av_score)
            {
                swap=d[j];
                d[j]=d[j+1];
                d[j+1]=swap;
            }
        }
    }
    for (int i = 0; i < a; i++)
    {
        printf("%s \t %f\n",d[i].name,d[i].av_score);
    }
    
}
void highest(int a)
{
    printf("\n***** Highest Average Score ******\n");
    float max = d[0].av_score;
    int j = 0;
    for (int i = 0; i < a; i++)
    {
        if (d[i].av_score > max)
        {
            max = d[i].av_score;
            j = i;
        }
    }
    printf("The highest Average score is %.2f of player %s \n", max, d[j].name);
}
void bowler_country(int a)
{
    char nation[20];
    int count;
    printf("Enter the country of bowler\n");
    scanf("%s", nation);
    for (int i = 0; i < a; i++)
    {
        if (strcmp(d[i].country, nation) == 0)
        {
            if (d[i].category == 2||d[i].category==3)
            {
                printf("%d) %s\n", count + 1, d[i].name);
                count++;
            }
        }
    }
}
void max_wicket(int a)
{
    printf("\n***** Highest Wicket Taker ******\n");
    int max = d[0].wicket;
    int j = 0;
    for (int i = 0; i < a; i++)
    {
        if (d[i].wicket > max)
        {
            max = d[i].wicket;
            j = i;
        }
    }
    printf("The highest Wicket taker is %d of player %s \n", max, d[j].name);
}
void display(int a)
{
    printf("\n*****Display the data***** \n");
    printf("Name \t country \t Age  ODI played  T-20 Played  Caterogy \n ");
    for (int i = 0; i < a; i++)
    {
        
        printf("%s\t%s\t %d \t %d \t %d \t %d \n", d[i].name, d[i].country, d[i].age, d[i].odi, d[i].t_20, d[i].category);
    }
}
int main()
{
    int num, option;
    printf("Enter the total no. of players \n");
    scanf("%d", &num);
    printf("Please Fill the data of players \n");
    for (int i = 0; i < num; i++)
    {
        printf("Enter the Name of Player no %d:\n", i + 1);
        scanf("%s", d[i].name);
        printf("Enter the age of Player :\n");
        scanf("%d", &d[i].age);
        printf("Enter the country of Player :\n");
        scanf("%s", d[i].country);
        printf("Enter the category of Player (1.Batsman 2.Bowler 3.All Rounder:\n");
        scanf("%d", &d[i].category);
        printf("Enter the ODI matches played by this player :\n");
        scanf("%d", &d[i].odi);
        printf("Enter the T-20 matches played by this player :\n");
        scanf("%d", &d[i].t_20);
        printf("Enter the Average Score of player :\n");
        scanf("%f", &d[i].av_score);
        printf("Enter count of wicket taken by the of player :\n");
        scanf("%d", &d[i].wicket);
        printf("Enter the runs of player\n");
        scanf("%d",&d[i].runs);
    }
    while (1)
    {
    printf("\nEnter the correct choice.\n 1. Number of batsman of a particular country.\n 2. Average batting score.\n 3. Highest Average score. \n 4. Number of bowlers of a particular country. \n 5. MAx. no of wicket taken by bowler. \n 6. Display board. \n 7. Exit\n");
    scanf("%d", &option);

        switch (option)
        {
        case 1:
            batsman_country(num);
            break;
        case 2:
            average(num);
            break;
        case 3:
            highest(num);
            break;
        case 4:
            bowler_country(num);
            break;
        case 5:
            max_wicket(num);
            break;
        case 6:
            display(num);
            break;
        case 7:
            goto end;
        default:
            printf("Enter valid option\n");
            break;
        }
    }
end:
return 0;
}
