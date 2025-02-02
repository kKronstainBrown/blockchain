---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-05"

keywords: channel update policy, endorsement policy, Network Monitor, number of channel operators

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 채널 작성 또는 업데이트
{: #ibp-create-channel}

채널은 데이터의 파티션을 지정하고 분리하는 믿을 수 없을 정도로 강력한 메커니즘이며 데이터 개인정보 보호정책에 대한 기반을 제공합니다. 같은 채널의 구성원만 이 채널의 데이터에 액세스할 수 있습니다.
{:shortdesc}

채널 보안을 위해 채널 업데이트 정책은 채널을 작성하거나 업데이트하기 전에 채널 작성 또는 업데이트 요청에 동의해야 하는 채널 운영자의 수를 정의하도록 구성됩니다.

## 채널 작성
{: #ibp-create-channel-creating-a-channel}

네트워크 모니터의 "채널" 화면에서 **새 채널** 단추를 클릭하고 다음 단계를 완료하여 채널 작성 요청을 제출하십시오.
1. 채널의 비즈니스 목표를 반영하는 이름을 선택하고 원하는 경우 설명을 추가해서 **다음**을 클릭하십시오. 채널 이름은 블록체인 네트워크에서 고유해야 합니다. 이 이름은 문자로 시작해야 하며 소문자, 숫자 또는 대시만 포함할 수 있습니다.
  ![채널 1 작성](../images/create_channel.png "채널 패널 1 작성")

2. 네트워크 구성원을 선택하고 **구성원 추가** 단추를 클릭하여 네트워크 구성원 조합을 초대하십시오. 초대한 구성원 각각에 대한 역할을 지정하여 권한을 사용자 정의하고 **다음**을 클릭하십시오.
  ![채널 2 작성](../images/create_channel_2.png "채널 패널 2 작성")

    * 채널 운영자는 채널 원장을 조회하거나 업데이트할 수 있습니다. 채널 운영자는 채널 작성 요청을 **승인** 또는 **거부**하고, 채널 업데이트 요청을 제출할 수 있는 권한이 있습니다. 각 채널에는 하나 이상의 **운영자**가 있어야 합니다.
    * 채널 작성자는 예를 들면 체인코드 함수를 호출하여 채널 원장을 업데이트할 수 있습니다. 채널 작성자는 채널에 체인코드를 인스턴스화할 수도 있습니다.
    * 채널 독자는 예를 들면 읽기 전용 체인코드 함수를 호출하여 채널 원장을 조회만 할 수 있습니다.

3. 채널 업데이트 요청을 승인할 채널 운영자의 수를 선택하여 채널 업데이트 정책을 구성하고 **요청 제출**을 클릭하십시오.
  ![채널 3 작성](../images/create_channel_3.png "채널 패널 3 작성")

초대된 구성원은 초대 이메일을 받게 됩니다. 또한, 네트워크 모니터의 **알림** 화면에서 "모두" 또는 "보류 중" 하위 탭에 있는 요청을 찾을 수 있습니다.
* 채널 운영자로서 초대된 구성원은 **요청 검토** 단추를 클릭하여 채널 구성을 검토한 후에 요청을 **승인** 또는 **거부**할 수 있습니다. "내 상태" 열은 요청에 대한 운영자의 투표 상태를 표시합니다.
    * _투표 보류 중_: 운영자가 요청을 처리하지 않았습니다.
    * _투표 승인됨_: 운영자가 요청을 승인했습니다.
    * _투표 거부됨_: 운영자가 요청을 거부했습니다.
    * _투표 마감_: 요청이 충분한 **승인** 투표를 획득하여 운영자가 더 이상 승인 또는 거부를 필요로 하지 않습니다.
* 채널 작성자 또는 독자로서 초대된 구성원은 "내 상태" 열 아래의 *필수 아님*을 볼 수 있습니다. 요청이 채널 운영자로부터 충분한 **승인** 투표를 얻기 전에 작성자 또는 독자는 **요청 검토** 단추를 클릭하여 채널 구성을 검토할 수 있습니다.

충분한 채널 운영자가 요청에 동의하면 임의의 채널 구성원이 **요청 제출** 단추를 클릭하여 새 채널을 작성할 수 있습니다. 모든 채널 구성원이 해당 네트워크 모니터의 "채널" 화면에서 채널을 찾을 수 있습니다.

### 관리 채널 작성

고도로 통제된 환전 시장에서는 다양한 운영자 또는 구성원이 정상적으로 처리할 채널에서 신뢰할 수 있는 서드파티에게 관리 역할을 지정해야 합니다.

이 경우 신뢰할 수 있는 서드파티는 스스로를 채널의 “운영자”로만 설정하고 다른 구성원은 “작성자”로 지정합니다. 이렇게 하면 두 개의 은행에 트랜잭션을 호출하는 기능이 계속 제공되면서 서드파티에게 채널을 편집하는 단독 권한이 제공됩니다. 다른 구성원을 "독자"로 설정하여 관리 "읽기 전용" 채널도 작성할 수 있습니다.

## 채널 업데이트
{: #ibp-create-channel-updating-a-channel}

채널의 구성을 수정하려는 경우(예: 채널 구성원을 추가하거나 제거, 또는 채널 업데이트 정책 변경), 채널 업데이트 요청을 제출할 수 있습니다. 네트워크 모니터의 "채널" 화면에서 수정할 채널을 찾아서 **조치** 헤더 아래의 드롭 다운 목록에서 **채널 편집**을 선택하십시오. 패널을 탐색하여 원하는 엔티티를 변경하고 **요청 제출**을 클릭하여 채널 업데이트 요청을 시작하십시오.

모든 채널 구성원이 채널 업데이트 요청에 대한 이메일 알림을 수신합니다.
* 새로 초대된 구성원은 채널에 가입하도록 초대하는 이메일 알림을 수신합니다. 또한, 네트워크 모니터의 **알림** 화면에 "투표 보류 중" 상태의 요청을 찾을 수 있습니다.
    * 채널 운영자로서 초대된 구성원은 **요청 검토** 단추를 클릭하여 채널 구성을 검토한 후에 채널 업데이트 요청을 **승인** 또는 **거부**할 수 있습니다.  "내 상태" 열은 요청에 대한 운영자의 투표 상태를 표시합니다.
        * _투표 보류 중_: 운영자가 요청을 처리하지 않았습니다.
        * _투표 승인됨_: 운영자가 요청을 승인했습니다.
        * _투표 거부됨_: 운영자가 요청을 거부했습니다.
        * _투표 마감_: 요청이 충분한 **승인** 투표를 획득하여 운영자가 더 이상 승인 또는 거부를 필요로 하지 않습니다.
    * 채널 작성자 또는 독자로서 초대된 구성원은 "내 상태" 열 아래의 *필수 아님*을 볼 수 있습니다. 요청이 채널 운영자로부터 충분한 **승인** 투표를 얻기 전에 작성자 또는 독자는 **요청 검토** 단추를 클릭하여 채널 구성을 검토할 수 있습니다.
* 제거된 구성원은 채널 변경에 대한 이메일 알림을 수신합니다.
* 기존 채널 운영자도 채널 업데이트에 대한 이메일 알림을 수신합니다. 또한 네트워크 모니터의 **알림** 화면에서 _투표 보류 중_ 상태의 요청을 찾아서 **승인**하거나 **거부**할 수 있습니다.
* 기존 채널 작성자도 채널 업데이트에 대한 이메일 알림을 수신합니다. 네트워크 모니터의 **알림** 화면에 _필수 아님_ 상태의 요청을 찾을 수 있습니다.

충분한 채널 운영자가 요청에 동의하면 임의의 채널 구성원이 **요청 제출** 단추를 클릭하여 채널을 업데이트할 수 있습니다. 모든 채널 구성원이 네트워크 모니터의 "채널" 화면에서 업데이트된 채널을 찾을 수 있습니다.

새 조직에서 채널에 가입하고 체인코드를 설치할 때 보증 정책은 자동으로 업데이트되지 않습니다. 예를 들어, 5개 조직 중 2개 조직에서 트랜잭션을 보증해야 하는 경우 새로운 조직에서 채널에 가입할 때 6개 조직 중 2개 조직이 필요하도록 정책이 업데이트되지 않습니다. 대신 새 조직이 정책에 나열되지 않으며 트랜잭션을 보증할 수 없습니다. [관련 체인코드 업데이트](/docs/services/blockchain/howto/install_instantiate_chaincode.html#install-instantiate-chaincode-update-cc)로 새 조직을 보증 정책에 추가할 수 있습니다. 자세한 정보는 [체인코드 보증 정책](/docs/services/blockchain/howto/install_instantiate_chaincode.html#install-instantiate-chaincode-endorsement-policy)을 참조하십시오.
{:important}
