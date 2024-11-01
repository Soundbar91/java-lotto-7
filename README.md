# java-lotto-precourse
## 프로젝트 소개
- 간단한 로또 발매기 프로그램이다.
- 사용자가 로또를 구입하고, 구매한 로또 대비 수익률을 출력하는 프로그램이다. 

## 학습 목표
- 관련 함수를 묶어 클래스를 만들고, 객체들이 협력하여 하나의 큰 기능을 수행하도록 한다.
- 클래스와 함수에 대한 단위 테스트를 통해 의도한 대로 정확하게 작동하는 영역을 확보한다.

## 요구사항
### 기능 요구 사항
- 로또 번호의 숫자 범위는 1~45까지이다. 
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다. 
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다. 
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다. 
  - 1등: 6개 번호 일치 / 2,000,000,000원 
  - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원 
  - 3등: 5개 번호 일치 / 1,500,000원 
  - 4등: 4개 번호 일치 / 50,000원 
  - 5등: 3개 번호 일치 / 5,000원
- 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다. 
- 로또 1장의 가격은 1,000원이다. 
- 당첨 번호와 보너스 번호를 입력받는다. 
- 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다. 
- 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다. 
- Exception이 아닌 IllegalArgumentException, IllegalStateException 등과 같은 명확한 유형을 처리한다.

### 입출력 요구 사항
#### 입력
- 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
- 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.
- 보너스 번호를 입력 받는다.

#### 출력
- 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.
- 당첨 내역을 출력한다.
- 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
- 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

### 프로그래밍 요구 사항
<details>
<summary>프로그래밍 요구 사항 1</summary>
JDK 21 버전에서 실행 가능해야 한다.<br>
프로그램 실행의 시작점은 Application의 main()이다.<br>
build.gradle 파일은 변경할 수 없으며, 제공된 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.<br>
프로그램 종료 시 System.exit()를 호출하지 않는다.<br>
프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.<br>
자바 코드 컨벤션을 지키면서 프로그래밍한다<br>
</details>

<details>
<summary>프로그래밍 요구 사항 2</summary>
iJndent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.<br>
3항 연산자를 쓰지 않는다.<br>
함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.<br>
JUnit 5와 AssertJ를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인한다.
</details>

<details>
<summary>프로그래밍 요구 사항 3</summary>
함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.<br>
else 예약어를 쓰지 않는다.<br>
Java Enum을 적용하여 프로그램을 구현한다.<br>
구현한 기능에 대한 단위 테스트를 작성한다. 단, UI(System.out, System.in, Scanner) 로직은 제외한다.
</details>

## 구현 기능
- 입출력을 담당하는 **view**
- 입력값의 유효성을 검증하는 **validator**
  - 로또 구입 금액이 1,000원 단위로 들어왔는지 체크
  - 로또 구입 금액이 숫자로만 구성됐는지 체크
  - 로또 구입 금액이 int 자료형의 범위를 넘어갔는지 체크
  - 사용자가 입력한 당첨 번호의 중복 여부 체크
  - 사용자가 입력한 당첨 번호가 로또 번호의 숫자 범위 안에 있는지 체크
  - 사용자가 입력한 당첨 번호가 쉼표를 기준으로 구분이 되었는지 체크
  - 사용자가 입력한 당첨 번호의 개수가 6개인지 체크
  - 사용자가 입력한 보너스 번호가 로또 번호의 숫자 범위 안에 있는지 체크
  - 사용자가 입력한 보너스 번호가 당첨 번호에 있는지 체크
  - 사용자가 입력한 당첨 번호와 보너스 번호가 숫자로 입력됐는지 체크
- 로또 발매기 로직을 처리하는 **service**
  - 당첨 번호를 추첨하는 기능
  - 로또 번호와 당첨 번호를 비교하는 기능
  - 수익률을 계산하는 기능
- view와 service를 연결해주는 **controller**
- 계층 간 데이터 운반을 담당하는 **dto**
