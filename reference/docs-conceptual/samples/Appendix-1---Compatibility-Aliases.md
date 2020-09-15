---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 부록 1 호환성 별칭
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758502"
---
# <a name="appendix-1---compatibility-aliases"></a>부록 1 - 호환성 별칭

PowerShell에는 **UNIX** 및 **cmd.exe** 사용자가 친숙한 명령을 사용할 수 있게 하는 몇 가지 별칭이 있습니다.
명령, 관련 PowerShell cmdlet 및 PowerShell 별칭은 다음 표에 나와 있습니다.

|            cmd.exe 명령            | UNIX 명령 | PowerShell cmdlet | PowerShell 별칭 |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| **cd**, **chdir**                     | **cd**       | `Set-Location`    | `sl`             |
| **cls**                               | **clear**    | `Clear-Host`      | `cls`            |
| **copy**                              | **cp**       | `Copy-Item`       | `cpi`            |
| **del**, **erase**, **rd**, **rmdir** | **rm**       | `Remove-Item`     | `ri`             |
| **dir**                               | **ls**       | `Get-ChildItem`   | `gci`            |
| **echo**                              | **echo**     | `Write-Output`    | `write`          |
| **md**                                | **mkdir**    | `New-Item`        | `ni`             |
| **move**                              | **mv**       | `Move-Item`       | `mi`             |
| **popd**                              | **popd**     | `Pop-Location`    | `popd`           |
| **pushd**                             | **pushd**    | `Push-Location`   | `pushd`          |
| **ren**                               | **mv**       | `Rename-Item`     | `rni`            |
| **type**                              | **cat**      | `Get-Content`     | `gc`             |

PowerShell 별칭을 찾으려면 [Get Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet을 사용합니다. Cmdlet의 별칭을 표시하려면 **Definition** 매개 변수를 사용하고 cmdlet 이름을 지정합니다.
별칭의 cmdlet 이름을 찾으려면 **Name** 매개 변수를 사용하고 별칭을 지정합니다.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
