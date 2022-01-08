## 목차

1. [TCP/IP 기초](#1-TCP/IP-기초)   
1.1 [TCP/IP는 무엇인가](#1.1-TCP/IP는-무엇인가)   
1.2 [TCP/IP는 어떻게 작동하는가](#1.2-TCP/IP는-어떻게-작동하는가)
2. [TCP/IP 프로토콜 시스템](#2-TCP/IP-프로토콜-시스템)   
2.1 [네트워크 접근 계층](#2.1-네트워크-접근-계층)   
2.2 [인터넷 계층](#2.2-네트워크-접근-계층)   
2.3 [서브넷팅과 CIDR](#2.3-서브넷팅과-CIDR)
2.4 [전송 계층](#2.4-전송-계층)

---
# 1 TCP/IP 기초

## 1.1 TCP/IP는 무엇인가

### TCP/IP 정의

* 컴퓨터 사이의 통신 표준 및 네트워크의 라우팅 및 상호연결에 대한 자세한 규칙을 지정하는 프로토콜 스위트

### TCP/IP 주요 기능

#### 논리 주소 지정
* 기존의 물리적인 네트워크와는 독립적으로 각 호스트를 유일하게 식별할 수 있는 주소 체계
#### 라우팅
* 인터넷 네트워크를 통해 다른 네트워크의 주소로 패킷을 전송하는 경로 결정
#### 이름 확인
* 사용자가 이해할 수 있는 영어와 숫자로 조합한 도메인 이름을 IP주소로 맵핑
#### 오류 제어 및 흐름 제어
* 전송에 오류가 있는지, 성공적으로 수신했는지 확인
#### 애플리케이션 지원
* 동일한 컴퓨터에서 실행될 경우, 각 애플리케이션에 속하는 패킷을 결정하는 수단 제공

### Q&A
  * 프로토콜 표준과 프로토콜 구현의 차이점   
    * 프로토콜 표준 : 규칙 시스템
    * 프로토콜 구현 : 컴퓨터에 네트워크 기능을 제공하기 위해 이러한 규칙들을 적용한 소프트웨어 구성요소
  * ARPAnet의 엔드 노드 검증이 중요한 기능인 이유
    * 네트워크는 설계상 중앙에서 제어하지 않음으로, 송수신 컴퓨터는 자신의 통신 검증을 담당
  * 대규모 네트워크는 왜 이름 확인을 사용하는지
    * IP주소는 기억하기 어렵고 틀리기 쉬움으로, 사용자가 이해하고 기억하기 쉬운 영어와 숫자로 조합된 도메인 이름을 사용

### 퀴즈
  * 네트워크 프로토콜은 무엇입니까?
    * 공통된 전송 매체를 통해 서로 통신하는 컴퓨터 또는 컴퓨터 유사 기기 사이에서 메세지를 주고 받는 양식과 규칙의 체계
  * 분산 방식으로 작동하게 하는 TCP/IP의 두 가지 기능은 무엇입니까?
    * 엔드 노드 검증 : 네트워크는 설계상 중앙에서 제어하지 않음으로, 메시지를 전달하는 체인의 양쪽 끝인 송수신 컴퓨터(엔드노드)는 자신의 통신을 검증
    * 동적 라우팅 : 노드는 여러 경로를 통해 연결되며, 라우터는 현재 통신 상태를 기반으로 경로를 재설정
  * 도메인 이름을 IP주소에 매핑을 담당하는 시스템은 무엇입니까?
  * RFC는 무엇입니까?
    * TCP/IP 및 인터넷 관련 정보를 제공하는 일련의 공식 기술 문서
  * 포트는 무엇입니까?
    * 각 애플리케이션에 속하는 패킷을 구분하기 위해서 사용하는 논리적 파이프라인

---

## 1.2 TCP/IP는 어떻게 작동하는가

### TCP/IP 모델의 프로토콜 계층

#### 네트워크 접근 계층
* 물리적 네트워크와의 인터페이스 제공
* 전송 매체의 데이터를 포맷
* 물리적 하드웨어 주소(MAC)를 기반으로 서브넷의 데 이터를 처리
* 오류 제어 기능
* 데이터 패키지 : 프레임, 비트 스트림(네트워크 접근 계층 內 하위 계층)
#### 인터넷 계층
* 하드웨어와 독립적으로 주소를 지정하는 기능을 통해 물리적 아키텍처가 다른 서브넷 간에 데이터를 전달
* 데이터 패키지 : 데이터 그램
#### 전송 계층
* 인터네트워크에 대한 흐름 제어, 오류 제어, 승인 서비스를 담당하며 네트워크 애플리케이션을 위한 인터페이스 역할
* 데이터 패키지 : 세그먼트(TCP), 데이터그램(UDP)
#### 응용 계층
* 네트워크 문제 해결, 파일 전송, 원격 제 어 및 인터넷 활동을 위한 애플리케이션 제공
* 특정 운영 환경을 위해 작성된 프로그램이 네트워크에 접근할 수 있도록 네트워크 API 지원
* 데이터 패키지 : 메시지

### OSI 모델 7계층
#### 물리 계층
* 데이터를 실제 전송 매체를 지나는 전기 또는 아날로그 펄스 스트림으로 변환
* 데이터 전송 감독
#### 데이터 링크 계층
* 네트워크 어댑터와의 인터페이스 제공
* 서브넷의 논리적 링크 유지
#### 네트워크 계층
* 논리 주소 지정
* 라우팅 지원
#### 전송 계층
* 인터네트워크에 대한 오류 제어 및 흐름 제어
#### 세션 계층
* 통신 애플리케이션 간에 세션 설정
#### 표현 계층
* 데이터를 표준 형식으로 변환
* 암호화 및 데이터 압축
#### 응용 계층
* 애플리케이션을 위한 네트워크 인터페이스 제공
* 파일 전송, 통신 등을 위한 네트워크 애플리케이션 지원

### Q&A
* TCP/IP 모듈식 설계의 주요 장점
  * TCP/IP의 모듈식 설계 덕분에 TCP/IP 프로토콜 스택은 특정 하드웨어 및 운영 환경에 쉽게 적응할 수 있습니다.   계층 하나는 스택의 나머지 부분에 영향을 주지 않고 변경될 수 있습니다.   네트워킹 소프트웨어를 잘 설계된 특정 구성 요소로 나누면 프로토콜 시스템과 상호 작용하는 프로그램을 더욱더 쉽게 작성할 수 있습니다.
* 네트워크 접근 계층의 기능
  * 특정 물리적 네트워크와 관련된 서비스를 제공   이러한 서비스에는 이더넷 케이블과 같은 특정 전송 매체를 통한 프레임 준비, 송신 및 수신이 포함
* TCP/IP 인터넷 계층에 해당하는 OSI 계층
  * 네트워크 계층

### 퀴즈
* TCP/IP 네트워크 접근 계층에 대응하는 두 개의 OSI 계층
  * 물리 계층
    * 데이터를 실제 전송 매체를 지나는 전기 또는 아날로그 펄스 스트림으로 변환
    * 데이터 전송 감독
  * 데이터 링크 계층
    * 네트워크 어댑터와의 인터페이스 제공
    * 서브넷의 논리적 링크 유지
* 한 네트워크 세그먼트에서 다른 네트워크 세그먼트로 데이터를 라우팅하는 데 어떤 TCP/IP 계층이 있습니까?
  * 인터넷 계층 ( OSI Layaer - 네트워크 계층 )
    * 하드웨어와 독립적으로 주소를 지정하는 기능을 통해 물리적 아키텍처가 다른 서브넷 간에 데이터를 전달
    * 데이터 패키지 : 데이터 그램
* TCP와 비교할 때 UDP의 장단점
  * TCP : 연결형 서비스를 지원하는 프로토콜
    * 연결형 서비스로 가상 회선 방식을 제공
    * 3-way handshaking 과정을 통해 연결을 설정하고, 4-way handshaking을 통해 해제
    * 흐름 제어 및 혼잡 제어
    * 높은 신뢰성 보장
    * UDP에 비해 속도가 드리다.
    * Full-Duplex, Point to Point 방식
  * UDP : 비연결형 프로토콜
    * 비연결형 서비스로 데이터그램 방식을 제공
    * 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.
    * UDP 헤더의 CheckSum 필드를 통해 최소한의 오류만 검출
    * 신뢰성이 낮다.
    * TCP보다 속도가 빠르다.
* 계층과 데이터를 캡슐화한다는 것의 의미
  * 송신 시스템의 각 계층은 수신 시스템에 상응하는 계층 관련 데이터를 추가
### 연습문제
* TCP/IP 스택에서 각 계층이 수행하는 기능
  * 네트워크 접근 계층
    * 물리적 네트워크와의 인터페이스 제공
    * 전송 매체의 데이터를 포맷
    * 물리적 하드웨어 주소(MAC)를 기반으로 서브넷의 데 이터를 처리
    * 오류 제어 기능
    * 데이터 패키지 : 프레임, 비트 스트림(네트워크 접근 계층 內 하위 계층)
  * 인터넷 계층
    * 하드웨어와 독립적으로 주소를 지정하는 기능을 통해 물리적 아키텍처가 다른 서브넷 간에 데이터를 전달
    * 데이터 패키지 : 데이터 그램
  * 전송 계층
    * 인터네트워크에 대한 흐름 제어, 오류 제어, 승인 서비스를 담당하며 네트워크 애플리케이션을 위한 인터페이스 역할
    * 데이터 패키지 : 세그먼트(TCP), 데이터그램(UDP)
  * 응용 계층
    * 네트워크 문제 해결, 파일 전송, 원격 제 어 및 인터넷 활동을 위한 애플리케이션 제공
    * 특정 운영 환경을 위해 작성된 프로그램이 네트워크에 접근할 수 있도록 네트워크 API 지원
    * 데이터 패키지 : 메시지
 
* 데이터그램을 다루는 계층
  * 인터넷 계층
    * 하드웨어와 독립적으로 주소를 지정하는 기능을 통해 물리적 아키텍처가 다른 서브넷 간에 데이터를 전달
    * 데이터 패키지 : 데이터 그램
* 새로 발명된 유형의 네트워크 하드웨어를 사용하기 위해 TCP/IP를 어떻게 변경해야 하는지 설명
  * TCP/IP는 모듈식 설계 되어있으므로 새로 발명된 유형의 네트워크 하드웨어를 지원하기 위한 새로운 계층 작성 또는 변경이 필요한 기존 계층에 대해서만 변경하고 나머지 스택은 그대로 둔다.
* TCP가 신뢰할 수 있는 프로토콜이라는 말의 의미
  * 흐름제어
    *  상대방이 받을 수 있을 만큼만 데이터를 효율적으로 전송
    *  흐름제어를 위해 슬라이딩 윈도우(Sliding Window)방식을 사용한다. 이는 상대방이 수신 가능한 크기(Window size)내에서 데이터를 연속해서 전송하는 방식으로 매 세그먼트 전송 시마다 수신확인응답(ACK)을 수신한 후 전송하게 되면 왕복시간(RTT:Round Trip Time)이 길 경우, 단위 시간당 데이터 전송량이 매우 떨어지므로 효율적으로 전송하기 위해 상대방이 받을 수 있는 범위 내에서 연속적으로 전송한다.
  * 오류제어
    * 데이터의 오류나 누락없이 안전한 전송을 보장
    * 오류 또는 누락 발생 시 재전송을 수행하여 이를 보정
  * 혼잡제어
    * 네트워크의 혼잡 정도에 따라 송신자가 데이터 전송량을 제어하는 것
    * 혼잡정도에 대한 판단기준은 데이터의 손실 발생 유무로 판단한다. 전송한 데이터에 누락이 발생하면 네트워크가 혼잡한 상태로 판단하여 전송량을 조절한다.
---
# 2 TCP/IP 프로토콜 시스템

## 2.1 네트워크 접근 계층

### 네트워크 접근 계층 정의

* 물리적 네트워크에 대한 데 이터를 준비하는 데 필요한 모든 서비스와 기능을 관리
* OSI 물리 계층 + 데이터 링크 계층(미디어 접근 제어(MAC), 논리 링크 제어(LLC))

### TCP/IP 주요 기능

* 컴퓨터의 네트워크 어댑터와 인터페이스
* 적절한 접근 방법의 규칙을 통한 데이터 전송 조정
* 데이터를 전송 매체를 지나는 전기 또는 아날로그 펄스 스트림으로 변환
* 수신 데이터의 오류 확인
* 수신 컴퓨터가 데이터의 오류를 확인할 수 있게 발신 데이터에 오류 검사 정보 추가

### 네트워크 아키텍처 : 실제 네트워크를 위한 설계, 해당 네트워크의 통신을 정의하는 사양의 모음
 * 접근 방법 : 컴퓨터가 전송 매체를 공유하는 방법을 정의하는 일련의 규칙
 * 데이터 프레임 형식 : 인터넷 계층의 IP 수준 데이터그램은 미리 정의된 형식의 데이터 프레임으로 캡슐화, 헤더에 포함된 데이터는 실제 네트워크에서 데이터를 전달하는 데 필요한 정보를 제공
 * 케이블 연결 유형 : 어댑터가 전송하는 비트 스트림의 전기적 특성과 같은 특정 기타 설계 매개변수에 영향
 * 케이블 연결 규칙 : 프로토콜, 케이블 유형 및 전기적 특성은 케이블 및 케이블 커넥터 사양의 최대 및 최소길이에 영향

### 물리 주소
 * OSI 모델 내에서 물리 주소 지정은 MAC 하위 계층이 담당
 * 물리 주소 지정 시스템은 네트워크 접근 계층 내에 캡슐화되므로 네트워크 아키텍처 사양에 따라 주소가 다른 형식을 취할 수 있음
 * ARA 및 RARP를 사용해 IP주소를 로컬 네트워크에 있는 네트워크 어댑터의 물리 주소와 연결

### CSMA/CD
 * 컴퓨터가 접근 매체로 데이터를 자유롭게 전송할 수 있는 시점을 결정하기 위한 반송파 감지 다중 접속/충돌 탐지 방법
 * 반송파 감지 다중 접속 : 전송 매체를 사용중인 곳이 있는지 판단
 * 충돌 탐지 : 동시에 사용하는 경우, 잠시 멈춘 후 다시 송신
 
### 네트워크 접근 계층 수행 순서
 1. 데이터그램 수신
 2. 이더넷 프레임의 데이터 필드에 전송하는 작은 조각으로 분리
 3. 데이터 조각을 프레임으로 패키징
 4. 데이터 프레임을 OSI 물리 계층에 해당하는 하위 레벨 구성 요소로 전달
 5. 프레임을 비트 스트림으로 변환해 전송 매체를 통해 전송
 
### Q&A
 * 네트워크 접근 계층에 정의된 서비스의 종류
   * 실제 네트워크에 접근하는 프로세스를 관리하는 서비스 및 사양
 * TCP/IP 네트워크 접근 계층에 해당하는 OSI 계층
   * 데이터 링크 계층, 물리 계층
 * 일반적인 LAN 아키텍터
   * 이더넷
 * CSMA/CD란
   * 이더넷이 사용하는 네트워크 접근 방법으로, 충돌 감지 기능을 갖춘 반송파 감지 다중 접속 기술
   * CSMA/CD에서 네트워크의 컴퓨터는 전송을 잠시 기다렸다가 두 컴퓨터가 한 번에 전송을 시도하면 중지하고 잠시 동안 대기한 후 전송

### 퀴즈
 * CRC
   * 주기적 덧붙임 검사, 데이터 프레임의 내용을 확인하는데 사용되는 체크섬 계산
 * 이더넷 네트워크에서 충돌 감지란
   * 두 컴퓨터가 한 번에 전송을 시도하는 것을 감지
 * 이더넷 물리 주소는 얼마나 큽니까?
   * 48비트
 * ARP
   * IP주소를 로컬 네트워크에 있는 네트워크 어댑터의 물리 주소와 연결
 
### 연습 문제
 * 물리 주소와 IP주소를 연결하는 두 가지 프로토콜  
   * ARP, RARP
 * 최소 세 가지 네트워크 아키텍처
   * IEEE 802.3(이더넷) : 사무실과 가정에서 많이 사용하는 일반적인 케이블 기반 네트워크
   * IEEE 802.11(무선 네트워킹) : 사무실과 가정, 커피숍에서 사용하는 무선 LAN 네트워크 지굿
   * IEEE 802.16(WiMAX) : 장거리 모바일 무선 연결에 사용하는 네트워크 기술
   * PPP(Point-to-Point Protocol) :  전화선을 통한 모뎀 연결에 사용하는 프로토콜
 * OSI 매체 접근 제어 및 온리 링크 제어 계층이 수행하는 기능
   * MAC : OSI 모델에 규정된 데이터 링크 계층의 일부이며, 네트워크 어댑터와의 인터페이스 제공
   * LLC : 서브넷을 통해 전달된 프 레임의 오류를 검사하고 서브넷에서 통신하는 장치 간의 링크를 관리

---

## 2.2 인터넷 계층

### 인터넷 프로토콜
 * 하드웨어로부터 독립적인 계층적 주소 지정 시스템을 제공하며 복잡하게 라우팅된 네트워크에서 데이터를 전달하는데 필요한 서비스를 제공

### IP 헤더 필드
 * 모든 IP 데이터그램은 IP 헤더로 시작하며, IP 헤더에 포함된 정보를 사용해 수신한 데이터그램을 처리한다.
 * 버전 : 4비트, 사용중인 IP 버전
 * IHL : 4비트, IP 헤더의 길이를 32비트 문자열로 제공
 * 서비스 유형 : 8비트, 데이터그램의 우선순위를 지정하는 방법을 제공
 * 총 길이 : 16비트, IP 데이터그램의 길이를 옷텟 단위로 식별, 총 길이에는 IP헤더와 데이터 페이로드 포함
 * 식별자 : 16비트, 소스IP에서 보낸 메시지에 지정된 증분 시퀀스 번호 ( 분할한 모든 데이터그램에 부여한 식별 번호이며 조잡할 때 사용  )
 * 플래그 : 조각화 가능성, 첫 비트는 0,  다음 비트는 DF Flag로 조각화 허용되는지(0) 아닌지(1), 다음 비트는 MF Flag로 더 많은 조각화가 진행되고 있음을 알려줌
 * 프래그먼트 오프셋 : 13비트, 각 프래그먼트에 할당된 숫자로 프래그먼트의 순서
 * TTL : 데이터그램이 삭제되기 전에 존속할 수 있는 시간 또는 라우터 홉
 * 홉 : 데이터그램이 대상으로 가는 도중에 교차해야 하는 라우터 수
 * 프로토콜 : 8비트, 데이터 페이로드를 수신할 프로토콜, 1 = ICMP, 6 = TCP, 17 = UDP
 * 헤더 체크섬 : 16비트, 헤더의 유효성 검증, 모든 라우터에서 TTL 감소하면서 재계산한다.
 * 소스 IP주소 : 32비트
 * 대상 IP주소 : 32비트
 * IP옵션 : 테스트, 디버깅 및 보안에 사용하는 여러 선택적 헤더 설정을 지원
 * 패딩 : IP 옵션 필드의 길이는 다를 수 있으므로 추가 헤더를 제공해 총 헤더 길이가 32비트의 배수가 되도록 하기 위한 것
 * IP 데이터 페이로드 : 전달할 데이터

### IP 주소
 * 클래스 A : IP 주소의 처음 8비트가 네트워크 ID에 사용, 10진수로 0~127, 2진 0
 * 클래스 B : IP 주소의 처음 16비트가 네트워크 ID에 사용, 10진수로 128~191, 2진 10
 * 클래스 C : IP 주소의 처음 24비트가 네트워크 ID에 사용, 10진수로 192~223, 2진 110

### 주소 확인 프로토콜
 * IP주소를 물리주소에 매핑한 ARP캐시를 검사해서 IP주소를 이용해 물리주소를 찾아 연결하는 것
 * ARP 캐시에 없으면 호스트는 ARP 요청 프레임이라는 브로드캐스트를 보내서 물리주소를 응답받아 ARP 캐시에 추가한다.

### RARP 
 * 물리주소는 알지만 IP주소는 알 수 없을 때 사용하는 것

### 인터넷 제어 메시지 프로토콜
 * 메시지를 최종 목적지로 보낼 때 라우터에서 발생한 문제를 소스 IP에 알리기 위한 것
 * 에코 요청 및 에코 응답 : 테스트에 사용하여 응답 뎅터그램으로 전송된 데이터를 반환하도록 요청
 * 소스 퀀치 : 데이터를 전송하는 속도를 늦추도록 요청
 * 도달 불가 목적지 : 전달할 수 없는 데이터그램을 수신한 경우 메시지를 소스 IP로 돌려보낸다.
 * 시간 초과 : TTL이 0에 도달해 데이터그램이 삭제되는 경우, 해당 메시지를 소스 IP로 전송
 * 라우팅 루프 : 데이터그램이 끝없이 순환하고 목적지에 도달하지 못할 때 발생, 정적 라우팅 항목을 라우팅 테이블에 배치하는 경우 종종 발생
 * 조각화 필요 : DF필드가 설정된 데이터그램을 수신하고 라우터가 데이터그램을 조각화해 다음 라우터 또는 대상으로 전달해야 할 때, 해당 메세지를 전송

### 퀴즈
 1. IP헤더에서 TTL필드의 목적은 무엇입니까?
  -  전달되지 못한 데이터그램이 인터넷 시스템 내에서 지속적으로 순환하여 넘쳐나게 되는 상황을 방지
 2. 클래스 A주소의 네트워크 및 호스트 ID 필드는 얼마나 됩니까?
  -  네트워크 : 8비트, 호스트 : 24비트
 3. 옥텟은 무엇입니까?
  - 8비트 배열
 4. IP주소는 무엇입니까?
  - 인터넷 네트워크에 연결된 디바이스에 대해 부여되는 식별 주소
 5. ARP와 RARP의 차이점은 무엇입니까?
  - ARP는 IP주소는 알지만 물리 주소를 알 수 없을 때 사용하며, RARP는 물리 주소는 알지만 IP주소를 알 수 없을 때 사용

### 연습문제
 1. 다음 2진수 옥텟을 10진수로 변환하세요.
    00101011 = 1 + 2 + 8 + 32 = 43
    01010010 = 2 + 16 + 64 = 82
    11010110 = 2 + 4 + 16 + 64 + 128 = 214
    10110111 = 1 + 2 + 4 + 16 + 32 + 128 = 183
    01001010 = 2 + 8 + 64 = 74
    01011101 = 1 + 4 + 8 + 16 + 64 = 93
    10001101 = 1 + 4 + 8 + 128  = 141
    11011110 = 2 + 4 + 8 + 16 + 64 + 128 = 222 
 2. 다음 10진수를 2진수  옥텟으로 변환하세요
    13  = 00001101
    184 = 10111000
    238 = 11101110
    37  = 00100101
    98  = 01100010
    161 = 10100001
    243 = 11110011
    189 = 10111101
 3. 다음 32비트 IP주소를 점으로 분리된 10진수 표기법으로 변환하세요
    11001111 00001110 00100001 01011100 = 207.14.33.92
    00001010 00001101 01011001 01001101 = 10.13.89.77
    10111101 10010011 01010101 01100001 = 189.147.85.97

---

## 2.3 서브넷팅과 CIDR

### (1) 서브넷팅
 * 정의 : 네트워크를 서브넷이라고 하는 작은 단위로 분리하는 것 
 * 서브넷 마스크 : 서브넷 ID에 사용할 주소로 얼마나 할당할지, 실제 호스트ID에 사용할 주소는 얼마나 남았는지를 나타내는 것

### (2) CIDR
 * 정의 : 클래스 구분 없이 라우팅 테이블의 주소 블록을 정의
 * VLSM  : 네트워크/서브넷 ID 역할을 하는 주소 내의 비트 수를 지정하는 CIDR 접두사

### 퀴즈
1. 서브넷 ID 비트는 어디에서 왔습니까?
 - 호스트 ID
2. 예전과 달리 지금 서브넷이 중요하지 않은 이유는 무엇입니까?
 - 서브넷 기능이 CIDR에 포함
3. CIDR간 라우팅에서 클래스리스란 무엇을 의미합니까?
 - 클래스의 구분이 없는 것
4. /26 네트워크에 몇 개의 호스트가 있을 수 있습니까?
 - 2^6-2개
5. 작은 네트워크에 여러 개를 더 큰 단일 네트워크 범위로 통합하는 것은 무엇입니까?
 - Super netting 

### 연습문제
1. 네트워크 주소 180.4.0.0에서 180.7.255.255를 단일 네트워크로 결합하면 얻을 수 있는 CIDR 네트워크 주소를 계산하세요.
 - 180.4.0.0     = 10110100 00000100 00000000 00000000
 - 180.7.255.255 = 10110100 00000111 11111111 11111111
 - 그러므로 180.4.0.0/14
2. 서브넷 마스크가 255.255.255.244인 경우, 서브넷 192.100.50.192에서 가능한 호스트 수를 결정하세요
 - 255.255.255.244 = 11111111 11111111 11111111 11110100 
 - 그러므로 2^5-2 = 30개
3. 연습 문제 2번에서 주어진 서브넷 마스크로 가능한 서브넷 수를 계산하세요.
 - 2^3 - 2 = 6개
4. 네트워크 195.50.100.0/23에서 호스트를 나타내는 가장 낮은 IP주소를 결정하세요
 - 195.50.100.0 = 11000011 00110010 01100100 00000000
 - 그러므로 11000011 00110010 01100100 00000001 = 195.50.100.1
5. 연습 문제 4번에서 호스트를 나타내는 최상위 IP 주소를 찾으세요.
 - 11000011 00110010 01100101 11111111 = 195.50.101.255

--- 

## 2.4 전송 계층

### (1) 전송 계층 기능
 * 네트워크 애플리케이션 인터페이스 : 대상 컴퓨터에서 작동하고 있는 특정 애플리케이션에 데이터 전송
 * 다중화 : 서로 다른 애플리케이션과 컴퓨터에서 데이터를 받아서 해당 데이터를 수신 컴퓨터에 있는 특정 애플리케이션에 전달
 * 역다중화 : 하나의 컴퓨터에서 여러 네트워크 애플리케이션을 동시에 지원
 * 오류검사, 흐름제어, 검증 : 송신기기와 수신기기 간의 데이터 전달을 보장할 수 있어야 한다.
   - TCP : 광범위한 오류 제어와 흐름 제어 기능을 제공해 성공적인 데이터 전송을 가능하게 하는 연결지향 프로토콜
   - UDP : 매우 기본적인 오류검사를 제공하고, 광범위한 기능이 필요하지 않은 상황을 위한 비연결 프로토콜

### (2) 전송 계층 개념
 * 연결 지향 프로토콜 : 전송 과정에서 통신하는 컴퓨터간의 연결을 설정 및 유지하고, 해당 연결상태를 모니터링
 * 비연결 프로토콜 : 수신 컴퓨터에 단방향 데이터그램을 보내고 데이터가 제대로 전송되는지 수신 컴퓨터에 알려지지 않는다. 또한, 수신 컴퓨터는 데이터를 받고 상태 정보를 송신 컴퓨터로 반환하지 않는다.
 * 포트 : 애플리케이션에서 전송계층 또는 전송계층에서 애플리케이션으로 이어진 통로
 * 소켓 : IP주소와 포트 번호를 합친 주소
 * 다중화 : 여러소스의 입력을 하나의 출력으로 묶는 작업
 * 비다중화 : 단일 소스의 입력을 받아서 다중 출력으로 운반하는 작업
 
### (3) TCP
 * 기능
   - 스트림 지향 처리 : 스트림으로 데이터를 처리, TCP가 미리 포맷된 블록이 아니라 한 번에 하나의 바이트로 데이터를 받아들이는 것을 의미, 데이터를 가변 길이 세그먼트로 포맷한 다음 인터넷 계층으로 전달
   - 리시퀀싱 : 데이터가 목적지에 순서가 정리되지 않은 채로 도착하면 재배열해 순서를 복원
   - 흐름 제어 : 대상 기기가 받을 수 있는 데이터 양을 초과하지 않도록 보장
   - 우선순위 및 보안 : 선택적 보안 및 우선순위 수준의 사양을 요구하지만 제공하지 않는다.
   - 우아한 연결 종료 : 연결이 종료되기 전에 모든 세그먼트를 주고받도록 보장
 * 데이터 포맷
   - 소스포트 : 16비트, 소스 기기의 애플리케이션에 할당된 포트
   - 대상포트 : 16비트, 대상 기기의 애플리케이션에 할당된 포트
   - 시퀀스 번호 : 32비트, SYN 플래그가 1로 설정되지 않은 한 세그먼트의 첫 바이트 시퀀스 번호 / SYN 플래그가 1이면 시퀀스 번호 필드는 시퀀스 번호를 동기화하는데 사용하는 초기 시퀀스 번호 (ISN)을 부여, 첫 옥텟의 시퀀스 번호는 해당 필드에서 보이는 번호보다 1이 더 크다 ( 즉, ISN+1 )
   - 승인 번호 : 32비트, 수신 컴퓨터가 수신할 다음 순서 번호로 마지막 수신한 바이트의 시퀀스 번호 +1
   - 데이터 오프셋 : 4비트, 헤더 길이 및 데이터 시작 위치
   - 예약 : 6비트, 향후 개발을 위해 제공한 것
   - 제어 플래그 : 각 1비트, 세그먼트에 대한 특별 정보
   - URG : 긴급 상황
   - ACK : 승인 번호 필드가 중요함
   - PSH : 파이프라인을 통해 지금까지 전송된 모든 데이터를 수신 애플리케이션으로 푸쉬
   - RST : 연결 리셋
   - SYN : 시퀀스 번호가 동기화되리라는 것을 알리고 연결의 시작을 표시
   - FIN : 더 전송할 데이터가 없음
   - 윈도우 : 16비트, 흐름제어를 위한 매개변수, 자유롭게 전송할 수 있는 마지막으로 확인한 시퀀스 번호를 넘어선 시퀀스 번호의 범위를 정의
   - 체크섬 : 16비트, 무결성 확인
   - 긴급 포인터 : 16비트, 긴급정보에 대한 시작점을 표시하는 시퀀스 번호를 가리키는 오프셋 포인터
   - 옵션 : 작은 옵션 설정 중 하나를 지정
   - 패딩 : 32비트 경계에서 데이터가 시작하도록 보장하는 추가 0비트
   - 데이터
 * 연결
   - 수동 개방 : 주어진 애플리케이션 프로세스는 TCP에 TCP포트를 통해 들어오는 연결 요청을 받을 준비가 되었음을 알림 (서버)
   - 능동 개방 : 애플리케이션은 수동 연결 상태에 있는 다른 컴퓨터에 TCP 연결을 요청 ( 클라이언트 )
   - 3방향 핸드셰이크 : 연결을 위한 메세지 교환
 * 흐름 제어
   - 슬라이딩 윈도우 : TCP가 사용하는 흐름 제어 방식, 송신 컴퓨터는 버퍼사이즈 필드라고도 하는 윈도우 필드를 사용해서 송신 컴퓨터가 전달할 수 있는 마지막으로 확인된 시퀀스 번호를 초과하는 시퀀스 번호의 윈도우를 정의하고 다음 응답을 받을 때까지 해등 윈도우를 초과해서 송신할 수 없다.
 * 연결 종료
   - 대기 상태 : FIN플래그 1이 되었을 때, 큐에 있는 세그먼트를 수신하고 처리하지만 애플리케이션으로부터 추가로 데이터를 받지는 않는다.
   - 연결 종료 : FIN플래그에 대한 응답을 확인하면 연결을 종료한다.

### (4) UDP
 * 목적 : 애플리케이션 계층에 데이터그램을 노출하는 것
 * 소스포트 : 16비트, 소스 기기의 애플리케이션에 할당된 포트
 * 대상포트 : 16비트, 대상 기기의 애플리케이션에 할당된 포트
 * 길이 : 16비트, 데이터그램의 길이를 옥텟으로 식별
 * 체크섬 : 16비트,무결성 확인

### (5) 방화벽
 * 특정 포트로의 접근을 차단하는 것

### 퀴즈
1. TCP 포트 25에는 어떤 서비스가 작동합니까?
 - SMTP : 이메일 전송에 사용하는 네트워크 프로토콜
2. UDP 포트 25에는 어떤 서비스가 작동합니까?
 - DNS : 도메인 이름을 호스트의 네트워크의 주소로 바꾸거나 그 반대 변화를 
3. TCP로 보낼 수 있는 가장 큰 레코드 크기는 얼마입니까?
 - TCP는 스트림 지향 처리이므로 데이터 레코드 개념이 존재하지 않는다.
4. TCP 능동 연결 상태와 TCP  수동 연결 상태의 차이점은 무엇입니까?
 - 수동 개방 : 주어진 애플리케이션 프로세스는 TCP에 TCP포트를 통해 들어오는 연결 요청을 받을 준비가 되었음을 알림 (서버)
 - 능동 개방 : 애플리케이션은 수동 연결 상태에 있는 다른 컴퓨터에 TCP 연결을 요청 ( 클라이언트 )
5. TCP 연결을 위한 최소 단계는 몇 단계입니까?
 - 3핸드 셰이크

### 연습문제
* 다음 목적 중 하나를 만족하는 나만의 네트워크 서비스를 만든다고 가정하겠습니다. 각 상황에 대해서 TCP 혹은 UDP 전송 프로콜 중 어떤 것으로 서비스를 설계할지 다음 요소를 고려해 생각해보세요. 
 * 뇌 수술에 대한 실시간 교육을 제공하기 위해 특수 하드웨어 인터페이스를 통한 원격 사용자와 통신하기
  - 실시간으로 데이터를 주고받아야 하는 상황에서는 신뢰성보다는 속도가 중요함으로 UDP
 * 고성능 클러스터에 사용되는 컴퓨터에 주기적인 통계 정보를 효율적으로 전달하기
  - 실시간 서비스가 아니며, 통계정보의 누락은 위험하기 때문에 TCP
 * 특수 장치가 환경 데이터를 홈 네트워크에 전달하기
  - 실시간 서비스가 아니며, 환경 데이터가 홈 네트워크에 영향을 줄 수 있으므로 TCP
  
  
 
