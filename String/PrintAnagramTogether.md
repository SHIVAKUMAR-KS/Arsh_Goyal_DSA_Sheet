# Examples
Input: arr[] = ["act", "god", "cat", "dog", "tac"]
Output: [["act", "cat", "tac"], ["god", "dog"]]
Explanation: There are 2 groups of anagrams "god", "dog" make group 1. "act", "cat", "tac" make group 2.
Input: arr[] = ["no", "on", "is"]
Output: [["is"],["no", "on"]]
Explanation: There are 2 groups of anagrams "is" makes group 1. "no", "on" make group 2.
Input: arr[] = ["listen", "silent", "enlist", "abc", "cab", "bac", "rat", "tar", "art"]
Output: [["abc", "cab", "bac"],["listen", "silent", "enlist"],["rat", "tar", "art"]]
Explanation: 
Group 1: "abc", "bac", and "cab" are anagrams.
Group 2: "listen", "silent", and "enlist" are anagrams.
Group 3: "rat", "tar", and "art" are anagrams.

```
 Map<String, List<String>> res = new HashMap<>();
        
        // Iterate over the list of strings
        for (String temp : arr) {
            // Convert the string to a char array, sort it, and convert it back to a string
            char[] chars = temp.toCharArray();
            Arrays.sort(chars);
            String sortedTemp = new String(chars);
            
            // Add the original string to the corresponding sorted key in the map
            res.putIfAbsent(sortedTemp, new ArrayList<>());
            res.get(sortedTemp).add(temp);
        }
        
        // Convert the map values to an ArrayList<ArrayList<String>>
        ArrayList<ArrayList<String>> ans = new ArrayList<>();
        for (List<String> group : res.values()) {
            ans.add(new ArrayList<>(group));
        }
        
        return ans;
```