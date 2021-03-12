---
description: PowerShell에서 실행할 명령을 결정 하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: ee5d2dfcd8e7353950bec27a320bf3e0f76281c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195061"
---
# <a name="about-command-precedence"></a>명령 우선 순위 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 실행할 명령을 결정 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

명령 우선 순위는 세션에 동일한 이름의 명령이 두 개 이상 포함 된 경우 PowerShell에서 실행할 명령을 결정 하는 방법을 설명 합니다. 세션 내의 명령은 동일한 이름의 명령으로 숨겨지거나 바꿀 수 있습니다. 이 문서에서는 숨겨진 명령 실행 방법과 명령 이름 충돌을 방지 하는 방법을 보여 줍니다.

## <a name="command-precedence"></a>명령 우선 순위

PowerShell 세션에 동일한 이름의 명령이 두 개 이상 포함 된 경우 PowerShell은 다음 규칙을 사용 하 여 실행할 명령을 결정 합니다.

명령에 대 한 경로를 지정 하는 경우 PowerShell은 경로에 지정 된 위치에서 명령을 실행 합니다.

예를 들어 다음 명령은 "C: TechDocs" 디렉터리에서 FindDocs.ps1 스크립트를 실행 합니다 \\ .

```
C:\TechDocs\FindDocs.ps1
```

Powershell은 경로 환경 변수에 나열 된 경로에 명령이 없거나 `$env:path` 스크립트 파일의 경로를 지정 하지 않은 경우 powershell 스크립트를 포함 하 여 실행 파일 (네이티브) 명령을 실행 하지 않습니다.

현재 디렉터리에 있는 스크립트를 실행 하려면 전체 경로를 지정 하거나 현재 디렉터리를 나타내는 점을 입력 합니다 `.\` .

예를 들어 현재 디렉터리에서 FindDocs.ps1 파일을 실행 하려면 다음을 입력 합니다.

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>실행 시 와일드 카드 사용

명령 실행에서 와일드 카드를 사용할 수 있습니다. 와일드 카드 문자를 사용 하는 것을 *와일드 카드 사용* 라고도 합니다.

PowerShell은 리터럴 일치를 위해 와일드 카드와 일치 하는 파일을 실행 합니다.

예를 들어 다음과 같은 파일을 포함 하는 디렉터리를 생각해 보겠습니다.

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

두 스크립트 파일의 내용이 동일 합니다. `$MyInvocation.MyCommand.Path` .
이 명령은 호출 되는 스크립트의 이름을 표시 합니다.

를 실행 하면 `[a1].ps1` `a.ps1` 파일이 리터럴 일치 이더라도 파일이 실행 됩니다 `[a1].ps1` .

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

이제 파일을 삭제 `a.ps1` 하 고 다시 실행 해 봅니다.

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

`[a1].ps1`리터럴 일치가 해당 와일드 카드 패턴과 일치 하는 유일한 파일 이기 때문에이 시간을 실행 하는 출력에서 볼 수 있습니다.

PowerShell에서 와일드 카드를 사용 하는 방법에 대 한 자세한 내용은 [about_Wildcards](about_Wildcards.md)를 참조 하세요.

> [!NOTE]
> 검색을 상대 경로로 제한 하려면 스크립트 이름 앞에 경로를 붙여야 합니다 `.\` . 이렇게 하면 해당 상대 경로에 있는 파일에 대 한 명령 검색을 제한 합니다. 이 접두사가 없으면 다른 PowerShell 구문이 충돌 하 고 파일을 찾을 수 있도록 보장 됩니다.

경로를 지정 하지 않으면 PowerShell은 현재 세션에 로드 된 모든 항목에 대해 명령을 실행할 때 다음과 같은 우선 순위 순서를 사용 합니다.

  1. Alias
  2. 함수
  3. Cmdlet
  4. 외부 실행 파일 (프로그램 및 비 PowerShell 스크립트)

따라서 "help"를 입력 하는 경우 PowerShell은 먼저 라는 이름의 별칭을 찾은 다음 라는 함수를 찾은 `help` 다음 `Help` 마지막으로 이라는 cmdlet을 찾습니다 `Help` . 찾은 첫 번째 항목을 실행 `help` 합니다.

예를 들어 세션에 cmdlet이 포함 되 고 두 함수 모두 명명 된 경우 `Get-Map` `Get-Map` PowerShell에서 함수를 실행 합니다.

> [!NOTE]
> 이는 로드 된 명령에만 적용 됩니다. `build` `build` 현재 세션으로 로드 되지 않은 모듈 내에 이름이 인 함수에 대 한 실행 파일과 별칭이 있으면 `Invoke-Build` PowerShell에서 실행 파일을 대신 실행 합니다 `build` . 이 경우 외부 실행 파일을 찾으면 모듈을 자동으로 로드 하지 않습니다. 지정 된 이름의 별칭, 함수 또는 cmdlet을 호출 하 여 모듈의 자동 로드를 트리거하는 외부 실행 파일이 없는 경우에만 해당 됩니다.

세션에 이름이 같은 동일한 유형의 항목이 포함 되어 있으면 PowerShell에서 최신 항목을 실행 합니다.

예를 들어 모듈에서 다른 cmdlet을 가져오는 경우 `Get-Date` 를 입력 하면 `Get-Date` PowerShell에서 네이티브 버전을 통해 가져온 버전을 실행 합니다.

## <a name="hidden-and-replaced-items"></a>숨겨진 항목과 대체 항목

이러한 규칙의 결과로 항목을 동일한 이름의 항목으로 바꾸거나 숨길 수 있습니다.

항목 이름을 모듈 또는 스냅인 이름으로 정규화 하는 등의 방법으로 원래 항목에 액세스할 수 있는 경우 항목은 "숨김" 또는 "숨김" 상태입니다.

예를 들어 세션에서 cmdlet과 이름이 동일한 함수를 가져오는 경우이 cmdlet은 스냅인 또는 모듈에서 가져온 것 이기 때문에 숨겨집니다 (대체 되지는 않음).

원본 항목에 더 이상 액세스할 수 없는 경우 항목은 "교체 됨" 또는 "덮어쓰기" 됩니다.

예를 들어 세션의 변수와 이름이 같은 변수를 가져오는 경우 원래 변수가 바뀌고 더 이상 액세스할 수 없습니다.
모듈 이름을 사용 하 여 변수를 한정할 수 없습니다.

또한 명령줄에 함수를 입력 한 다음 동일한 이름의 함수를 가져오면 원래 함수가 바뀌고 더 이상 액세스할 수 없습니다.

### <a name="finding-hidden-commands"></a>숨겨진 명령 찾기

[Get 명령](xref:Microsoft.PowerShell.Core.Get-Command) Cmdlet의 **all** 매개 변수는 숨겨지거나 바뀐 경우에도 지정 된 이름의 모든 명령을 가져옵니다. PowerShell 3.0부터 기본적으로 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.

다음 예의 세션에는 `Get-Date` 함수와 [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet이 포함 되어 있습니다.

다음 명령은를 `Get-Date` 입력할 때 실행 되는 명령을 가져옵니다 `Get-Date` .

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

다음 명령은 **all** 매개 변수를 사용 하 여 모든 `Get-Date` 명령을 가져옵니다.

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>숨겨진 명령 실행

동일한 이름을 가질 수 있는 다른 명령과 명령을 구분 하는 항목 속성을 지정 하 여 특정 명령을 실행할 수 있습니다. 이 메서드를 사용 하 여 모든 명령을 실행할 수 있지만 숨겨진 명령을 실행 하는 데 특히 유용 합니다.

#### <a name="qualified-names"></a>정규화된 이름

Cmdlet의 모듈 정규화 된 이름을 사용 하면 동일한 이름의 항목으로 숨겨진 명령을 실행할 수 있습니다. 예를 들어 `Get-Date` 이 cmdlet을 모듈 이름으로 정규화 하 여 실행할 수 있습니다 **.**

배포 하려는 스크립트를 작성할 때이 기본 방법을 사용 합니다. 스크립트가 실행 되는 세션에 있을 수 있는 명령을 예측할 수 없습니다.

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

`New-Map`모듈에 의해 추가 된 명령을 실행 하려면 모듈의 정규화 된 `MapFunctions` 이름을 사용 합니다.

```powershell
MapFunctions\New-Map
```

명령을 가져온 모듈을 찾으려면 명령의 **ModuleName** 속성을 사용 합니다.

```
(Get-Command <command-name>).ModuleName
```

예를 들어 cmdlet의 원본을 찾으려면 다음과 같이 `Get-Date` 입력 합니다.

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> 변수나 별칭은 한정할 수 없습니다.

#### <a name="call-operator"></a>Call 연산자

또한 연산자를 사용 `Call` `&` 하 여 숨겨진 명령을 [get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (별칭은 "Dir") 또는 import-module과 결합 하 여 실행할 수 있습니다 `Get-Command` . [](xref:Microsoft.PowerShell.Core.Get-Module)

Call 연산자는 자식 범위에서 문자열과 스크립트 블록을 실행 합니다. 자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.

예를 들어 라는 별칭을 사용 하 여 숨겨진 함수를 사용 하는 경우 `Map` `Map` 다음 명령을 사용 하 여 함수를 실행 합니다.

```powershell
&(Get-Command -Name Map -CommandType Function)
```

또는

```powershell
&(dir Function:\map)
```

숨겨진 명령을 변수에 저장 하 여 쉽게 실행할 수도 있습니다.

예를 들어 다음 명령은 함수를 변수에 저장 한 `Map` `$myMap` 다음 연산자를 사용 하 여 `Call` 실행 합니다.

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>바뀐 항목

"대체" 항목은 더 이상 액세스할 수 없는 항목입니다. 모듈 또는 스냅인에서 같은 이름의 항목을 가져와서 항목을 바꿀 수 있습니다.

예를 들어 `Get-Map` 세션에 함수를 입력 하 고 라는 함수를 가져오면 `Get-Map` 원래 함수를 대체 합니다. 현재 세션에서 검색할 수 없습니다.

호출 연산자나 정규화 된 이름을 사용 하 여 실행할 수 없으므로 변수와 별칭을 숨길 수 없습니다. 모듈 또는 스냅인에서 변수와 별칭을 가져오면 세션의 변수가 동일한 이름으로 바뀝니다.

### <a name="avoiding-name-conflicts"></a>이름 충돌 방지

명령 이름 충돌을 관리 하는 가장 좋은 방법은이를 방지 하는 것입니다. 명령의 이름을 사용 하는 경우 고유한 이름을 사용 합니다. 예를 들어 명령의 명사에 이니셜 또는 회사 이름 머리글자어를 추가 합니다.

또한 PowerShell 모듈 또는 다른 세션에서 세션으로 명령을 가져올 때 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 또는의 매개 변수를 사용 합니다.

[가져오기-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet을 통해 명령 이름의 명사에 접두사를 추가 합니다.

예를 들어 다음 명령은 `Get-Date` `Set-Date` 모듈을 가져올 때 PowerShell과 함께 제공 되는 및 cmdlet과의 충돌을 방지 합니다 `DateFunctions` .

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

자세한 내용은 다음을 참조 `Import-Module` `Import-PSSession` 하세요.

## <a name="see-also"></a>참고 항목

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias-Provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Function-Provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [모듈 가져오기](xref:Microsoft.PowerShell.Core.Import-Module)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
