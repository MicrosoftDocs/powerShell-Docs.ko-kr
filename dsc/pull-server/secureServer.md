---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버 모범 사례
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079203"
---
# <a name="pull-server-best-practices"></a>끌어오기 서버 모범 사례

적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

요약: 이 문서는 솔루션을 준비하고 있는 엔지니어를 지원하는 프로세스 및 확장성을 포함하기 위해 작성되었습니다. 세부 내용에서는 고객이 식별하고 제품 팀이 검증을 통해 미래에 대비하고 안정적이라고 간주되는 권장 사항으로 확인한 모범 사례를 제공합니다.

| |문서 정보|
|:---|:---|
작성자 | Michael Greene
검토자 | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
게시 날짜 | 2015년 4월

## <a name="abstract"></a>요약

이 문서는 Windows PowerShell Desired State Configuration 끌어오기 서버 구현을 준비 중인 사용자에게 공식 지침을 제공하기 위해 작성되었습니다. 끌어오기 서버는 몇 분만에 배포할 수 있는 간단한 서비스입니다. 이 문서는 배포 시 사용할 수 있는 기술적인 방법 지침도 제공하지만, 모범 사례와 배포 전 고려할 사항을 참조할 수 있다는 점에서 유용합니다.
이 문서를 읽으려면 DSC에 대한 기본 사항과 DSC 배포에 포함되는 구성 요소를 설명하는 용어를 잘 알고 있어야 합니다. 자세한 내용은 [Windows PowerShell Desired State Configuration 개요](/powershell/dsc/overview) 항목을 참조하세요.
DSC는 클라우드 주기에 따라 개선될 것이므로 끌어오기 서버를 비롯한 기본 기술도 발전하고 새로운 기능을 도입할 것으로 예상됩니다. 이 문서의 부록에 포함된 버전 테이블에서는 이전 릴리스에 대한 참조와 진취적인 디자인을 권장하기 위한 미래에 대비한 솔루션에 대한 참조를 제공합니다.

이 문서의 두 가지 주요 섹션은 다음과 같습니다.

- 구성 계획
- 설치 가이드

### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework의 버전

이 문서의 정보는 Windows Management Framework 5.0에 적용됩니다. 끌어오기 서버를 배포 및 운영하는 데 WMF 5.0이 필요하지는 않지만 이 문서에서는 버전 5.0을 주로 설명합니다.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

DSC(Desired State Configuration)는 CIM(Common Information Model)을 설명하는 MOF(Managed Object Format)라는 산업 구문을 사용하여 구성 데이터를 배포 및 관리할 수 있는 관리 플랫폼입니다. 오픈 소스 프로젝트인 OMI(Open Management Infrastructure)는 Linux 및 네트워크 하드웨어 운영 체제를 비롯한 다양한 플랫폼에서 이러한 표준을 성공적으로 개발하기 위해 마련되었습니다. 자세한 내용은 [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim)(MOF 사양에 연결되는 DMTF 페이지) 및 [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php)(OMI 문서 및 원본)을 참조하세요.

Windows PowerShell에서는 선언적 구성을 만들고 관리하는 데 사용할 수 있는 Desired State Configuration의 언어 확장 집합을 제공합니다.

### <a name="pull-server-role"></a>끌어오기 서버 역할

끌어오기 서버는 구성을 저장하여 대상 노드에서 액세스할 수 있게 하는 중앙 집중식 서비스를 제공합니다.

끌어오기 서버 역할은 웹 서버 인스턴스나 SMB 파일 공유로 배포할 수 있습니다. 웹 서버 기능에는 OData 인터페이스가 포함되며 필요에 따라 구성이 적용될 때 대상 노드가 성공 또는 실패에 대한 확인을 다시 보고하는 기능도 포함될 수 있습니다. 이 기능은 많은 수의 대상 노드가 있는 환경에서 유용합니다.
대상 노드(클라이언트라고도 함)가 끌어오기 서버를 가리키도록 구성한 후 최신 구성 데이터 및 모든 필수 스크립트가 다운로드되어 적용됩니다. 이 작업은 일회성 배포 또는 되풀이 작업으로 수행될 수 있으므로 끌어오기 서버가 대규모 변경을 관리하기 위한 중요한 자산도 됩니다. 자세한 내용은 [Windows PowerShell Desired State Configuration 끌어오기 서버](/powershell/dsc/pullServer) 및

[밀어넣기 및 끌어오기 구성 모드](/powershell/dsc/pullServer)를 참조하세요.

## <a name="configuration-planning"></a>구성 계획

엔터프라이즈 소프트웨어 배포의 경우 올바른 아키텍처를 계획하고 배포를 완료하는 데 필요한 단계를 준비하기 위해 미리 수집할 수 있는 정보가 있습니다. 다음 섹션에서는 준비하는 방법 및 미리 수행해야 할 수 있는 조직 연결과 관련된 정보를 제공합니다.

### <a name="software-requirements"></a>소프트웨어 요구 사항

끌어오기 서버를 배포하려면 Windows Server의 DSC 서비스 기능이 필요합니다. 이 기능은 Windows Server 2012에서 도입되었으며 WMF(Windows Management Framework)의 지속적인 릴리스를 통해 업데이트되었습니다.

### <a name="software-downloads"></a>소프트웨어 다운로드

Windows 업데이트에서 최신 콘텐츠를 설치하는 것 외에도 DSC 끌어오기 서버를 배포하기 위한 모범 사례인 다음과 같은 두 가지 다운로드가 있습니다. 최신 버전의 Windows Management Framework 및 끌어오기 서버 프로비전을 자동화하는 DSC 모듈

### <a name="wmf"></a>WMF

Windows Server 2012 R2에는 DSC 서비스라는 기능이 포함되어 있습니다. DSC 서비스 기능은 OData 엔드포인트를 지원하는 이진 파일을 비롯한 끌어오기 서버 기능을 제공합니다.
WMF는 Windows Server에 포함되어 있으며 Windows Server 릴리스 사이에 빠른 주기로 업데이트됩니다. [WMF 5.0의 새 버전](https://www.microsoft.com/en-us/download/details.aspx?id=54616)에는 DSC 서비스 기능에 대한 업데이트가 포함될 수 있습니다. 따라서 WMF의 최신 릴리스를 다운로드하고 릴리스 정보를 검토하여 해당 릴리스에 DSC 서비스 기능에 대한 업데이트가 포함되어 있는지 확인하는 것이 좋습니다. 업데이트 또는 시나리오의 디자인 상태가 안정적 또는 실험적으로 나열되는지를 나타내는 릴리스 정보 섹션도 검토해야 합니다.
빠른 릴리스 주기를 달성하기 위해 WMF가 미리 보기로 릴리스된 동안에도 기능을 프로덕션 환경에서 사용할 수 있도록 개별 기능을 안정적이라고 선언할 수 있습니다.
지금까지 WMF 릴리스에서 업데이트된 다른 기능은 다음과 같습니다(자세한 내용은 WMF 릴리스 정보 참조).

- Windows PowerShell, Windows PowerShell ISE(통합 스크립팅
- 환경), Windows PowerShell 웹 서비스(관리 OData
- IIS 확장), Windows PowerShell DSC(Desired State Configuration)
- WinRM(Windows 원격 관리), WMI(Windows Management Instrumentation)

### <a name="dsc-resource"></a>DSC 리소스

DSC 구성 스크립트를 사용하여 서비스를 프로비전하면 끌어오기 서버 배포를 간소화할 수 있습니다. 이 문서에는 프로덕션 준비가 된 서버 노드를 배포하는 데 사용할 수 있는 구성 스크립트가 포함되어 있습니다. 구성 스크립트를 사용하려면 Windows Server에 포함되지 않은 DSC 모듈이 필요합니다. 필요한 모듈 이름은 DSC 리소스 **xDscWebService**를 포함하는 **xPSDesiredStateConfiguration**입니다. XPSDesiredStateConfiguration 모듈은 [여기](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)에서 다운로드할 수 있습니다.

**PowerShellGet** 모듈에서 `Install-Module` cmdlet을 사용합니다.

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** 모듈은 모듈을 다음 위치로 다운로드합니다.

`C:\Program Files\Windows PowerShell\Modules`

계획 작업|
---|
Windows Server 2012 R2용 설치 파일에 액세스할 수 있나요?|
배포 환경에서 인터넷에 액세스하여 온라인 갤러리에서 WMF 및 모듈을 다운로드할 수 있나요?|
운영 체제를 설치한 후 최신 보안 업데이트를 어떻게 설치하나요?|
환경에서 인터넷에 액세스하여 업데이트를 다운로드할 수 있거나 로컬 WSUS(Windows Server Update Services) 서버가 있나요?|
오프라인 추가를 통해 업데이트를 이미 포함하는 Windows Server 설치 파일에 액세스할 수 있나요?|

### <a name="hardware-requirements"></a>하드웨어 요구 사항

끌어오기 서버 배포는 물리적 서버와 가상 서버 모두에서 지원됩니다. 끌어오기 서버의 크기 요구 사항은 Windows Server 2012 R2의 요구 사항과 일치합니다.

CPU: 1.4GHz 64비트 프로세서 메모리: 512MB 디스크 공간: 32GB 네트워크: 기가비트 이더넷 어댑터

계획 작업|
---|
물리적 하드웨어에 배포하나요? 가상화 플랫폼에 배포하나요?|
대상 환경에 대한 새 서버를 요청하는 절차는 어떻게 되나요?|
서버를 사용할 수 있을 때까지 걸리는 평균 소요 시간은 어떻게 되나요?|
필요한 서버의 크기는 어떻게 되나요?|

### <a name="accounts"></a>계정

끌어오기 서버 인스턴스를 배포하는 데 필요한 서비스 계정 요구 사항은 없습니다.
그러나 로컬 사용자 계정의 컨텍스트에서 웹 사이트를 실행할 수 있는 시나리오가 있습니다.
웹 사이트 콘텐츠를 위해 스토리지 공유에 액세스해야 하고 Windows Server 또는 스토리지 공유를 호스트하는 장치가 도메인에 연결되지 않은 경우를 예로 들 수 있습니다.

### <a name="dns-records"></a>DNS 레코드

끌어오기 서버 환경에서 작동하는 클라이언트를 구성할 때 사용할 서버 이름이 필요합니다.
테스트 환경에서는 일반적으로 서버 호스트 이름이 사용되거나 DNS 이름 확인을 사용할 수 없는 경우 서버의 IP 주소를 사용할 수 있습니다.
프로덕션 환경 또는 프로덕션 배포를 나타내기 위해 설계된 랩 환경에서는 DNS CNAME 레코드를 만드는 것이 가장 좋습니다.

DNS CNAME을 사용하면 호스트(A) 레코드를 참조하는 별칭을 만들 수 있습니다.
추가 이름 레코드는 나중에 변경이 필요한 경우 유연성을 높이기 위한 것입니다.
CNAME은 클라이언트 구성을 격리할 수 있으므로 끌어오기 서버를 교체하거나 끌어오기 서버를 추가하는 등 서버 환경을 변경할 때 해당하는 클라이언트 구성을 변경할 필요가 없습니다.

DNS 레코드의 이름을 선택할 때는 항상 솔루션 아키텍처를 고려하세요.
부하 분산을 사용하는 경우 HTTPS를 통한 트래픽을 보호하는 데 사용되는 인증서가 DNS 레코드와 동일한 이름을 공유해야 합니다.

시나리오 |모범 사례
:---|:---
테스트 환경 |가능하면 계획된 프로덕션 환경을 재현합니다. 간단한 구성에는 서버 호스트 이름이 적합합니다. DNS를 사용할 수 없는 경우 호스트 이름 대신 IP 주소를 사용할 수 있습니다.|
단일 노드 배포 |서버 호스트 이름을 가리키는 DNS CNAME 레코드를 만듭니다.|

자세한 내용은 [Windows Server에서 DNS 라운드 로빈 구성](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))을 참조하세요.

계획 작업|
---|
DNS 레코드를 만들고 변경하기 위해 누구에게 연결해야 하는지 아나요?|
DNS 레코드 요청의 평균 소요 시간은 얼마나 되나요?|
서버의 정적 호스트 이름(A) 레코드를 요청해야 하나요?|
CNAME으로 무엇을 요청하나요?|
필요한 경우 어떤 유형의 부하 분산 솔루션은 활용하나요? (자세한 내용은 부하 분산이라는 섹션 참조)|

### <a name="public-key-infrastructure"></a>공개 키 인프라

오늘날의 대부분의 조직에서는 네트워크 트래픽 특히, 서버 구성 방법과 같은 중요한 데이터를 포함하는 트래픽을 전송 중 유효성을 검사하거나 암호화해야 합니다.
일반 텍스트의 클라이언트 요청을 지원하는 HTTP를 사용하여 끌어오기 서버를 배포할 수도 있지만 HTTPS를 사용하여 트래픽 보안을 유지하는 것이 좋습니다. DSC 리소스 **xPSDesiredStateConfiguration**에 있는 매개 변수 집합을 사용하여 HTTPS를 사용하도록 서비스를 구성할 수 있습니다.

끌어오기 서버의 HTTPS 트래픽 보안을 설정하는 데 필요한 인증서 요구 사항은 다른 HTTPS 웹 사이트 보안 설정과 다르지 않습니다. Windows Server 인증서 서비스의 **웹 서버** 템플릿은 필요한 기능을 제공합니다.

계획 작업|
---|
인증서 요청이 자동화되지 않은 경우 인증서를 요청하기 위해 누구에게 연락해야 하나요?|
요청의 평균 소요 시간은 얼마나 되나요?|
인증서 파일을 어떻게 전송받나요?|
인증서 개인 키를 어떻게 전송받나요?|
기본 만료 시간은 얼마나 되나요?|
끌어오기 서버 환경의 DNS 이름을 정한 경우 이 이름을 인증서 이름에 사용할 수 있나요?|

### <a name="choosing-an-architecture"></a>아키텍처 선택

IIS 또는 SMB 파일 공유에 호스트된 웹 서비스를 사용하여 끌어오기 서버를 배포할 수 있습니다. 대부분의 경우 웹 서비스 옵션을 사용하면 유연성이 늘어납니다. HTTPS 트래픽이 네트워크 경계를 트래버스하는 경우는 드물지 않지만, SMB 트래픽은 네트워크 간에 차단되거나 필터링되는 경우가 많습니다. 또한 웹 서비스에서는 중앙에서 가시성 향상을 위해 클라이언트가 상태를 서버에 다시 보고하는 메커니즘을 제공하는 준수 서버 또는 웹 보고 관리자(두 항목 모두 이 설명서의 이후 버전에서 다룸)를 포함하는 오션도 제공합니다.
SMB는 정책에서 웹 서버를 사용하면 안 되도록 지정하는 환경 및 웹 서버 역할을 필요하지 않게 하는 다른 환경 요구 사항에 대한 옵션을 제공합니다.
두 경우 모두 트래픽 서명 및 암호화에 필요한 요구 사항을 평가해야 합니다. HTTPS, SMB 서명 및 IPSEC 정책 모두 고려할 만한 옵션입니다.

#### <a name="load-balancing"></a>부하 분산

웹 서비스와 상호 작용하는 클라이언트는 단일 응답으로 반환되는 정보를 요청합니다. 순차 요청이 필요하지 않으므로 부하 분산 플랫폼이 임의의 시점에 세션이 단일 서버에서 유지 관리되는지 확인할 필요가 없습니다.

계획 작업|
---|
트래픽 부하를 서버 간에 분산하기 위해 어떤 솔루션을 사용하나요?|
하드웨어 부하 분산 디바이스를 사용할 경우 디바이스에 새 구성을 추가하도록 누가 요청하나요?|
부하 분산된 새 웹 서비스를 구성하는 요청의 평균 소요 시간은 얼마나 되나요?|
요청에 어떤 정보가 필요하나요?|
추가 IP를 요청해야 하나요? 아니면 부하 분산을 담당하는 팀이 이를 처리하나요?|
필요한 DNS 레코드가 있고 부하 분산 솔루션을 구성하는 팀에 이 레코드가 필요하나요?|
부하 분산 솔루션을 사용하려면 PKI를 디바이스에서 처리해야 하나요? 또는 세션 요구 사항이 없는 경우 부하 분산 솔루션에서 HTTPS 트래픽 부하를 분산할 수 있나요?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>끌어오기 서버에서 구성 및 모듈 준비

구성 계획의 일환으로 끌어오기 서버에서 호스트할 DSC에 모듈 및 구성을 고려해야 합니다. 구성 계획을 위해 콘텐츠를 준비하고 끌어오기 서버에 배포하는 방법에 대한 기본 사항을 이해하는 것이 중요합니다.

향후 이 섹션이 확장되어 DSC 끌어오기 서버 운영 가이드에 포함됩니다.  이 가이드에서는 자동화를 사용하여 시간에 따라 모듈 및 구성을 관리하는 일일 프로세스를 설명합니다.

#### <a name="dsc-modules"></a>DSC 모듈

구성을 요청하는 클라이언트는 필수 DSC 모듈이 필요합니다. 끌어오기 서버는 클라이언트로의 DSC 모듈 주문형 배포를 자동화합니다. 끌어오기 서버를 처음으로 랩 또는 개념 증명으로 배포하는 경우에는 PowerShell 갤러리와 같은 공용 리포지토리 또는 DSC 모듈용 PowerShell.org GitHub 리포지토리에서 제공되는 DSC 모듈을 사용할 가능성이 높습니다.

PowerShell 갤러리와 같은 신뢰할 수 있는 온라인 원본인 경우에도 공용 리포지토리에서 다운로드하는 모든 모듈은 프로덕션에서 사용하기 전에 모듈을 사용할 환경에 대한 PowerShell 경험 및 지식이 있는 사용자가 검토해야 합니다. 이 작업을 수행하는 동안 모듈에서 제거할 수 있는 설명서 및 예제 스크립트와 같은 추가 페이로드가 있는지 확인하는 것이 좋습니다. 이렇게 하면 모듈을 네트워크를 통해 서버에서 클라이언트로 다운로드하는 첫 번째 요청에서 클라이언트당 네트워크 대역폭이 줄어듭니다.

각 모듈은 모듈 페이로드를 포함하는 ModuleName_Version.zip이라는 특정 형식의 ZIP 파일로 패키지해야 합니다. 파일을 서버에 복사한 후 체크섬 파일을 만들어야 합니다. 클라이언트가 서버에 연결할 때 이 체크섬을 사용하여 DSC 모듈의 콘텐츠가 게시된 후 변경되지 않았는지 확인합니다.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

계획 작업|
---|
테스트 또는 랩 환경을 계획하는 경우 유효성을 검사하기 위해 어떤 시나리오가 중요할까요?|
필요한 모든 사항을 처리할 리소스를 포함하는 공개된 모듈이 있나요? 아니면 리소스를 직접 만들어야 하나요?|
인터넷에 액세스하여 공용 모듈을 검색할 수 있는 환경인가요?|
누가 DSC 모듈을 검토하나요?|
프로덕션 환경을 계획하는 경우 DSC 모듈을 저장하기 위한 로컬 리포지토리로 무엇을 사용할 예정인가요?|
중앙 팀이 애플리케이션 팀의 DSC 모듈을 수락할 계획인가요? 절차는 어떻게 되나요?|
원본 리포지토리에서 서버로 프로덕션이 준비된 DSC 모듈의 패키징, 복사 및 체크섬 만들기를 자동화할 계획인가요?|
귀하의 팀이 자동화 플랫폼을 관리할 계획인가요?|

#### <a name="dsc-configurations"></a>DSC 구성

끌어오기 서버의 용도는 DSC 구성을 클라이언트 노드에 배포하기 위한 중앙 집중식 메커니즘을 제공하는 것입니다. 구성은 서버에 MOF 문서로 저장됩니다.
각 문서의 이름은 고유한 **GUID**를 사용하여 지정됩니다. 클라이언트가 끌어오기 서버와 연결하도록 구성된 경우 요청해야 하는 구성의 **GUID**도 제공받습니다. **GUID**로 구성을 참조하는 이 시스템은 글로벌 고유성을 보장하며 구성을 노드별로 세부적으로 적용하거나 구성이 동일한 여러 서버에 걸친 역할 구성으로 적용할 수 있습니다.

#### <a name="guids"></a>GUID

끌어오기 서버 배포를 고려할 때 구성 **GUID** 계획에 더욱 주의를 기울여야 합니다. **GUID** 처리 방법에 대한 특별한 요구 사항은 없으며 환경마다 프로세스가 고유할 수 있습니다. 중앙에 저장된 CSV 파일, 단순한 SQL 테이블, CMDB, 다른 도구 또는 소프트웨어 솔루션과 통합해야 하는 복잡한 솔루션 등 프로세스가 단순하거나 복잡할 수 있습니다. 두 가지 일반적인 접근 방식은 다음과 같습니다.

- **서버당 GUID 할당** - 모든 서버 구성을 개별적으로 확실히 제어할 수 있습니다. 서버 수가 적은 환경에서 효과적인 이 접근 방식을 채택하면 정확하게 업데이트할 수 있습니다.
- **서버 역할당 GUID 할당** - 웹 서버와 같이 동일한 기능을 수행하는 모든 서버가 동일한 GUID를 사용하여 필요한 구성 데이터를 참조합니다.  여러 서버가 동일한 GUID를 공유하는 경우 구성이 변경되면 이들 서버가 모두 동시에 업데이트됩니다.

  GUID는 악의적인 의도를 가진 사람에 의해 환경의 서버 배포 및 구성 방법에 대한 정보를 얻는 데 활용될 수 있으므로 중요한 데이터로 고려해야 합니다. 자세한 내용은 [PowerShell Desired State Configuration 끌어오기 모드에서 GUID 안전하게 할당](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/)을 참조하세요.

계획 작업|
---|
구성이 준비되면 누가 끌어오기 서버 폴더로 복사하나요?|
구성을 애플리케이션 팀에서 작성하는 경우 구성을 전달하는 프로세스는 어떻게 되나요?|
구성이 여러 팀에서 작성되면 리포지토리를 사용하여 저장하나요?|
구성을 서버에 복사하고 구성이 준비되면 체크섬을 만드는 프로세스를 자동화하나요?|
GUID를 서버 또는 역할에 매핑하는 방법은 무엇이고 GUID를 어디에 저장하나요?|
클라이언트 머신을 구성하는 프로세스로 무엇을 사용하며, 구성 GUID를 만들고 저장하는 프로세스와 어떻게 통합하나요?|

## <a name="installation-guide"></a>설치 가이드

*이 문서에 제공된 스크립트는 안정적인 예제입니다. 스크립트를 프로덕션 환경에서 실행하기 전에 항상 신중히 검토하세요.*

### <a name="prerequisites"></a>필수 구성 요소

서버에서 PowerShell 버전을 확인하려면 다음 명령을 사용합니다.

```powershell
$PSVersionTable.PSVersion
```

가능하면 최신 버전의 Windows Management Framework로 업그레이드합니다.
그리고 다음 명령을 사용하여 `xPsDesiredStateConfiguration` 모듈을 다운로드합니다.

```powershell
Install-Module xPSDesiredStateConfiguration
```

이 명령은 모듈을 다운로드하기 전에 사용자의 승인을 요청합니다.

### <a name="installation-and-configuration-scripts"></a>설치 및 구성 스크립트

DSC 끌어오기 서버를 배포하는 최상의 방법은 DSC 구성 스크립트를 사용하는 것입니다. 이 문서에서는 DSC 웹 서비스만 구성하는 기본 설정과 DSC 웹 서비스를 포함하는 종단 간 Windows Server를 구성하는 고급 설정이 모두 포함된 스크립트를 제공합니다.

참고:  현재 `xPSDesiredStateConfiguration` DSC 모듈을 사용하려면 EN-US 로캘의 서버가 필요합니다.

### <a name="basic-configuration-for-windows-server-2012"></a>Windows Server 2012에 대한 기본 구성

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Windows Server 2012 R2에 대한 고급 구성

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>끌어오기 서버 기능 확인

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>클라이언트 구성

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>추가 참조, 코드 조각 및 예제

이 예제에서는 테스트를 위해 클라이언트 연결을 수동으로 시작하는 방법(WMF5 필요)을 보여 줍니다.

```powershell
Update-DscConfiguration –Wait -Verbose
```

[Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet은 CNAME 형식 레코드를 DNS 영역에 추가하는 데 사용됩니다.

[체크섬을 만들고 DSC MOF를 SMB 끌어오기 서버에 게시](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0)하는 PowerShell 함수는 필요한 체크섬을 자동으로 생성한 다음 MOF 구성과 체크섬 파일을 SMB 끌어오기 서버에 복사합니다.

## <a name="appendix---understanding-odata-service-data-file-types"></a>부록 - ODATA 서비스 데이터 파일 형식 이해

OData 웹 서비스를 포함하는 끌어오기 서버 배포 중 정보를 만들기 위해 데이터 파일이 저장됩니다. 파일 형식은 아래 설명된 대로 운영 체제에 따라 다릅니다.

- **Windows Server 2012** 파일 형식은 항상 .mdb입니다.
- **Windows Server 2012 R2** 구성에 .mdb를 지정하지 않은 경우 파일 형식은 기본적으로 .edb입니다.

끌어오기 서버를 설치하기 위한 [고급 예제 스크립트](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)에서는 web.config 파일 설정을 자동으로 제어하여 파일 형식으로 인한 오류 발생을 방지하는 방법에 대한 예제도 찾을 수 있습니다.
