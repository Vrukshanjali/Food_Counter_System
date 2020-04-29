# Food_Counter_System
#include<stdio.h> 
int main() 
{ 
      int i, total = 0, x, limit, counter = 0, t_quantum,n,a,m; 
      int wait_time = 0, turnaround_time = 0, arrival_time[10], burst_time[10], temp[10]; 
      float average_wait_time, average_turnaround_time;
      printf("\nEnter Total Number of Customers: "); 
      scanf("%d", &limit); 
      x = limit; 
      for(i = 0; i < limit; i++) 
      {
            printf("\nProvide the details for Customer[%d]\n", i + 1);
            printf("Arrival Time:\t");
            scanf("%d", &arrival_time[i]);
            printf("Would you like to :\n");
            printf("1.Choose from menu\n2.Exit\n");
            scanf("%d",&a);
            if(a==1||a==2)
            {
			
			if(a==2)
            {
            	break;
			}
			else
			{
		    	printf("1.Veg Burger\n2.Chicken Burger\n3.Fries\n4.Coke\n5.Burger and fries\n6.Combo\n7.Exit\n");
                scanf("%d",&n);
               
			 if(n==1)
			 {
				 burst_time[i]=8;
				 temp[i] = burst_time[i];
			 }
             if(n==2)
             {
             	 burst_time[i]=10;
				 temp[i] = burst_time[i];	
			 }
			 if(n==3)
			 { 
			 	 burst_time[i]=6;
				 temp[i] = burst_time[i];
			 }
			 if(n==4)
			 {
			 	 burst_time[i]=3;
				 temp[i] = burst_time[i];
			 }
			 if(n==5)
			 {
			 	printf("Do you want a 1.Veg burger or 2.Non-veg burger?\n");
			 	scanf("%d",&m);
			 	if(m==1)
			 	{
			 	  burst_time[i]=14;
				  temp[i] = burst_time[i];	
				}
				else
				{
			      burst_time[i]=16;
				  temp[i] = burst_time[i];	
				}
				 
		     }
			 if(n==6)
			 {
			     printf("Do you want a 1.Veg burger or 2.Non-veg burger?\n");
			 	scanf("%d",&m);
			 	if(m==1)
			 	{
			 	  burst_time[i]=14;
				  temp[i] = burst_time[i];	
				}
				else
				{
			      burst_time[i]=16;
				  temp[i] = burst_time[i];	
				}	
		     }
		     if(n==7)
		     {
		     	break;
			 }
		}
		}
		 else
		 {
			 printf("Invalid option\n");
			 continue;
		 }
		}
            
       
      printf("\nEnter Time Quantum:\t"); 
      scanf("%d", &t_quantum); 
      printf("\nCustomer ID\t\tBurst Time\t Turnaround Time\t Waiting Time\n");
      for(total = 0, i = 0; x != 0;) 
      { 
            if(temp[i] <= t_quantum && temp[i] > 0) 
            { 
                  total = total + temp[i]; 
                  temp[i] = 0; 
                  counter = 1; 
            } 
            else if(temp[i] > 0) 
            { 
                  temp[i] = temp[i] - t_quantum; 
                  total = total + t_quantum; 
            } 
            if(temp[i] == 0 && counter == 1) 
            { 
                  x--; 
                  printf("\nProcess[%d]\t\t%d\t\t %d\t\t\t %d", i + 1, burst_time[i], total - arrival_time[i], total - arrival_time[i] - burst_time[i]);
                  wait_time = wait_time + total - arrival_time[i] - burst_time[i]; 
                  turnaround_time = turnaround_time + total - arrival_time[i]; 
                  counter = 0; 
            } 
            if(i == limit - 1) 
            {
                  i = 0; 
            }
            else if(arrival_time[i + 1] <= total) 
            {
                  i++;
            }
            else 
            {
                  i = 0;
            }
      } 
      average_wait_time = wait_time * 1.0 / limit;
      average_turnaround_time = turnaround_time * 1.0 / limit;
      printf("\n\nAverage Waiting Time:\t%f", average_wait_time); 
      printf("\nAvg Turnaround Time:\t%f\n", average_turnaround_time); 
      return 0; 
}
