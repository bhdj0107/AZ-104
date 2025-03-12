AZ-104 Day #1
===================

* Notes
    - 자료 공유
    > https://1drv.ms/u/s!AmlADRmU8M8uk_Zx845G11GdHVqp1A?e=QluzWB

    - 추가 학습 자료
    > ### DOCS
    > https://learn.microsoft.com/ko-kr/docs/
    > ### CERTIFICATION
    > https://learn.microsoft.com/ko-kr/certifications/
    > ### Learn Profile
    > https://learn.microsoft.com/ko-kr/users/me


# Azure 구조
    조직 - 테넌트 - 엔트라 ID [무료]
               ㄴ 구독 [유료]

    테넌트는 조직을 '''추상''' 하고 있음.

    Entra ID를 [tName] 으로 생성하면,
    tName.onmicrosoft.com 으로 기본 도메인 명이 부여됨

    사용자 지정 도메인을 등록하려면 [Entra ID] 설정 콘솔에서 도메인 소유권을 증명하면 됨.

# 테넌트
하나의 조직을 표상 (?)


# Entra ID
Microsoft 에서 제공하는 많은 서비스들에 대해서
SSO 를 제공해주는 솔루션

Active Directory에서 [인증] 관련 기능만 세분화 해서 제공

HTTP, HTTPS 기반의 통신 채널을 메인으로 지원함.

하나의 Entra ID 는 여러 조직 (테넌트)에 속할 수 있음.

* 개념
    
    ID : 
    > 인증할 수 있는 개체 (Service Principal?)
    
    계정 : 
    > 연결된 데이터가 있는 ID
    
    Microsoft Entra ID 계정 : 
    > Microsoft Entra ID 또는 기타 Microsoft 클라우드 서비스를 통해 만든 ID (also able 사용자 지정 도메인)
    
    테넌트 / 디렉터리:
    > 신뢰할 수 있는 전용 인스턴스. 조직이 Microsoft 클라우드 서비스 구독에 등록할 때 테넌트가 자동으로 생성됨
    > * 추가 인스턴스를 만들 수 있음
    > * Microsoft Entra ID는 ID 서비스를 제공하는 기본 제품임
    > * 테넌트 라는 용어는 단일 조직을 나타내는 단일 인스턴스를 의미
    > * 테넌트 와 디렉터리는 종종 같은 의미로 사용됨

    도메인:
    > 하나의 Entra ID 하위에 여러 도메인들이 포함될 수 있음.

* Entra ID > Device ID 종류

    |등록 디바이스|조인 디바이스|하이브리드 조인 디바이스|
    |---|---|---|
    |BYOD 지원 (Bring-Your-Own-Device)|클라우드 우선 또는 클라우드 전용, 조직용|Active Directory 컴퓨터 인증을 사용하는 디바이스에 Win32 앱을 배포한 경우|
    |등록된 디바이스는 Microsoft 계정을 사용하여 로그인함|조직 소유 디바이스|계속해서 그룹 정책을 사용하여 디바이스를 관리하려는 경우|
    |리소스 액세스 권한을 부여하는 Entra ID 계정에 연결됨|Entra ID에만 조인됨 - 조직 계정이 필요함|기존 이미지 솔루션을 사용하여 디바이스를 배포하려는|
    |Microsoft Intune과 같은 MDM(Mobile Device Management) 도구를 사용하여 제어|조건부 액세스 정책을 사용할 수 있음||
    |OS - Window 10 이상, iOS, Android, MacOS|OS - Windows 10 이상 디바이스|OS - Windows 7 이상 디바이스|

* 셀프 서비스 암호 재설정
    
    Entra ID 는 **테넌트 (조직)** 에 속하는 사용자의 IDENTITY 목록으로, 그 소유자가 암호를 분실하였을 때, 스스로 암호를 초기화 할 수 있도록 설정할 수 있음.

    비밀번호 초기화를 위해 단일 인증 / 2FA 등을 요구하도록 설정할 수 있음.

* 핵심적인 기능 / 1. 사용자와 그룹

    전역 관리자 또는 사용자 관리자는 사용자 계정을 관리할 수 있음.
    > * 사용자 생성
    > * 그룹 생성
    > * 권한 관리 / 로그 정보 관리

* 그룹 계정

    2가지 종류
    > 보안 그룹 / Microsoft 365 그룹
    > 두 가지 그룹은 서로 배타적임. 서로가 될 수 없음.

    * 할당 유형
    > * 할당됨 (직접 계정을 그룹에 할당)
    > * 동적 사용자 (Selector 를 통해 지정)
    > * 동적 디바이스 (보안 그룹만 해당)


* 핵심적인 기능 / 2. 온-프레미스 AD와 동기화 가능
    > Entra ID Connector 를 통해 구현

* 핵심적인 기능 / 3. Guest 계정
    > 다른 Entra ID에 속한 ID를 Guest 계정으로 초대하여 권한을 부여할 수 있음.
# 구독
Azure의 모든 서비스는 유료.
모든 서비스는 구독 하위에 존재하며, 모든 결제는 **구독** 단위로 청구됨.

즉, 리소스를 만들 때는 어떤 구독을 기반으로 만들지를 지정해야 함.

하나의 테넌트는 여러개의 구독을 가질 수 있음.


# 추가 링크
> https://docs.microsoft.com/learn/modules/allow-users-reset-their-password/

> https://docs.microsoft.com/ko-kr/learn/modules/manage-device-identity-ad-join/

> https://docs.microsoft.com/learn/modules/implement-manage-hybrid-identity/