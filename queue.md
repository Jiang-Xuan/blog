title: '队列的介绍'
date: 2016-10-11 10:44:00
tags: ['队列', '数据结构']
---

## 队列和栈非常相似，但是使用了不同的规则，而非后进先出
队列是遵循<span class="grey-text">FIFO</span>（First In First Out，先进先出，也称之为先来先服务）。队列在尾部添加新元素，并从顶部移除元素。最新添加的元素必须排在队列的末尾。常见的例子就是排队。
### 创建队列
我们需要创建自己的类来表示一个队列。先从最基本的声明类开始：
<pre><code>	function Queue() {
		//这里是属性和方法
	}
</code></pre>
首先需要一个用于存储队列中元素的数据结构。我们可以使用数组，就像在上一章Stack类中那样使用（你会发现Queue类和Stack类非常相似，只是添加和移除元素的规则不同）：
<pre><code>var items = [];</code></pre>
接下来需要声明一些队列可用的方法。
 
- **enqueue(element(s))**：向队列尾部添加一个（或多个）新的项。
- **dequeue()**：移除队列的第一（即排在队列最前面）项，并返回被移除的元素。
- **front()**：返回队列中的第一个元素——最先被添加，也就是最先被移除的元素。队列不做任何变动（不移除元素，只返回元素信息——与Stack类的peek方法发非常相似）。
- **isEmpty()**：如果队列不包含任何元素，返回true，否则返回false。
- **size()**：返回队列包含的元素的个数，与数组的length非常相似。
 
首先要实现的是enqueue方法。这个方法负责向队列添加新元素。这里有一个非常重要的细节，新的项只能添加到队列末尾：

	this.enqueue = function(element) {
		items.push(element);
	}

既然我们使用数组来存储队列的元素，就可以用JavaScript的array类的push方法。

接下来要实现dequeue方法。这个方法负责从队列移除项。由于队列遵循先进先出原则，最先添加的项也是最先被移除的。可以用JavaScript的array类的shift方法。shift方法会从数组中移除存储在索引0（第一个位置）的元素：

	this.dequeue = function() {
		return items.shift()
	}

只有enqueue方法和dequeue方法可以添加和移除元素，这样就保证了Queue类遵循先进先出原则。
现在来为我们的类实现一些额外的辅助方法。如果想知道队列最前面的项是什么，可以使用front方法。这个方法会返回队列的最前面的项（数组的索引为0）：

	this.front = function() {
		return items[0];
	}

下一个是isEmpty方法。如果队列为空，它会返回true，否则返回false（注意这个方法和Stack类里面的一样）：

	this.isEmpty = function() {
		return items.length === 0;
	}

对于isEmpty方法，可以简单的验证内部数组的length是否为0.

我们也可以为Queue类实现类似于array类的length属性的方法。size方法也跟Stack类里面的一样：

	this.size = function() {
		return items.length;
	}

完成！我们的Queue类就实现好了。也可以像Stack类一样增加一个print方法：

	this.print = function() {
		console.log(items.toString());
	}

## 完整的Queue类

	function Queue() {
		var items = [];

		this.enqueue = function(element) {
			items.push(element);
		}
		this.dequeue = function() {
			return items.shit();
		}
		this.front = function() {
			return items[0];
		}
		this.isEmpty = function() {
			return items.length === 0;
		}
		this.size = function() {
			return items.length;
		}
		this.print = function() {
			console.log(items.toString());
		}
	}