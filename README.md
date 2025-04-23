#include<stdio.h>
int main()
{
    int n; //size
    printf("Size of array (max size 100): ");
    scanf("%d",&n);
    if (n<=0 || n>100)
    {
        printf("Invalid size! Must be between 1 and 100.\n");
        return 1;
    }
    int arr[100];
    printf("Array : ");
    for(int i=0; i<n; i++)
    {
        scanf("%d",&arr[i]);  //user data
    }
    printf("\nChose any Options :\n");
    printf("1)Insert  2)Update  3)Delete  4)Sort  5)Search  6)Display \n");
    printf("\n");
    int option;
    printf("Your choice : ");
    scanf("%d",&option);

    if(option==1)
    {
        if (n >= 100)
        {
            printf("Array is full! Cannot insert more elements.\n");
            return 1;
        }
        int num,pos;
        printf("The number to add in the array: ");
        scanf("%d",&num );
        printf("\nChose between the number 0 to %d\n",n);
        printf("\nThe position : ");
        scanf("%d",&pos);
        printf("Original array : ");
        if(pos<0 || pos>n)
        {
            printf("Invalid array size! Size must be between 1 and %d.\n",n);
            return 1;
        }
        else
        {
            for(int i=0; i<n; i++)
            {
                printf("%d ",arr[i]);
            }
            printf("\n");
            for(int i=n; i>pos; i--)
            {
                arr[i]=arr[i-1];
            }
            arr[pos]=num; //insert the number
            n++; //increase the size

            printf("\nUpdated array : ");
            for(int i=0; i<n; i++)
            {
                printf("%d ",arr[i]);
            }
            printf("\n");
        }
    }

    else if(option==2)
    {
        int pos,num;
        printf("Enter the position (1 to %d) to change: ",n);
        scanf("%d",&pos);
        if (pos<1 || pos>n)
        {
            printf("Invalid position! It must be between 1 and %d.\n",n);
        }
        else
        {
            printf("Enter the new number for position %d:",pos);
            scanf("%d",&num);
            arr[pos-1]=num; //update the element and 0-based

            printf("Updated array: ");
            for (int i=0; i<n; i++)
            {
                printf("%d ",arr[i]);
            }
            printf("\n");
        }

    }

    else if(option==3)
    {
        int pos;
        printf("\nEnter the position of the element to delete: ");
        scanf("%d", &pos);
        if (pos >= 1 && pos <= n)
        {
            for (int i = pos - 1; i<n-1; i++)
            {
                arr[i] = arr[i + 1];
            }
            n--;

            printf("Updated array : ");
            for (int i=0; i<n; i++)
            {
                printf("%d ",arr[i]);
            }
            printf("\n");

        }
        else
        {
            printf("\nInvalid position! Must be between 1 and %d.\n",n);
        }
    }
    else if(option==4)
    {
        for(int i=0; i<n-1; i++)
        {
            for(int j=0; j<n-1-i; j++)
            {
                if(arr[j]>arr[j+1])
                {
                    int temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                }
            }
        }
        printf("\nSorted array : ");
        for (int i=0; i<n; i++)
        {
            printf("%d ",arr[i]);
        }
        printf("\n");
    }

    else if(option==5)
    {
        int num;
        printf("\nEnter the number to search for : ");
        scanf("%d",&num);
        int found=0;
        for(int i=0; i<n; i++)
        {
            if(arr[i]==num)
            {
                printf("Number %d found at position %d.\n",num,i+1);
                found=1;
                break;
            }
        }
        if(!found)
        {
            printf("\nNumber %d not found in the array.\n", num);
        }
    }

    else if(option==6)
    {
        printf("\nArray contents : ");
        for (int i=0; i<n; i++)
        {
            printf("%d ",arr[i]);
        }
        printf("\n");
    }
    else
    {
        printf("Invalid choice");
    }
}
