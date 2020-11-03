---
description: PowerShell에서 작업 위치에 있는 항목에 액세스 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 070b28dee62771fc7014a9a8aa6c1732c3f0b2cd
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224673"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>간단한 설명
PowerShell에서 작업 위치에 있는 항목에 액세스 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

현재 작업 위치는 명령이 가리키는 기본 위치입니다.
즉, 명령의 영향을 받는 항목 또는 위치에 대 한 명시적 경로를 제공 하지 않는 경우 PowerShell에서 사용 하는 위치입니다. 대부분의 경우 현재 작업 위치는 PowerShell FileSystem 공급자를 통해 액세스 하는 드라이브 이며 경우에 따라 해당 드라이브의 디렉터리입니다.
예를 들어 현재 작업 위치를 다음 위치로 설정할 수 있습니다.

```powershell
C:\Program Files\Windows PowerShell
```

따라서 다른 경로를 명시적으로 제공 하지 않는 한 모든 명령이이 위치에서 처리 됩니다.

PowerShell은 드라이브가 현재 드라이브가 아닌 경우에도 각 드라이브에 대 한 현재 작업 위치를 유지 관리 합니다. 이렇게 하면 다른 위치의 드라이브만 참조 하 여 현재 작업 위치에서 항목에 액세스할 수 있습니다.
예를 들어 현재 작업 위치가 C: Windows 라고 가정 \\ 합니다. 이제 다음 명령을 사용 하 여 현재 작업 위치를 HKLM: 드라이브로 변경 한다고 가정 합니다.

```powershell
Set-Location HKLM:
```

현재 위치는 이제 레지스트리 드라이브 이지만 \\ 다음 예제와 같이 c: 드라이브를 사용 하 여 c: Windows 디렉터리의 항목에 계속 액세스할 수 있습니다.

```powershell
Get-ChildItem C:
```

PowerShell은 해당 드라이브의 현재 작업 위치가 Windows 디렉터리인 것을 기억 하므로 해당 디렉터리에서 항목을 검색 합니다. 다음 명령을 실행 하면 결과가 동일 하 게 됩니다.

```powershell
Get-ChildItem C:\Windows
```

PowerShell에서 Get-Location 명령을 사용 하 여 현재 작업 위치를 확인 하 고 Set-Location 명령을 사용 하 여 현재 작업 위치를 설정할 수 있습니다. 예를 들어 다음 명령은 현재 작업 위치를 C: 드라이브의 Windows 디렉터리로 설정 합니다.

```powershell
Set-Location c:\windows
```

현재 작업 위치를 설정한 후에는 다음 예제에 표시 된 것 처럼 명령에 드라이브 이름 (콜론)을 포함 하 여 다른 드라이브의 항목에 계속 액세스할 수 있습니다.

```powershell
Get-ChildItem HKLM:\software
```

예제 명령은 레지스트리에서 HKEY 로컬 컴퓨터 hive의 소프트웨어 컨테이너에 있는 항목 목록을 검색 합니다.

또한 PowerShell을 사용 하면 특수 문자를 사용 하 여 현재 작업 위치와 부모 위치를 나타낼 수 있습니다. 현재 작업 위치를 나타내려면 단일 마침표를 사용 합니다. 현재 작업 위치의 부모를 나타내려면 두 개의 마침표를 사용 합니다. 예를 들어 다음은 현재 작업 위치에 있는 시스템 하위 디렉터리를 지정 합니다.

```powershell
Get-ChildItem .\system
```

현재 작업 위치가 C: windows 인 경우 \\ 이 명령은 c: windows 시스템의 모든 항목 목록을 반환 합니다 \\ \\ . 그러나 두 개의 기간을 사용 하는 경우 다음 예제와 같이 현재 작업 디렉터리의 부모 디렉터리가 사용 됩니다.

```powershell
Get-ChildItem ..\"program files"
```

이 경우 PowerShell은 두 기간을 C: 드라이브로 처리 하므로,이 명령은 C: Program Files 디렉터리의 모든 항목을 검색 합니다 \\ .

슬래시로 시작 하는 경로는 현재 드라이브의 루트에서 경로를 식별 합니다. 예를 들어 현재 작업 위치가 C: \\ Program Files \\ PowerShell 이면 드라이브의 루트는 c입니다. 따라서 다음 명령은 C: Windows 디렉터리의 모든 항목을 나열 합니다 \\ .

```powershell
Get-ChildItem \windows
```

컨테이너 또는 항목의 이름을 제공할 때 드라이브 이름, 슬래시 또는 마침표로 시작 하는 경로를 지정 하지 않으면 컨테이너 또는 항목이 현재 작업 위치에 있는 것으로 간주 됩니다. 예를 들어 현재 작업 위치가 C: windows 인 경우 \\ 다음 명령은 c: \\ windows 시스템 디렉터리에 있는 모든 항목을 반환 합니다 \\ .

```powershell
Get-ChildItem system
```

디렉터리 이름이 아닌 파일 이름을 지정 하는 경우 PowerShell은 해당 파일에 대 한 세부 정보를 반환 합니다 (해당 파일이 현재 작업 위치에 있는 것으로 가정).

## <a name="see-also"></a>참고 항목

[Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)
