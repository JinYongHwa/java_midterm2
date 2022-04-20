# 중간고사 시험문제

> 은행에 다니는 진용화는 자신의 업무를 전산화시키기위해 다음을 만족시키는 프로그램을 JAVA로 만들고자한다

```
사용자로부터 계좌번호를 입력받는다 
계좌번호가 1로 시작하면 '적금계좌' 이고,
계좌번호가 1로 시작하지 않으면 '보통예금계좌' 이다


계좌의 공통조건
모든 계좌는 계좌의 잔액이상 출금이 불가능하다 (10점)
모든 계좌는 계좌 생성시 잔액이 0원으로 만들어진다 (10점)
모든 계좌는 입금액에 제한이 없으며 소숫점단위로는 입금이 불가능하다 (10점)

보통예금계좌 조건
'보통예금계좌'는 입금할때마다 이자를 1%를 추가해 준다 ( 10,000원 입금시 잔액은 10,100원이 추가됨) (20점)
'보통예금계좌'는 입금 및 출금이 자유롭다 (공통조건을 만족하는한) (10점)

적금계좌 조건
'적금계좌'는 입금할때마다 이자를 7%를 추가해 준다 ( 10,000원 입금시 잔액은 10,700원이 추가됨) (20점)
'적금계좌'는 200만원 이상 잔액이 있어야만 출금이 가능하다 (20점)
```

### 위의 조건을 만족시키는 Main 클래스를 작성하였다
### 아래의 세개의 클래스를 완성하여 E-Class에 업로드하세요
```
Account - 계좌 Class
NormalAccount - 보통예금계좌 Class
SavingAccount - 적금계좌 class
```


``` java

import java.util.Scanner;

public class Main {
	
	public static void main(String[] args) {
		Scanner scanner=new Scanner(System.in);
		System.out.println("계좌번호를 입력해주세요");
		String accountNumber=scanner.next();		//계좌번호 입력받기
		Account account;
		if(accountNumber.startsWith("1")) {		//계좌번호가 '1'로 시작하면 적금계좌
			//계좌 생성시에 계좌번호를 넣어서 생성
			account=new SavingAccount(accountNumber);	
		}
		else {	//계좌번호가 '1'로 시작하지 않으면 '보통예금계좌' 이다
			//계좌 생성시에 계좌번호를 넣어서 생성
			account=new NormalAccount(accountNumber); 
		}
		
		while(true) {
			try {
				System.out.println("입금 또는 출금할 금액을 입력해주세요 0을 입력하면 프로그램이 종료됩니다");
				int balance=scanner.nextInt();	//사용자로부터 입금 또는 출금액 입력받기
				if(balance>0) {	//0보다 클경우 입금
					account.deposit(balance);
				}
				else if(balance<0) {	//0보다 작을경우 출금
					account.withdraw(Math.abs(balance));
				}
				else {		//0을 입력받을경우 프로그램이 종료됨
					break;
				}
				account.printAccount();	//입금 또는 출금후 계좌번호와 잔액을 출력
			}catch(Exception e) {

			}
		}
		
	}
}
```

### 실행예시
#### 적금계좌일때
![image](https://user-images.githubusercontent.com/21700482/164146268-6c39ecde-89cd-4b9b-8dc1-b0392c99f7d1.png)


#### 보통예금계좌일때
![image](https://user-images.githubusercontent.com/21700482/164146157-29dd5c84-3799-440f-84f5-158f8abfacbd.png)

