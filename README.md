# FCFS-problem-2
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
    int p[4],a[4],b[4],temp,c[4];
    for(int i=0;i<4;i++)
    {
        scanf("%d%d%d",&p[i],&a[i],&b[i]);
        c[i]=p[i];
    }
    for(int i=0;i<4-1;i++)
    {
        for(int j=0;j<4-i-1;j++)
        {
            if(a[j]>a[j+1])
            {
                temp=a[j];
                a[j]=a[j+1];
                a[j+1]=temp;
                
                temp=p[j];
                p[j]=p[j+1];
                p[j+1]=temp;
                
                temp=b[j];
                b[j]=b[j+1];
                b[j+1]=temp;
            }
        }
    }
    int k=0,sum=0;
    for(int i=0;i<4;i++)
    {
        if(i==0)
            c[i]=0;
        else
        {
            sum=sum+b[i-1];
            c[i]=sum-a[i];
        }
    }
    for(int i=0;i<4;i++)
    {
        for(int j=0;j<4-1-i;j++)
        {
            if(p[j]>p[j+1])
            {
                temp=p[j];
                p[j]=p[j+1];
                p[j+1]=temp;
                temp=c[j];
                c[j]=c[j+1];
                c[j+1]=temp;
            }
        }
    }
    for(int i=0;i<3;i++)
    {
        printf("P%d (WT=%d), ",i+1,c[i]);
    }
    printf("P4 (WT=%d)",c[3]);
        

    /* Enter your code here. Read input from STDIN. Print output to STDOUT */    
    return 0;
}
