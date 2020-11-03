---
description: PowerShell에서 cmdlet 및 명령에 대 한 대체 이름을 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: 5595c1595a36ebbc6ae7c77afb45f95996815f8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221833"
---
# <a name="about-aliases"></a>별칭 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 cmdlet 및 명령에 대 한 대체 이름을 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

별칭은 cmdlet 또는 명령 요소 (예: 함수, 스크립트, 파일 또는 실행 파일)에 대 한 대체 이름 또는 애칭입니다. PowerShell 명령에서 명령 이름 대신 별칭을 사용할 수 있습니다.

별칭을 만들려면 New-Alias cmdlet을 사용 합니다. 예를 들어 다음 명령은 cmdlet에 대 한 "가스" 별칭을 만듭니다 `Get-AuthenticodeSignature` .

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

Cmdlet 이름에 대 한 별칭을 만든 후에는 cmdlet 이름 대신 별칭을 사용할 수 있습니다. 예를 들어 SqlScript.ps1 파일의 Authenticode 서명을 가져오려면 다음을 입력 합니다.

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

또는 다음과 같이 입력 합니다.

```powershell
gas SqlScript.ps1
```

Microsoft Office Word에 대 한 별칭으로 "word"를 만드는 경우에는 다음 대신 "word"를 입력할 수 있습니다.

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>기본 제공 별칭

PowerShell에는 Set-Location cmdlet에 대 한 "cd" 및 "chdir"을 포함 하는 기본 제공 별칭 집합과 Get-ChildItem cmdlet에 대 한 "ls" 및 "dir"이 포함 되어 있습니다.

기본 제공 별칭을 포함 하 여 컴퓨터의 모든 별칭을 가져오려면 다음을 입력 합니다.

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>별칭 CMDLET

PowerShell에는 별칭을 사용 하도록 설계 된 다음 cmdlet이 포함 되어 있습니다.

- `Get-Alias` -현재 세션의 모든 별칭을 가져옵니다.
- `New-Alias` -새 별칭을 만듭니다.
- `Set-Alias` -별칭을 만들거나 변경 합니다.
- `Export-Alias` -하나 이상의 별칭을 파일로 내보냅니다.
- `Import-Alias` -PowerShell로 별칭 파일을 가져옵니다.

Cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```powershell
Get-Help <cmdlet-Name> -Detailed
```

예를 들어 다음과 같이 입력합니다.

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>별칭 만들기

새 별칭을 만들려면 New-Alias cmdlet을 사용 합니다. 예를 들어 Get-help에 대 한 "gh" 별칭을 만들려면 다음을 입력 합니다.

```powershell
New-Alias -Name gh -Value Get-Help
```

전체 cmdlet 이름을 사용 하는 것 처럼 명령에 별칭을 사용할 수 있으며, 매개 변수와 함께 별칭을 사용할 수 있습니다.

예를 들어 Get-WmiObject cmdlet에 대 한 자세한 도움말을 보려면 다음을 입력 합니다.

```powershell
Get-Help Get-WmiObject -Detailed
```

또는 다음과 같이 입력 합니다.

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>별칭 저장

만든 별칭은 현재 세션에만 저장 됩니다. 다른 세션에서 별칭을 사용 하려면 PowerShell 프로필에 별칭을 추가 합니다. 또는 Export-Alias cmdlet을 사용 하 여 별칭을 파일에 저장 합니다.

더 자세한 내용을 보려면 다음을 입력하십시오.

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>별칭 가져오기

기본 제공 별칭, PowerShell 프로필의 별칭 및 현재 세션에서 만든 별칭을 포함 하 여 현재 세션의 모든 별칭을 가져오려면 다음을 입력 합니다.

```powershell
Get-Alias
```

특정 별칭을 가져오려면 Get-Alias cmdlet의 Name 매개 변수를 사용 합니다. 예를 들어 "p"로 시작 하는 별칭을 가져오려면 다음을 입력 합니다.

```powershell
Get-Alias -Name p*
```

특정 항목에 대 한 별칭을 가져오려면 정의 매개 변수를 사용 합니다. 예를 들어 Get-ChildItem cmdlet에 대 한 별칭을 가져오려면 다음을 입력 합니다.

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>가져오기 별칭 출력

Get-Alias는 System.management.automation.aliasinfo 개체 (System.management.automation.aliasinfo) 인 개체의 한 가지 유형만 반환 합니다. 하이픈을 포함 하지 않는 별칭의 이름 (예: "cd")은 다음 형식으로 표시 됩니다.

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

이렇게 하면 필요한 정보를 쉽고 빠르게 얻을 수 있습니다.

하이픈을 포함하는 별칭에는 화살표 기반 별칭 이름 형식이 사용되지 않습니다. 이러한 이름은 일반적인 약어 나 애칭 대신 cmdlet 및 함수에 대 한 기본 대체 이름이 될 수 있으며 작성자는 명확 하지 않을 수 있습니다.

## <a name="alternate-names-for-commands-with-parameters"></a>매개 변수가 있는 명령의 대체 이름

Cmdlet, 스크립트, 함수 또는 실행 파일에 별칭을 할당할 수 있습니다. 명령 및 매개 변수에 별칭을 할당할 수 없습니다. 예를 들어 cmdlet에 별칭을 할당할 수는 `Get-Eventlog` 있지만 명령에 별칭을 할당할 수는 없습니다 `Get-Eventlog -LogName System` .

명령을 포함 하는 함수를 만들 수 있습니다. 함수를 만들려면 "function" 이라는 단어를 입력 한 다음 함수 이름을 입력 합니다. 명령을 입력 하 고 중괄호 ()로 묶습니다 {} .

예를 들어 다음 명령은 syslog 함수를 만듭니다. 이 함수는 `Get-Eventlog -LogName System` 다음 명령을 나타냅니다.

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

이제 명령 대신 "syslog"를 입력할 수 있습니다. 새 함수에 대 한 별칭을 만들 수 있습니다.

함수에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>별칭 개체

PowerShell 별칭은 System.management.automation.aliasinfo 클래스의 인스턴스인 개체로 표현 됩니다. 이 형식의 개체에 대 한 자세한 내용은 MSDN (Microsoft Developer Network) 라이브러리의 [System.management.automation.aliasinfo 클래스][aliasinfo] 를 참조 하세요.

별칭 개체의 속성 및 메서드를 보려면 별칭을 가져옵니다.
그런 다음 Get-Member cmdlet으로 파이프 합니다. 다음은 그 예입니다. 

```powershell
Get-Alias | Get-Member
```

별칭 등의 특정 별칭 속성 값을 보려면 `dir` 별칭을 가져옵니다. 그런 다음 Format-List cmdlet으로 파이프 합니다. 예를 들어 다음 명령은 "dir" 별칭을 가져옵니다. 그런 다음이 명령은 별칭을 Format-List cmdlet으로 파이프 합니다. 그런 다음이 명령은 와일드 카드 문자 ()와 함께 Format-List의 Property 매개 변수를 사용 \* 하 여 별칭의 모든 속성을 표시 합니다 `dir` . 다음 명령은 다음 작업을 수행 합니다.

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>PowerShell 별칭 공급자

PowerShell에는 별칭 공급자가 포함 됩니다. 별칭 공급자를 사용 하면 파일 시스템 드라이브와 마찬가지로 PowerShell에서 별칭을 볼 수 있습니다.

별칭 공급자는 Alias: 드라이브를 노출 합니다. Alias: 드라이브로 이동 하려면 다음을 입력 합니다.

```powershell
Set-Location Alias:
```

드라이브의 내용을 보려면 다음을 입력 합니다.

```powershell
Get-ChildItem
```

다른 PowerShell 드라이브에서 드라이브의 내용을 보려면 드라이브 이름으로 경로를 시작 합니다. 콜론 (:)을 포함 합니다. 다음은 그 예입니다. 

```powershell
Get-ChildItem -Path Alias:
```

특정 별칭에 대 한 정보를 가져오려면 드라이브 이름과 별칭 이름을 입력 합니다. 또는 이름 패턴을 입력 합니다. 예를 들어 "p"로 시작 하는 모든 별칭을 가져오려면 다음을 입력 합니다.

```powershell
Get-ChildItem -Path Alias:p*
```

PowerShell 별칭 공급자에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```powershell
Get-Help Alias
```

## <a name="see-also"></a>참고 항목

- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
