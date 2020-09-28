# lv3\_정수삼각형

 동적계획법

{% page-ref page="lv3\_.md" %}

![](../.gitbook/assets/image%20%286%29.png)









 solution  -&gt; 입력받은 행에 하기,

 solution2 -&gt; copy배열 만들어서하기 



```text
import java.util.Arrays;

public class 정수삼각형 {

	public static void main(String[] args) {

		System.out.println(solution(new int[][] { { 7 }, { 3, 8 }, { 8, 1, 0 }, { 2, 7, 4, 4 }, { 4, 5, 2, 6, 5 } }));

	}

	public static int solution(int[][] triangle) {
		int answer = 0;

		for (int i = 1; i < triangle.length; i++) {
			triangle[i][0] += triangle[i - 1][0];
			triangle[i][i] += triangle[i - 1][i - 1];
			for (int j = 1; j < i; j++) {
				triangle[i][j] += Math.max(triangle[i - 1][j - 1], triangle[i - 1][j]);
			}
		}
		for (int i = 0; i < triangle.length; i++) {
			answer = Math.max(answer, triangle[triangle.length - 1][i]);
		}
		return answer;
	}

	public static int solution2(int[][] triangle) {
		int answer = 0;
		int n = triangle.length;
		int copy[][] = new int[n][n];

		copy[0][0] = triangle[0][0];

		for (int i = 1; i < n; i++) {
			copy[i][0] = copy[i - 1][0] + triangle[i][0];
			copy[i][i] = copy[i - 1][i - 1] + triangle[i][i];
		}
		// for (int[] a : copy)
		// System.out.println(Arrays.toString(a));

		for (int i = 2; i < n; i++) {
			for (int j = 1; j < i; j++) {
				copy[i][j] = Math.max(copy[i - 1][j - 1], copy[i - 1][j]) + triangle[i][j];
			}
		}

		for (int i = 0; i < n; i++) {
			answer = Math.max(answer, copy[n - 1][i]);
		}

		return answer;
	}

}

```

