---
title: 用C语言实现链表
date: 2020-04-05 09:40:19
tags: 
    - C语言 
    - 原创
categories: 编程
---
# 用C语言实现链表，附代码注释
这里给已经在学C和数据结构的小伙伴提供一些弹药支持，虽然不知道管不管用，在这里大佬就勿扰了吧！哈哈！

在实现一个简单的链表前需要用到哪些知识点呢？

 - C语言基础知识，比如要用到的结构体、指针、函数、运算
 - 一点数据结构的知识，在学习数据结构也能看到链表的身影，我们这里实现的是单项链表
 - 有手，有脑

现在上代码：

```
# include<stdio.h>
# include<malloc.h>

//创造链表 
//定义一个节点类型
typedef struct node{
	int data;
	char name[10];
	struct node *next;
}noDe,* pnoDe; 

// 输入函数 
pnoDe funkin(void){
 	pnoDe pHead = (pnoDe)malloc(sizeof(noDe));	//定义头指针和尾指针分别指向头和尾节点 
 	pnoDe ptail = pHead;
	ptail->next = NULL;
	 
	int n,score;	//有效节点的数量  
	char name[10];	
	printf("please funkin a number:");
	scanf("%d",&n);			 
 
// 连续输入学生及成绩数据 
	for(int i=0;i<n;i++){
		pnoDe pNew = (pnoDe)malloc(sizeof(noDe));
		printf("please scanf the score of number %d :",i+1);
		scanf("%d %s",&(pNew->data),pNew->name);
		/*核心代码*/
		ptail->next = pNew;	   //让尾节点指针指向新节点 
		ptail = pNew;	//让尾指针指向新节点 ,并移动到下一个节点 
		ptail->next = NULL;	//让新节点指针域为空 
	}	
	
	return pHead;
} 

// 输出函数 
void out(pnoDe pHead){
	int k = 1;
	pnoDe p = pHead->next;
	while(p != NULL){
		printf("\nfunkout number %d: ",k);
		printf("score= %d\nname= %s\n",p->data,p->name);
		p = p->next;
		k++;
	}
	
	return;
}

int main(void){
	pnoDe pHead = NULL;
	pHead = funkin();
	out(pHead);
	return 0;	
} 





```

代码并不难懂，大概就是先输入需要创建的节点数或有效数据个数，之后创建了一个会构造链表的函数，并返回头指针。这个时候链表其实已经创建好了，并且已经放入了数据。之后，输出函数out()会输出数据。ok，就是这么简单！觉得可以就点赞加关注，博主会定期更新哦！哈！最后附上个人博客链接：[csdn博客](https://blog.csdn.net/Gobullin)
