AZ-104 Day #1
===================

### Notes
- 자료 공유 (Onedrive)
    > https://1drv.ms/u/s!AmlADRmU8M8uk_Zx845G11GdHVqp1A?e=QluzWB

- 추가 학습 자료

    > ### DOCS
    > https://learn.microsoft.com/ko-kr/docs/
    > ### CERTIFICATION
    > https://learn.microsoft.com/ko-kr/certifications/
    > ### Learn Profile
    > https://learn.microsoft.com/ko-kr/users/me<hr>

---
### Azure 구조
    조직 - 테넌트 - 엔트라 ID [무료]
                ㄴ 구독 [유료]

테넌트는 조직을 **표상**함.

Entra ID를 [tName] 으로 생성하면,
tName.onmicrosoft.com 으로 기본 도메인 명이 부여됨

사용자 지정 도메인을 등록하려면 [Entra ID] 설정 콘솔에서 도메인 소유권을 증명하면 됨.

---
### 테넌트
하나의 조직을 표상 (?)

---
### Entra ID
Microsoft 에서 제공하는 많은 서비스들에 대해서
SSO 를 제공해주는 솔루션

Active Directory에서 [인증] 관련 기능만 세분화 해서 제공

HTTP, HTTPS 기반의 통신 채널을 메인으로 지원함.

하나의 Entra ID 는 여러 조직 (테넌트)에 속할 수 있음.

#### 개념
    
ID : 
> 인증할 수 있는 개체 (Service Principal?)

계정 : 
> 연결된 데이터가 있는 ID

Microsoft Entra ID 계정 : 
> Microsoft Entra ID 또는 기타 Microsoft 클라우드 서비스를 통해 만든 ID (also able 사용자 지정 도메인)

테넌트 / 디렉터리:

신뢰할 수 있는 전용 인스턴스. 조직이 Microsoft 클라우드 서비스 구독에 등록할 때 테넌트가 자동으로 생성됨<br>
* 추가 인스턴스를 만들 수 있음
* Microsoft Entra ID는 ID 서비스를 제공하는 기본 제품임
* 테넌트 라는 용어는 단일 조직을 나타내는 단일 인스턴스를 의미
* 테넌트 와 디렉터리는 종종 같은 의미로 사용됨

도메인:
> 하나의 Entra ID 하위에 여러 도메인들이 포함될 수 있음.

#### Entra ID > Device ID 종류

|등록 디바이스|조인 디바이스|하이브리드 조인 디바이스|
|---|---|---|
|BYOD 지원 (Bring-Your-Own-Device)|클라우드 우선 또는 클라우드 전용, 조직용|Active Directory 컴퓨터 인증을 사용하는 디바이스에 Win32 앱을 배포한 경우|
|등록된 디바이스는 Microsoft 계정을 사용하여 로그인함|조직 소유 디바이스|계속해서 그룹 정책을 사용하여 디바이스를 관리하려는 경우|
|리소스 액세스 권한을 부여하는 Entra ID 계정에 연결됨|Entra ID에만 조인됨 - 조직 계정이 필요함|기존 이미지 솔루션을 사용하여 디바이스를 배포하려는|
|Microsoft Intune과 같은 MDM(Mobile Device Management) 도구를 사용하여 제어|조건부 액세스 정책을 사용할 수 있음||
|OS - Window 10 이상, iOS, Android, MacOS|OS - Windows 10 이상 디바이스|OS - Windows 7 이상 디바이스|

#### 셀프 서비스 암호 재설정
    
    Entra ID 는 **테넌트 (조직)** 에 속하는 사용자의 IDENTITY 목록으로, 그 소유자가 암호를 분실하였을 때, 스스로 암호를 초기화 할 수 있도록 설정할 수 있음.

    비밀번호 초기화를 위해 단일 인증 / 2FA 등을 요구하도록 설정할 수 있음.

#### 핵심적인 기능 / 1. 사용자와 그룹

전역 관리자 또는 사용자 관리자는 사용자 계정을 관리할 수 있음.
* 사용자 생성
* 그룹 생성
* 권한 관리 / 로그 정보 관리

#### 그룹 계정

2가지 종류
보안 그룹 / Microsoft 365 그룹
두 가지 그룹은 서로 배타적임. 서로가 될 수 없음.

* 할당 유형
    * 할당됨 (직접 계정을 그룹에 할당)
    * 동적 사용자 (Selector 를 통해 지정)
    * 동적 디바이스 (보안 그룹만 해당)

#### 관리 단위
Entra ID 내에서의 리소스들을 논리적으로 관리(?)

#### 핵심적인 기능 / 2. 온-프레미스 AD와 동기화 가능
> Entra ID Connector 를 통해 구현

#### 핵심적인 기능 / 3. Guest 계정
> 다른 Entra ID에 속한 ID를 Guest 계정으로 초대하여 권한을 부여할 수 있음.

#### RBAC (Role-Based Access Control)
> 역할을 기반으로 해서 '''구독''' 또는 '''리소스 그룹''' 또는 ''리소스''' 의 접근 권한을 설정

---
### 구독
Azure의 모든 서비스는 유료.
모든 서비스는 구독 하위에 존재하며, 모든 결제는 **구독** 단위로 청구됨.

즉, 리소스를 만들 때는 어떤 구독을 기반으로 만들지를 지정해야 함.

하나의 테넌트는 여러개의 구독을 가질 수 있음.

### 구독 사용법 식별
|구독|사용법|
|:---:|---|
|무료|최초 30일간 $200 크레딧, 12개워간 무료인 제한된 엑세스 포함|
|종량제|매월 요금 부과|
|CSP|Microsoft 클라우드 솔루션 공급자 파트너를 통해 할인을 적용받을 수 있는 계약<br>-> 대부분 중소기업을 대상으로 함|
|엔터프라이즈|단일 계약(신규 라이선스 및 Softwarte Assurance 대상 할인 적용)<br>-> 대기업급 조직을 대상으로 함|
|학생|12개월 동안 $100 포함 - 학생 엑세스 확인 필요|

* 서비스 제한 (권한) / 할당량 식별 가능
* 하나의 구독 아래에는 많은 리소스 그룹 & 리소스가 포함될 수 있음
* 구독의 종류 / 리전의 종류 등에 따라 생성 & 관리 가능한 리소스의 종류가 다를 수 있음

#### 관리 그룹
하나의 테넌트 아래에 **수많은 구독**이 존재하여 관리에 어려움이 있을 수 있다.   
이를 **관리 그룹**이라는 논리적 집합으로 묶어서 보안, 정책 등의 관리가 가능하다.
    
> ### 정책이란 ?
> 서비스가 제공되는 국가 / 지역 / 기업 등에 따라, 적용되야 할 규칙   
> ex) 보안 규칙 - 해당 정책을 적용받는 범위에서는 IP 대역이 어떠어떠 해야함 등
>   
> 각 정책은 json 을 통해 선언적으로 작성되며 (개별 정책 := definition)   
> 개별 정책을 묶어서 선언할 수도 있다 (initiative / 묶음 정책?)
>   
> 코드를 이용한 선언적 방식이기 떄문에, 개별 정책이 서술되어 있는 json 파일등을
> github 과 같은 서비스를 통해 공유 가능함
---
### Region

> Azure가 제공되는 대부분의 국가에서는 2개 이상의 Region이 Pairing의 원칙에 의하여 운영되고 있음

원래 각 Region 은 300 마일 거리를 두어야 하지만,   
한국의 경우 1. 화강암 지대 / 2. Korea South가 여러개의 IDC 로 구성됨   
에 기반하여 가깝게 구성되어 있음

---
### 리소스 그룹

    !!! Infra Structure as Coded !!!

전통적인 IT 산업에서 **동일한 인프라 구조** 가 필요한 경우에, 온-프레미스 환경에서는 수동으로 일일이 리소스를 Ochestration 해야 했지만, **리소스 그룹** 과 같은 논리 그룹을 사용하면 쉽게 구조를 복제하여 구성할 수 있다.


---
### 리소스

리소스는 **태그**를 통해 관리될 수 있음   
key-value 형식을 따름

#### 리소스 비용
> 리소스에 따라, 리전에 따라 비용이 각기 다를 수 있음   
> 컴퓨팅 비용, 스토리지 비용, 네트워킹 비용으로 구성됨   
> 네트워킹의 경우 인바운드, 아웃바운드 비용이 다르고   
> 동일 리전 / 리전 간 이동 / Azure 외부로의 이동 별로 비용이 다름

> Reserved Instance(예약 인스턴스)를 통해 비용 할인이 가능

> On-Premise용 License 중에는 Azure 리소스에도 적용 가능한 Hybrid 라이선스들이 있음   
> 해당 라이선스를 통해서도 비용 할인이 가능


---
### RBAC
> Role-Based Access Control

역할 기반의 접근 제어   
소유자, 기여자, 독자 등 여러가지 역할을 통해 CRUD 등의 권한을 설정할 수 있음
> 역할의 종류는 다양하나, 일반적으로 [소유자, 기여자, 독자] 3가지의 역할로도 충분히 관리 가능

#### 역할
하나의 테넌트 아래에는 Entra ID 와 구독이 존재하는데   
Entra ID 에서의 역할과 구독에서의 역할이 다름 (역할의 종류가 다르다는 건지?)

#### 역할 정의 만들기
기본 역할 외에 사용자 지정 이름을 갖는 임의의 역할을 만들 수 있으며,
Code Based Rule을 통해 기본 역할을 포함한 각 역할의 세부 권한을 조정(Override) 할 수 있음

---
### 추가 링크
> https://docs.microsoft.com/learn/modules/allow-users-reset-their-password/

> https://docs.microsoft.com/ko-kr/learn/modules/manage-device-identity-ad-join/

> https://docs.microsoft.com/learn/modules/implement-manage-hybrid-identity/

---
