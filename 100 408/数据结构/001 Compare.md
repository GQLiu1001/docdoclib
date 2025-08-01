# Comparable接口

Java 的 `Comparable<T>` 接口是用来 **定义对象之间的自然顺序** 的，也就是说，如果你希望你的类对象可以比较大小、进行排序（比如放到 `TreeSet`、`PriorityQueue`、`Collections.sort()` 里），你就可以让你的类实现 `Comparable<T>` 接口。

需要让想要定义排序的类 implements Comparable<类名> 然后实现抽象方法：
```java
    @Override
    public int compareTo(Person other) {
        return this.age - other.age; // 按年龄升序（小顶堆）
    }

	@Override
	public int compareTo(Person other) {
    return other.age - this.age; // 年龄降序（大顶堆）
	}
```
# Comparator接口

`Comparator` 是 **外部比较器**，可以给不同的排序方式，**输入两个对象进行比较**，不要求类本身实现 `compareTo()`。

```java
	//小顶堆 / 小的在前
	Comparator<Integer> asc = (a, b) -> a - b;
	//大顶堆 / 大的在前
	Comparator<Integer> desc = (a, b) -> b - a;
```

**PS：按输入顺序排列(this在前 && o1在前) 小顶堆 升序！**

| 特性   | `Comparable<T>`（内部自然排序）           | `Comparator<T>`（外部定制排序）   |
| ---- | --------------------------------- | ------------------------- |
| 方法名  | `int compareTo(T o)`              | `int compare(T o1, T o2)` |
| 方法位置 | 类本身实现                             | 排序时额外传入                   |
| 对象数量 | 单对象调用                             | 比较两个对象                    |
| 排序种类 | 唯一“自然顺序”                          | 可定制多种排序方式                 |
| 用途   | 实现类可直接排序（如 TreeSet、PriorityQueue） | 对已有类提供不同排序逻辑              |
| 常用场景 | 类自身能定义排序                          | 不想/不能改类；需要多种排序方式          |
# lambda 快速实现排序
```java
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
	    return merge;
    }
```