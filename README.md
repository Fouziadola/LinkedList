//linked list solving by fouziadola

#include<iostream>
using namespace std;

class Node{
    public:
    int data;
    Node* next;
};
Node* insert_infirst(Node* head,int value){
    Node* t=head;
    Node* temp1= new Node();
    temp1->data=value;
    temp1-> next=t;
    return temp1;
}

Node* insert_inmiddle(Node* head,int value,int target){//after
     Node* middle=head;
    Node* temp2= new Node();
    temp2->data=value;
    temp2->next=NULL;
    while(middle->next!=NULL){
        if(middle->data==target){
            temp2->next=middle->next;
           middle->next= temp2;
            
        }
        middle=middle->next;
    }
    return head;
    
}
Node* insert_inmiddlel(Node* head,int value,int target){//before
    Node* middlebefore=head;
    Node* temp3= new Node();
    temp3->data=value;
    if(middlebefore->data == target){
        insert_infirst( head,value);
        
    }
    while(middlebefore->next->data!=target && middlebefore->data!= NULL){
        middlebefore=middlebefore->next;
        if(middlebefore->next==NULL){
            break;
        }
    }
    temp3->next= middlebefore->next;
     middlebefore->next=temp3;
     return head;
}
Node* insert_inlast(Node* head,int value){
    Node* last=head;
    
    while(last->next!=NULL){
        last=last->next;
    }
    Node* temp4= new Node();
    temp4->data= value;
    last->next=temp4;
    temp4->next=NULL;
    return head;
}
Node* deletion(Node* head,int value){
    Node* temp5= head;
    if(temp5->data==value){
        head=temp5->next;
        free(temp5);
        return head;
    }
    Node* prev;
    while(temp5!=NULL && temp5->data!=value){
        prev= temp5;
        temp5=temp5->next;
    }
     if(temp5 == NULL){
        cout << "The item doesn't exist \n";
        return head;
    }
    prev -> next = temp5 -> next;
    free(temp5);
    return head;
}

int main(){
    Node* prev;
    Node* head= new Node();
    head->data=10;
    head->next=NULL;
    prev= head;
    for(int i=20;i<=30;i=i+10){
Node* temp= new Node();
    temp->data=i;
    temp->next=NULL;
    prev->next=temp;
    prev=temp;
    }
    head=insert_infirst(head,5);
    head =insert_inmiddle(head,25,20);
    head =insert_inmiddlel(head,15,20);
    head=insert_inlast(head,35);
    head=deletion(head,20);
    Node* cursor;
    cursor= head;
    while(cursor){
        cout<<cursor->data <<endl;
        cursor=cursor->next;
    }
    
    
    
    return 0;
} 
