# timu1
import numpy as np
from numpy import *
x=int(input("请输入矩阵维度n:"))
list=[]
for n in range(x):
    n=input()
    x_lst = n.split(' ')
    x_lst = [int(x_lst[i]) for i in range(len(x_lst))]
    list.append(x_lst)
x=np.array(list)
try:
    B=np.linalg.inv(x)
except:
    print("矩阵不存在逆矩阵")
else:
    print(B)



    题目二
    #include
#include<math.h>
using namespace std;
class Matrix
{
private:
double data[10][20];
int size;
static int times;
public:
void qiuNi();
void setSize();
void show();
void chuShi();
};
int Matrix::times = 1;
void Matrix::setSize()
{
int n;
cin >> n;
size = n;
}
void Matrix::show()
{
cout << “(” << times << “)” << endl;
times++;
int i, j;
for (i = 0; i<size; i++)
{
for (j = 0; j<2 * size; j++)
{
cout.width(10);
cout.flags(ios::right);
cout << data[i][j] << " ";
}
cout << endl;
}
cout << “***********************************************” << endl;
cout << endl;
}
void Matrix::chuShi()
{
int i, j;
data[10][20] = { 0 };
for (i = 0; i<size; i++)
{
for (j = 0; j<2 * size; j++)
{
if (j<size)
{
cin >> data[i][j];
}
else if (j == i + size)
data[i][j] = 1.0;
else
data[i][j] = 0.0;
}
}
cout << “开始求逆:” << endl;
show();
}
void Matrix::qiuNi()
{
int i, j, k;
int maxI = 0;
for (i = 1; i<size; i++)
{
if (fabs(data[maxI][0])<fabs(data[i][0]))
maxI = i;
}
if (maxI != 0)
{
double temp;
for (j = 0; j<2 * size; j++)
{
temp = data[0][j];
data[0][j] = data[maxI][j];
data[maxI][j] = temp;
}
}
double temp2;
for (i = 0; i<size; i++)
{
if (data[i][i] != 0)
temp2 = 1.0 / data[i][i];
else
{
cout << “此矩阵无逆矩阵!” << endl;
return;
}
for (j = 0; j<2 * size; j++)
data[i][j] = temp2;
for (j = 0; j<size; j++)
{
if (j != i)
{
double temp3 = data[j][i];
for (k = 0; k<2 * size; k++)
data[j][k] -= temp3data[i][k];
}
}
}
show();
}
int main()
{
Matrix a;
a.setSize();
a.chuShi();
a.qiuNi();
return 0;
}



题目三
with open("input.txt","r") as file_object:
    key=20237842						  
message=file_object.read()			  
ml=len(message)					  
kl=len(key)
key=ml//kl*key+key[:ml%kl]		  
pwd=[]						      
for i in range(len(key)):
	pwd.append(chr(ord(key[i])^ord(message[i]))) 
print(''.join(pwd))



题目四
#include <bits/stdc++.h>       
using namespace std;
int main()
{
    char s[100];
    cin>>s;
    int t=0;
    int n=strlen(s);
    for (int i=0;i<n;i++)
    if(s[i]=='.'||s[i]=='/'||s[i]=='%') t=i;
    if (t==0)
    {
        reverse(s,s+n);
        int j=0;
        while (s[j]=='0') ++j;
        if (j==n) cout<<"0";
        else cout<<s+j;
    }
    else if (t==n-1)
    {
        reverse(s,s+n-1);
        int j=0;
        while (s[j]=='0') ++j;
        if (j==n-1) cout<<"0%";
        else cout<<s+j;
    }
    else if (s[t]=='/')
    {
        reverse(s,s+t);
        int j=0;
        while (s[j]=='0') ++j;
        if (j==t) cout<<"0/";
        else
        {
            for (int i=j;i<=t;i++) cout<<s[i];
        }
        reverse(s+t+1,s+n);
        j=t+1;
        while(s[j]=='0') ++j;
        cout<<s+j;
    }
    else
    {
        reverse(s,s+t);
        int j=0;
        while (s[j]=='0') ++j;
        if (j==t) cout<<"0.";
        else 
        {
            for (int i=j;i<=t;i++) cout<<s[i];
        }
        reverse(s+t+1,s+n);
        j=t+1;
        while (s[j]=='0'&&j<n) ++j;
        int k=n-1;
        while (s[k]=='0'&&k>t) --k;
        if (j>k) cout<<'0';
        else 
       {
            for (int i=j;i<=k;i++) cout<<s[i];
        }
    }
    return 0;
}



题目五
#include <iostream>
#include <cmath> // 用于sqrt函数计算模长

class Vector {
private:
    double x;
    double y;

public:
    // 构造函数
    Vector(double x_val, double y_val) : x(x_val), y(y_val) {}

    // 向量相加方法
    Vector add(const Vector& other) const {
        return Vector(x + other.x, y + other.y);
    }

    // 打印向量分量方法
    void print() const {
        std::cout << "(" << x << ", " << y << ")" << std::endl;
    }

    // 计算并打印向量模长方法
    void dir() const {
        double magnitude = std::sqrt(x * x + y * y);
        std::cout << "Magnitude: " << magnitude << std::endl;
    }
};

int main() {
    // 创建两个向量
    Vector v1(3.0, 4.0);
    Vector v2(1.0, 2.0);

    // 打印向量
    std::cout << "Vector v1: ";
    v1.print();

    std::cout << "Vector v2: ";
    v2.print();

    // 向量相加
    Vector v3 = v1.add(v2);

    // 打印相加后的向量
    std::cout << "Vector v3 (v1 + v2): ";
    v3.print();

    // 计算并打印相加后向量的模长
    std::cout << "Magnitude of v3: ";
    v3.dir();

    return 0;
}



题目六
import socket
import math
server=socket.socket()
server.connect(("localhost", 12345))
while True:
    
    recv_data = server.recv(1024).decode("UTF-8") 

    squared1=math.pow(a);
    squared2=math.pow(b);
    NN=math.sqrt(squared1+squared2);
    hylength=NN
  
    send_msg = hylength
    server.send(send_msg.encode("UTF-8"))

