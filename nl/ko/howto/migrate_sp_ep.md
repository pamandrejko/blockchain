---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-31"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 스타터 플랜에서 엔터프라이즈 플랜으로 마이그레이션
{: #migrate_starter_to_enterprise}


***[이 페이지가 도움이 되었습니까? 알려주십시오.](https://www.surveygizmo.com/s3/4501493/IBM-Blockchain-Documentation)***


{{site.data.keyword.blockchainfull}} Platform [스타터 플랜](../starter_plan.html)에서는 PoC와 데모를 실행하고 체인코드와 애플리케이션을 사용해 보는 테스트 및 개발 환경을 제공합니다. 프로덕션 환경으로 이동할 준비가 되면 스타터 플랜 네트워크에서 [엔터프라이즈 플랜](../enterprise_plan.html) 네트워크로 마이그레이션할 수 있습니다.{:shortdesc}

엔터프라이즈 플랜 네트워크에서는 다음 프로덕션 준비 기능을 제공하여 프로덕션 워크로드를 지원합니다.

- 스타터 플랜 네트워크 이외에 추가 글로벌 위치에서 사용 가능한 Blockchain 네트워크
- 스토리지 한계가 없음(스타터 플랜의 경우 20GB)
- 모든 네트워크가 원활하게 실행되도록 향상된 CPU와 RAM 관리
- 다음 기능을 포함하는 강화된 보안:
  - 보안 서비스 컨테이너(SSC)를 통해 특정 시점에 Blockchain 이미지를 변조하고 로드할 수 없게 하며 애플리케이션 코드와 데이터를 이동 중이나 저장 중에 모두 기밀 상태로 보호
  - 키 관리 및 키 스토리지용 [하드웨어 보안 모듈(HSM)](../glossary.html#hsm)
  - 퍼베이시브 디스크 암호화
- 고가용성, 재해 복구, 충돌 결함 허용 및 롤링 업그레이드
- 선택적 고급 지원

## 고려사항
{: #migrate_starter_to_enterprise_considerations}

스타터 플랜 네트워크에서 엔터프라이즈 플랜 네트워크로 마이그레이션하기 전에 다음 고려사항을 읽으십시오.

- **가격:** 엔터프라이즈 플랜 네트워크를 사용하는 조직의 월별 요금은 인스턴스당 $1000 멤버십 요금과 피어당 $1000 피어 요금이 포함됩니다. 자세한 정보는
[엔터프라이즈 플랜 가격](pricing.html#enterprise-plan-pricing)을 참조하십시오.
- **Hyperledger Fabric 버전:** 엔터프라이즈 플랜 네트워크는 Hyperledger Fabric v1.1에서 실행됩니다.  
- **영향받는 리소스:** 체인코드(스마트 계약), 비즈니스 네트워크 정의, 클라이언트 애플리케이션.
- **필요한 시간:** 스타터 플랜에서 엔터프라이즈 플랜으로 기본 네트워크를 마이그레이션하는 데 최소 한나절이 소요될 수 있습니다.
- **기존 원장 데이터**는 스타터 플랜 네트워크에서 엔터프라이즈 플랜 네트워크로 이동할 수 없습니다. 테스트 데이터를 프로덕션 환경에 두는 것은 적합하지 않기 때문입니다.

**참고:** *기본* 네트워크에는 두 개의 피어, 단일 채널 및 단일 체인코드나 비즈니스 네트워크 아카이브(`.bna`) 파일이 포함된 두 개의 조직이 있습니다. 실제 마이그레이션 시간은 엔터프라이즈 플랜 네트워크에 필요한 네트워크 컴포넌트의 크기와 복잡도에 따라 달라질 수 있습니다.

## 마이그레이션 체크리스트
{: #migrate_starter_to_enterprise_checklist}

스타터 네트워크에서 엔터프라이즈 플랜 네트워크로의 이동을 준비하려면 여러 태스크를 수행해야 합니다. 나중 섹션에서 자세한 지시사항을 찾을 수 있지만 요약은 다음과 같습니다.

- 엔터프라이즈 플랜 네트워크를 작성합니다.
- Hyperledger Composer를 사용하여 `.bna`를 개발한 경우 `.bna` 파일을 찾아 마이그레이션합니다.
- 테스트 스타터 플랜 네트워크에서 원하는 조직과 피어 구성을 다시 작성합니다.
- 엔터프라이즈 플랜 네트워크에서 실행할 체인코드(Go 또는 Node에 작성됨)를 식별합니다.
- 엔터프라이즈 플랜 네트워크의 새 API 엔드포인트 정보로 클라이언트 애플리케이션을 업데이트합니다.

### 엔터프라이즈 플랜 네트워크 작성
{: #migrate_starter_to_enterprise_create_network}

마이그레이션하기 전에 엔터프라이즈 플랜 네트워크를 작성해야 합니다. 자세한 정보는 [엔터프라이즈 플랜 네트워크 작성](../get_start.html#creating-a-network)을 참조하십시오.

### `.bna` 파일 마이그레이션
{: #migrate_starter_to_enterprise_bna}

**참고:** 스타터 플랜 네트워크에서 `.bna` 파일을 사용하지 않는 경우 이 단계를 건너뛸 수 있습니다.

Hyperleger Composer를 사용하여 비즈니스 네트워크를 정의하고 `.bna` 파일을 스타터 플랜 네트워크에 배치한 경우 동일한 `.bna` 파일을 엔터프라이즈 플랜 네트워크에 배치할 수 있습니다.

- 비즈니스 네트워크 아카이브 파일(`.bna`)이 있는 경우 [엔터프라이즈 플랜에서 비즈니스 네트워크 배치](../develop_enterprise.html)에 대한 지시사항을 따르십시오.
- `.bna` 파일이 없으면 `composer network download` 명령을 사용하여 스타터 플랜 인스턴스에서 검색하십시오. `composer network download` 명령에 대한 자세한 정보는 [Hyperledger Composer 명령행 문서 ![외부 링크 아이콘](../images/external_link.svg "외부 링크 아이콘")](https://hyperledger.github.io/composer/latest/reference/commands){:new_window}를 참조하십시오. 그런 다음 [엔터프라이즈 플랜에서 비즈니스 네트워크 배치](../develop_enterprise.html)의 지시사항을 따를 수 있습니다.

### 네트워크 구성 다시 작성
{: #migrate_starter_to_enterprise_config_network}

엔터프라이즈 플랜 네트워크에서 스타터 플랜 네트워크의 조직(멤버), 채널 및 피어의 구성을 다시 작성할 수 있습니다. 네트워크 모니터 UI를 통해 해당 조직을 초대하여 네트워크 리소스를 다시 작성(스타터에서와 같이 조직을 **전환**할 수 없음에 유의)하고 채널을 작성하며 피어를 작성(다시 초대된 조직이 자체 피어를 작성해야 함)할 수 있습니다.

1. {{site.data.keyword.cloud_notm}}에서 엔터프라이즈 플랜 네트워크에 로그인하고 네트워크 모니터를 입력합니다.
2. "멤버" 화면에서 조직(멤버)을 다시 작성하고 "채널" 화면에서 채널을 다시 작성하며 "개요" 화면에서 피어를 다시 작성합니다. 네트워크 리소스 작성에 관한 자세한 정보는 [엔터프라이즈 플랜 네트워크 운영](../v10_dashboard.html#overview)을 참조하십시오.
3. 스타터 플랜 네트워크에서와 동일한 방식으로 구성원을 추가하고 채널 정책을 설정하여 채널을 구성합니다.

**참고:** 고가용성을 얻으려면 조직에 대해 두 개 이상의 피어를 작성하여 동일한 채널에 가입한 다음 필요한 경우 한 피어에서 다른 피어로 전환하도록 클라이언트 애플리케이션을 적절하게 코딩해야 합니다.

### 체인코드 마이그레이션
{: #migrate_starter_to_enterprise_cc}

체인코드는 로컬 환경에서 외부적으로 개발하고 클라이언트 애플리케이션에서 호출합니다. 스타터 플랜 네트워크에서 테스트한 체인코드를 엔터프라이즈 플랜 네트워크에서 선택한 피어에 설치하고 인스턴스화하려면 [체인코드 설치, 인스턴스화 및 업데이트](./install_instantiate_chaincode.html#installchaincode)의 지시사항을 따르십시오.

### 클라이언트 애플리케이션 업데이트
{: #migrate_starter_to_enterprise_app}

스타터 플랜 네트워크에 대해 테스트한 기존 클라이언트 애플리케이션을 엔터프라이즈 플랜 네트워크의 새 API 엔드포인트 정보로 업데이트해야 합니다. 자세한 정보는 [네트워크 인증 정보와 연결 프로파일 검색](../get_start.html#retrieving-network-credentials-and-connection-profile)을 참조하십시오.

고가용성과 관련하여 클라이언트 애플리케이션에서 피어가 응답하지 않고 트랜잭션을 다른 피어로 라우팅하는 경우를 감지해야 합니다.

## 기존 스타터 플랜 네트워크에서 수행할 사항
{: #migrate_starter_to_enterprise_existing_network}

기존 스타터 플랜 네트워크를 샌드박스 환경으로 계속 사용하여 새로운 프로젝트를 생성하고 기존 체인코드의 변경사항을 테스트할 수 있습니다. 또한 엔터프라이즈 플랜 네트워크로 마이그레이션되지 않은 테스트 원장 데이터를 스타터 플랜 네트워크에서 유지보수할 수 있습니다.

모든 테스트를 완료하고 모두 제대로 작동하는지 확인할 때까지 스타터 네트워크를 삭제하지 마십시오. 그러나 더 이상 스타터 네트워크와 포함된 원장 데이터가 필요하지 않게 되면 네트워크를 삭제해도 안전합니다. 자세한 정보는 [네트워크 삭제 또는 그대로 두기](../get_start_starter_plan.html#deleting-or-leaving-a-network)를 참조하십시오.