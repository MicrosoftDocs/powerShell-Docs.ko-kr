---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 친숙한 명령 이름 사용
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353252"
---
# <a name="using-familiar-command-names"></a>친숙한 명령 이름 사용

PowerShell은 대체 이름으로 명령을 참조하도록 별칭을 지원합니다. 별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 PowerShell의 유사한 작업에 사용할 수 있도록 해줍니다.

별칭은 새 이름을 다른 명령과 연결합니다. 예를 들어 PowerShell에는 출력 창을 지우는 `Clear-Host`라는 내부 함수가 있습니다. 명령 프롬프트에서 `cls` 또는 `clear` 별칭을 입력할 수 있습니다. PowerShell은 이러한 별칭을 해석하고 `Clear-Host` 함수를 실행합니다.

이 기능은 사용자가 PowerShell을 익히는 데 도움이 됩니다. 첫째, 대부분의 **cmd.exe** 및 Unix 사용자는 이름으로 이미 알고 있는 대규모 명령 모음을 보유하게 됩니다. PowerShell의 해당 명령이 동일한 결과를 생성하지 않을 수 있습니다. 그러나 결과는 사용자가 PowerShell 명령 이름을 모르는 상태로 사용해도 될만큼 충분히 유사합니다. "단순 반복 암기"는 새 명령 셸을 학습할 때 겪게 되는 또 다른 어려움입니다. 수년 동안 **cmd.exe**를 사용해왔다면 화면을 지우기 위해 반사적으로 `cls` 명령을 입력할 수 있을 것입니다. `Clear-Host`에 대한 별칭이 없으면, 오류 메시지가 수신되고 출력을 지우기 위해 어떻게 해야 할지 알 수 없을 것입니다.

다음은 PowerShell에서 사용할 수 있는 몇 가지 일반적인 **cmd.exe** 및 Unix 명령 목록입니다.

|||||
|-|-|-|-|
|cat|dir|mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|type|
|del|lp|r|write|
|diff|ls|ren||

`Get-Alias` cmdlet은 별칭과 연결된 네이티브 PowerShell 명령의 실제 이름을 표시합니다.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>표준 별칭 해석

앞서 설명한 별칭은 다른 명령 셸에 대한 이름 호환성을 유지하기 위해 디자인되었습니다.
PowerShell에 기본 제공된 대부분의 별칭은 간결하게 디자인되었습니다. 이름이 짧을수록 입력하기가 더 쉽지만, 어떤 명령을 나타내는지 잘 모르면 이해하기 어렵습니다.

PowerShell 별칭은 명확성과 간결성 간에 균형을 유지하려고 합니다. PowerShell은 일반 noun가 verb에 대한 표준 별칭 집합을 사용합니다.

예제 약어:

| Noun 또는 Verb | 약어 |
|--------------|--------------|
| get          | g            |
| Set(영문)          | s            |
| 항목         | i            |
| 위치     | l            |
| 명령      | cm           |
| 별칭        | al           |

이러한 별칭은 축약 이름을 아는 경우 이해할 수 있습니다.

| Cmdlet 이름    | 별칭 |
|----------------|-------|
| `Get-Item `    | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

PowerShell 별칭에 익숙한 경우 **sal** 별칭이 `Set-Alias`를 나타낼 것으로 쉽게 추측할 수 있습니다.

## <a name="creating-new-aliases"></a>새 별칭 만들기

`Set-Alias` cmdlet을 사용하여 사용자 고유의 별칭을 만들 수 있습니다. 예를 들어 다음 문은 앞서 설명한 표준 cmdlet 별칭을 만듭니다.

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

내부적으로 PowerShell은 시작할 때 비슷한 명령을 사용하지만 이러한 별칭은 변경할 수 없습니다.
이러한 명령 중 하나를 실행하려고 하면 별칭을 수정할 수 없다는 오류 메시지가 나타납니다. 예:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
