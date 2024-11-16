# Examples
Input
["MyStack", "push", "push", "top", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 2, 2, false]

Explanation
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top(); // return 2
myStack.pop(); // return 2
myStack.empty(); // return False
 

```
class MyStack {
    private Queue<Integer> main;
    private Queue<Integer> helper;

    public MyStack() {

        main =new LinkedList<>();
        helper=new LinkedList<>();
        
    }
    
    public void push(int x) {
        while(main.size()>0){
            helper.add(main.remove());
        }
        main.add(x);

        while(helper.size() > 0){
            main.add(helper.remove());
        }
        
    }
    
    public int pop() {
        return main.remove();
        
    }
    
    public int top() {
        return main.peek();
    }
    
    public boolean empty() {

        if(main.size() ==0){
            return true;
        }else{
            return false;
        }
        
    }
}
```
