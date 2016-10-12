title: '欧几里得算法'
date: 2016-10-11 17:23:00
tags: ['算法', '欧几里得']
---

欧几里得算法，又称碾转相除法，是数论中的一项基本技术，欧几里得算法提出至今已经2000多年，它通过一个简单的过程来确定两个整数的最大公因子GCD(greatest common divisor)。

## 1. 欧几里得算法
#### 1.1 定义
在定义欧几里得算法之前，先定义一些基本概念。

>**因子**：设a,b是整数，若存在整数d使得b=ad，则称a是b的一个因子，也成a整除b或称b是a的倍数，记为 a|b
>**最大公因子**：若整数c满足c|a,c|b，则称c为整数a和b的公因子。a和b的最大公因子记为gcb(a,b)
>**欧几里得算法**：要计算两个整数a和b的最大公因子，令<code>r<sub>0</sub>=a</code>,<code>r<sub>1</sub>=b</code>，然后计算相继的商和余数
><div class="row"><div class="col s12 center"><span class="flow-text teal-text text-darken-2">r<sub>i</sub>=q<sub>i+1</sub> * r<sub>i+1</sub> + r<sub>i+2</sub> (i=0,1,2,3...)</span></div></div>
><p style="text-align:right">引用来源：[http://m.blog.csdn.net/article/details?id=8393110](http://m.blog.csdn.net/article/details?id=8393110 'http://m.blog.csdn.net/article/details?id=8393110')</p>

#### 1.2 算法描述
欧几里得算法（Euclid Algorithm）输入两个非负的整数a和b，输出a和b的最大公因子：

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>欧几里得算法</title>
	</head>
	<body>
		<label>第一个数：</label>
		<input type="text" id="r0"><br>
		<label>第二个数：</label>
		<input type="text" id="r1"><br>
		<button id="count">计算最大公因子</button><br>
		<input type="text" disabled="disabled" id="result">
		<script>
			var countBtn = document.getElementById('count')
			countBtn.onclick = function() {
				var r0 = document.getElementById('r0').value
				var r1 = document.getElementById('r1').value
				var result = document.getElementById('result')
				console.log(r0, r1)
				euclid(+r0, +r1, result)
			}
			function euclid(r0, r1, result) {
				if(r1 > 0) {
					euclid(r1, r0 % r1, result)
				} else {
					result.value = r0
				}
			}
		</script>
	</body>
	</html>
