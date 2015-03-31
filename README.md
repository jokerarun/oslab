#include<stdio.h>
int main()
{
  int time,bt[10],at[10],sum_bt=0,smallest,n,i;
  int sum_turnaround=0,sum_wait=0;
  printf("no of processes : ");
  scanf("%d",&n);

printf("Enter arrival time : ");
  for(i=0;i<n;i++)
  {
    
    scanf("%d",&at[i]);}

printf("Enter burst time :");
for(i=0;i<n;i++)
    {
    scanf("%d",&bt[i]);
    sum_bt+=bt[i];
  }
  bt[9]=9999;
  printf("\n\nProcess\t   WT \t  TAT\n\n");
  for(time=0;time<sum_bt;)
  {
    smallest=9;
    for(i=0;i<n;i++)
    {
      if(at[i]<=time && bt[i]>0 && bt[i]<bt[smallest])
        smallest=i;
    }
    if(smallest==9)
    {
      time++;
      continue;
    }
    printf("P%d\t \t%d\t \t%d\n",smallest,time-at[smallest],time+bt[smallest]-at[smallest]);
    sum_turnaround+=time+bt[smallest]-at[smallest];
    sum_wait+=time-at[smallest];
    time+=bt[smallest];
    bt[smallest]=0;
  }
  printf("\n\n avg WT = %.2f",sum_wait*1.0/n);
  printf(" Avg WT = %.2f",sum_turnaround*1.0/n);
  return 0;
}
