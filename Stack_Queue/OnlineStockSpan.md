# Examples
Input
["StockSpanner", "next", "next", "next", "next", "next", "next", "next"]
[[], [100], [80], [60], [70], [60], [75], [85]]
Output
[null, 1, 1, 1, 2, 1, 4, 6]

Explanation
StockSpanner stockSpanner = new StockSpanner();
stockSpanner.next(100); // return 1
stockSpanner.next(80);  // return 1
stockSpanner.next(60);  // return 1
stockSpanner.next(70);  // return 2
stockSpanner.next(60);  // return 1
stockSpanner.next(75);  // return 4, because the last 4 prices (including today's price of 75) were less than or equal to today's price.
stockSpanner.next(85);  // return 6

----------------------------------------------------------------
# Explanation
isme check karna h ki ,array me agar decrement ho rha h toh bas 1 ans hoga aur koi element increment aaya toh count return kar do jaha se initial increment ho rha

```
class StockSpanner {

    int count=-1;
    Stack<Integer> st;
    ArrayList<Integer> res;
    public StockSpanner() {
        st=new Stack<>();
        res=new ArrayList<>();
        
    }
    
    public int next(int price) {
        while(!st.isEmpty() && res.get(st.peek())<=price){
            st.pop();
        }
        count++;
        int ans=count+1;
        if(!st.isEmpty()){
            ans=count-st.peek();
        }
        res.add(price);
        st.add(count);

        return ans;
    }
}

```