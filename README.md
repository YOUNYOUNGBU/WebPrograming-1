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
