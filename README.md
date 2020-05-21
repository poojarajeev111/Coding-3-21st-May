
#include<stdio.h> 
#include<stdlib.h>

struct Node 
{ 

    int data; 

    struct Node* next; 
}; 
void push(struct Node** head_ref, int new_data) 
{ 

    struct Node* new_node = 

            (struct Node*) malloc(sizeof(struct Node)); 


    new_node->data  = new_data; 


    new_node->next = (*head_ref);      


    (*head_ref)    = new_node; 
} 

void printList(struct Node *node) 
{ 

    while (node!=NULL) 

    { 

       printf("%d ", node->data); 

       node = node->next; 

    } 
}  

  

 Node* deleteDuplicates(Node* head) { 

        if (head == nullptr) return nullptr; 

        if (head->next == nullptr) return head; 

  

        if (head->data == head->next->data) { 

            Node *tmp; 

            
            tmp = head->next; 

            head->next = head->next->next; 

            free(tmp); 

            return deleteDuplicates(head); 

        } 

  

        else {  

     

            head->next = deleteDuplicates(head->next); 

            return head; 

        } 

    } 

  

int main() 
{ 

    struct Node* head = NULL; 

    push(&head, 20); 

    push(&head, 13); 

    push(&head, 13);   

    push(&head, 11); 

    push(&head, 11); 

    push(&head, 11);                                     

  

    printf("\n Linked list before duplicate removal  "); 

    printList(head);  

    head = deleteDuplicates(head);  

  

    printf("\n Linked list after duplicate removal ");          

    printList(head);             

    

    return 0; 
} 
