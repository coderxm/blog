---
title: 小码moneykeeper
date: 2020-05-14 07:07:24
author: coder小码
tags: moneykeeper
categories: c/c++
keywords: [c,实战]
toc: true
---
### 纯c小项目，小码资金管理工具moneykeeper
作者：coderxm
公众号：小码之光

---
 你小码哥回来啦！最近闷得慌，又在学java(自学，想走这条路，哎，一个人找到所爱的真的很难,说不定哪天真的挂了，就来不及了)，慢慢地觉得特别吃力了，主要是学习环境不好，住在一个‘破房子’里，人口又多，真的是烦，而且还不是自个家（没家）。有意识地数了数钱口袋，发现是真的穷死光，哎！！！郁闷啊啊啊！感觉连自个亲人都被抛弃地感觉！(**除了自己，谁都别信！**因为别指望他们能帮你买房买车，理解你的世界！) 总想做点什么，于是敲了敲几行代码，做了个小钱钱管理工具，以后方便看看钱兜(哎！)，自己觉得挺简单实用地就分享给大家了，源码也给哈！
下载地址		:	[小码理财moneykeeper](https://github.com/coderxm/moneykeeper.git)

---
###### 项目代码
```
#include<stdio.h>
#include<string.h>
#include<windows.h>
#include<conio.h>


// 户名结构体 
typedef struct{
	char hum[100];
//	char money[10];
}hums;

// 构造函数
void outdata(void); 
void empty(char *sf);
void putdata(hums *hm);
void qorw(hums *hm);
int strint(char *s);

int main(void){
		
	hums zhanghu[11];	//定义户名结构体数组 
	char get[4]; 
	char command[4];
	
	FILE *fpr;
	fpr = fopen("E:\\wokfilc\\moneykeeper\\data.txt","r");
	fgets(get,5,fpr);
	fclose(fpr);
	
	if(get=='\0'||get==" "){
		printf("无账户信息!");
		qorw(zhanghu);
	}else{
		outdata();
		printf("请继续写入wd或退出quit：\n");
		scanf("%s",command);
		if(strcmp(command,"quit")==0){
			exit(0);
		}else if(strcmp(command,"wd")==0){
			putdata(zhanghu);
			outdata();
			qorw(zhanghu);
		}else{
			printf("输入错误，请重新输入：\n");
			qorw(zhanghu);
		}
	}
	
	return 0;
} 

//输出信息 
void outdata(){
	FILE *fpr;
	fpr = fopen("E:\\wokfilc\\moneykeeper\\data.txt","r");
	
	int sum=0;
	char DataStr[100];
	printf("*****$$*****\n正在输出账户信息：\n");
	while(feof(fpr)==0){
		fseek(fpr,0L,SEEK_CUR);				//?
		fgets(DataStr,100,fpr);
		if(DataStr!='\0'&&DataStr!=" "){
			printf("%s \n",DataStr);
		}		
		sum = sum+strint(DataStr);
		empty(DataStr);
	} 
	fclose(fpr);
	printf("您的总资金合计为：%d元\n",sum);
}

//empty初始化清空数组 
void empty(char *sf){
	int sfsize = 0;
	sfsize = sizeof(sf); 
	for(int n=0;n<sfsize;n++){
		sf[n] = '\0'; 
	}
} 

//写入数据 
void putdata(hums *hm){
	FILE *fpw;
	fpw = fopen("E:\\wokfilc\\moneykeeper\\data.txt","w+");
	
	int i = 0;
	char input[100];
	printf("(回车)请写入账户数据：\n");
	
	do{
		int len = 0;
		empty(input); 
		printf("请写入第%d个账户数据:\n",i+1);
		scanf("%s",input);	
		len = strlen(input);
		strcpy(hm[i].hum,input); 
		strcat(hm[i].hum,"\n");
		fputs(hm[i].hum,fpw);
		i = i+1;
	}while( (strcmp(input,"end"))!=0&&(i<11) );
	
	fclose(fpw);	//写入完毕后关闭文件 
}

//字符串中提取数字 
int strint(char *s){
	int slen=0;
	int Money=0;
	int ml = 0;
	char money[10];
	slen = strlen(s);
	for(int n=0;n<slen;n++){
		if(s[n]>=48&&s[n]<=57){
			money[ml]=s[n];
			ml++;
		}
	}
	Money = atoi(money);
	return Money;
}

//选择（退出或重新写入）函数
void qorw(hums *hm){
    char getput[10];
	printf("请选择(重新)输入wrdo或退出quit：\n");
	scanf("%s",getput);
	while(strcmp(getput,"quit")!=0){
		if(strcmp(getput,"quit")==0){
			return;
		}else if(strcmp(getput,"wrdo")==0){
			putdata(hm);
			qorw(hm);
			return;
		}else{
			printf("重新输入,");
			qorw(hm);
			return;
		}
	}
} 





```

---
源码讲解就不用了吧！相信坚定走这路的人学过c，能看懂吧！主要是也让大家有个真实的现实观，好好管管小钱钱，别胡乱挥霍，以后说不定有大用处！至少能给你一个**真正的家**(一个固定的住处)！好啦！拜拜，学习去喽！

---
最后：
个人站点：[博客园](https://www.cnblogs.com/coderma)
公众号：
![小码之光](https://img-blog.csdnimg.cn/20200513202720997.jpg#pic_center)

---
