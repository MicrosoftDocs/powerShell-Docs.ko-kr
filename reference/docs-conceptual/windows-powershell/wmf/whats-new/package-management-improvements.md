---
ms.date: 06/12/2017
title: WMF 5.1의 향상된 패키지 관리
description: Windows PowerShell 5.1에는 업데이트된 패키지 관리 cmdlet이 포함되어 있습니다.
ms.openlocfilehash: 572ebd1f0aa3cf09579e13c3ea52ae3e979e421f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663182"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>WMF 5.1의 향상된 패키지 관리

WMF 5.1에서 수정된 사항은 다음과 같습니다.

## <a name="version-alias"></a>버전 별칭

**시나리오** : 시스템에 P1 패키지의 버전 1.0 및 2.0이 설치되어 있는데 버전 1.0을 제거하려는 경우 `Uninstall-Package -Name P1 -Version 1.0`을 실행하면 cmdlet 실행 후 버전 1.0이 제거되어야 합니다. 그러나 결과로 버전 2.0이 제거됩니다.

이는 `-Version` 매개 변수가 `-MinimumVersion` 매개 변수의 별칭이기 때문입니다. PackageManagement에서 최소 버전이 1.0인 정규화된 패키지를 찾을 경우 최신 버전을 반환합니다. 일반적으로 최신 버전을 찾는 것이 필요한 결과이므로 일반적인 사례에서는 이 동작이 필요합니다. 그러나 `Uninstall-Package` 사례에는 적용하지 않아야 합니다.

**해결 방법** : `-Version` 별칭을 PackageManagement(즉, OneGet) 및 PowerShellGet에서 완전히 제거했습니다.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>NuGet 공급자를 부트스트래핑할지 묻는 메시지 여러 번 표시

**시나리오** : `Find-Module`, `Install-Module` 또는 다른 PackageManagement cmdlet을 컴퓨터에서 처음으로 실행하면 PackageManagement에서 NuGet 공급자를 부트스트랩하려고 합니다. 이는 PowershellGet 공급자도 NuGet 공급자를 사용하여 PowerShell 모듈을 다운로드하기 때문입니다.
그런 다음 PackageManagement에서는 NuGet 공급자 설치를 허용할지 묻는 메시지를 표시합니다. 사용자가 부트스트래핑에 대해 “예"를 선택하면 NuGet 공급자의 최신 버전이 설치됩니다.

그러나 경우에 따라 컴퓨터에 이전 버전의 NuGet 공급자가 설치된 경우 이전 버전의 NuGet이 PowerShell 세션에 먼저 로드되는 경우가 있습니다. 즉, PackageManagement에서 경합 상태가 발생합니다. 그러나 PowerShellGet이 작동하려면 최신 버전의 NuGet 공급자가 필요하므로 PowerShellGet에서는 PackageManagement에 NuGet 공급자를 다시 부트스트랩하도록 요청합니다.
따라서 NuGet 공급자를 부트스트래핑할지 묻는 메시지 여러 번 표시됩니다.

**해결 방법** : WMF 5.1에서 PackageManagement는 NuGet 공급자를 부트스트랩하라는 메시지가 여러 번 표시되지 않도록 최신 버전의 NuGet 공급자를 로드합니다.

$env:ProgramFiles\PackageManagement\ProviderAssemblies 또는 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies에 있는 경우 NuGet 공급자(NuGet-Anycpu.exe)의 이전 버전을 수동으로 삭제하여 이 문제를 해결할 수도 있습니다.

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>인트라넷 액세스만 가능한 컴퓨터에서 PackageManagement 지원

**시나리오** : 기업 시나리오로 사용자가 인터넷에 연결되어 있지 않고 인트라넷만 사용하는 환경에서 작업하는 사례가 있습니다. WMF 5.0에서 PackageManagement는 이러한 사례를 지원하지 않습니다.

**시나리오** : WMF 5.0에서 PackageManagement는 인트라넷에만 연결되고 인터넷에는 연결되지 않은 컴퓨터를 지원하지 않았습니다.

**해결 방법** : WMF 5.1에서는 다음 단계에 따라 인트라넷 컴퓨터에서 PackageManagement를 사용하도록 허용할 수 있습니다.

1. 인터넷에 연결된 다른 컴퓨터에서 `Install-PackageProvider -Name NuGet`을 사용하여 NuGet 공급자를 다운로드합니다.

2. `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 또는 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`에서 NuGet 공급자를 찾습니다.

3. 이 이진 파일을 인트라넷 컴퓨터에서 액세스할 수 있는 폴더 또는 네트워크 공유 위치에 복사한 다음 `Install-PackageProvider -Name NuGet -Source <Path to folder>`를 사용하여 NuGet 공급자를 설치합니다.

## <a name="event-logging-improvements"></a>향상된 이벤트 로깅

패키지를 설치하면 컴퓨터 상태가 변경됩니다. 이제 WMF 5.1에서 PackageManagement는 `Install-Package`, `Uninstall-Package` 및 `Save-Package` 활동에 대한 이벤트를 Windows 이벤트 로그에 기록합니다. 이벤트 로그는 PowerShell의 경우와 동일한 `Microsoft-Windows-PowerShell, Operational`입니다.

## <a name="support-for-basic-authentication"></a>기본 인증 지원

WMF 5.1에서 PackageManagement는 기본 인증이 필요한 리포지토리에서 패키지를 찾고 설치할 수 있습니다. `Find-Package` 및 `Install-Package` cmdlet에 자격 증명을 제공할 수 있습니다. 다음은 그 예입니다.

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>프록시 뒤에 있는 PackageManagement 사용 지원

WMF 5.1에서 PackageManagement는 새 프록시 매개 변수 `-ProxyCredential` 및 `-Proxy`를 사용합니다. 이러한 매개 변수를 사용하여 PackageManagement cmdlet에 프록시 URL 및 자격 증명을 지정할 수 있습니다. 기본적으로 시스템 프록시 설정이 사용됩니다. 다음은 그 예입니다.

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
