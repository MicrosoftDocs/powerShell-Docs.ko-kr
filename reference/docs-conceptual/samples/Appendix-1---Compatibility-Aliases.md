---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 부록 1 호환성 별칭
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030335"
---
# <a name="appendix-1---compatibility-aliases"></a>부록 1 - 호환성 별칭

Windows PowerShell에는 UNIX 및 Cmd 사용자가 Windows PowerShell에서 친숙한 명령 이름을 사용할 수 있게 해주는 여러 전환 별칭이 있습니다. 아래 표에는 가장 일반적인 별칭이 나와 있으며, 별칭 뒤에 Windows PowerShell 명령과 표준 Windows PowerShell 별칭(있는 경우)이 표시됩니다.

Get-Alias cmdlet을 사용하면 Windows PowerShell 내에서 별칭이 가리키는 Windows PowerShell 명령을 찾을 수 있습니다. 예를 들어 **get-alias cls**를 입력합니다.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 명령|UNIX 명령|PS 명령|PS 별칭|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host**(함수)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
