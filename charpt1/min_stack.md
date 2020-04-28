# 155. Min Stack





## 2 解法

### 解法一：

本题的关键在于如何存储最小值。 因为最小值并不是一个，而是一组。每次push、pop都有可能导致当前栈的最小值发生变化。可用另一个栈来存储最小值。

```java
public class MinStack {
	private Stack<Integer> stack;
	private Stack<Integer> minStack;
	public MinStack() {
		stack = new Stack<Integer>();
		minStack = new Stack<Integer>();
	}
	
	public void push(int x) {
		stack.push(x);
		if (minStack.isEmpty() || (x < minStack.peek())) minStack.push(x);
	}
	
	public void pop() {
		if(stack.peek() == minStack.peek()) minStack.pop();
    stack.pop();
	}
	
	public int top() {
		return stack.peek();
	}
	
	public int getMin() {
		return minStack.peek();
	}
}
```



### 解法二：

如果不使用另一个栈来存储最小值序列，可用一个变量存储。但是历史的最小值要压入栈内。



### 解法三： 	

如果不使用java的原生栈，那就要使用单链表来实现stack。链表的结点里面加一个min值，每次push的时候，写入当前最小值到min。

```java
public class MinStack {
	class ListNode{
		int value;
		int min;
		ListNode next;
		ListNode(int val, int min){
			this.value = val;
			this.min = min;
			this.next = null;
		}
	}
	
	private ListNode stack;
	public MinStack() {
	}
	
	public void push(int x) {
		if (this.stack == null) {
			this.stack = new ListNode(x, x);
		}else {
			int min = this.stack.min;
			if (x < min) min = x;
			ListNode tmp = new ListNode(x, min);
			tmp.next = this.stack;
			this.stack = tmp;
		}
	}
	
	public void pop() {
		if (this.stack != null) {
			this.stack = this.stack.next;
		}
	}
	
	public int top() {
		if (this.stack == null)
			return -1;
		else
			return this.stack.value;
	}
	
	public int getMin() {
		if (this.stack == null)
			return -1;
		else
			return this.stack.min;
	}
}
```

