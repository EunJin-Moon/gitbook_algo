# lv2\_전화번호부

 문제는 접두사가 같은지 비교

 contain이 아닌 앞에 있는 문자와 비교 때문에 startWith

{% page-ref page="lv2\_.md" %}



![](../.gitbook/assets/image%20%286%29.png)



```text
	public static boolean solution(String[] phone_book) {
			int len = phone_book.length;
			for (int i = 0; i < len - 1; i++) {
	            String str = phone_book[i];
	            int cnt = 0;
				for(String next : phone_book){
	                if(next.startsWith(str))
	                	cnt++;
	            }
				if(cnt>1)
					return false;
			}
			return true;
	}
```

