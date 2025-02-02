---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: IBM Cloud accounts, IBM Blockchain Platform, pay your own fees, pay for others

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 지불 모드
{: #paying-mode}

{{site.data.keyword.blockchainfull}} Platform은 멤버십 요금 및 피어 요금을 월별로 부과합니다. 네트워크 구성원은 네트워크 인스턴스를 작성하기 위한 영역이 포함된 {{site.data.keyword.cloud_notm}} 계정으로 요금을 지불할 수 있습니다. 또는 하나의 네트워크 구성원이 네트워크에 있는 다른 구성원 또는 모든 구성원의 요금을 지급하여 네트워크 비용을 지불할 수 있습니다. 필요하면 지급인이 비용을 다른 구성원에게 다시 이전할 수도 있습니다.
{:shortdesc}

선택하는 네트워크 플랜 및 사용하는 리소스의 양에 따라 요금이 다릅니다. 가격에 대한 자세한 정보는 [가격](/docs/services/blockchain/howto/pricing.html#ibp-pricing)을 참조하십시오.

여러 조직이 컨소시엄을 빌드하는 경우, 참여하는 조직이 기능적 이메일 주소를 사용하여 해당 네트워크를 작성하는 것이 좋습니다. 이 경우, 네트워크에 대한 액세스는 단일 개인의 가용성에 의존하지 않습니다.


## 전제조건
{: #paying-mode-prereq}

모든 네트워크 구성원에게는 유료 {{site.data.keyword.cloud_notm}} 계정(예: **종량과금제** 계정)이 있어야 {{site.data.keyword.cloud_notm}}에 {{site.data.keyword.blockchainfull_notm}} Platform 서비스 인스턴스를 작성할 수 있습니다. 계정이 없으면 계정을 하나 [등록](https://cloud.ibm.com/registration)하고 유료 계정으로 업그레이드하십시오. 계정을 종량과금제 유형으로 업그레이드하려면 {{site.data.keyword.cloud_notm}} 콘솔에서 **관리** > **청구 및 사용량** > **청구**로 이동하고 **신용카드 추가**를 클릭하십시오.


## 자신의 요금 지불
{: #paying-mode-pay-your-own}

{{site.data.keyword.blockchainfull_notm}} Platform에서 블록체인 네트워크를 작성하거나 가입하면 {{site.data.keyword.cloud_notm}} 계정에 멤버십 요금과 피어 요금이 청구됩니다.


## 다른 네트워크 구성원을 위해 지불
{: #paying-mode-pay-for-others}

네트워크의 한 구성원이 같은 블록체인 네트워크에 있는 한 명 이상의 다른 네트워크 구성원 요금을 지불할 수 있습니다. 이 모드로 지불하려면 지급인 및 다른 네트워크 구성원이 다음 단계를 완료해야 합니다.

1. 지급인이 비용을 지급할 대상 구성원을 위해 {{site.data.keyword.cloud_notm}}에 개별 Cloud Foundry 영역을 작성합니다.
   1. {{site.data.keyword.cloud_notm}}에 로그인하십시오.
   2. 메뉴 표시줄에서 **관리** > **계정** > **Cloud Foundry 조직**을 클릭하십시오.
   3. 네트워크를 작성할 Cloud Foundry 조직의 **세부사항 보기**를 클릭하십시오. 네트워크에 조직이 없는 경우 **새 Cloud Foundry 조직 추가** 단추를 클릭하여 작성하십시오.
   4. **Cloud Foundry 영역 추가** 단추를 클릭하여 다른 네트워크 구성원을 위한 영역을 작성하십시오. 영역을 위한 지역을 선택하고 이름을 지정하고 **추가**를 클릭하십시오.  영역 작성자만 작성된 영역에 액세스할 수 있습니다.  
   **참고**: 지급인이 둘 이상의 구성원의 요금을 지불하는 경우 지급인이 이 단계를 반복하여 지불하는 요금의 대상 구성원을 위해 개별 영역을 작성해야 합니다.
2. 지급인은 지급인의 {{site.data.keyword.cloud_notm}} 계정에 다른 구성원을 초대하고 특정 영역에 대한 액세스 권한을 제공합니다. 각 구성원에게는 하나의 영역에 대한 액세스 권한만 있습니다.
   1. 메뉴 표시줄에서 **관리** > **계정** > **사용자**를 클릭하십시오.  
   2. **사용자 초대**를 클릭하여 사용자 액세스 권한을 지정하십시오.
      1. Cloud Foundry 조직에 초대할 단일 사용자의 이메일 주소를 지정하십시오.
      2. **Cloud Foundry 액세스** 섹션에서 다음과 같이 선택하십시오.
         - **조직**: 네트워크를 작성할 Cloud Foundry 조직입니다.
         - **조직 역할**: 감사자입니다.
         - **지역**: 이 사용자의 영역을 작성한 지역입니다.
         - **영역**: 이 사용자를 위해 작성한 영역입니다.
         - **영역 역할**: 개발자입니다.
      3. **사용자 초대**를 클릭하십시오.  
   **참고**: 지급인이 둘 이상의 구성원 요금을 지불하는 경우 지급인이 이 단계를 반복하여 다른 구성원을 초대하고 각 구성원의 액세스 권한을 지정해야 합니다.
3. 지급인이 블록체인 네트워크 {{site.data.keyword.blockchainfull_notm}} Platform을 작성하고 네트워크의 네트워크 모니터에서 블록체인 네트워크에 다른 구성원을 초대합니다. 네트워크 구성원 초대에 대한 자세한 정보는 [구성원](/docs/services/blockchain/v10_dashboard.html#ibp-dashboard-members)을 참조하십시오.
4. 그러면 각 구성원은 네트워크에 가입할 수 있는 초대가 포함된 알림 이메일을 수신합니다. 구성원은 다음 단계를 완료하여 네트워크에 가입할 수 있습니다.
   1. 알림 이메일에서 "진행" 단추를 클릭하십시오. 그러면 {{site.data.keyword.cloud_notm}}의 블록체인 서비스 페이지로 이동합니다.
   2. {{site.data.keyword.cloud_notm}}에 로그인하고 지급인이 사용자를 추가하는 올바른 {{site.data.keyword.cloud_notm}} 조직과 영역을 사용하는지 확인하십시오.
      1. {{site.data.keyword.cloud_notm}} 콘솔의 오른쪽 상단에서 프로파일 아바타를 클릭하십시오.
      2. **계정** 드롭 다운 목록에서 지급인의 계정을 선택하십시오.  블록체인 서비스 인스턴스를 프로비저닝하는 계정 및 조직에게 비용이 청구됩니다.  
   3. {{site.data.keyword.cloud_notm}} 카탈로그에서 **Blockchain**을 검색하고 서비스 인스턴스를 작성하십시오.
      1. 나중에 알아볼 수 있도록 **서비스 이름** 필드에 구체적인 이름을 입력하십시오.
      2. 지급인이 사용자를 추가한 조직 및 영역이 맞는지 확인하십시오.
      3. 네트워크 인스턴스를 작성할 멤버십 플랜을 선택하십시오. 멤버쉽 플랜은 지급인이 네트워크를 작성하는 데 사용한 플랜과 같아야 합니다.
      4. **작성**을 클릭하십시오.
   4. 블록체인 서비스 인스턴스를 작성한 후 마법사에 따라 네트워크에 가입하십시오.  자세한 정보는 [네트워크 가입](/docs/services/blockchain/get_start.html#getting-started-with-enterprise-plan-join-nw)을 참조하십시오.

### 알려진 제한사항
{: #paying-mode-limitation}
- 모든 구성원이 지급인의 {{site.data.keyword.cloud_notm}} 계정 내에 있으므로 지급인은 모든 구성원의 블록체인 인스턴스에 액세스할 수 있으며 이를 위장할 수 있습니다. 따라서 이 지불 모드는 PoC 환경의 경우 또는 지급인이 {{site.data.keyword.blockchainfull_notm}} Platform의 모든 관리를 처리하고 구성원에게 애플리케이션만 제공되는 경우에 가장 적합합니다.  
- 지급인의 Cloud Foundry 조직에 있는 모든 구성원은 조직의 모든 영역을 볼 수 있습니다.  하지만 액세스 권한이 없으므로 조직을 편집하거나 수정할 수 없습니다.  
- 지급인의 Cloud Foundry 조직에 있는 모든 구성원은 동일한 Cloud Foundry 조직의 기타 구성원의 {{site.data.keyword.cloud_notm}} ID를 볼 수 있습니다.   
- 지급인의 {{site.data.keyword.cloud_notm}} 계정에 모든 구성원을 추가하고 블록체인 인스턴스를 프로비저닝하고 네트워크에 가입하는 액세스 권한을 지정하면, 지급인은 다른 서비스를 작성하는 액세스 권한을 구성원에게 제공하며 이로 인해 추가 요금이 발생할 수 있습니다. 모든 구성원은 지급인의 계정에 추가 비용을 초래하는 무단 서비스를 자신의 계정에서 작성하지 않는다는 계약에 서명할 수 있습니다.  

## 구성원이 사용자 대신 지불하도록 허용
{: #paying-mode-let-other-pay}

다른 구성원의 계정을 지급인의 계정에 추가하는 대신 다른 구성원이 지급인의 계정을 **청구 관리자**로 자신의 계정에 추가할 수 있습니다. 이 모드로 지불하려면 지급인 및 다른 네트워크 구성원이 다음 단계를 완료해야 합니다.

1. 지급인이 지급인의 계정으로 블록체인 네트워크 {{site.data.keyword.blockchainfull_notm}} Platform을 작성합니다.
2. 다른 구성원이 지급인의 계정을 **청구 관리자**로 자신의 {{site.data.keyword.cloud_notm}} 계정에 추가합니다.
  1. {{site.data.keyword.cloud_notm}} 콘솔 맨 위의 메뉴 표시줄에서 **관리** > **계정** > **사용자**를 클릭하십시오.
  2. **사용자** 페이지에서 **사용자 초대** 단추를 클릭하십시오.
  3. **이메일 주소** 필드에서 지급인의 계정을 추가하십시오.
  4. **Cloud Foundry 액세스** 섹션의 드롭다운 목록에서 지급인의 계정을 추가할 조직을 선택하십시오.
  5. **청구 관리자**를 **조직 역할**로 선택하십시오.
  6. 다른 필드를 적절하게 구성한 다음 **사용자 초대**를 클릭하십시오.  
3. 지급인이 네트워크의 네트워크 모니터에서 블록체인 네트워크에 다른 구성원을 초대합니다. 네트워크 구성원 초대에 대한 자세한 정보는 [구성원](/docs/services/blockchain/v10_dashboard.html#ibp-dashboard-members)을 참조하십시오.
4. 그러면 각 구성원은 네트워크에 가입할 수 있는 초대가 포함된 알림 이메일을 수신합니다. 구성원이 네트워크에 가입할 수 있습니다. 자세한 정보는 [다른 네트워크 구성원을 위해 지불](/docs/services/blockchain/howto/paying_mode.html#paying-mode-pay-for-others)의 **4단계**를 참조하십시오.

### 알려진 제한사항
{: #paying-mode-let-other-pay-limitation}

지급인의 {{site.data.keyword.cloud_notm}} 계정을 청구 관리자로 다른 구성원 계정에 추가하고 다른 구성원이 계정을 사용하여 다른 서비스를 구매하고 나면 지급인이 해당 요금도 지불해야 합니다. 모든 구성원은 지급인의 계정에 추가 비용을 초래하는 무단 서비스를 자신의 계정에서 작성하지 않는다는 계약에 서명할 수 있습니다.  


## 다른 구성원에게 비용 이전
{: #paying-mode-transfer-billing}

네트워크 구성원에게 대신 지불해 줄 구성원이 있어도 나중에 다른 구성원이 청구 비용을 인계할 수 있습니다. 지급인이 사용자를 위해 지불하는 것을 중지할 수 있도록 계정에서 지급인 계정을 제거할 수 있습니다.

1. {{site.data.keyword.cloud_notm}} 콘솔 맨 위의 메뉴 표시줄에서 **관리** > **계정** > **Cloud Foundry 조직**을 클릭하십시오.
2. 지급인의 계정을 추가할 조직을 클릭하십시오.
3. **사용자** 탭으로 전환하십시오.
4. 사용자 테이블에서 지급인의 계정을 찾아 **조직에서 제거** 링크를 클릭하십시오.

계정에서 지급인의 계정을 제거하고 나면 블록체인 네트워크 멤버십 요금과 피어 요금이 계정에 청구됩니다.
