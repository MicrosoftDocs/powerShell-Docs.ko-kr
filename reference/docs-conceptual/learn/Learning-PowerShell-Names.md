---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: PowerShell 명령 이름 학습
ms.openlocfilehash: a65ffcdca6510093b0a77234e20546b6cc1f02bf
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030419"
---
# <a name="learning-powershell-command-names"></a>PowerShell 명령 이름 학습

명령 및 매개 변수의 이름을 학습하는 것은 대부분의 명령줄 인터페이스에서 상당한 시간이 소요됩니다. 이러한 문제는 몇 가지 패턴에 따라 발생합니다. 정기적으로 사용해야 하는 명령과 매개 변수를 배우는 유일한 방법은 외우는 것입니다.

새 명령 또는 매개 변수를 사용할 때 항상 이미 알고 있는 것을 사용할 수 있는 것은 아닙니다. 새 이름을 찾아 학습해야 합니다. 일반적으로 명령줄 인터페이스는 하나의 작은 툴 세트로 시작해서 점점 증가하게 됩니다. 표준 구조가 없는 이유도 쉽게 알 수 있습니다.
각 명령이 별도 도구이므로 명령의 이름에는 이러한 방식이 논리적일 수 있습니다. PowerShell에는 명령 이름을 처리하는 더 좋은 방법이 있습니다.

## <a name="learning-command-names-in-traditional-shells"></a>기존 셸에서 명령 이름 학습

대부분의 명령은 서비스나 프로세스와 같은 운영 체제 또는 애플리케이션의 요소를 관리하도록 만들어졌습니다. 명령의 이름은 패밀리에 맞거나 맞지 않을 수 있습니다. 예를 들어 Windows 시스템에서는 `net start` 및 `net stop` 명령을 사용하여 서비스를 시작하고 중지할 수 있습니다. **Sc.exe**는 또 다른 Windows용 서비스 제어 도구입니다. 이 이름은 **net.exe** 서비스 명령에 대한 명명 패턴에는 맞지 않습니다. 프로세스 관리의 경우, Windows에는 프로세스를 표시하는 **tasklist.exe** 명령과 프로세스를 중단하는 **taskkill.exe** 명령이 있습니다.

또한 이러한 명령에는 불규칙한 매개 변수 사양이 있습니다. `net start` 명령을 사용하여 원격 컴퓨터에서 서비스를 시작할 수는 없습니다. **sc.exe** 명령을 사용하여 원격 컴퓨터에서 서비스를 시작할 수 있습니다. 하지만 원격 컴퓨터를 지정하려면 이름 앞에 이중 백슬래시를 사용해야 합니다. DC01이라는 원격 컴퓨터에서 스풀러 서비스를 시작하려면 `sc.exe \\DC01 start spooler`를 입력합니다.
DC01에서 실행되는 작업을 나열하려면 **/S** 매개 변수와 컴퓨터 이름을 백슬래시 없이 사용합니다. 정의합니다(예: `tasklist /S DC01`).

> [!NOTE]
> PowerShell v6 이전에는 `sc`가 `Set-Content` cmdlet에 대한 별칭이었습니다. 따라서 **sc.exe** 명령을 v6 이전의 PowerShell 버전에서 실행하려면 파일 확장명 **exe**를 포함하여 전체 파일 이름 **sc.exe**를 포함해야 합니다.

서비스 및 프로세스는 수명 주기가 잘 정의된 컴퓨터에서 관리 가능한 요소의 예입니다. 서비스 및 프로세스를 시작 또는 중지하거나, 현재 실행 중인 모든 서비스나 프로세스의 목록을 가져올 수 있습니다. 서비스 및 프로세스 간에는 중요한 기술적 차이가 있지만, 서비스 및 프로세스에서 수행하는 작업은 개념적으로 동일합니다. 또한 매개 변수를 지정하여 한 동작을 사용자 정의하기 위해 선택하는 것도 개념적으로 비슷할 수 있습니다.

PowerShell은 이러한 유사성을 이용하여 cmdlet을 이해하고 사용하기 위해 알아야 하는 고유 이름 수를 줄입니다.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>cmdlet에 명령을 쉽게 기억할 수 있도록 verb-noun 이름 사용

PowerShell은 "동사-명사(Verb-noun)" 네이밍 시스템을 사용합니다. 각 cmdlet 이름은 표준 동사와 특정 명사를 하이픈으로 연결해 만듭니다. PowerShell의 verb는 영어 동사가 아닐 수도 있지만 PowerShell에서는 특정 동작을 나타냅니다. noun은 모든 언어의 명사와 매우 유사합니다. 시스템 관리에서 중요한 특정 유형의 개체를 설명합니다. 몇 가지 예를 살펴보면 두 부분으로 이루어진 이러한 이름이 학습에 어떻게 도움이 되는지를 쉽게 확인할 수 있습니다.

PowerShell에는 권장되는 표준 verb 집합이 있습니다. noun은 덜 제한적이지만 verb가 작용하는 대상을 설명합니다. PowerShell에는 `Get-Process`, `Stop-Process`, `Get-Service` 및 `Stop-Service`와 같은 명령이 있습니다.

noun 2개와 verb 2개를 포함하는 이 예제에서 일관성을 유지해도 학습이 크게 간소화되지 않습니다. 이 목록을 10개의 verb와 10개의 noun으로 이루어진 표준화된 집합으로 확장합니다. 이제 20개의 단어만 이해하면 됩니다.
하지만 이러한 단어는 100개의 고유한 명령 이름으로 조합될 수 있습니다.

이름을 참조하여 PowerShell 명령이 수행하는 작업을 쉽게 이해할 수 있습니다. 컴퓨터를 종료하는 명령은 `Stop-Computer`입니다. 네트워크에 있는 모든 컴퓨터를 나열하는 명령은 `Get-Computer`입니다. 시스템 날짜를 가져오는 명령은 `Get-Date`입니다.

`Get-Command`에 대해 **Verb** 매개 변수를 사용하여 특정 verb를 포함하는 모든 명령을 나열할 수 있습니다. 예를 들어 verb `Get`을 사용하는 모든 cmdlet을 보려면 다음과 같이 입력합니다.

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

동일한 유형의 개체에 영향을 주는 명령 패밀리를 표시하려면 **Noun** 매개 변수를 사용합니다. 예를 들어, 서비스 관리에 사용할 수 있는 명령을 보려면 다음 명령을 실행합니다.

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>cmdlet에서 표준 매개 변수 사용

앞에서 설명한 것처럼 기존 명령줄 인터페이스에서 사용되는 명령이 항상 일관된 매개 변수 이름을 갖는 것은 아닙니다. 매개 변수는 입력하기는 쉽지만 초보 사용자가 이해하기 어려운 단일 문자나 약어로 되어 있는 경우가 많습니다.

대부분의 다른 기존 명령줄 인터페이스와 달리 PowerShell은 매개 변수를 직접 처리하며, 매개 변수에 대한 이러한 직접 액세스와 함께 개발자 지침을 사용하여 매개 변수 이름을 표준화합니다. 이 지침에 따르면 모든 cmdlet이 표준을 준수하도록 권장되지만 항상 표준을 따른다고 보장할 수는 없습니다.

PowerShell은 매개 변수 구분 기호도 표준화합니다. 매개 변수를 PowerShell 명령과 함께 사용할 때는 항상 이름 앞에 ‘-’을 사용합니다. 다음과 같은 예제를 참조하세요.

```powershell
Get-Command -Name Clear-Host
```

매개 변수의 이름은 **Name**이지만 명령줄에서 매개 변수로 사용할 때는 `-Name`으로 입력됩니다.

다음은 표준 매개 변수 이름 및 사용법의 몇 가지 일반적인 특성입니다.

### <a name="the-help-parameter-"></a>도움말 매개 변수(?)

cmdlet에서 `-?` 매개 변수를 지정하면 PowerShell에서 해당 cmdlet에 대한 도움말이 표시됩니다.
cmdlet은 실행되지 않습니다.

### <a name="common-parameters"></a>공통 매개 변수

PowerShell에는 몇 가지 *공통 매개 변수*가 있습니다. 이러한 매개 변수는 PowerShell 엔진에 의해 제어됩니다. 공통 매개 변수는 항상 동일한 방법으로 작동합니다. 일반 매개 변수로는 **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** 및 **OutBuffer**가 있습니다.

### <a name="recommended-parameter-names"></a>권장되는 매개 변수 이름

PowerShell 핵심 cmdlet은 유사한 매개 변수에 표준 이름을 사용합니다. 반드시 이러한 표준 이름을 사용해야 하는 것은 아니지만 표준 이름 사용을 권장하는 명시적 지침이 있습니다.

예를 들어 컴퓨터를 나타내는 매개 변수의 권장되는 이름은 Server, Host, System, Node 또는 기타 일반적인 대체 단어가 아니라 **ComputerName**입니다. 기타 중요한 권장 매개 변수 이름으로는 **Force**, **Exclude**, **Include**, **PassThru**, **Path** 및 **CaseSensitive**가 있습니다.
