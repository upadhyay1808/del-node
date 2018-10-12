/* del-node*/
#include<stdio.h>
#include<stdlib.h>
struct node
{
	int data;
	struct node* next;
};
struct node*head;
void insert (int ,int );
void delet(int);
void insert (int n,int x)
{
	struct node* temp1=(struct node*)malloc(sizeof(struct node));
	temp1->data=x;
	temp1->next=NULL;
	if(n==1)
	{
		temp1->next=head;
		head=temp1;
	}
	else
	{
		struct node* temp2=head;
		for(int i=0;i<n-2;i++)
		{
			temp2=temp2->next;
		}
		temp1->next=temp2->next;
		temp2->next=temp1;
	}
	return;
}
void print()
{
	struct node* temp=head;
	while(temp!=NULL)
	{
		printf("%d ",temp->data);
		temp=temp->next;
	}
}
 void delet(int pos)
{
struct node* temp1=head;
	if(pos==1)
	{
		head=temp1->next;
		free(temp1);
	}
	else
	{
		
		for(int i=0;i<pos-2;i++)
		{
			temp1=temp1->next;
		}
		struct node* temp2;
		temp2=temp1->next;
		temp1->next=temp2->next;
		free(temp2);
	}
}
int main()
{
	head=NULL;
	insert(1,4);
	insert(2,6);
	insert (3,3);
	insert(4,1);
	insert(1,10);
	print();
	int pos;
	scanf("%d",&pos);
	delet(pos);
	print(); 
}
