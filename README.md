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








