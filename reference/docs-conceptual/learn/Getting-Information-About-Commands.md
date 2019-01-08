---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 명령에 대한 정보 가져오기
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403312"
---
# <a name="getting-information-about-commands"></a>명령에 대한 정보 가져오기

PowerShell `Get-Command`는 현재 세션에서 사용할 수 있는 모든 명령을 표시합니다.
`Get-Command` cmdlet을 실행하면 다음 출력과 유사한 내용이 표시됩니다.

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

이 출력은 내부 명령을 표 형식으로 요약하는 **cmd.exe**의 도움말 출력과 유사합니다. 위에 표시된 `Get-Command` 명령 출력의 발췌 부분에서 표시되는 모든 명령의 CommandType은 Cmdlet입니다. cmdlet은 PowerShell의 내장 명령 형식입니다. 이 형식은 **cmd.exe**의 `dir` 및 `cd`와 같은 명령이나 Unix 셸(예: bash)의 기본 제공 명령과 거의 일치합니다.

`Get-Command` cmdlet에는 각 cmdlet의 구문을 반환하는 **Syntax** 매개 변수가 있습니다. 다음 예제에서는 `Get-Help` cmdlet의 구문을 가져오는 방법을 보여 줍니다.

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>유형별로 사용 가능한 명령 표시

`Get-Command`명령은 현재 세션에 있는 cmdlet만 표시합니다. PowerShell에서는 실제로 다양한 유형의 명령을 지원합니다.

- 별칭
- 함수
- 스크립트

외부 실행 파일 또는 등록된 파일 형식 처리기가 있는 파일도 명령으로 분류됩니다.

세션의 모든 명령을 가져오려면 다음과 같이 입력하세요.

```powershell
Get-Command *
```

이 목록에는 검색 경로에 있는 외부 명령이 포함되므로 수천 개의 항목이 포함될 수 있습니다.
찾을 명령의 수를 줄이는 것이 좋습니다.

> [!NOTE]
> 별표(\*)는 PowerShell 명령 인수에서 와일드카드 일치에 사용됩니다. \*는 "하나 이상의 문자 일치"를 의미합니다. `Get-Command a*`를 입력하여 문자 "a"로 시작하는 모든 명령을 찾을 수 있습니다. **cmd.exe**의 와일드카드 일치와 달리 PowerShell의 와일드카드는 점(.)도 일치시킵니다.

다른 형식의 네이티브 명령을 가져오려면 `Get-Command`의 **CommandType** 매개 변수를 사용합니다.
cmdlet을 실행한 경우 반환된 쿼럼 리소스에 대한 정보를 검토할 수 있습니다.

명령에 할당된 애칭인 명령 별칭을 가져오려면 다음과 같이 입력하세요.

```powershell
Get-Command -CommandType Alias
```

현재 세션의 함수를 가져오려면 다음과 같이 입력하세요.

```powershell
Get-Command -CommandType Function
```

PowerShell의 검색 경로에 스크립트를 표시하려면 다음과 같이 입력하세요.

```powershell
Get-Command -CommandType Script
```