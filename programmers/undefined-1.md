# 괄호변환

 문제글 그대로 구현하는 문

{% page-ref page="undefined-1.md" %}

```text
class Solution {
    public String solution(String p) {
        String answer = "";
        answer = solve(p);
        return answer;
    }
    static String solve(String w){
        if(w.equals(""))
            return "";
        int i=0;
        int left=0;
        int right=0;
        for(i=0;i<w.length();i++){
            if(w.charAt(i)=='(')
                left++;
            else
                right++;
            if(left == right)
                break;
        }
        String u = w.substring(0,i+1);
        String v = w.substring(i+1);
        // System.out.println(u+":"+v);
        //올바른 괄호라면 v를 다시 재귀 
        if(isRight(u)){
            return u+solve(v);
        }else{
            String tmp = "("+solve(v)+")";
            //앞뒤 제거 
            u = u.substring(1,u.length()-1);
            u = reverse(u);
            return tmp+u;
        }
        
    }
    static boolean isRight(String w){
        int count = 0;
        for(int i=0;i<w.length();i++){
            if(w.charAt(i)=='('){
                count++;
            }else
                count--;
            if(count<0)
                return false;
        }
        return count==0;
        
    }
    static String reverse(String u) {
		StringBuffer sb = new StringBuffer();
		for(int i=0;i<u.length();i++) {
			if(u.charAt(i)=='(')
				sb.append(')');
			else
				sb.append('(');
		}
		return sb.toString();
	}
}
```





