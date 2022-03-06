## 목차

1. [TCP/IP 기초](#1-TCP/IP-기초)   
1.1 [TCP/IP는 무엇인가](#1.1-TCP/IP는-무엇인가)   
1.2 [TCP/IP는 어떻게 작동하는가](#1.2-TCP/IP는-어떻게-작동하는가)
2. [TCP/IP 프로토콜 시스템](#2-TCP/IP-프로토콜-시스템)   
2.1 [네트워크 접근 계층](#2.1-네트워크-접근-계층)   
2.2 [인터넷 계층](#2.2-네트워크-접근-계층)   
2.3 [서브넷팅과 CIDR](#2.3-서브넷팅과-CIDR)   
2.4 [전송 계층](#2.4-전송-계층)   
2.5 [응용 계층](#2.5-응용-계층)   
3. [TCP/IP 네트워크](#3-TCP/IP-네트워크)   
3.1 [라우팅](#3.1-라우팅)   
3.2 [연결하기](#3.2-연결하기)   
3.3 [이름확인](#3.3-이름확인)   
3.4 [TCP/IP 보안](#3.4-TCP/IP-보안)   
3.5 [구성하기](#3.5-구성하기)   
3.6 [IPv6](#3.6-IPv6)   
4. [도구와 서비스](#4-도국와-서비스)   
4.1 [클래식 도구](#4.1-클래식-도구)   
4.2 [클래식 서비스](#4.2-클래식-서비스)   
5. [인터넷](#5-인터넷)   
5.1 [인터넷 자세히 살펴보기](#5.1-인터넷-자세히-살펴보기)   
5.2 [HTTP, HTML 및 월드 와이드 웹](#5.2-HTTP,-HTML,-및-월드-와이드-웹)   
5.3 [웹 서비스](#5.3-웹-서비스)

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

---

## 2.5 응용 계층

### (1) TCP/IP 응용 계층
 * 정의 : TCP와 UDP 포트로부터 정보를 주고받는 네트워크 인식 스포트웨어 구성 요소의 모음

### (2) TCP/IP 응용 계층에 상응하는 OSI 계층
 * 응용 계층 : 사용자 애플리케이션을 위한 서비스와 네트워크 접근을 제공하는 구성 요소
 * 표현 계층 : 데이터를 플랫포모 중립 형태로 변환하고 암호화 및 데이터 압축을 처리
 * 세션 계층 : 네트워크로 연결된 컴퓨터의 애플리케이션 간의 통신을 관리, 이름 확인 기 능이나 보안 같이 전송 계층에서 없는 통신 관련 기능 제공

### (3) 네트워크 서비스
 * 파일 서비스, 원격 접근 서비스, 이메일과 HTTP 웹 서비스 프 로토콜 같은 사용자 경험을 제공하는 다양한 네트워크 서비스 제공
 * 파일 및 프린트 서비스
   * 프린트 서버 : 프린터를 작동시키고 해당 프린터에 요청된  문서 출력을 처리
   * 파일 서버 : 하드 디스크 드라이브 같은 데이터 저장 장치를 작동시키고 해당 장치에 쓰기 및 읽기 요청을 처리
 * 이름 확인 서비스 : 사전 정의되고 사용자에게 친숙한 영숫자 이름을 IP주소에 매핑하는 과정
 * 원격 접근
   * 리다이렉터 : 로컬 컴퓨터의 서비스 요청을 가로채서 해당 요청이 로컬에서 처리되어야 하는지 또는 네트워크의 다른 컴퓨터로 전달되어야 하는지 확인, 리퀘스터

### (4) API
 * 애플리케이션이 운영 환경의 다른 부분에 접근하기 위해 사용할 수 있는 프로그래밍 구성 요소의 잘 정의된 집합체

### (5) 퀴즈
1. 연결을 확인할 수 있는 네트워크 유틸리티는 무엇입니까?
  - PING
2. 웹 페이지를 불러오는 데 사용되는 응용 계층은 무엇입니까?
  - HTTP, 사용자 정의 도구를 구축하기 위한 웹 관련 프로토콜 및 구성 요소 집합
3. 메일을 가져오는 데 사용되는 두 응용 계층은 무엇입니까?
  - IMAP : 이메일 메시지에 접근하는데 사용하는 공통 프로토콜
  - POP : 메일 서버에서 이메일을 내려받는 데 사용되는 프로토콜
4. 호스트 이름을 IP 주소와 매핑하는 데 사용되는 프로토콜은 무엇입니까?
  - DNS
5. 컴퓨터 시간을 동기화하는 데 사용되는 프로토콜은 무엇입니까?
  - NTP

---
# 3 TCP/IP 네트워크

## 3.1 라우팅

### 라우팅 과정

  1. 라우터는 연결된 네트워크 중 하나에서 데이터를 수신
  2. 라우터는 데이터를 프로토콜에서 인터넷 계층으로 전달
  3. 라우터는 IP헤더에서 대상 주소를 확인
  4. 라우팅 테이블을 통해 해당 데이터를 어디로 전달할지 결정
  5. 해당 데이터를 전송에 적절한 네트워크 접근 계층 소프트웨어와 어댑터에 전달

### 라우팅 유형

* 정적 라우팅 : 네트워크 관리자가 라우팅 정보를 수동으로 입력
* 동적 라우팅 : 라우팅 프로토콜을 사용해 얻은 라우팅 정보를 바탕으로 라우팅 테이블을 동적으로 생성

### 라우팅 테이블
 * 대상 네트워크 ID를 데이터그램이 대상 네트워크에 도달하는 경로의 중간 지 점인 다음 홉의 IP주소에 맵핑

### 직접 라우팅, 간접 라우팅
 * 직접 라우팅 : 라우터가 모든 서브넷에 직접적으로 연결되어 있는 것 (소규모, 단순 및 영구 네트워크에 효과적 )
 * 간접 라우팅 : 라우터가 모든 서브넷에 직접적으로 연결되지 않은 것

### 동적 라우팅 알고리즘
 1. 거리 벡터 라우팅
   * 라우터 간 필요한 통신을 최소화하고, 라우팅 테이블의 데이터양을 최소화하기 위한 것
   * 라우터가 모든 네트워크 세그먼트의 완전한 경로를 알 필요 없이 세그먼트에 지정된 데이터그램을 어느 방향으로 보낼지만 아는 것
   * 세그먼트 간의 거리는 데이터그램이 한 세그먼트에서 다른 세그먼트로 반드시 교차해야 하는 라우터의 개수 (홉 카운트)
 2. 링크 상태 라우팅
   * 모든 라우터가 네트워크 토 폴로지 자체 내부 맵을 작성
   * 라우터가 직접적으로 연결된 네트워크의 다른 라우터와 링크의 상태도 포함하여 토폴로지를 구성 
 
### 외부라우터
 * 자율네트워크와 라우팅 정보를 주고받으며, 자신과 인접한 자율 네트워크의 라우팅 정보를 유지
 * 프로토콜 : 경계 게이트웨이 프로토콜(BGP), ASN을 사용해서 인터넷의 맵을 설계하고 자율 시스템을 통해 CIDR기반의 클래스리스 IP주소를 경로에 연결
 
### 내부라우터
 * 자율네트워크 내에서 작동하는 것
 * 내부 게이트웨이 : 라우팅 정보를 공유하는 자율 지역 내의 라우터
 * RIP
   * 거리 벡터 프토코콜
   * 홉 카운트로 목적지에 도달하는 최상의 경로 설정
   * 수신 대기 라우터가 필요하며, 다른 라우터로부터 경로와 홉 카운트 메시지를 수신하고 통합
   * 능동 RIP 노드 : 일반적인 거리 벡터 방식으로 데이터를 교환하는 과정에 참여하는 라우터
   * 수동 RIP 노드 : 호스트 컴퓨터
   * 능동 RIP 참여자 : 자신의 라우팅 테이블을 다른 라우터로 전송하고 다른 라우터로부터 변경 사항을 수신 대기
   * 수동 RIP 참여자 : 변경사항을 수신 대기하지만 자신의 라우팅 테이블은 전파하지 않음
   * 이미 존재하는 홉카운트가 수신 후 증가한 홉 카운트와 일치한다면 기존 경로를 유지함으로써 불필요한 경로 혼동을 방지
   * 라우터의 개수가 너무 많아지면 라우팅 테이블의 느린 수렴때문에 홉의 최대 개수를 15개로 제한하지만, 계층 배열로 더 크게 구성할 수 있음
 * OSPF
   * 링크 상태 라우팅
   * 각 라우터는 라우터 ID를 할당받는다.
   * 토폴로지 내에서 라우터 ID를 사용해 라우터를 구별
   * 각 라우터는 루트에서 네트워크를 트리 형식으로 구성한다. ( 최단 경로 트리 )
 
### 퀴즈
 1. 동적 라우팅의 두 가지 종류는 무엇입니까?
   1) 거리 벡터 라우팅
     * 라우터 간 필요한 통신을 최소화하고, 라우팅 테이블의 데이터양을 최소화하기 위한 것
     * 라우터가 모든 네트워크 세그먼트의 완전한 경로를 알 필요 없이 세그먼트에 지정된 데이터그램을 어느 방향으로 보낼지만 아는 것
     * 세그먼트 간의 거리는 데이터그램이 한 세그먼트에서 다른 세그먼트로 반드시 교차해야 하는 라우터의 개수 (홉 카운트)
   2) 링크 상태 라우팅
     * 모든 라우터가 네트워크 토 폴로지 자체 내부 맵을 작성
     * 라우터가 직접적으로 연결된 네트워크의 다른 라우터와 링크의 상태도 포함하여 토폴로지를 구성 
 2. 라우터가 몰티홈이 되야하는 이유는 무엇입니까?
   * 두 개 이상의 네트워크와 상호 연결하기 위해
 3. 외부 라우터에 가장 흔한 라우터 프로토콜은 무엇입니까?
   * BGP, Border Gateway Protocol의 약자로 서로 다른 AS를 연결해 주는 경계 게이트웨이 프로토콜
 4. 클래스리스 라우팅이 더 효율적인 이유는 무엇입니까?
   * 다중 클래스 네트워크를 단일 엔티티로 취급할 수 있게 해서 라우터 간 반드시 전송해야 하는 필수 정보를 줄일 수 있음.
 5. OSPF는 어떤 유형의 라우팅의 예입니까?
   * 내부 라우터

### 연습문제
 1. 현재 사용되는 라우팅 프로토콜 3개를 나열하세요.
   * RIP
    * 거리 벡터 프토코콜
    * 홉 카운트로 목적지에 도달하는 최상의 경로 설정
    * 수신 대기 라우터가 필요하며, 다른 라우터로부터 경로와 홉 카운트 메시지를 수신하고 통합
    * 능동 RIP 노드 : 일반적인 거리 벡터 방식으로 데이터를 교환하는 과정에 참여하는 라우터
    * 수동 RIP 노드 : 호스트 컴퓨터
    * 능동 RIP 참여자 : 자신의 라우팅 테이블을 다른 라우터로 전송하고 다른 라우터로부터 변경 사항을 수신 대기
    * 수동 RIP 참여자 : 변경사항을 수신 대기하지만 자신의 라우팅 테이블은 전파하지 않음
    * 이미 존재하는 홉카운트가 수신 후 증가한 홉 카운트와 일치한다면 기존 경로를 유지함으로써 불필요한 경로 혼동을 방지
    * 라우터의 개수가 너무 많아지면 라우팅 테이블의 느린 수렴때문에 홉의 최대 개수를 15개로 제한하지만, 계층 배열로 더 크게 구성할 수 있음
  * OSPF
    * 링크 상태 라우팅
    * 각 라우터는 라우터 ID를 할당받는다.
    * 토폴로지 내에서 라우터 ID를 사용해 라우터를 구별
    * 각 라우터는 루트에서 네트워크를 트리 형식으로 구성한다. ( 최단 경로 트리 )
   * BGF : 서로 다른 AS를 연결해 주는 경계 게이트웨이 프로토콜
 2. OSPF가 어떻게 RIP보다 더 유연한 최상 경로 선택 방식을 제공하는지 설명하세요.
   * 거리 벡터 라우팅은 효율성이 데이터그램이 교차해야 하는 라우터 개수와 일치한다고 가정할 때만 가치 있는 접근 방식이다.
   * 느린 링크를 통한 경로는 홉의 개수가 동일하다고 해도 고속 링크를 통한 경로보다 더 오래걸린다.
   * 거리 벡터 라우팅은 모든 목적지에 대한 라우팅 테이블 엔트리를 유지해야 함으로, 대규모 라우터 그룹에는 제대로 확장할 수 없다.
 3. 정적 라우팅의 장점과 단점을 나열하세요.
   * 장점 : 경로 설정을 위한 부하가 적다. 다른 네트워크를 거치지 않아 보안성이 좋다.
   * 단점 : 대규모 네트워크에 적합하지 않다. 네트워크 관리자의 시간 투자 필요. 변화에 빠르게 적응할 수 없다.

---
## 3.2 연결하기

### 무선 네트워크
 * 노드가 움직일 수 있음으로, 네트워크는 반드시 참여하고 있는 기기의 위치 변화에 반응할 수 있어야 한다.
 * 즉, 다른 네트워크 세그먼트로 이동한다면 다른 주소로 구성

### 독립 기본 서비스 셋
 * 임시 네트워크, 소규모 컴퓨터 집합에 적합
 * 참여 컴퓨터의 근접성에 의존
 * 연결 관리를 위한 인프라를 제공하지 않음
 * 로컬LAN 또는 인터넷과 같은 더 큰 네트워크와 연결할 방법을 제공하지 않기에 제한적

### 인프라 기본 서비스 셋
 * 액세스 포인트 : 무선 브로드 캐스트를 통해 무선 네트워크와 통신하고 기존 연결을 통해 일반 이더넷 네트워크에 연결

### 802.11
 * 로빙기기가 네트워크가 제공하는 영역 내 모든 공간에서 이동 중에도 연결 상태를 유지하는 것
 * OSI 데이터 링크 계층, 물리 계층 (TCP/IP 네트워크 접근 계층)을 정의
 * 프레임 형식
  * 프레임 제어 : 프로토콜 버전
  * 지속/ID : 전송 지속 시간의 추정치를 제공하는 필드
  * 주소 필드 : 48비트 물리 주소 필드
   * 수신지 주소 : 프레임이 지정된 기기
   * 송신지 주소 : 프레임을 보내는 기기
   * 수신기 주소 : 프레임을 처리해야 하는 무선 기기
   * 송신기 주소 : 무선네트워크에 프레임을 전달하는 기기
  * 시퀀스 제어 : 프레그먼트 번호이자 프레임의 시퀀스 번호
  * 프레임 바디 : 프레임과 함께 전송되는 데이터, 상위 계층 프로토콜 헤더를 포함
  * 프레임 검사 순서 : 전송 오류를 검사하고, 전송 간 프레임이 바뀌었는지를 검증하는 순환 중복 검사
 * 연관 : 기기가 무선 네트워크를 통해 이동하면서 이용할 수 있는 가장 가장 가까운 액세스 포인트를 등록하는 과정
 
### 802.11 보안
 * 프로토콜 : 유선 동등 프라이버시(WEP), 확장 가능 인증 프로토콜(EAP), 와이파이 보호 접근(WPA2)
 * WEP 목표
  * 기밀유지 : 도청방지, RC4 알고리즘
  * 무결성 : 데이터가 변경되지 않았음을 보장, RC4 알고리즘
  * 인증 : 통신 당사자가 자신이 누구인지, 네트워크에서 작동하는데 필요한 권한이 있는지 확인

### 모바일 IP
 * 홈 네트워크의 영구 주소를 유지
 * 홈 네트워크에 위치한 홈 에이전트(특수 라우터)는 기기의 현재 위치를 연구주소에 연결하는 테이블을 유지, 관리
 * 기기가 새로운 네트워크에 진입하면, 네트워크에서 작동하는 외부 에이전트를 통해 방문자 목록에 모바일 장치를 추가하고, 홈 에이전트에 기기의 현재 위치에 대한 정보를 보낸다
 * 데이터그램이 홈 네트워크에 도착하면, 데이터그램은 외부 네트워크로 캡슐화되어 전달되는 방식

### 블루투스
 * OSI 데이터 링크 계층, 물리 계층 (TCP/IP 네트워크 접근 계층)을 정의
 * 짧은 거리 내에서 작동하는 무선장치를 위한 안정적이고 고 성능 환경을 제공
 * 네트워크 액세스 포인트를 통해 기존 네트워크에 무슨 네트워크를 연결

### 전화 접속 네트워크
 * 포인트 투 포인트 연결
 * 여러 컴퓨터가 전송 매체를 공유할 수단을 제공할 필요가 없기 떄문에 LAN기반 구성보다 단순
 * 전화선을 통한 전송률은 이더넷과 같은 LAN기반 네트워크의 전송률보다 낮으므로, 프로토콜 자체의 데이터 오버헤드를 최소화하는 프로토콜이 적합
 * 단순히 정보를 전달하는 수단이므로 논리 주소 지정과, 인터네트워크 오류 제어는 필요하지 않음

### 포인트 투 포인트 프로토콜(PPP)
 * 모뎀 기반 네트워크 기능을 완전하게 보완하기 위해 상호작용하는 프토코로의 집합체
 * 주 목적은 데이터그램을 전송하는 것
 * 반드시 모뎀 연결을 설정하고 관리하는 자신의 프로토콜과 관련된 정보와 함께 데이터를 전송해야 한다.
 * 집합체를 아래 3개의 카테고리로 분리
  * 다중 프로토콜 데이터그램 캡슐화 수단 (단, 하나 이상의 프로토콜 시스템에서 데이터그램을 수신할 준비가 되어 있어야 함)
  * 연결 설정, 구성 및 테스트를 위한 링크 제어 프로토콜(LCP)
  * 상위 계층 프로토콜 시스템을 지원하는 네트워크 제어 프로토콜(NCP)
 * 데이터 형식
  * 프로토콜 : 프로토콜 유형에 대한 식별 번호를 제공하는 필드
  * 동봉 데이터 : 프레임과 함께 전송되는 제어 패킷 혹은 상위 계층 데이터그램
  * 패딩 : 프로토콜 필드에 지정된 프로토콜이 요구하는 추가 바이트
 * 연결과정
  1. LCP 를 사용하여 PPP 연결에 필요한 최대 허용 프레임 길이와 인증과정에서 사용할 인증 프로토콜의 종류 등을 PPP 단말과 서버간에 협상한다.
  2. LCP 단계에서 결정된 프로토콜(PAP or CHAP)을 사용하여 인증절차를 수행한다.
  3. 인증 성공 후, IPCP 를 사용하여 네트워크계층 프로토콜에 대한 설정값을 할당한다.
  4. 상기 과정이 모두 성공하면 IP 와 같은 네트워크계층 프로토콜을 PPP 의 Payload 로 담아 전송한다.

### 브릿지
 * 물리주소로 패킷을 필터링하고 전송하는 연결장치, OSI 데이터링크 계층에서 작동

### 허브
 * 자신의 포트 중 하나에서 전송을 수신하고,해당 전송을 다른 모든 포트에 알리는 네트워크 장치

### 스위치
 * 자신의 포트 중 하나로 수신한 데이터를 어디로 보내야 할지 알고 있음.
 * 각 포트를 해당 포트에 연결된 어댑터의 물리 주소에 연결하고, 프레임의 목적지 주소를 확인하고 연결된 포트에 프레임을 송신
 * 스위칭 방식
   * 컷 스루 : 목적지 주소를 얻자마자 프레임 전송을 시작
   * 저장 및 전송 : 재전송 이전 모든 프레임을 수신, 재전송 처리의 속도를 늦추지만 잘못된 프레임을 필터링하기에 전체적인 성능을 높임

###  퀴즈
 1. 독립 기본 서비스 집합 무선 네트워크의 다른 이름은 무엇입니까?
  * 임시네트워크
   * 소규모 컴퓨터 집합에 적합
   * 참여 컴퓨터의 근접성에 의존
   * 연결 관리를 위한 인프라를 제공하지 않음
   * 로컬LAN 또는 인터넷과 같은 더 큰 네트워크와 연결할 방법을 제공하지 않기에 제한적
 2. 허브와 스위치의 차이점은 무엇입니까?
   * 허브 : 자신의 포트 중 하나에서 전송을 수신하고,해당 전송을 다른 모든 포트에 알리는 네트워크 장치
   * 스위치 : 자신의 포트 중 하나로 수신한 데이터를 어디로 보내야 할지 알고 있음.

---
## 3.3 이름확인

### 호스트 파일
 * 호스트 이름을 IP주소와 연관시키는 테이블을 가진 파일, 소규모이자 고립된 TCP/IP 네트워크를 위한 이름 확인을 제공하는 방법

### DNS
 * 하나 이상의 특별한 서버에 이름 확인 데이터를 올려놓고 네트워크를 위한 이름 확인 서비스를 제공

###  퀴즈
 1. 별칭에 사용되는 리소스 레코드의 유형은 무엇입니까?
  - CNAME : 정식 이름의 줄임말, A레코드로 표시되는 실제 호스트 이름에 매핑
 2. DS 리소스 레코드와 DNSKEY 리소스 레코드는 왜 다른 서버에 저장되어 있습니까?
  - 자식의 DNSKEY를 검증하기 위해 부모의 DS키를 사용하는 방식이기 때문

---

## 3.4 TCP/IP 보안

### 방화벽
 * 방화벽 : 네트워크 통로에 위치해서, 네트워크의 인바운드 패킷 헤더를 검사, 수락 또는 거부
 * 패킷 필터 : 포트 번호 검사를 통해 패킷의 목적을 결정
 
###  프록시
 * 프록시 서버 : 인터넷 자원에 대한 요청을 가로채서 클라이언트와 요청 대상 서버 간에 중개자 역할을 하며, 클라이언트를 대신해 요청을 전달
 * 리버스 프록시 : 외부 소스로부터 요청을 수신해서 내부 네트워크로 전달

### 퀴즈
1. 프록시 서버는 어떻게 웹 브라우저의 응답 속도를 높입니까?
 - 컨탠츠 캐싱을 통해 접근한 웹 페이지를 복사해 저장해두고 추후 해당 페이지에 대한 요청이 있을 때마다 내부적으로 제공
2. 업데이트하는 것이 왜 중요합니까?
 - 취약점을 악용하는 것을 방지하기 위해
3. 스크립트에 사용자의 입력 문자열의 유형과 길이를 확인하는 단계를 추가해야 하는 이유는 무엇입니까?
 - 버퍼 오버플로, 인젝션 공격을 예방하기 위해

---

## 3.5 구성하기

### 정적 IP 주소 지정 단점
 * 각 클라이언트는 반드시 개별적으로 구성해야하며, IP 주소 공간이나 다른 매개변수를 변경하면 개별적으로 재구성
 * 현재 네트워크와 연결되어 있는지 상관없이 IP주소를 사용
 * 다른 서브네트워크에 할당도리 경우, 수동으로 재구성
 
### DHCP
 * DHCP 서버는 정적 IP주소 정보로 구성
 * TCP/IP 구성은 서버로부터 전송됨으로, 일부 TCP/IP 구성이 네트워크에서 변경된다면 DHCP서버만 업데이트
 * 주소 임대 과정
  1) HDCPDISCOVER : DHCP 클라이언트가 UDP포트 67에서 지정된 데이터그램을 브로드캐스팅(DHCP 발견 메시지, DHCP서버에 대한 요청)
  2) DHCPOFFER : DHCP 서버가 DHCP오퍼라고 하는 응답 데이터그램을 브로드캐스팅을 통해 송신
  3) DHCPREQUEST : 클라이언트는 오퍼를 선택하고, DHCP 요청 데이터그램을 브로드캐스트
  4) DHCPACK : DHCP 서버가 DHCP 요청 데이터그램을 수신하고 응답 데이터그램을 구성

### 릴레이 에이전트
 * DHCP 클라이언트와 서버가 하나 이상의 라우터로 분리된 서로 다른 네트워크에 있는 경우, 중개를 통해 DHCP가 작동할 수 있도록 하는 역할
 * 과정
  1) DHCP 클라이언트로부터 브로드 캐스트 수신
  2) DHCP 서버에 해당 요청을 직접 재전송
  3) DHCP 서버로부터 응답을 수신
  4) 응답을 로컬 세그먼트에 다신 브로드캐스팅

### DHCP 시간 필드
 * T1 : 언제 임대 갱신 프로세스를 시작해야 하는지를 나타내는 시간
 * T2 : DHCP 클라이언트가 모든 DHCP서버에 브로드캐스팅 요청을 시작할 수 있는 시간

### 네트워크 주소 변환(NAT)
 * 로컬 컴퓨터가 인터넷 자원에 연결을 시도하면 NAT 장치가 대신 연결을 시도
 * 로컬 네트워크는 모든 네트워크의 주소 공간을 사용

### 제로 구성
 * 링크 로컬 주소 지정 : 169.254.0.0 ~ 169.254.255.255 사이의 개인 주소 범위에서 IP 주소를 자체 할당
 * 멀티캐스트 DNS :  사전 구성된 호스트 파일이 없는 DNS 이름 확인은 특정 IP 주소와 포트 번호 요청을 통해 IP 주소로 확인
 * DNS 서비스 검색 : 클라이언트가 네트워크에서 가능한 서비스를 배울 수 있는 수단, SRV 리소스 레코드에 대한 쿼리에 의존
  * 인스턴스 : 서비스의 특정 인스턴스
  * 서비스 : 서비스의 이름
  * 도메인 : 서비스의 원천 도메인

### 퀴즈
1. 다른 네트워크의 DHCP 서버로부터 한 네트워크의 DHCP 클라이언트가 IP주소를 임대받기 위해 요구되는 것은 무엇입니까?
 - 릴레이 에이전트
2. DNS-SD는 주로 어떤 DNS 레코드에 의존합니까?
 - SRV 리소스 레코드

---

## 3.6 IPv6

### IPv6 목표
 * 확장된 주소 지정 기능
  * 더 많은 계층적 주소 지정 수준을 제공
  * 주소를 자동으로 구성하는 기능 개선
  * 애니캐스트 주소 지정을 지원해 수신 중인 데이터그램이 가능한 목표 그룹이 주어진 상태에서 가장 가까운 혹은 최적의 목적지에 도달할 수 있도록 함
 * 간단한 헤더 형식
  * IPv4 헤더 필드가 삭제되고, 다른 필드는 선택 사항
 * 확장과 옵션에 대한 지원 개선
  * 선택적 확장 헤더에 일부 헤더 정보를 포함함으로써 메인 헤더의 공간을 낭비하지 않고 가능한 정보 필드의 범위를 넓힘
  * 확장 헤더는 라우터가 처리하지 않아서 전송 과정이 더욱 효율적
 * 흐름 레이블링
  * 데이터그램을 특정 흐름 레벨로 표시
  * 흐름레벨이란 특수 처리 방식이 필요한 데이터그램의 클래스
 * 인증 및 개인 정보 보호 향상
  * 인증, 기밀성, 데이터 무결성 기술 지원

### IPv6 헤더
 * 버전 : 4비트, IP 버전 번호를 식별
 * 트래픽 클래스 : 8비트, 데이터그램에 포함된 데이터 유형을 식별
 * 흐름 레이블 : 20비트, 흐름 레벨 지정
 * 페이로드 길이 : 16비트, 데이터의 길이 결정
 * 다음 헤더 : 8비트, 다음에 나오는 헤더 유형을 정의
 * 홉 제한 : 8비트, 허용되는 나머지 홉 수
 * 송신지 주소  : 128비트, 보낸 컴퓨터의 IP 주소
 * 수신지 주소  : 128비트, 받는 컴퓨터의 IP 주소

### IPv6 확장 헤더
 * 홉셜 옵션 헤더
  * 전송 경로를 따라 라우터를 선택적 정보와 연관시키는 목적
  * 점보 페이로드 : 패딩 옵션으로, 65,535바이트보다 긴 데이터 페이로드를 전송할 때 사용
 * 수신지 옵션 헤더
  * 선택적 정보를 수신 노드에 연결하는 것
 * 라우팅 헤더
  * 데이터그램이 목적지까지 가는 경로를 라우팅하는 하나 이상의 라우터를 명시
  * 데이터 필드
   * 다음 헤더 : 다음에 오는 헤더의 유형을 식별
   * 헤더 길이 : 헤더의 길이를 바이트로 명시
   * 라우팅 유형 : 라우팅 헤더 유형을 명시
   * 남은 세그먼트 : 수신지 이전에 명시적으로 정의된 라우터 세그먼트 수
   * 유형별 데이터 : 주어진 특정 라우팅 유형을 위한 데이터 필드 식별
  * 프레그먼트 헤더
   * 조각난 데이터그램을 재조립하는데 필요한 정보를 포함
   * MTU : 라우터가 전송할 수 있는 가장 큰 단위
   * 경로 MTU : 경로에 보낼 수 있는 가장 큰 데이터 단위
  * 인증 헤더
   * 보안과 인증 정보를 제공
   * 데이터그램이 전송 중에 변경되었는지 결정하는데 사용
  * 암호화된 보안 페이로드 헤더
   * 암호화와 기밀성을 제공
   * ESP 기능을 사용해 전송하려는 일부 또는 모든 데이터를 암호화
  
  
### 서브넷팅
 * 주소의 첫 64비트

### 멀티캐스팅
 * 호스트는 단일 멀티캐스트 ㅈ소를 공유하는 멀티캐스트 그룹에 참여
 * 그룹에 속하지 않은 호스트는 메시지에 신경 쓸 필요가 없음으로  브로드캐스트 보다 효율적
 * 접두사 : FF02::/16

### 링크로컬
 * 라우터를 통과하지 않고 로컬 네트워크 세그먼트 간의 통시에만 사용
 * 접두사 : FE80::/10

### 인접 탐색
 * 로털 네트워크에서 IPv6 주소를 확인하려는 호스트는 주소와 관련된 요청 노드 멀티캐스트 주소를 계산
 * 호스트는 인접 요청 패킷을 송신자가 확인하고자하는 IPv6 주소를 포함한 요청 멀티캐스트 주소에 전송해 응답할 주소의 소유자를 요청
 * 송신자는 자신의 물리 주소도 전송해 응답하기 위한 수신지 주소로 사용
 * IPv6 주소의 소유자는 자신의 물리 주소와 링크 로컬 주소를 포함한 이웃 알림 패킷과 함께 응답

### 자동 구성
 * 물리 주소의 해시를 기반으로 컴퓨터에 링크 로컬 주소를 할당
 * 물리 주소는 모두 고유하고, 링크 로컬 주소 또한 고유하므로, IPv4 제로콘프 네트워크에서 발생하는 몇몇 주소 충돌 문제를 예방
 * 48비트 물리 주소는 표준 번환으로 64비트 문자열 주소로 변환되고, 64비트 결과는 링크 로컬 접두사 FE80::/10 끝에 붙어 완전한 링크 로컬 주소 생성
 * 호스트는 중복 주소 검출 프로세스를 통해서 주소가 로컬 세그먼트에서 사용 중인지 확인하고 사용 중이지 않다면 자동 구성된 주소로 가정

### IPv6 터널
 * IPv6 내에 IPv6를 캡휼화하는 것
 * 터널의 엔드 포인트에 있는 터널 서버는 IPv6 패킷을 받아 IPv4 헤더 안에 포함시키고 원래 IPv6 패킷이 추출되고 대상 IPv6 네트워크에 전송되는 또 다른 엔드 포인트로 전송
 * 접두사 : 2002::/16

### 6in4
 * 프로토콜 헤더에 있는 41값을 사용해 IPv6 터널링 패킷 신호를 보내는 기술
 * 터널 엔드 포인트의 고정 설정을 요구
 * IPv6 주소 내 에 IPv4 목적지 주소를 포함
 

### 6to4
 * IPv6 네트워크가 IPv6를 지원하는 터널 제공자 또는 ISP와 계약되지 않은 경우에도 IPv4 네트워크를 통해 IPv6 패킷을 끼워넣는 것
 * 릴레이 서버는 해당 IPv6 주소를 받아서 IPv4 주소를 추출하고 IPv4 패킷 내에 IPv6 패킷을 캡슐화 한 뒤 목적지 주소에 보낸다.
 * 목적지에서 패킷은 원본 IPv6 패킷이 추출되고 전송되는 애니캐스트 주소 192.88.89.1에서 6to4 릴레이로 전송

### TSP
 * 터널 매개변수의 동적인 협상을 허용하는 기술
 * 서버는 목적지 네트워크의 연결 간으한 엔드 포인트와 연결 매개변수를 협상하여 두 엔드포인트가 연결될 수 있도록 한다.

### 퀴즈
1. 왜 멀티캐스트가 브로드캐스트보다 더 효율적입니까?
 * 그룹에 속하지 않은 호스트는 메시지에 신경 쓸 필요가 없음으로  브로드캐스트 보다 효율적
2. 왜 IPv6 자동 구성이 IPv4 제로콘프 자동 구성보다 더 안정적입니까?
 * 물리 주소는 모두 고유하고, 링크 로컬 주소 또한 고유하므로, IPv4 제로콘프 네트워크에서 발생하는 몇몇 주소 충돌 문제를 예방
3. 6to4를 위해 예약된 IPv6 주소 접두사는 무엇입니까?
 * 2002::/16

---
# 4 도구와 서비스

## 4.1 클래식 도구

### 네트워크 연결 문제
* 프로토콜 장애 또는 잘못된 구성 : 프로토콜 소프트웨어가 작동하지 않거나 올바르게 구성되지 않음
* 회선 문제 : 케이블이 연결되지 않았거나 작동하지 않음
* 잘못된 이름 확인 : DNS 혹은 NetBIOS 이름이 확인되지 않음. IP주소로 리소스에 접근할 수 있지만, 호스트 이름 혹은 DNS 이름으로는 접근할 수 없음
* 과도한 트래픽 : 네트워크가 작동하는 것처럼 보이지만, 느리게 작동

### PING
* 인터넷 제어 메시지 프로토콜(ICMP) Echo Request 명령을 사용해 수신 컴퓨터에 메시지를 전송
* 수신 컴퓨터가 존재하고 작동 중이면 ICMP Echo Reply 메시지를 사용해 응답
* 송신하는 컴퓨터가 응답을 수신하면 핑이 완료되었다는 메시지 출력
* 루프백 주소로 핑을 보내서 TCP/IP가 로컬 컴퓨터에서 올바르게 작동하는지 확인
* 로컬 IP 주소로 핑을 보내서 네트워크 어댑터가 작동하고 로컬 IP주소가 구성되어 있는지 확인
* 기본 게이트웨이로 핑을 보내서 컴퓨터가 로컬 서브넷과 통신하는지 확인하고, 기본 게이트웨이가 온라인 상태인지 확인
* 기본 게이트웨이 이외의 주소로 핑을 보내서 게이트웨이가 성공적으로 로컬 네트워크 세그먼트를 넘어서 패킷을 전달하는지 확인
* 호스트 이름으로 로컬 호스트와 원격 호스트에 핑을 보내서 이름 확인이 작동하는지 확인

### 구성 정보 유틸리티
* 로컬 컴퓨터의 IP 주소, 서브넷 마스크 및 기본 게이트웨이 등의 정보를 출력

### 주소 확인 프로토콜
* IP 주소와 상응하는 물리 주소를 확인하기 위해 사용되는 주요 TCP/IP 프로토콜
* 각 호스트는 ARP 캐시를 유지
* ARP 캐시의 엔트리는 기본으로 동적, 지정된 데이터그램이 전송되고 현재 엔트리가 대상 컴퓨터의 캐시에 존재하지 않을 때 자동으로 캐시에 추가

### 텔넷
* 원격 컴퓨터에 터미널과 같은 접근을 제공하는 구성 요소의 집합
* 텔넷 서버와 텔넷 클라이언트 간의 상호 작용을 정의하는 규칙 시스템인 프로토콜
* 원격 사용자가 입력한 키보드 명령어가 네트워크를 거쳐 다른 컴퓨터의 입력이 되는 수단을 제공하기 위한 목적

### 버클리 원격 유틸리티
* 원격 접근 제 공을 위해 설계된 명령줄 유틸리티 집합
* 신뢰할 수 있는 접근이라는 개념 사용

### 단순 망 관리 프로토콜
* 네트워크에서 원격 장치를 관리하고 모니터링하기 위해 설계된 프로토콜
* SNMP 아키텍처 구성 요소
  * 네트워크 모니터 : SNMP 관리 소프트웨어를 가진 일반 컴퓨터
  * 노드 : 네트워크에 있는 장치
  * 커뮤니티 : 공통 관리 프레임워크의 노드 그룹
* MIB
  * 각 정보의 고유한 주소를 포함하는 계층적 주소 공간
  * 주소 공간에 계층적으로 정렬된 매개변수의 집합
* 단점
  * UDP 위의 애플리케이션 계층에 있으므로, 하위 계층에서 무슨 일이 일어나는지 볼 수 없다.
  * SNMP 모니터와 에이전트가 통신하기 위해 운영 프로토콜 스택이 필요
  * 쿼리 응답 메커니즘은 상당한 네트워크 트래픽 유발
  * MIB 내 수천 개의 주소 장소를 통해 작은 정보 조각을 많이 얻을 수 있음
  * 특정 장치의 정보를 제공하기 위해 설계됨으로 네트워크 세그먼트에서 무슨 일이 일어나는지는 직접 볼 수 없다.

### 원격 모니터링
* 원격 LAN을 모니터링하고 관리할 목적
* 네트워크 미디어에서 직접 데이터를 캡쳐하기에 LAN 전체에 대한 모습을 제공

### 퀴즈
1. 웹 서핑 중 페이지 로딩이 멈췄습니다. 가장 먼저 사용해야 할 문제 해결 도구는 무엇입니까?
 * 일부 사이트에 핑을 보내서 간단한 네트워크 연결 테스트를 진행
2. ARP 캐시의 콘텐츠를 보여 주는 명령어는 무엇입니까?
 * arp -a 명령어를 사용해 모든 ARP 캐시 엔트리를 볼 수 있음.
3. TCP를 통해 어떤 호스트가 연결되었는지 어떻게 볼 수 있습니까?
 * netstat -p TCP를 사용해 설정된 TCP 연결을 표시
4. 일부 route의 버전은 라우팅 테이블을 출력하는 옵션이 없습니다. 어떤 유틸리티를 사용해야 합니까?
 * netstat -r 을 사용해 라우팅 테이블 정보를 확인
5. 텔넷 대신 ssh를 선호하는 이유는 무엇입니까?
 * 암호화 연결을 통해 안전하게 작동

---

## 4.2 클래식 서비스

### HTTP
* 하이퍼텍스트 마크업 언어(HTML)형식으로 데이터와 이미지를 전송하고 요청하기 위한 응용 계층 프로토콜

### 이메일
* 클라이언트 애플리케이션과 서버 애플리케이션 간의 상호 작용에 의존
* 한 쌍의 서버 시스템에 의존하기 때문에 이메일 리더 구성 인터페이스에 '수신 서버'와 '송신 서버'를 구성
* 송신 서버 : 간이 우편 전송 프로토콜(SMTP)을 사용해 사용자로부터 송신 메시지를 받아서 다른 SMTP 서버의 네트워크를 통해 목적지 주소로 전송
* 수신 서버 : POP 혹은 IMAP 프로토콜을 사용해 이메일 계정으로 지정된 메시지를 수신하며, 메시지를 연결하고 접근하기 위해 메일 리더로부터의 요청을 수신

### FTP
* 사용자가 TCP/IP 네트워크를 사 용하는 두 컴퓨터간에 파일을 전송하는 프로토콜
* TCP 프로토콜을 사용하기 때문에 클라이언트와 서버 컴퓨터 간의 신뢰할 수 있는 연결 지향 세션을 통해 작동

### 단순 파일 전송 프로토콜(TFTP)
* TFTP 클라이언트와 TFTP 데몬을 실행하고 있는 TFTP 서버 간에 파일을 전송할 때 사용
* UDP 프로토콜 사용
* 파일을 읽고 쓸 수만 있음

### 파일 및 프린트 서비스
* 네트워크 파일 시스템(NFS) : 사용자가 원격 컴퓨터에 위치한 디렉터리와 파일을 로컬 컴퓨터에 위치한 것처럼 접근 허용
* 서버 메시지 블록 (SMB) : 탐색기, 네트워크 환경 및 맵 네트워크 드라이브 기능과 같은 윈도우 사용자의 네트워크 인터페이스 통합 도구를 지원
* 공용 인터넷 파일 시스템 (CIFS) : 네트워크를 위한 SMB 파일 공유 프로토콜의 확장된 버전이며, 윈도우와 유닉스 환경을 동시에 지원하는 인터넷의 표준 파일 규약의 프로토콜

### 경량 디렉터리 접근 프토콜(LDAP)
* 디렉터리 서비스
* LDAP 서버는 논리적이고 트리와 같은 계층으로 구성된 네트워크 리소스 정보의 디렉터리를 유지 관리
* LDAP 디렉터리는 파일 디렉터리 구조처럼 계층적으로 구성
* 각 엔트리는 트리에 자신의 위치를 정의하는 식별이름(DN)을 갖는다.
* 식별이름(DN) : 자신의 컨테이너와 엔트리가 있는 컨테이너의 계층을 정의하는 일련의 구성 요소와 컨테이너 내의 엔트리를 고유하게 정의하는 상대 식별이름(RND)으로 구성
* 도메인 구성 요소(DC) : 디렉터리 구조를 정의하는 중첩 컨테이너 체인의 항목
* 조직 단위(OU) : 관리 편의성을 위한 컨테이너 그룹화 항목
* 정식 이름(CN) : 컨테이너에 고유한 객체의 인간 친홪거 이름

### 퀴즈
1. FTP의 put과 mput 명령어의 차이점은 무엇입니까?
 - put : 하나의 명령으로 하나의 파일을 전송
 - mput : 하나의 명령으로 여러 파일을 전송
2. TFTP를 사용해 디렉터리의 파일을 나열할 수 있습니까?
 - tftp는 파일을 읽고 쓸 수만 있으며, 디렉터리에 있는 컨텐츠를 나열하거나 디렉터리를 생성 또는 삭제하거나 ftp처럼 사용자 로그인을 허용할 수 없음.
3. 유닉스/리눅스 삼바 파일 서버에 사용되는 파일 서비스 프로토콜은 무엇입니까?
 - 서버 메시지 블록(SMB) : 탐색기, 네트워크 환경 및 맵 네트워크 드라이브 기능과 같은 윈도우 사용자의 네트워크 인터페이스 통합 도구를 지원

---
# 5 인터넷

## 5.1 인터넷 자세히 살펴보기

### URI
* 통합 자원 식별자
* 인터넷의 리소스를 식별하기 위해 사용하는 텍스트 문자열

### URL
* 유일 자원 지시자
* 스킴 : 요청을 해석하기 위해 시스템을 식별
* 권한 : URL에 지정된 서비스에 접근하기 위해 필요한 정보 제공 ( 이름, 비밀번호, 호스트, 포트 )

### 퀴즈
1. 티어1과 티어2 네트워크의 차이점은 무엇입니까?
 - 티어1 : 다른 모든 티어1 네트워크에서 트래픽을 무료로 전달하는 피어링 장치를 갖음
 - 티어2 : 티어1 제공자에게 접근을 임대, 다른 티어2 제공자와 피어링 관계를 맺어 지역 백본 형성, 다운스트림 클라이언트를 위한 중복 경로 제공
2. URL의 어느 부분이 스킴입니까?
 - 요청을 해석하기 위해 시스템을 식별하기 위한 부분
3. URL에서 스킴은 어디에 위치합니까?
 - 콜론, 이중 슬래쉬 앞
4. 인터넷에서 일반적으로 사용되는 네 가지 스킴은 무엇입니까?
 - http, https, ftp, file
5. URL의 대상 디렉터리에서 파일 이름이 생략되어 있다면 대부분의 웹 서버에서 기본적으로 보내는 파일은 무엇입니까?
 - 도메인의 웹 페이지, 일반적으로 index.html

---

## 5.2 HTTP, HTML 및 월드 와이드 웹

### HTML
* HTTP의 과정을 통해 전달되는 페이로드

### CSS
* HTML을 사전 정의된 문자나 단락 스타일의 목록에서 고를 수 있는 전자 출판 도구, 또는 최신 워드 프로세서처럼 만들기 위한 것
* 스타일 : 폰트 크기, 색상, 간격, 패딩 및 여백 같은 매개변수 집합

### HTTP
* 응용 계층 수준이 프로토콜
* HTML 문서를 전송하는 목적

### 스크립팅
* 서버 사이드 스크립팅 : 서버가 클라이언트에서 입력을 받아 처리
* 클라이언트 사이드 스크립팅 : 스크립트를 나머지 HTML코드와 텍스트와 함께 전송하고 스크립트는 브라우저가 실행

### 시멘틱 웹
* 자원 기술 프레임워크(RDF) : 의미를 나타내는 관계를 표현하기 위한 프레임 워크, 트리플 ( 주제, 술어, 목적어 )

### 퀴즈
1. HTTP가 협상 단계를 지원하는 이유는 무엇입니까?
- 서버와 브라우저의 설정이 다른 경우, 협상 단계를 통해 특정 형식 및 환경 설정 옵션을 공통으로 설정
2. HTML 문서의 주요 섹션은 무엇입니까?
- <head>, <body>
3. 책 제목과 가격 정보와 함께 백엔드 데이터베이스를 포함한 웹 사이트가 있습니다. 사용자에게 해당 정보를 제공하기 위해 서버 사이드 스크립트를 사용해야 합니까? 아니면 클라이어늩 사이드 스크립트를 사용해야 합니까?
- 서버 사이드 스크립트를 사용하는 것이 안전함
4. 막 새로운 시스템을 설치해 잘 작동하고 있는데, 웹 사이트에 가서 PDF 파일을 클릭하면 열리지 않습니다. 어떻게 고쳐야 합니까?
- 브라우저가 PDF 파일을 인식하고, 읽을 수 있도록 설정
5. RDF 트리플의 세 부분은 무엇입니까?
- 주어, 술어, 목적어
6. 왜 일부 전문가들은 어도비 플래시 및 유사 도구가 몇 년 안에 영향력을 잃을 것이라 생각합니까?
- HTML5는 드로잉, 임베디드 오디오 및 비디오 등 다양한 기능이 포함됨.
 
---
 
## 5.3 웹 서비스

### 퀴즈
1. CMS 도구가 보통 웹 브라우저를 통해 접근할 수 있는 이유는 무엇입니까?
 - CMS는 웹 서버에서 작동하는 웹 서버의 확장 기능이기 때문에
2. 피어 투 피어 네트워크의 특징은 무엇입니까?
 - 전체 네트워크의 컴퓨터가 클라이언트와 서버의 역할을 수행
3. XML 스키마는 무엇입니까?
 - XML 데이터를 서식화하고 해석하기 위한 로드맵, 스키마 문서를 통해 XML 데이터의 유효성을 확인하기 쉽고, XML 데이터를 분석 및 처리하는 새로운 클라이언트 애플리케이션을 만들기 쉬움
4. HTTP PUT과 POST 방식의 차이점은 무엇입니까?
 - PUT : 리소스를 직접 생성 혹은 수정 ( 전체 리소스의 컨텐츠를 교체 ) 
 - POST : 서버에 데이터를 전송해 리소스를 수정 ( 서버에 정보를 접수해 업데이트가 어떻게 진행되는지 추정하지 않고, 리소스를 업데이트하기 위해 사용 
5. REST가 PUT을 강조하는 이유는 무엇입니까?
 - PUT은 POST와 달리, 동일한 행동은 동일한 결과를 이끌어냄으로 명확성과 단순성에 확실한 가치를 두는 것을 강조
6. 왜 많은 전문가가 다른 유사 웹 서비스 아키텍처와 비교해 REST가 더 안전하다고 생각합니까?
 - REST 모델은 서버 내부와 인터페이스로부터 모든 작업을 숨기기 때문에 보안적인 관점에서 다른 기술보다 안전함.
 
 
 
