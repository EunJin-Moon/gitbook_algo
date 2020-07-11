# 주사위굴리기

```text
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_14499_주사위굴리기 {
	static int[][] dxy = { {}, { 0, 1 }, { 0, -1 }, { -1, 0 }, { 1, 0 } }; // 동서북남

	static class Dice {
		int top, bottom, west, east, south, north;

		public Dice() {
			this.top = 0;
			this.bottom = 0;
			this.west = 0;
			this.east = 0;
			this.south = 0;
			this.north = 0;
		}

		public void moveEast() {
			int temp = top;
			top = west;
			west = bottom;
			bottom = east;
			east = temp;
		}

		public void moveWest() {
			int temp = top;
			top = east;
			east = bottom;
			bottom = west;
			west = temp;
		}

		public void moveNorth() {
			int temp = top;
			top = south;
			south = bottom;
			bottom = north;
			north = temp;
		}

		public void moveSouth() {
			int temp = top;
			top = north;
			north = bottom;
			bottom = south;
			south = temp;
		}

	}

	static int N, M, K;

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		int x = Integer.parseInt(st.nextToken());
		int y = Integer.parseInt(st.nextToken());
		K = Integer.parseInt(st.nextToken());

		int[][] map = new int[N][M];
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < M; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		int[] order = new int[K];
		st = new StringTokenizer(br.readLine());
		for (int k = 0; k < K; k++) {
			order[k] = Integer.parseInt(st.nextToken());
		}
		solve(map, order, x, y);

	}

	static void solve(int[][] map, int[] order, int x, int y) {
		Dice dice = new Dice();

		int nx, ny;

		for (int i = 0; i < K; i++) {
			nx = x + dxy[order[i]][0];
			ny = y + dxy[order[i]][1];

			if (nx < 0 || nx >= N || ny < 0 || ny >= M)
				continue;
			// 동 서 북 남
			if (order[i] == 1) {
				dice.moveEast();
			} else if (order[i] == 2) {
				dice.moveWest();
			} else if (order[i] == 3)
				dice.moveNorth();
			else if (order[i] == 4)
				dice.moveSouth();

			// 숫자복사
			if (map[nx][ny] == 0)
				map[nx][ny] = dice.bottom;
			else {
				dice.bottom = map[nx][ny];
				map[nx][ny] = 0;
			}

			System.out.println(dice.top);
			x = nx;
			y = ny;
		}

	}

}

```

