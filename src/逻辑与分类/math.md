1. 概率
	条件概率：P(AB)=P(A)P(B|A)=P(B)P(A|B)  （即事件A和事件B同时发生的概率等于在发生A的条件下B发生的概率乘以A的概率）
	推导出贝叶斯公式：P(B|A)=P(A|B)P(B)/P(A)
	全概率公式：P(A)=P(PAB1)+P(AB2)+....=P(A|B1)P(B1)+P(A|B2)P(B2)+..P(A|Bn)P(Bn),假设B是由相互独立的事件组成的概率空间{B1,b2，...bn}
	P(A|Bn)P(Bn)称为先验概率
	根据贝叶斯公式可推导：
	后验概率P(Bi|A)=P(A|Bi)P(Bi)/P(A)=P(A|Bi)P(Bi)/(P(A|B1)P(B1)+P(A|B2)P(B2)+..P(A|Bn)P(Bn))
	
![[Pasted image 20230828143600.png]]

2. 欧拉函数
	任意给定正整数n，小于等于n的正整数之中，有多少个与n构成互质关系=φ(n)