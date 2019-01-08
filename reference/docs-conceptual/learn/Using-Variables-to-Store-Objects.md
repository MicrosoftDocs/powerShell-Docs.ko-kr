---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 변수를 사용하여 개체 저장
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402476"
---
# <a name="using-variables-to-store-objects"></a>변수를 사용하여 개체 저장

PowerShell에서는 개체에 대한 작업을 수행합니다. PowerShell을 사용하면 변수라고 하는 명명된 개체를 만들 수 있습니다.
변수 이름은 영숫자 문자 및 밑줄만 포함할 수 있습니다. PowerShell에서 사용하는 경우는 변수는 항상 \$ 문자와 변수 이름을 차례로 입력하여 지정합니다.

## <a name="creating-a-variable"></a>변수 만들기

변수를 만들려면 다음과 같이 유효한 변수 이름을 입력해야 합니다.

```
PS> $loc
PS>
```

이 예제에서는 `$loc`에 값이 없기 때문에 아무 결과도 반환하지 않습니다. 동일한 단계에서 변수를 만드는 작업과 변수에 값을 할당하는 작업을 수행할 수 있습니다. PowerShell은 변수가 없는 경우에만 만듭니다.
그렇지 않으면 지정된 값을 기존 변수에 할당합니다. 다음 예제에서는 현재 위치를 변수 `$loc`에 저장합니다.

```powershell
$loc = Get-Location
```

이 명령을 입력할 때 PowerShell은 출력을 표시하지 않습니다. PowerShell은 ‘Get-location’의 출력을 `$loc`로 보냅니다. PowerShell에서 할당 또는 리디렉션되지 않는 데이터는 화면으로 전송됩니다. `$loc`를 입력하면 현재 위치가 표시됩니다.

```
PS> $loc

Path
----
C:\temp
```

`Get-Member`를 사용하여 변수의 내용에 대한 정보를 표시할 수 있습니다. `Get-Member`는 `Get-Location`의 출력과 마찬가지로 `$loc`가 **PathInfo** 개체임을 보여 줍니다.

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>변수 조작

PowerShell에는 변수를 조작할 수 있는 여러 명령이 포함되어 있습니다. 다음과 같이 입력하면 이러한 명령의 전체 목록을 쉽게 확인할 수 있습니다.

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell은 또한 여러 시스템 정의 변수를 만듭니다. `Remove-Variable` cmdlet을 사용하여 현재 세션에서 PowerShell에 의해 제어되지 않는 변수를 제거할 수 있습니다. 다음 명령을 입력하면 모든 변수를 지울 수 있습니다.

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

`Get-Variable` cmdlet은 이전 명령을 실행한 후에 PowerShell 시스템 변수를 표시합니다.

또한 PowerShell은 변수 드라이브도 만듭니다. 변수 드라이브를 사용하는 모든 PowerShell 변수를 표시하려면 다음 예제를 사용합니다.

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>cmd.exe 변수 사용

PowerShell에서는 모든 Windows 프로세스(**cmd.exe** 포함)에서 사용할 수 있는 동일한 환경 변수를 사용할 수 있습니다. 이러한 변수는 `env:`라는 드라이브를 통해 표시됩니다. 다음 명령을 입력하면 이러한 변수를 볼 수 있습니다.

```powershell
Get-ChildItem env:
```

표준 `*-Variable` cmdlet은 환경 변수를 사용하도록 디자인되지 않았습니다. 환경 변수는 `env:` 드라이브 접두사를 사용하여 액세스합니다. 예를 들어 **cmd.exe**의 **% SystemRoot %** 변수에는 운영 체제의 루트 디렉터리 이름이 포함됩니다. PowerShell에서 `$env:SystemRoot`를 사용하여 동일한 값에 액세스합니다.

```
PS> $env:SystemRoot
C:\WINDOWS
```

또한 PowerShell에서 환경 변수를 만들고 수정할 수도 있습니다. PowerShell의 환경 변수는 운영 체제에서 사용되는 환경 변수에 대해 동일한 규칙을 따릅니다. 다음 예제는 새 환경 변수를 만듭니다.

```powershell
$env:LIB_PATH='/usr/local/lib'
```

필수는 아니지만, 환경 변수 이름을 모두 대문자로 지정하는 것이 일반적입니다.
