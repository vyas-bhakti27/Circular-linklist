#include<stdio.h>   // Circular linked list
#include<stdlib.h>  
struct node   
{  
  int data;  
  struct node *next;   
};  
  struct node *head;  
      
void beginsert ();   
void lastinsert ();  
void randominsert();  
void begin_delete();  
void last_delete();  
void random_delete();  
void display();  
void search(); 
 
void main ()  
    {  
        int op=0;  
        while(op != 7)   
        {  
            
            printf("\nEnter your choice to perform operation\n");    
            printf("enter 1.Insert in begining\n enter 2.Insert at last\n enter 3.Delete from Beginning\n enter 4.Delete from last\n enter 5.display\n enter 6.Exit\n");  
            printf("\nEnter your choice?\n");         
            scanf("\n%d",&op);  
            switch(op)  
            {  
                case 1:  
                beginsert();      
                break;  
                case 2:  
                lastinsert();         
                break;  
                case 3:  
                begin_delete();       
                break;  
                case 4:  
                last_delete();        
                break;    
                case 5:  
                display();        
                break;  
                case 6:  
                exit(0);  
                break;  
                default:  
                printf("not valid choice !");  
            }  
        }  
    }  
void beginsert()  
    {  
        struct node *ptr,*temp;   
        int item;   
        ptr = (struct node *)malloc(sizeof(struct node));  
        if(ptr == NULL)  
        {  
            printf("\nOVERFLOW");  
        }  
        else   
        {  
            printf("\nEnter the node data?");  
            scanf("%d",&item);  
            ptr -> data = item;  
            if(head == NULL)  
            {  
                head = ptr;  
                ptr -> next = head;  
            }  
            else   
            {     
                temp = head;  
                while(temp->next != head)  
                    temp = temp->next;  
                ptr->next = head;   
                temp -> next = ptr;   
                head = ptr;  
            }   
            printf("\nnode inserted\n");  
        }  
                  
    }  
void lastinsert()  
    {  
        struct node *ptr,*temp;   
        int item;  
        ptr = (struct node *)malloc(sizeof(struct node));  
        if(ptr == NULL)  
        {  
            printf("\nOVERFLOW\n");  
        }  
        else  
        {  
            printf("\nEnter Data?");  
            scanf("%d",&item);  
            ptr->data = item;  
            if(head == NULL)  
            {  
                head = ptr;  
                ptr -> next = head;    
            }  
            else  
            {  
                temp = head;  
                while(temp -> next != head)  
                {  
                    temp = temp -> next;  
                }  
                temp -> next = ptr;   
                ptr -> next = head;  
            }  
              
            printf("\nnode inserted\n");  
        }  
      
    }  
      
void begin_delete()  
    {  
        struct node *ptr;   
        if(head == NULL)  
        {  
            printf("\nUNDERFLOW");    
        }  
        else if(head->next == head)  
        {  
            head = NULL;  
            free(head);  
            printf("\nnode deleted\n");  
        }  
          
        else  
        {   ptr = head;   
            while(ptr -> next != head)  
                ptr = ptr -> next;   
            ptr->next = head->next;  
            free(head);  
            head = ptr->next;  
            printf("\nnode deleted\n");  
      
        }  
    } 
 
void last_delete()  
    {  
        struct node *ptr, *preptr;  
        if(head==NULL)  
        {  
            printf("\nUNDERFLOW");  
        }  
        else if (head ->next == head)  
        {  
            head = NULL;  
            free(head);  
            printf("\nnode deleted\n");  
      
        }  
        else   
        {  
            ptr = head;  
            while(ptr ->next != head)  
            {  
                preptr=ptr;  
                ptr = ptr->next;  
            }  
            preptr->next = ptr -> next;  
            free(ptr);  
            printf("\nnode deleted\n");  
      
        }  
 }  
      
    
 void display()  

    {  
        struct node *ptr;  
        ptr=head;  
        if(head == NULL)  
        {  
            printf("\nnothing to print");  
        }     
        else  
        {  
            printf("\n printing values ... \n");  
              
            while(ptr -> next != head)  
            {  
              
                printf("%d\n", ptr -> data);  
                ptr = ptr -> next;  
            }  
            printf("%d\n", ptr -> data);  
        }  
                  
    }
