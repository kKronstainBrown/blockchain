---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-31"

keywords: blockchain network, Starter Plan, getting started

subcollection: blockchain

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:external: target="_blank" .external}

# 스타터 플랜 정보
{: #starter-plan-about}

<!--[placeholder] Starter Plan is deprecated on May 30. No new Starter Plan networks can be created then. Your existing networks are not affected, but you can use them and get IBM's support on them for only another 30 days. You might consider using {{site.data.keyword.blockchainfull_notm}} Platform free 2.0 beta instead.
{: note} -->

{{site.data.keyword.blockchainfull}} Platform 스타터 플랜은 조직이 다중 조직 블록체인 네트워크를 시뮬레이션하고 신속하게 애플리케이션을 개발하며 샘플 스마트 계약 및 비즈니스 네트워크에 대한 작업을 수행할 수 있도록 하는 엔트리 레벨 옵션입니다. 또한 다른 멤버십 옵션과 동일한 UI 경험을 제공하여 학습 과정을 줄여줍니다. 2018년 10월 4일 이후에 작성된 새 스타터 플랜 네트워크는 Hyperledger Fabric V1.2.1에 빌드됩니다. 이전 스타터 플랜 네트워크는 Fabric V1.1.0 레벨로 유지됩니다.
{:shortdesc}

**스타터 플랜**은 블록체인 네트워크 개발을 시작하거나
블록체인 기술 학습을 시작하려는 사용자를 위한 환경입니다. 프로덕션 환경으로 이동하기 전에 스타터 플랜을 개발 또는
테스트 환경으로 사용하여 소규모로
네트워크의 멤버십 또는 트랜잭션 볼륨을 시작할 수 있습니다.

 스타터 플랜 네트워크를 배치하려면 {{site.data.keyword.cloud_notm}}에서 [스타터 멤버십](https://cloud.ibm.com/catalog/services/ibm-blockchain-5-prod){: external}에 지금 가입하십시오. 네트워크 개발을 시작할 준비가 되었을 때 [스타터 플랜 시작하기](/docs/services/blockchain/get_start_starter_plan.html#getting-started-with-starter-plan)를 방문하십시오.


**참고:**
- {{site.data.keyword.blockchainfull_notm}} Platform 스타터 플랜은 개발 및 테스트 환경이며 프로덕션 워크로드에는 적합하지 않습니다. 프로덕션 환경이 필요한 경우 [엔터프라이즈 플랜 정보](/docs/services/blockchain/enterprise_plan.html#enterprise-plan-about)를 참조하십시오.
- {{site.data.keyword.blockchainfull_notm}} Platform은 {{site.data.keyword.cloud_notm}}의 플랫폼 서비스로, 모든 멤버십 오퍼링은 서비스 레벨 계약(SLA)의 [{{site.data.keyword.cloud_notm}} 서비스 이용 약관](http://www-03.ibm.com/software/sla/sladb.nsf/sla/bm){: external}을 따릅니다. 스타터 플랜은 단일 지역의 데이터 센터에서 프로비저닝됩니다. 사용 가능한 지역의 목록은 [{{site.data.keyword.blockchainfull_notm}} Platform 위치](/docs/services/blockchain?topic=blockchain-ibp-regions-locations#ibp-regions-locations)를 참조하십시오.

## 스타터 플랜이 제공하는 내용
{: #starter-plan-about-what-starter-plan-offers}

- **_한 번의 클릭으로 준비되는 네트워크_**
    스타터 플랜은 한 번의 클릭으로 라이브 블록체인 네트워크를 프로비저닝합니다. 각 네트워크는 CA, 순서 지정자, 두 개의 조직(조직당 피어 하나씩) 및 체인코드를 거래하고 배치할 기본 채널과 함께 제공됩니다. {{site.data.keyword.blockchainfull_notm}} Platform은 이 네트워크의 작성 및 구성을 처리하며(가동 준비가 되면 업데이트할 수 있음) 개발에 초점을 맞추도록 합니다. 스타터 플랜 네트워크는 Fabric V1.2에서 빌드되며 CouchDB를 상태 데이터베이스로 사용합니다.
- **_비용 효율성_**
   스타터 플랜 멤버십 옵션은 엔터프라이즈 플랜 멤버십 옵션과 동일한 여러 블록체인 기능을 적은 비용으로 제공합니다. 자세한 정보는 [스타터 플랜 가격](/docs/services/blockchain/howto/pricing.html#ibp-pricing-starter-pricing)을 참조하십시오.
- **_다중 조직 네트워크 시뮬레이션_**
   스타터 플랜을 사용하여 다중 조직의 네트워크 빌드를 시뮬레이션할 수 있습니다. 실제로 네트워크에 다른 조직을 초대할 필요는 없지만 다른 조직의 역할을 할 수는 있습니다. 이 메커니즘을 통해 새 조직이 네트워크에 가입하는 방법, 여러 조직이 네트워크에서 함께 작업하는 방법 등을 학습할 수 있습니다. 네트워크 모니터에서 조직 간에 전환하여 여러 조직의 보기를 통해 네트워크를 보고 관리할 수 있습니다.

{{site.data.keyword.IBM_notm}}은 Composer CLI, JavaScript API, REST 서버 및 웹 플레이그라운드를 포함하여 프로덕션에서 Hyperledger Composer를 사용하는 네트워크를 지원하지 않습니다.
{:note}

## 스타터 플랜이 사용자에게 적합한지 여부
{: #starter-plan-about-is-starter-suitable-for-you}

다음 상황 중 하나인 경우 스타터 플랜이 블록체인 과정을 시작하는 데 적합합니다.
- **_{{site.data.keyword.blockchainfull_notm}} Platform에 대해 학습합니다._**
        {{site.data.keyword.blockchainfull_notm}} Platform에 관심이 있는 경우 또는 심지어 블록체인을 처음 사용하는 경우에도 스타터 플랜은 실제 블록체인 네트워크를 개발하고 통제하는 방법을 학습할 수 있는 좋은 방법을 제공합니다. 프로덕션 네트워크의 경우와 같이 네트워크를 구성하는 컴포넌트를 찾고 멤버십을 관리하고 체인코드("스마트 계약"이라고도 함) 배치 및 관리 방법과 채널을 추가하는 방법(및 채널 권한을 관리하는 방법)을 학습하며, 새 블록이 생성되었을 때 추적할 수 있습니다.
- **_라이브 네트워크에서 데모 솔루션을 빌드합니다._**
        스타터 플랜은 블록체인 애플리케이션 시연을 위한 강력한 환경을 제공합니다. 사용 준비가 된 블록체인 네트워크를 사용하면 네트워크 모니터가 제공하는 운영 및 관리 도구를 통해 동료, 관리 및 파트너에게 빠른 프리젠테이션을 수행할 수 있습니다.
- **_단일 조직 개발 이상을 수행합니다._**
        스타터 플랜에서는 다중 조직의 역할을 할 수 있으며, 이를 통해 {{site.data.keyword.blockchainfull_notm}} Platform이 애플리케이션 테스트 및 트랜잭션 호출뿐만 아니라 채널 작성과 체인코드 설치와 같은 협업 태스크를 관리하는 방법을 확인할 수 있습니다. 또한 스타터 플랜 네트워크에서 협업할 다른 사용자를 초대할 수도 있습니다(엔터프라이즈 플랜의 경우와 같이). 이를 통해 체인코드와 트랜잭션을 보증하는 여러 당사자가 있는 보다 실제적인 환경을 빌드할 수 있습니다.
- **_블록체인 애플리케이션을 반복적으로 개발하고 테스트합니다._**
        스타터 플랜은 블록체인 네트워크에서 코드를 지속적으로 개발하고 테스트할 수 있는 스테이징 영역을 제공합니다. 클라우드로 이동하면 개발자 및 테스터가 기능에 초점을 맞춰 단위 테스트에서 기능 테스트로 쉽게 이동할 수 있습니다. 스타터 플랜은 운영 및 관리 도구 뿐만 아니라 엔터프라이즈 플랜과 동일한 블록체인 네트워크 기능을 제공합니다. 사용자 프로젝트를 엔터프라이즈 플랜 중 하나로 사용할 준비가 되면 스타터 플랜과 동일한 방식으로 운영되지만 네트워크를 확장할 수 있는 가능성이 높아집니다.

## 스타터 플랜 고려사항
{: #starter-plan-about-considerations}

스타터 플랜은 {{site.data.keyword.blockchainfull_notm}} Platform의 시작점이며 개발 및 테스트용으로 사용됩니다.  스타터 플랜을 사용하기 전에 다음 항목을 확인하십시오.

- **{{site.data.keyword.cloud_notm}} 계정 요구사항**
    유료 {{site.data.keyword.cloud_notm}} 계정(예: **종량과금제** 유형)이 있어야 합니다. {{site.data.keyword.blockchainfull_notm}} Platform에서 제공하는 모든 멤버십 플랜에는 {{site.data.keyword.cloud_notm}} 유료 계정이 필요합니다. 계정을 종량과금제 유형으로 업그레이드하려면 {{site.data.keyword.cloud_notm}} 콘솔에서 **관리** > **청구 및 사용량** > **청구**로 이동하고 **신용카드 추가**를 클릭하십시오.
- **엔터프라이즈 플랜과의 차이점**
    - 각 조직에 하나의 CA만 있고 네트워크에는 하나의 [순서 지정자](/docs/services/blockchain/glossary.html#glossary-orderer)만 있으므로 [CA](/docs/services/blockchain/glossary.html#glossary-CA) 및 순서 지정 서비스에서 결함 허용이 되지 않습니다.
    - 순서 지정 서비스는 [SOLO](/docs/services/blockchain/glossary.html#glossary-solo) [합의](/docs/services/blockchain/glossary.html#glossary-consensus)만 사용합니다. 스타터 플랜 네트워크는 모든 피어에 대한 합의를 수행하는 하나의 순서 지정자로만 구성됩니다.
    - [하드웨어 보안 모듈(HSM)](/docs/services/blockchain/glossary.html#glossary-hsm)은 강력한 인증 및 암호 처리를 위한 디지털 키를 보호하고 관리할 수 없습니다.
- **스타터 플랜 버전 및 업그레이드**
    - 2018년 10월 4일 이후에 작성된 새 스타터 플랜 네트워크는 Hyperledger Fabric V1.2.1에 빌드됩니다. 이전 스타터 플랜 네트워크는 Fabric V1.1.0 레벨로 유지됩니다.
    - 이전 스타터 플랜 네트워크에 추가된 새 피어는 Fabric v1.2.1에 빌드됩니다. 역호환성으로 인해 네트워크의 성능이 영향을 받지 않습니다.
    - 채널을 작성하거나 업데이트하는 경우 고급 [채널 구성](https://hyperledger-fabric.readthedocs.io/en/release-1.2/config_update.html){: external} 설정 및 [액세스 제어 목록](https://hyperledger-fabric.readthedocs.io/en/release-1.2/access_control.html){: external}을 사용할 수 있는 옵션이 제공됩니다. 
    - Hyperledger Fabric v1.2의 [서비스 발견](https://hyperledger-fabric.readthedocs.io/en/release-1.2/discovery-overview.html){: external} 및 [개인용 데이터](https://hyperledger-fabric.readthedocs.io/en/release-1.2/private-data/private-data.html){: external} 기능은 스타터 플랜에서 지원되지 않습니다. 
    - Fabric V1.1.0에 있는 이전 스타터 플랜 네트워크를 [재설정](/docs/services/blockchain/v10_dashboard.html#ibp-dashboard-reset-network)하면 새 네트워크는 Fabric V1.2 레벨에 있습니다. 네트워크를 재설정하면 새 네트워크에 체인코드 또는 .bna 파일을 설치하고 이전 네트워크의 멤버를 다시 초대해야 합니다.
- **새 리소스 제한사항**
    스타터 플랜은 각 피어에 1개의 CPU 및 4Gi RAM을 지정하고 피어를 포함하는 각 {{site.data.keyword.cloud_notm}} 서비스 인스턴스에 20Gi 스토리지를 지정합니다. 체인코드 컨테이너와 원장 블록은 가장 리소스 집약적인 네트워크 컴포넌트입니다. 네트워크에 피어가 많거나 많은 블록을 생성하거나 대규모 체인코드 파일을 사용하는 사용자는 리소스 제한사항이 성능에 민치는 영향을 경험할 수 있습니다. [네트워크 모니터의 "개요" 화면](/docs/services/blockchain/v10_dashboard.html#ibp-dashboard-storage)에서 스토리지의 네트워크 사용량을 볼 수 있습니다.
- **유지보수 및 업그레이드**
    스타터 플랜 유지보수 및 네트워크 업데이트는 고정된 스케줄에 따라 수행됩니다. 유지보수 기간 중에는 새 네트워크를 프로비저닝할 수 없고 짧은 시간 동안 네트워크 인터럽션이 발생할 수 있습니다.
- **데이터 보존**
    스타터 플랜에서는 릴리스 업그레이드 시 데이터가 보존된다고 보장하지 않습니다.
- **마이그레이션 고려사항**
    스타터 플랜 네트워크에서 다른 멤버십 플랜으로의 데이터 마이그레이션은 현재 지원되지 않습니다. 하지만 스타터 플랜에서 테스트한 `.bna` 파일, 체인코드 및 애플리케이션은 마이그레이션할 수 있습니다. 자세한 정보는 [스타터 플랜에서 엔터프라이즈 플랜으로 마이그레이션](/docs/services/blockchain/howto/migrate_sp_ep.html#migrate_starter_to_enterprise)을 참조하십시오.
