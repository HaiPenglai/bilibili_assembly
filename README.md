## bilibili汇编语言速成指南资料【收藏不迷路】

主要资料：**pdf**,环境压缩包，代码

## 如何下载

![image](./实战篇代码/GitHub下载.png)

## 实战篇-代码

#### 5.11输出hello world

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db 'hello world','$'
data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
		mov ax,data
		mov ds,ax
		lea dx,str		
		mov ah,9
		int 21H

		mov ah,4cH
		int 21H
codesg ends
end start

```

#### 5.12字符串转大写

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db 'hello world','$'
data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
	mov ax,data
	mov ds,ax
	
	mov bx,0
	mov cx,11
	s:
		mov al,[bx]
		and al,1011111B
		mov [bx],al
		inc bx
		loop s
		
		;mov dx,offset str
		lea dx,str		
		mov ah,9
		int 21H

		mov ah,4cH
		int 21H
codesg ends
end start


comment    *
c++
数组当中的最大值
int res=0
for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
return res

求最小值
int res=FF
for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
return res


for(int i=0;i<str.size();i++)str[i]转大写
* comment	

```

#### 5.13字符串转小写

 ```assembly
 assume cs:codesg,ds:data,ss:stack
 data segmeNT
 	str db 'hello world','$'
 data ends
 stack segment
 	db 10 dup (0) 
 stack ends
 codesg SEgment
 	start:	
 	mov ax,data
 	mov ds,ax
 	
 	mov bx,0
 	mov cx,11
 	s:
 		mov al,[bx]
 		or al,0100000B
 		mov [bx],al
 		inc bx
 		loop s
 		
 		;mov dx,offset str
 		lea dx,str		
 		mov ah,9
 		int 21H
 
 		mov ah,4cH
 		int 21H
 codesg ends
 end start
 
 
 comment    *
 c++
 数组当中的最大值
 int res=0
 for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
 return res
 
 求最小值
 int res=FF
 for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
 return res
 
 
 for(int i=0;i<str.size();i++)str[i]转大写
 * comment	
 
 ```

#### 5.14求数组最小值

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db 'hello world','$'
data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
	mov ax,data
	mov ds,ax
	
	mov bx,0
	mov cx,11
	mov ah,0FFH
	s:
		mov al,[bx]
		cmp ah,al
		jna s1
		mov ah,al
	s1:
		mov [bx],al
		inc bx
		loop s
		
		;mov dx,offset str
		lea dx,str		
		mov ah,9
		int 21H

		mov ah,4cH
		int 21H
codesg ends
end start


comment    *
c++
数组当中的最大值
int res=0
for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
return res

求最小值
int res=FF
for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
return res


for(int i=0;i<str.size();i++)str[i]转大写
* comment	

```

#### 5.15求数组最大值

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db 'hello world','$'
data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
	mov ax,data
	mov ds,ax
	
	mov bx,0
	mov cx,11
	mov ah,0
	s:
		mov al,[bx]
		cmp ah,al
		jnb s1
		mov ah,al
	s1:
		mov [bx],al
		inc bx
		loop s
		
		;mov dx,offset str
		lea dx,str		
		mov ah,9
		int 21H

		mov ah,4cH
		int 21H
codesg ends
end start



comment    *
c++
数组当中的最大值
int res=0
for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
return res

求最小值
int res=FF
for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
return res


for(int i=0;i<str.size();i++)str[i]转大写
* comment	

```

#### 5.22拷贝数组

```assembly
assume cs:code,ds:data,ss:stack
data segment 
	arr db 1,2,3,4,10,20,30,40
	res db 8 dup (0)
data ends

stack segment 
	
	db 100 dup (0)
stack ends

code segment 
	start:
		mov ax,data
		mov ds,ax
		
		mov bx,0
		mov cx,8
		for:
			mov al,arr[bx]
			mov ds:res[bx],al
			inc bx
		loop for
			
		mov ax,4c00H
		int 21
code ends
end start


comment *
求和
vector<int>arr={1,2,3,4,10,20,30,40};
int sum=0;
for(int i=0;i<arr.size();i++)sum+=arr[i];
拷贝
vector<int>arr={1,2,3,4,10,20,30,40};
int res[8];
for(int i=0;i<8;i++)res[7-i]=arr[i];
for(int i=7;i>=0;i--)res[i
*comment 
```

#### 5.23用si，di翻转数组

```assembly
assume cs:code,ds:data,ss:stack
data segment 
	arr db 1,2,3,4,10,20,30,40
	res db 8 dup (0)
data ends

stack segment 
	
	db 100 dup (0)
stack ends

code segment 
	start:
		mov ax,data
		mov ds,ax
		
		mov si,0
		mov di,7
		mov cx,8
		for:
			mov al,arr[si]
			mov ds:res[di],al
			inc si
			dec di
		loop for
			
		mov ax,4c00H
		int 21
code ends
end start


comment *
求和
vector<int>arr={1,2,3,4,10,20,30,40};
int sum=0;
for(int i=0;i<arr.size();i++)sum+=arr[i];
拷贝
vector<int>arr={1,2,3,4,10,20,30,40};
int res[8];
for(int i=0;i<8;i++)res[7-i]=arr[i];
for(int i=7;i>=0;i--)res[i
*comment 
```

#### 5.31用栈翻转数组

 ```assembly
assume cs:code,ds:data,ss:stack
data segment 
	arr dw 1111H,2222H,3333H,4444H,5555H,6666H,7777H,8888H
	res db 800 dup (0)
data ends

stack segment 
	db 1000 dup (0)
stack ends

code segment 
	start:
		mov ax,data
		mov ds,ax
		mov ax,stack
		mov ss,ax
		mov sp,100

		mov bx,0
		mov cx,8
		for:	
			push ds:arr[bx]
			add bx,2
 		loop for

		mov bx,0
		mov cx,8
		for1:	
			pop ds:arr[bx]
			add bx,2
 		loop for1

			
		mov ax,4c00H
		int 21
code ends
end start


comment *
求和
vector<int>arr={1,2,3,4,10,20,30,40};
int sum=0;
for(int i=0;i<arr.size();i++)sum+=arr[i];
拷贝
vector<int>arr={1,2,3,4,10,20,30,40};
int res[8];
for(int i=0;i<8;i++)res[i]=arr[i];
for(int i=0;i<8;i++)res[7-i]=arr[i];

for(int i=0,j=7;i<8;i++,j--)res[j]=arr[i];
翻转
vector<int>arr={1,2,3,4,10,20,30,40};
stack<int>stk;
for(int i=0;i<8;i++)stk.push(arr[i]);
for(int i=0;i<8;i++)arr[i]=stk.top(),stk.pop();
求斐波那契数列
int arr[100]={1,1};
for(int i=2;i<10;i++)arr[i]=arr[i-1]+arr[i-2];
*comment 
 ```

#### 5.32动态规划求斐波那契数列

```assembly
assume cs:code,ds:data,ss:stack
data segment 
	arr dw 1H,1H,100 dup (0)
	res db 800 dup (0)
data ends

stack segment 
	db 100 dup (0)
stack ends

code segment 
	start:
		mov ax,data
		mov ds,ax
		mov ax,stack
		mov ss,ax
		
		mov bx,4
		mov cx,30
		for :
			mov dx,0
			add dx,ds:arr[bx-2]
			add dx,ds:arr[bx-4]
			mov ds:arr[bx],dx
		add bx,2
		loop for
			
		mov ax,4c00H
		int 21
code ends
end start


comment *
求和
vector<int>arr={1,2,3,4,10,20,30,40};
int sum=0;
for(int i=0;i<arr.size();i++)sum+=arr[i];
拷贝
vector<int>arr={1,2,3,4,10,20,30,40};
int res[8];
for(int i=0;i<8;i++)res[i]=arr[i];
for(int i=0;i<8;i++)res[7-i]=arr[i];

for(int i=0,j=7;i<8;i++,j--)res[j]=arr[i];
翻转
vector<int>arr={1,2,3,4,10,20,30,40};
stack<int>stk;
for(int i=0;i<8;i++)stk.push(arr[i]);
for(int i=0;i<8;i++)arr[i]=stk.top(),stk.pop();
求斐波那契数列
int arr[100]={1,1};
for(int i=2;i<10;i++)arr[i]=arr[i-1]+arr[i-2];
*comment 


```



#### 5.42二重循环把指定矩形转大写

 ```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db 'aaaaabbbbbccccc '
	db 'aaaaabbbbbccccc '
	db 'aaaaabbbbbccccc '
	db 'aaaaabbbbbccccc ','$'

data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
	mov ax,data
	mov ds,ax
	
	mov bx,0
	mov cx,4
	for:
	      mov dx,cx
		mov si,0
		mov cx,5
		for1:
			mov al,ds:str[bx+si]
			and al,11011111B
			mov ds:str[bx+si],al
		inc si
		loop for1
	     mov cx,dx
	add bx,16
	loop for
		
	lea dx,str		
	mov ah,9
	int 21H

	mov ah,4cH
	int 21H
codesg ends
end start



comment *
	 	bx
	for(int i=0;循环4次;i+=16){
				si
		for(int j=0;循环五次;j++){
			arr[j+i]转大写
		}
	}
	
	
	for(int i=0;i<;i+=16)
		arr[i+5]转大写

	for(int i=0;i<arr.size();i++){
		for(int j=0;j<arr[0].size();j++){
				cout <<arr[2][5]<<" ";	
}cout<<endl;
}
*comment 


comment    *
c++
数组当中的最大值
int res=0
for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
return res

求最小值
int res=FF
for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
return res


for(int i=0;i<str.size();i++)str[i]转大写
* comment	

 ```

#### 5.51冒泡排序

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	arr db 0A2H,24H,07H,3AH,1BH,0F1H,3BH,25H,81H

data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
	mov ax,data
	mov ds,ax
	
	
	mov bx,0
	mov cx,8
	for:
	      mov dx,cx
		mov si,8
		mov cx,8
		sub cx,bx
		for1:
			mov ah,ds:arr[si]
			mov al,ds:arr[si-1]
			cmp ah,al
			jnb all
				xchg ah,al
				mov ds:arr[si],ah
				mov ds:arr[si-1],al				
	
			all:
				
		dec si
		loop for1
	     mov cx,dx
	add bx,1
	loop for

	mov ah,4cH
	int 21H
codesg ends
end start



comment *
	 	bx
	for(int i=0;循环4次;i+=16){
				si
		for(int j=0;循环五次;j++){
			arr[j+i]转大写
		}
	}
	
	
	for(int i=0;i<;i+=16)
		arr[i+5]转大写

	for(int i=0;i<arr.size();i++){
		for(int j=0;j<arr[0].size();j++){
				cout <<arr[2][5]<<" ";	
}cout<<endl;
}
*comment 



comment    *
c++
数组当中的最大值
int res=0
for(int i=0;i<str.size();i++)if(res<s[i])res=s[i];
return res

求最小值
int res=FF
for(int i=0;i<str.size();i++)if(res>s[i])res=s[i];
return res


for(int i=0;i<str.size();i++)str[i]转大写
* comment	

```

#### 5.61十进制转16进制

```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db '00012345','$'
data ends
stack segment
	db 10 dup (0) 
stack ends
codesg SEgment
	start:	
		mov ax,data
		mov ds,ax

		mov bx,0
		mov cx,8
		mov ax,0
		s:
			mov dx,ax
			shl ax,1
			shl ax,1	
			shl ax,1
			shl dx,1
			add ax,dx
;乘10

			add al,str[bx]
			adc ah,0
			sub ax,30H		
		
			inc bx 
			loop s
	



		mov ah,4cH
		int 21H
codesg ends
end start



comment *
string str="00000100"
int res=0
for(int i=0;i<8;i++)res=res*10+str[i]-'0';
return res
*comment 




```

#### 5.61十进制转16进制并输出

 ```assembly
assume cs:codesg,ds:data,ss:stack
data segmeNT
	str db '00002333','$'
	res db '0000','$'
data ends
stack segment
	db 100 dup (0) 
stack ends
codesg SEgment
	start:	
		mov ax,data
		mov ds,ax
		mov ax,stack
		mov ss,ax		
		mov sp,10
		mov si,4

		mov bx,0
		mov cx,8
		mov ax,0
		s:
			mov dx,ax
			shl ax,1
			shl ax,1	
			shl ax,1
			shl dx,1
			add ax,dx
;乘10

			add al,str[bx]
			adc ah,0
			sub ax,30H		
		
			inc bx 
			loop s
		
;ax=3039
	
		mov cx,4
		l:
			mov dx,ax
			and dx,0FH
			add dx,30H
			cmp dx,3AH
			jb s1
			add dx,7H
;求出3039的ASCII码，push
		s1:
			dec si
			mov ds:res[si],dl
			shr ax,1
			shr ax,1
			shr ax,1
			shr ax,1
			loop l

		;mov dx,offset res
	 	lea  dx,res
		mov ah,9
		int 21H

		mov ah,4cH
		int 21H
codesg ends
end start



comment *
string str="00000100"
int res=0
for(int i=0;i<8;i++)res=res*10+str[i]-'0';
return res


if (res=0)ans++;

cmp ax,bx
jne s1
inc dx
s1:


if (x==1)res=10
else res =20


mov res,10
cmp x,1
je s1
add res,10
s1:


*comment 






 ```



 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 
