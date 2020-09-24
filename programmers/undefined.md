# 삼각달팽이



while문활용하

answer의 길이-&gt; 재귀



{% page-ref page="undefined.md" %}

![](../.gitbook/assets/image%20%283%29.png)



```text
import java.util.Arrays;

public class 삼각달팽이 {

	public static void main(String[] args) {

		System.out.println(Arrays.toString(solution(4)));
		 System.out.println(Arrays.toString(solution(5)));
		 System.out.println(Arrays.toString(solution(6)));
		 
//		 [1,2,9,3,10,8,4,5,6,7]
//		[1,2,12,3,13,11,4,14,15,10,5,6,7,8,9]
//		[1,2,15,3,16,14,4,17,21,13,5,18,19,20,12,6,7,8,9,10,11]

	}
	

	public static int[] solution(int n) {
		int N = isLen(n);
		int[] answer = new int[N];

		int[][] map = new int[n][n];
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				map[i][j] = -1;
			}
		}
		int i = 0, j = 0, num = 1;

		map[i][j] = num;
		while (num < N) {
			while (i + 1 < n && num < N && map[i + 1][j] < 0) {
				map[++i][j] = ++num;
			}
			while (j + 1 < n && num < N && map[i][j + 1] < 0) {
				map[i][++j] = ++num;
			}
			while (i - 1 > 0 && j - 1 > 0 && num < N && map[i - 1][j - 1] < 0) {
				map[--i][--j] = ++num;
			}
		}

		for (int[] m : map)
			System.out.println(Arrays.toString(m));
		int idx = 0;
		for (i = 0; i < n; i++) {
			for (j = 0; j < n; j++) {
				if (map[i][j] > 0) {
					answer[idx] = map[i][j];
					idx++;
				}
			}
		}
		return answer;
	}

	private static int isLen(int n) {
		if (n == 1)
			return 1;
		return n + isLen(n - 1);
	}

}

```

