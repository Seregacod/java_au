# Stream

+ [Top K Frequent Words](#top-k-frequent-words)
<!---->

## Top K Frequent Words

https://leetcode.com/problems/top-k-frequent-words/

```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
                 return Arrays.stream(words)
                    .collect(Collectors.toMap(Function.identity(), v -> 1, Integer::sum))
					.entrySet()
                    .stream()
                    .sorted((Comparator.comparingInt(Map.Entry<String, Integer>::getValue)
						.reversed())
						.thenComparing(Map.Entry<String, Integer>::getKey))
                    .map(Map.Entry<String, Integer>::getKey)
                    .limit(k)
                    .collect(Collectors.toList());   
    }
}
```
