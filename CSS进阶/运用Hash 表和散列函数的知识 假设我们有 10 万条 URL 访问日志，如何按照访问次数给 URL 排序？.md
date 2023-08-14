运用Hash 表和散列函数的知识 假设我们有 10 万条 URL 访问日志，如何按照访问次数给 URL 排序？

sort URLs by access count using hash table and hash function

###### ANSWER | GPT-4 MODEL

我们可以使用哈希表和散列函数来解决这个问题。基本思路是使用哈希表来记录每个URL的访问次数，然后对这个哈希表进行排序来得到访问次数的排名。

以下是步骤：

1. 创建一个哈希表，键是URL，值是对应的访问次数。遍历URL访问日志，每遇到一个URL，就将其对应的访问次数加1。

```
const urlMap = new Map();
logs.forEach(url => {
  if (urlMap.has(url)) {
    urlMap.set(url, urlMap.get(url) + 1);
  } else {
    urlMap.set(url, 1);
  }
});
```

1. 将哈希表转换为数组，数组的每个元素是一个包含URL和对应访问次数的数组。然后使用数组的sort方法，按照访问次数进行排序。

```
const urlArray = Array.from(urlMap);
urlArray.sort((a, b) => b[1] - a[1]);
```

这样，urlArray就是一个已经按照访问次数从大到小排序的数组，数组的每个元素是一个包含URL和对应访问次数的数组。

注意，这个方法的时间复杂度是O(n log n)，其中n是URL的数量。因为哈希表的插入和查找操作的时间复杂度都是O(1)，但是排序操作的时间复杂度是O(n log n)。所以，如果URL的数量非常大，这个方法可能会比较慢。