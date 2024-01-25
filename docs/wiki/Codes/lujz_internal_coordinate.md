---
title: 批量计算二面角/键角/键长代码的使用
author: Jingze Lu
comments: true
tags:
  - Python
  - Numpy
  - Shared Code
---

## 1. 代码简介

代码定义了一个Atom类，在类的实例化时传入原子编号。调用`cal()`函数可以根据原子编号的数量，批量计算二面角/键角/键长。`cal()`默认计算脚本目录下所有的 **Gaussian** 输出文件（.log），如果需要计算特定的文件，请在`cal()`传入文件名。

## 2. 使用示例
将 .py 文件和存有原子数据的 .log 文本放在同一目录下。

### 2.1 二面角的计算

​	在类的实例化时，传入四个参数。注意中间两个原子为面的交线。

```python
import math
import os
import numpy as np

a = Atom(9, 8, 13, 14)  # 实例化
a1 = a.cal()
""" >>>
文件10.log中，(9, 8, 13, 14)号原子形成的二面角是：180.00
文件11.log中，(9, 8, 13, 14)号原子形成的二面角是：170.00
文件14.log中，(9, 8, 13, 14)号原子形成的二面角是：140.00
文件16.log中，(9, 8, 13, 14)号原子形成的二面角是：120.00
文件19.log中，(9, 8, 13, 14)号原子形成的二面角是：100.00
"""

```

计算特定某几个文件：

```python
a = Atom(9, 8, 13, 14)  # 实例化
a1 = a.cal('10.log','11.log')
""" >>>
文件10.log中，(9, 8, 13, 14)号原子形成的二面角是：180.00
文件11.log中，(9, 8, 13, 14)号原子形成的二面角是：170.00
"""
```

控制保留小数位数，使用 `decimal` 参数（默认保留两位小数）：

```python
a = Atom(9, 8, 13, 14)  # 实例化
a1 = a.cal('10.log', decimal=5)
""" >>>
文件10.log中，(9, 8, 13, 14)号原子形成的二面角是：179.99520
"""
```

### 2.2 键角的计算

只需要在类的实例化时传入三个参数即可，**注意第二个原子为顶角**。

```python
a = Atom(9, 8, 13)  # 实例化
a1 = a.cal('10.log', decimal=5)
""" >>>
文件10.log中，(9, 8, 13)号原子形成的键角是：27.06505
"""
```

### 2.3 键长的计算

同理，在类的实例化时传入两个参数。


## 3. 可能出现的问题

**1 结果得出的二面角与我想要的二面角互补？**

注意实例化时四个原子编号的顺序。对于（1，2，3，4）中，求的是123平面和234平面的二面角。

**2 如何把结果导入到 csv 或其他文本中？**

还未完成，自己写一个脚本去吧。



## 4. 源码

```python
#!/usr/bin/python3
import math
import os
import numpy as np


class Atom:
	"""可以用来批量计算.log文件中的键长、键角和二面角"""
	def __init__(self, *atom):
		self.matrix = None
		self.atom = atom

	def get_coor_data(self, file_name):
		"""从.log文件中获取原子坐标"""
		with open(file_name) as f:
			lines = f.readlines()
			for i, line in enumerate(lines):
				if line.startswith(' NAtoms='):
					natoms = int(line.split()[1])  # 定位
				elif 'Standard orientation' in line:
					geom = [row.split()[-3:] for row in lines[i + 5:i + 5 + natoms]]  # 以空格为区分，按列切
					geom = [[float(item) for item in sublist] for sublist in geom]
		return geom

	def cal(self, *file_name, decimal=2):
		"""接收参数，把计算结果输出到屏幕上。"""
		dic = dict(zip([2, 3, 4], ['键长', '键角', '二面角']))  # 建立对应关系
		if not len(self.atom) in [2, 3, 4]:
			print('原子数不对哦')
			exit(0)
		for file in file_name if len(file_name) != 0 else os.listdir():
			if file.endswith('.log'):
				print(f'文件{file}中，{self.atom}号原子形成的{dic[len(self.atom)]}是：', end='')
				print(f'%.{decimal}f' % self.calculate(file))

	def calculate(self, file_name):
		"""根据原子坐标数，判断计算键长、键角或二面角"""
		self.matrix = self.get_coor_data(f'{file_name}')
		theta = (self.calculate_bond_length() if len(self.atom) == 2 else
		         self.calculate_bond_angle() if len(self.atom) == 3 else
		         self.calculate_dihedral_angle() if len(self.atom) == 4 else
		         float('inf'))
		return theta

	def calculate_bond_length(self):
		"""计算两点间的长度"""
		p1, p2 = [self.matrix[i - 1] for i in self.atom]
		v1 = (p2[0] - p1[0], p2[1] - p1[1], p2[2] - p1[2])
		return np.linalg.norm(v1)

	def calculate_bond_angle(self) -> float:
		"""计算三个点形成的角，p2是顶点"""
		p1, p2, p3 = [self.matrix[i - 1] for i in self.atom]
		v1 = (p2[0] - p1[0], p2[1] - p1[1], p2[2] - p1[2])
		v2 = (p3[0] - p1[0], p3[1] - p1[1], p3[2] - p1[2])
		dot_product = np.dot(v1, v2)
		norm_n1 = np.linalg.norm(v1)
		norm_n2 = np.linalg.norm(v2)
		theta = np.arccos(dot_product / (norm_n1 * norm_n2))
		return math.degrees(theta)

	def calculate_dihedral_angle(self) -> float:
		"""计算四个点的二面角，返回角度，p2p3是两面的交线"""
		p1, p2, p3, p4 = [self.matrix[i - 1] for i in self.atom]

		def calculate_norm_vectors(p1, p2, p3):
			"""计算三个点所成平面的法向量"""
			v1 = (p2[0] - p1[0], p2[1] - p1[1], p2[2] - p1[2])
			v2 = (p3[0] - p1[0], p3[1] - p1[1], p3[2] - p1[2])
			v = np.cross(np.array(v1), np.array(v2))
			return v

		n1 = calculate_norm_vectors(p1, p2, p3)
		n2 = calculate_norm_vectors(p2, p3, p4)
		dot_product = np.dot(n1, n2)
		norm_n1 = np.linalg.norm(n1)
		norm_n2 = np.linalg.norm(n2)
		theta = np.arccos(dot_product / (norm_n1 * norm_n2))
		return math.degrees(theta)
# 使用示例
if __name__ == '__main__':
	a = Atom(9, 8, 13, 14)
	a1 = a.cal()
```

