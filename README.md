"웹 프로그래밍응용" 시간에 배웠던 내용들을 복습해서 기록할 것이다.

# 1. 자바 연습
이중 for문을 이용해서 별 찍기

(1) / 모양 코드
<pre>
<code>
package chap_01;

public class _03_Variables {
    public static void main(String[] args) {

        for(int i = 0; i < 5; i++){
            for(int j = 0; j < 4 - i; j++){
                System.out.print(" ");
            }
            for(int k = 0; k < i + 1; k++){
                if(k <= 0){
                    System.out.print("*");
                }
                else {
                    System.out.print("\t");
                }
            }
            System.out.println();
        }

    }
}
</code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/d5e3c725-27fc-4e9d-8edf-62a3ca69ceac)

(2) 다이아몬드 모양 코드
<pre>
<code>
package chap_01;

public class _03_Variables {
    public static void main(String[] args) {

        for(int i = 0; i < 4; i++){
            for(int j = 0; j < 3 - i; j++){
                System.out.print(" ");
            }

            for(int k = 0; k < 2 * i + 1; k++){
                System.out.print("*");
            }

            System.out.println();
        }

        for(int q = 0; q < 3; q++){
            for(int w = 0; w < 1 + q; w++){
                System.out.print(" ");
            }

            for(int e = 0; e < 5 - 2 * q; e++ ){
                System.out.print("*");
            }

            System.out.println();
        }

    }
}
    </code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/5fe7262f-c3bd-4554-8b93-864d0ed6ee52)

(3) 이차원 배열 코드
<pre>
<code>
public class Main{
    public static void main(String[] args) {

        String[][] coffees = new String[][] {
                {"coffee", "coffee2", "coffee3"},
                {"coffee", "coffee4", "coffee5"},
                {"coffee", "coffee6", "coffee7"}
        };


        System.out.println(coffees[1][1]);


    }
}
    </code>
</pre>

(4) 이차원 배열 순회 코드
-1-
<pre>
<code>
public class Main{
    public static void main(String[] args) {

        String[][] coffees = new String[][] {
                {"coffee", "coffee2", "coffee3"},
                {"coffee4", "coffee5", "coffee6" },
                {"coffee8", "coffee9", "coffee10"}
        };


        for(int i = 0; i < 3; i++){
            for(int j = 0; j < 3; j++){
                System.out.println(coffees[i][j]);
            }
        }
    }
}
 </code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/e3767b67-c896-4b64-a7b3-a79229ee9b5b)

-2-
<pre>
<code>
public class Main{
    public static void main(String[] args) {

        String[][] coffees = new String[][] {
                {"coffee", "coffee2", "coffee3"},
                {"coffee4", "coffee5", "coffee6" , "coffee7"},
                {"coffee8", "coffee9", "coffee10", "coffee11", "coffee12"},
        };


        for(int i = 0; i < coffees.length; i++){
            for(int j = 0; j < coffees[i].length; j++){
                System.out.println(coffees[i][j]);
            }
        }
    }
}
 </code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/c056ba5b-c0f2-4bd5-bceb-9d841ca3e449)

-3-
<pre>
<code>
public class Main{
    public static void main(String[] args) {


        String[][] seats = new String[10][15];
        String[] eng = {"A","B","C","D","E" ,"F", "G", "H", "I", "J"};

        for(int i=0; i<seats.length; i++){
            for(int j=0; j<seats[i].length; j++){
                seats[i][j] = eng[i] + (j+1);
            }
        }

        for(int i =0; i<seats.length; i++){
            for(int j = 0; j<seats[i].length; j++){
                System.out.print(seats[i][j] + " ");
            }
            System.out.println();
        }
    }
}
 </code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/982b4b25-4021-4403-83f3-9e7d836d4e9e)

(5) 숫자 야구 게임 
옛날에 자바 프로그래밍 시간때 중간고사 대체과제로 내주신 숫자 야구 게임인데 예전에는 엄청 어렵다고 생각했는데 지금은 시간은 꽤 걸리지만 안보고 할 수 있을 정도까지 왔다.
아직 코드가 잘 정리되지 않는 것 같긴 한데 그래도 한게 어디야 후후

<pre>
<code>
import java.util.Random;
import java.util.Scanner;

public class Main {

    public static int rand() {
        Random rand = new Random();
        int ranNum = (int) (Math.random() * 9 + 1);
        return ranNum;
    }

    public static int[] noSame() {
        int num1 = rand();
        int num2 = rand();
        int num3 = rand();
        int[] numArray = new int[3];

        numArray[0] = num1;
        numArray[1] = num2;
        numArray[2] = num3;

        while (true) {
            if (numArray[0] == numArray[1]) {
                numArray[0] = rand();
                numArray[1] = rand();

            }

            if (numArray[1] == numArray[2]) {
                numArray[1] = rand();
                numArray[2] = rand();

            }

            if (numArray[0] == numArray[2]) {
                numArray[0] = rand();
                numArray[2] = rand();

            }
            if ((numArray[0] != numArray[1]) && (numArray[1] != numArray[2]) && (numArray[0] != numArray[2])) {
                break;
            }
        }

        return numArray;
    }

    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);

        int ball = 0;
        int strike = 0;
        int out = 0;
        int count = 0;

        int[] myNum = new int[3];
        int[] comNum = noSame();
        System.out.println("----------------숫자 야구 게임 입니다 --------------");

        while (true) {
            System.out.print("숫자를 입력하세요: ");
            for (int i = 0; i < myNum.length; i++) {
                myNum[i] = scan.nextInt();
            }

            if(myNum[0] == myNum[1] || myNum[0] == myNum[2] || myNum[1] == myNum[2]){
                System.out.println("중복된 숫자를 입력하셨습니다 다시 입력해주세요");
                continue;
            }

            for (int i = 0; i < 3; i++) {
                if (comNum[i] == myNum[i]) {
                    strike++;
                }
            }

            for (int j = 0; j < 3; j++) {
                for (int k = 0; k < 3; k++) {
                    if (j != k && comNum[j] == myNum[k]) {
                        ball++;
                    }
                }
            }

            if (comNum[0] == myNum[0] && comNum[1] == myNum[1] && comNum[2] == myNum[2]) {
                System.out.println(strike + "스트라이크입니다");
                break;
            }
            System.out.println(strike + "스트라이크" + ball + "볼" );
            
            strike = 0;
            ball = 0;
            count++;

        }

        System.out.println("시도 횟수: " + count);
    }
}
</code>
</pre>

결과 화면

![image](https://github.com/user-attachments/assets/6aeb2b80-ea8d-423f-95a8-fcc734029f1c)


