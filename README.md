# Merge-LL
Merge two sorted linked lists
//Merge two sorted linked list
#include<iostream>
using namespace std;

struct Node{
	int data;
	Node* next;
	Node(int d){
		data=d;
		next=NULL;
	}
};

Node* sortedMerge(Node* a,Node* b){
	if(a==NULL){
		return b;
	}
	if(b==NULL){
		return a;
	}
	Node* head=NULL,*tail=NULL;
	if(a->data<=b->data){
		head=tail=a;
		a=a->next;
	}
	else{
		head=tail=b;
		b=b->next;
	}
	while(a!=NULL && b!=NULL){
		if(a->data<=b->data){
			tail->next=a;
			tail=a;
			a=a->next;
		}
		else{
			tail->next=b;
			tail=b;
			b=b->next;
		}
	}
	if(a==NULL){
		tail->next=b;
	}
	else{
		tail->next=a;
	}
	return head;
}

Node* insertAtEnd(Node* head,int y){
	Node* temp = new Node(y);
	if(head==NULL){
		return temp;
	}
	Node* curr=head;
	while(curr->next!=NULL){
		curr=curr->next;
	}
	curr->next=temp;
	return head;
}

void printList(Node* head){
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data;
		curr=curr->next;
	}
}

int main(){
	Node* head1=NULL;
	int n1;
	cin>>n1;
	for(int i=1;i<=n1;i++){
		int x;
		cin>>x;
		head1=insertAtEnd(head1,x);
	}
	printList(head1);
	cout<<endl;
	Node* head2=NULL;
	int n2;
	cin>>n2;
	for(int i=1;i<=n2;i++){
		int x;
		cin>>x;
		head2=insertAtEnd(head2,x);
	}
	printList(head2);
	cout<<endl;
	sortedMerge(head1,head2);
	printList(head1);
}
