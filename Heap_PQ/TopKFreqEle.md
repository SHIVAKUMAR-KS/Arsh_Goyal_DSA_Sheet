# Examples
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
Example 2:
--------------------
Input: nums = [1], k = 1
Output: [1]
 

```

class Number implements Comparable<Number>{
    int ele;
    int freq;
    Number(int ele,int freq){
        this.ele=ele;
        this.freq=freq;
    }

    public int compareTo(Number that){
        return that.freq-this.freq;
    }
}
class Solution {
    
    public int[] topKFrequent(int[] nums, int k) {
        PriorityQueue<Number> pq=new PriorityQueue<>();
        HashMap<Integer,Integer> map=new HashMap<>();

        for(int ele:nums){
            map.put(ele,map.getOrDefault(ele,0)+1);
        }
        for(Map.Entry<Integer,Integer> entry : map.entrySet()){
            Number number=new Number(entry.getKey(),entry.getValue());
            pq.offer(number);
        }
        int res[]=new int[k];
        int index=0;
        while(index<k){
            res[index]=pq.poll().ele;
            index++;
        }
        return res;
    }
}
```