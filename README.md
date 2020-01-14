# Evaluate Reverse Polish Notation 
## https://leetcode.com/problems/evaluate-reverse-polish-notation


## Implementation :

```java
  public static int evalRPN(String[] tokens) {
      Stack<Integer> st = new  Stack<>();
      for(String s : tokens){
        if(isOperator(s)){
         int rightOperand = st.pop();
         int leftOperand = st.pop();
         st.push(evaluate(leftOperand, rightOperand, s));
        } else{
          st.push(Integer.parseInt(s));
        }
      }
      return st.pop();
  }

  private static boolean isOperator(String token) {
    if (token.equals("+") || token.equals("-") || token.equals("*") 
        || token.equals("/")) {
      return true;
    }
    return false;
  }

  private static int evaluate(int left, int right , String operator){
    int result = 0;
    switch(operator){
        case "+" : result = left + right; break;
        case "-" : result = left - right; break;
        case "*" : result = left * right; break;
        case "/" : result = left / right; break;
    }
    return result;
  }
```
