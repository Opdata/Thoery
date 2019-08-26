접근 제어자
Public : 같은 컨트랙트 내부 호출 가능, 상속받은 컨트랙트도 호출 가능, 외부 컨트랙트도 호출 가능, 상태변수에 public 접근제어사 선언시 컴파일러에서 자동적으로 그 변수의 getter 함수를 만들어준다.
Private : 컨트랙트 내부만 호출 가능
Internal : 같은 컨트랙트 내부 호출가능, 함수가 정의된 컨트랙트를 상속하는 컨트랙트에서도 호출이 가능, 상태변수는 default로 internal 선언
External : 함수가 컨트랙트 바깥에 호출될 수 있고, 같은 컨트랙트 내의 다른 함수에 의해 호출될수 없다는 점을 제외하면 public 과 동일, 상태변수에 쓸 수 없다

함수 타입 제어자 
view : 읽기O 변경X, 컨트랙트 외부에서 호출되면 가스 비용 없음 but, 다른 함수에 의해 내부적으로 호출되면 가스 소모
pure : 읽기X 함수의 인자 값만 활용하여 반환 값 정함(블록체인의 어떤 데이터로 읽지않으며 저장하지도 않음), 컨트랙트 외부에서 호출되면 가스 비용 없음 but, 다른 함수에 의해 내부적으로 호출되면 가스 소모
constant : 0.4.17버전 이전에는 view/pure 대신 쓰임
payable : 함수가 ETH를 받을 수 있게 함, 가스 비용 있음

솔리디티에서 읽는다는 것으로 간주하는 케이스
- 다양한 상태변수를 읽을때
- address(this.balance) 또는 address.balance 로 접근시
- 블록, 트랜잭션, 메시지의 멤버의 누군사 접근시(msg.sig , msg.data 제외)
- pure가 표시되지않은 함수 호출시
- 특정 opcode를 포함한 어셈블리 인라인 사용시

event
- 블록체인 상에서 앱의 액션이 발생했을때 의사소통 방법, 컨트랙트는 이벤트가 발생하면 행동을 취함
- 이벤트가 등록되면 블록안 내용과같이 기록된다.

ex)
event IntegersAdded(uint x, uint y, uint result); // 이벤트 선언
function add(uint _x, uint _y) public {
    IntegersAdded(_x,_y, result); // 이벤트 실행
    return result;
}

YourContract.IntegersAdded(function(error, result){ // 자바스크립트로 구현시 형태
    
})

array.push() : 파라미터 값을 넣고 변수의 배열 index return함

mapping
- mapping(_keyType => _ValueType)
- 키-값(key-value) 저장소, 데이터를 저장하고 검색하는데 이용
- KeyType은 매핑, 동적 크기배열, 컨트랙트, 열거형, 구조체를 제외한 거의 모든 유형이 될 수 있다.
- ValueType은 매핑 타입을 포함한 어떤 타입이든 될 수 있다.

adddress

msg.sender
- 솔리디티의 전역변수이며 솔리디티에서 함수 실행은 항상 호출을 해야 실행되는 구조이다, 그러므로 msg.sender 가 필요하다
- 이 함수를 call 한 사람을 알수있다, 이걸 활용하면 이더리움 블록체인의 보안성을 높일 수 있다.

require()
- 인자로 전달되는 bool 값이 false이면 즉시 함수 실행 종료하고 모든 상태 변화을 되돌림
- 솔리디티는 스트링 비교 기능을 가지고 있지않기때문에 keccak256 해시값을 비교하여 같은지 판단한다.

상속 is

ex)
contract Doge {
  function catchphrase() public returns (string) {
    return "So Wow CryptoDoge";
  }
}

contract BabyDoge is Doge {
  function anotherCatchphrase() public returns (string) {
    return "Such Moon BabyDoge";
  }
}

-> BabyDoge는 Doge 컨트랙트의 public인 어느함수에도 접근이 가능하다

import
- 다른파일을 가져올떄,

ex)
import "./somecontract.sol";

데이터위치 storage, memory
1. storage : 블록체인 상에 영구적으로 저장되는 변수, 주로 상태변수(함수 외부에 선언된 변수), 함수 내 로컬변수(상태변수가 아닌것들)
+ 배열과 문자열이 로컬변수로 쓰일때는 storage가 default 이며 memory로 강제로 바꿀수있다.)
+ 배열 선언과 동시에 리터럴을 사용하여 정의할때 memory로 지정해주지 않으면 오류가 난다.
2. memory : 임시, 컨트랙트 함수에 대한 외부 호출들이 일어나는 사이에 지워짐, 주로 함수내에 선언된 변수(함수의 매개변수, 리턴값), 값 타입들

보통 자동으로 설정되어 신경쓰지안아도 되지만 함수 내의 '구조체', '배열' 을 처리할떄 사용할때가 있다.


블록체인상에 있으면서 우리가 소유하지 않은 컨트랙트와 우리 컨트랙트가 상호작용 하려면 인터페이스를 정의해야 한다
인터페이서 선언은 컨트랙트 선언과 같다.
ex)
contract KittyInterface{
    function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}
컨트랙트 선언후, 다른 컨트랙트와 상호작용하고자 하는 함수만을 선언할뿐.

반환값 처리
- 다수의 반환값을 처리하는 함수가 있을떄,
function multipleReturns() internal returns(uint a, uint b, uint c){
  return (1,2,3);
}

(a,b,c) = multipleReturns();  // 여러값을 다 받을때
(,,c) = multipleReturns();  //하나의 값에만 관심있을떄

생성자(Contructor)
- 컨트랙트와 동일한 이름을 가진 생략할 수 있는 특별한 함수, 컨트랙트가 생성될떄 딱 한번만 실행된다.

ex)
function Ownable() public {
    owner = msg.sender;
  }


함수 제어자(function Modifier)
- 다른 함수들에 대한 접근을 제어하기 위해 사용되는 일종의 유사 함수, 보통 함수 실행전에 요구사항 충족 여부 확인을 하는데에 사용
* 함수 호출하듯이 호출할 수 없지만, 함수 정의부 끝에 해당 함수의 작동 방식을 바꾸도록 제어자의 이름을 붙일 수 있다.
ex)
modifier onlyOwner() {
    require(msg.sender == owner);
    _;
  }

function likeABoss() external onlyOwner {
    LaughManiacally("Muahahahaha");
  }

* 위와 같이 접근을 제한해서 오직 컨트랙트의 소유자만 해당 함수를 실행할 수 있도록 할 수 있다,
likeABoss 함수를 호출하면 onlyOwner의 코드가 먼저 실행된다. 그리고 _; 부분을 likeABoss함수로 되돌아가 해당 코드를 실행하게 된다.

modifier olderThan(uint _age, uint _userId) {
  require (age[_userId] >= _age);
  _;
}

function driveCar(uint _userId) public olderThan(16, _userId) {
  // 필요한 함수 내용들
}

* 인수 또한 받을 수 있다.


값타입
bool
bytes : 1~32 byte 지정가능, byte형에 문자를 저장할수는 있지만, hex값으로 저장하는게 바람직, uint256 같이 byte == bytes1 과 같다.
int : 8~256 bit 지정가능, 음수가능
uint : 8~256 bit 지정가능, 양수값만
address : 20byte값 앞의 0x를 제외하면 40글자, 이더리움 계정 주소를 저장하는 타입, 두개의 멤버 소유(balance : 소유한 ETH 확인 , transfer : 주소로 ETH 전송)
enum : 사용자 정의타입을 만드는 방법중 하나, - 자세히 알아볼것

동적타입
byte, string
ex) byte[] name;
ex) string[] name;
- 문자열은 32바이트를 넘어갈때 쓰는것이 좋다.

최적화
- uint8, uint16 등 하위 타입을 써도 이미 256비트의 저장 공간을 잡기때문에 전혀 의미가 없다
- 하지만 구조체안에서 여러개의 uint를 사용한다면 가능한 작은 크기의 uint를 사용해야 한다.
- 또한 uint32 a, uint32 b, uint32 b 같이 동일한 데이터타입을 붙여서 선언하는것이 좋다. (데이터 타입 압축)
- 쓸데없는 연산 줄이고, pure, view 는 가스 소모가 없으니 잘 활용하며, 비싼 연산(상태변수 연산 등)을 줄인다.
- 동적인 타입보다 고정시킨 타입을 쓰는게 더 효율적이다.
- 무제한 크기의 배열 반복을 피한다. -> 매핑을 사용해서 쉽게 해결

시간함수 
seconds, minutes, hours, days, weeks, years, now

구조체를 인수로 전달할수있다.
function _doStuff(Zombie storage _zombie) internal{

}



?????
this.balance
- 컨트랙트에 저장돼있는 전체 잔액

????????
참고: 만약 view 함수가 동일 컨트랙트 내에 있는, view 함수가 아닌 다른 함수에서 내부적으로 호출될 경우, 여전히 가스를 소모할 것이네. 이것은 다른 함수가 이더리움에 트랜잭션을 생성하고, 이는 모든 개별 노드에서 검증되어야 하기 때문이네. 그러니 view 함수는 외부에서 호출됐을 때에만 무료라네.

???????
자바스크립트 artifacts , it

???????????/
솔리디티 emit