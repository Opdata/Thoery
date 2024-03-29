https://github.com/ethereum/wiki/wiki/%5BKorean%5D-White-Paper
https://ko.wikipedia.org/wiki/%EC%9D%B4%EB%8D%94%EB%A6%AC%EC%9B%80
http://wiki.hash.kr/index.php/%EC%9D%B4%EB%8D%94%EB%A6%AC%EC%9B%80 // 이더리움 해시넷
http://ethereum.stackexchange.com/questions/14/what-proof-of-work-function-does-ethereum-use //POW 알고리즘
https://blog.theloop.co.kr/2017/03/28/%EC%8A%A4%EB%A7%88%ED%8A%B8-%EC%BB%A8%ED%8A%B8%EB%9E%99%ED%8A%B8smart-contract-%EA%B0%9C%EC%9A%94-1/
// 스마트 컨트랙트(Smart Contract)

비탈릭 부테린(Vitalik Buterin)이라는 19세 청년 개발자가 탈중앙화의 개념을 송금 외에 다른 분야에 적용하고자 해서 개발
2014년 1월 스크립팅 언어를 사용할 수 있는 플랫폼에 대한 백서 출간 -> 개발팀 꾸려지고 EVM(Etherum Virtual machine)에 대해 설명 -> 자금 크라우드 펀딩
-> 펀딩 참가자 비트코인으로 이더리움 밸튜 토큰(이더) 구입 -> 2015 5월 이더리움 플랫폼 올림픽 베타버전 라이브 -> 이더리움 서비스 시작
-> 2017년 10월 1차 비잔티움 하드포크, 스마트컨트랙트 보안 개선, 채굴보상 5 -> 3개로 감소

이더리움은 퍼블릭 블록체인 기반의 분산 컴퓨팅 플랫폼, 수많은 작은 컴퓨터가 모인 하나의 큰 컴퓨터로도 생각할 수 있다.
이더리움 블록체인을 통해 중앙 권한없이 두 당사자간에 돈을 이체할 수 있으며, 중단 시간, 검열, 사기 또는 제3자의 간섭없이 실행되도록 보장한다.
모든 노드는 서로 연결되어 있고, 코드와 데이터의 전체 복사본을 가지고 있다. 이더리움 블록체인에 코드를 배포하면 모든 노드로 복제된다.

모든 클라이언트는 응용프로그램의 자체 인스턴스와 통신한다.
-> 연결할 중앙서버가 없으며, 상호 작용하려는 모든 노드는 실행중인 블록체인의 전체 복사본이 필요하다.

전체 블록체인의 양이 거대해지면서 단일/중앙화된 서버에 의존하지 않는 방법
-> 블록체인 서버 호스팅,Metamask 등 을 사용하여 하드와 램을 많이 사용하지 않아도 블록체인 전체 복사본을 다운로드하고 실행하면서 탈중앙을 훼손하지 않음

이더리움 블록체인 2가지 구성 요소
- 데이터베이스 : 모든 트랜잭션은 블록체인에 저장되며, 배포행위 등 모든 트랜잭션은 공개되며 누구나 볼 수 있고 확인할 수 있다.
이 데이터는 절대로 조작할 수 없으며, 모든 노드에 동일하게 복사본이 있는지 확인하고, 유효하지 않은 데이터가 데이터베이스에 기록되지 않도록 하기위해
작업증명(POS - Proof of Work)이라는 알고리즘을 사용하여 네트워크를 보호한다.

- 코드 : 스마트 컨트랙트 코드를 저장하고 실행
+솔리디티(Solidity) 라는 언어로 논리/응용 프로그램 코드를 작성하고 솔리디티 컴파일러를 사용하여
이더리움 바이트코드(Ethereum Byte Code)로 컴파일한 다음 바이트코드를 블록체인에 배포

-> 이더리움 블록체인은 데이터를 저장하고 코드를 저장하며 EVM(Ethereum Virtual Machine) 에서 실행한다.
EVM(Ethereum Virtual Machine)
- 이더리움 가상 머신으로, 단순하지만 강력하고, 강력한 튜링 완전성을 가진 256비트 가상머신으로 누구나 임의의 EVM 바이트코드를 실행할수 있다.
- geth, parity 등의 이더리움 클라이언트를 설치하고 실행하면 EVM이 시작되고, 트랜잭션의 동기화, 유효성 검사 및 실행을 시작한다.

스마트 컨트랙트(Smart Contract)
- 실제 계약은 여러 당사자 간의 서면 합의이다, 하지만 디지털 명령어로 계약을 작성하고 코드로 변환하고 블록체인에 배포하면 디지털 계약이 된다.
- 계약이 블록체인에 배포되면 이를 중지하거나 수정할 수 없다.

이더, 단위
- 이더리움 블록체인의 기본 통화 단위는 이더(Ether), 세부 단위는 wei(최소)->babbage->lovelace->shannon->szabo->finney->ether->grand
- 이더와 웨이가 자주 쓰이며 스마트 컨트랙트에서 실제로 쓰이는 단위

주소                ***************************************** 추가예정
- (이더리움 주소 생성방식), 개인키 생성 -> 개인키로부터 공개키 생성 -> keccak256 알고리즘으로 공개키의 해시값 계산 -> 생성된 해시갑의 뒤쪽
20바이트 취하여 주소 생성
- 각 주소에는 해당 개인키가 있다, 공개키 암호화 원리 참고.
- 블록체인과 상호 작용하려면 주소 + 개인키 쌍이 필요하다.
- 이더리움 주소는 공개되어 있으며 전 세계 누구와도 공유 할 수 있다, 주소 + 개인키는 어떤 데이터베이스에도 저장되지 않으며 사용자만이 통제한다.


계정
- 이더리움 주소와 개인키의 조합을 계정이라고 하며, 계정은 이더 잔고 보유, 트랜잭션 전송을 할 수 있다.
- 계정의 유형은 2가지 (외부 소유 계정(EOA), 컨트랙트 계정) 으로 나뉜다.

1. 외부 소유 계정(EOA)
- 공개주소와 개인키의 조합
- 다른 계정과 이더를 송수신하고, 스마트 컨트랙트에 트랜잭션을 보낼수 있다.

2. 컨트랙트 계정
- 상응하는 개인키가 없으며, 블록체인에 배포할때 생성된다. 컨트랙트 계정 대신 컨트랙트로만 표시되기도 한다.
- 다른 계정과 이더를 송수신하고, 관련된 코드를 담고, EOA나 다른 컨트랙트의 호출을 받아 트랙잭션을 발생시킨다.


지갑
- 이더리움 계정을 저장하고 관리하는데 사용되는 플러그인 또는 라이브러리, 지갑을 통해 여러 게정을 관리, 트랜잭션 서명, 잔고 추적
- 지갑 유형 2가지(비결정적 지갑, 결정론적 지갑)

1. 비결정적 지갑
- 임의의 개인키 / 공캐기 쌍을 사용하는 유형의 지갑, 개인키 공개키 쌍을 많이 생성할 수 있지만 키 간의 상관관계는 없다

2. 결정론적 지갑
- 모든 키가 시드(seed) 라는 단일 시작 지점에서 파생되며, 시드는 사용자가 다른 정보를 요구하지 않고 지갑을 쉽게 백업 복원 하게하며
개인키를 모른 채 공개키를 생성할 수 있게 해준다.
- 시드는 사람이 읽을 수 있는 니모닉 문구단어로 배열된다.

가스
- 연산의 단위를 말한다.
- 연산에 소모되는 비용을 옵코드(opcode) 라고한다.
- 이더리움 블록체인에 스마트 계약을 배포하고 트랜잭션을 실행하기 위해서는 각 상호 작용과 관련된 비용이 소모된다
- 블록체인에서 트랜잭션을 실행하려면 네트워크 채굴자에게 이더를 지불해야 한다.
- 트랜잭션을 위해 지불하는 이더의 양은 트랜잭션에 얼마나 많은 단위 연산이 포함되는지에 따라 달라진다. 
- 네트워크 상태, 컴퓨팅 자원에 따라서도 비용이 달라진다.
- 이더의 가격은 변동이 있지만 가스가격은 변동이 없다.
ex) 다른 계정으로 돈 보낼떄, 컨트랙트 배포할때, 함수 상태변수에 변화를 줄때 등
https://ethgasstation.info/ //네트워크에서 트랜잭션을 처리하는데 사용되는 가스 평균가들을 볼 수 있다.
https://converter.murkin.me // 이더리움 단위 계산

가스 가격
- 트랜잭션에 많은 가스가 필요한걸 알아도, 실제 채굴자에게 지불해야하는 이더의 양은 아직 알 수 없다. 이것을 결정하는 가스 가격(gas price)
이다. 트랜잭션 생성자가 원하는 가스 가격을 설정할 수 있으며, 트랜잭션 소비에 100000가스를 소비하고 가스 가격을 3Gwei 설정시
수수료로 3000000Gwei를 지불하게 된다.
- 가스 가격이 높을수록 트랜잭션이 더 빨리 처리된다, 대부분 채굴자는 가스 가격의 내림차순으로 트랜잭션을 분류하고 가스 가격이 높은
트랜잭션을 선택하여 블록에 포함시키기 때문, 가격을 낮게 책정해도 되지만 블록에 포함될때 까지의 대기시간이 상당히 길다.
- 수수료 예상량 = 가스한도(Gas limit) * 가스비(Gas price) 
- 트랜잭션이 일어나야 실제 사용된 가스 비용을 알수 있다. -> Etherscan 에서 Gas Used By Txn(트랜잭션에 사용된 가스비) * Gas Price(가스 가격) = 실제 수수료값

가스 한도
- 트랜잭션이 소모하는 가스의 양은 정확하게 파악하는 것은 매우 어렵다, 예상치 못한 과도한 트랜잭션 전송 이더 수수료를 소모하는 것을
피하기 위해 가스의 최대 금액(한도)를 지정할 수 있다.
* 가스 한도를 블록 가스 한도(Block gas limit) 과 혼동하면 안된다.
블록 가스 한도 : 이더리움의 각 블록에 적용되는 최대 캡, 현재 이더리움 블록은 가스 총액이 800만원 이내의 범위에서만 트랜잭션을 포함
할 수 있다.
- 각 블록에 대해 가스 제한이 있는 이유는, 누군가가 무한 루프를 실행할 수 없도록 하기 위함(무한 루프 발생시 트랜잭션이 실행
이 완료되지 않아 블록 채굴이 발생하지 않기 때문)

Geth
- 이더리움 재단에서 제공하는 공식 클라이언트 소프트웨어, Go로 개발되었다.
- Geth로 처음시작시 네트워크 내의 다른 이더리움 클라이언트(노드 라고도 불림)에 연결하는 작업을 먼저 시작하고 블록체인의 전체 사본을 내려받게 된다.
- 블록체인 복사본을 최신 상태로 유지하기위해 끊임없이 다른 노드와 통신한다.
- 블록채굴, 트랜잭션 추가, 트랜잭션 검증, 트랜잭션 실행, RPC(Remote Precedure call)를 통해 상호작용할 수 있는 API를 노출하여 서버 역할 등을 할 수 있다.

Geth console
- 블록체인에 연결할 수 있는 자바스크립트 클라이언트

Parity
- 이더리움 프로토콜의 또 다른 구현체, 러스트(Rust) 언어로 개발되었다.

ganache(가나슈)  ********** 추가할것******
- 개발목적으로만 쓰이는 인메모리 블록체인
- geth와 parity를 사용하여 트랜잭션을 실행했을때 15초가 걸리는데, 개발 속도가 느려질 수 있기때문에 가나슈라는 메모리내 블록체인을 사용하여
100개의 이더가 미리 탑재되있고 10개의 테스트 계정을 얻을 수 있다.

Web3.JS
- 이더리움 블록체인과 상호작용하는데 사용하는 자바스크립트 라이브러리, 모든 프론트엔드 프레임워크에서 탈중앙 애플리케이션을 이요하게 할 수 있다.
- RPC(Remote Precedure call)을 추출하는 라이브러리

Ethers.js
- web3JS와 비슷한 이더리움 자바스크립트 라이브러리

Truffle
- Dapp 개발에 가장 널리 사용되는 프레임워크, 스마트 계약을 컴파일하고 배포하는 복잡성을 많이 추상화한다.
http://truffleframework.com/

OpenZeppelin
- 안전한 스마트컨트랙트 개발을 위한 라이브러리

Metamask
- 이더리움 지갑 중 인기있는 지갑 중 하나, 크롬 플러그인으로 설치 가능

Embark
- Truffle와 비슷한 Dapp 프레임워크

RPC(Remote Precedure call)
-

이더리움은 이론적으로 블록의 크기에 제한이 없지만, Gas에 의해 실질적으로 통제된다.


