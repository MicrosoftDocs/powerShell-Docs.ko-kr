---
description: PSModulePath 환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 58aabc4f4821ce41782d3b9837eb67f19f6a07a9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222042"
---
# <a name="about-psmodulepath"></a>PSModulePath 정보

`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.

기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.

- 시스템 전체 위치: 이러한 폴더에는 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다. 이러한 모듈은 폴더에 저장 됩니다 `$PSHOME\Modules` . Windows 관리 모듈이 설치 되는 위치 이기도 합니다.

- 사용자가 설치한 모듈: 사용자가 설치 하는 모듈입니다.
  `Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다. 자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.

  - Windows에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME\Documents\PowerShell\Modules` 폴더입니다. **AllUsers** 범위의 위치는 `$env:ProgramFiles\PowerShell\Modules` 입니다.
  - 비 Windows 시스템에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME/.local/share/powershell/Modules` 폴더입니다. **AllUsers** 범위의 위치는 `/usr/local/share/powershell/Modules` 입니다.

또한 Program Files 디렉터리와 같은 다른 디렉터리에 모듈을 설치 하는 설치 프로그램은 해당 위치를의 값에 추가할 수 있습니다 `$env:PSModulePath` .

> [!NOTE]
> Windows에서 사용자 지정 위치는 `PowerShell\Modules` 사용자 프로필의 **Documents** 폴더에 있는 폴더입니다. 해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다. Microsoft OneDrive는 **문서** 폴더의 위치를 변경할 수도 있습니다. 다음 명령을 사용 하 여 **문서** 폴더의 위치를 확인할 수 있습니다 `[Environment]::GetFolderPath('MyDocuments')` .

## <a name="modifying-psmodulepath"></a>PSModulePath 수정

현재 세션에 대 한 기본 모듈 디렉터리를 변경 하려면 다음 명령 형식을 사용 하 여 환경 변수 값을 변경 합니다 `PSModulePath` .

예를 들어 `C:\Program Files\Fabrikam\Modules` PSModulePath 환경 변수의 값에 디렉터리를 추가 하려면 다음을 입력 합니다.

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

명령의 세미콜론 ()은 `;` 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다. Windows가 아닌 플랫폼에서 콜론 ()은 `:` 환경 변수의 경로 위치를 구분 합니다.

모든 세션에서의 값을 변경 하려면 `PSModulePath` PowerShell 프로필에 이전 명령을 추가 하거나 **Environment** 클래스의 **SetEnvironmentVariable** 메서드를 사용 합니다.

다음 명령은 **GetEnvironmentVariable** 메서드를 사용 하 여의 컴퓨터 설정을 가져오고 SetEnvironmentVariable 메서드를 사용 하 여 `PSModulePath` **SetEnvironmentVariable** `C:\Program Files\Fabrikam\Modules` 값에 경로를 추가 합니다.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

사용자 설정에 대 한 경로를 추가 하려면 대상 값을 **사용자** 로 변경 합니다.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

**System.object** 클래스의 메서드에 대 한 자세한 내용은 [환경 메서드](/dotnet/api/system.environment)를 참조 하세요.

## <a name="powershell-psmodulepath-construction"></a>PowerShell PSModulePath 생성

값은 `$env:PSModulePath` PowerShell이 시작 될 때마다 생성 됩니다.
값은 PowerShell의 버전 및 실행 방법에 따라 달라 집니다.

### <a name="windows-powershell-startup"></a>Windows PowerShell 시작

Windows PowerShell은 다음 논리를 사용 하 여 `PSModulePath` 시작 시를 생성 합니다.

- `PSModulePath`존재 하지 않는 경우 **CurrentUser** , **AllUsers** 및 `$PSHOME` modules 경로를 결합 합니다.
- `PSModulePath`존재 하는 경우:
  - 가 `PSModulePath` 모듈 경로를 포함 하는 경우 `$PSHOME` :
    - 모듈 경로 앞에 **AllUsers** 모듈 경로가 삽입 됨 `$PSHOME`
  - 사람이
    - `PSModulePath`사용자가 의도적으로 위치를 제거 했기 때문에 정의 된 대로만 사용 `$PSHOME`

**CurrentUser** 모듈 경로에는 사용자 범위가 없는 경우에만 접두사로 추가 됩니다 `$env:PSModulePath` . 그렇지 않으면 사용자 범위가 `$env:PSModulePath` 정의 된 대로 사용 됩니다.

### <a name="powershell-core-6-startup"></a>PowerShell Core 6 시작

Powershell Core 6은 `$env:PSModulePath` powershell에서 시작 된 것을 감지 하는 경우 콘텐츠를 사용 하지 않습니다. 다음을 사용 하 여 덮어씁니다.

- **CurrentUser** 모듈 경로 + **AllUsers** 모듈 경로 + `$PSHOME` 모듈 경로 + Windows PowerShell `$PSHOME` 모듈 경로입니다.

### <a name="powershell-7-startup"></a>PowerShell 7 시작

Windows에서 대부분의 환경 변수에 대해 사용자 범위 변수가 존재 하는 경우 새 프로세스는 동일한 이름의 컴퓨터 범위 변수가 있는 경우에도 해당 값을 사용 합니다.

PowerShell 7에서 `PSModulePath` 는 `Path` 환경 변수가 Windows에서 처리 되는 방식과 유사 하 게 처리 됩니다. Windows에서 `Path` 는 다른 환경 변수와 다르게 처리 됩니다. 프로세스가 시작 되 면 Windows는 사용자 범위를 `Path` 컴퓨터 범위와 결합 합니다 `Path` .

- 사용자 범위를 검색 합니다. `PSModulePath`
- 상속 된 환경 변수를 처리 하는 비교 `PSModulePath`
  - 동일한 경우:
    - **AllUsers** `PSModulePath` 환경 변수의 의미 체계에 따라 끝에 AllUsers를 추가 합니다. `Path`
    - Windows `System32` 경로는 정의 된 컴퓨터에서 제공 `PSModulePath` 되므로 명시적으로 추가할 필요가 없습니다.
  - 다른 경우 사용자가 명시적으로 수정 하 고 **AllUsers** 를 추가 하지 않는 것으로 처리 합니다. `PSModulePath`
- PS7 사용자, 시스템 및 `$PSHOME` 경로를 해당 순서로 접두사로 사용 합니다.
  - 이 `powershell.config.json` 사용자 범위를 포함 하는 경우 `PSModulePath` 사용자에 대 한 기본값 대신 해당 사용자를 사용 합니다.
  - `powershell.config.json`에 시스템 범위가 포함 된 경우 `PSModulePath` 시스템에 대 한 기본값 대신이를 사용 합니다.

Unix 시스템은 사용자 및 시스템 환경 변수를 분리 하지 않습니다.
`PSModulePath` 는 상속 되며 PS7 경로는 접두사가 아직 정의 되지 않은 경우 접두사로 지정 됩니다.

### <a name="starting-windows-powershell-from-powershell-7"></a>PowerShell 7에서 Windows PowerShell 시작

이 설명에서 _Windows PowerShell_ 은 및를 모두 의미 `powershell.exe` `powershell_ise.exe` 합니다.

의 값은 `$env:PSModulePath` 다음 수정 사항을 사용 하 여에 복사 됩니다 `WinPSModulePath` .

- PS7 사용자 모듈 경로를 제거 합니다.
- 시스템 모듈 경로 PS7 제거
- PS7 모듈 경로를 제거 합니다. `$PSHOME`

PS7 모듈이 Windows PowerShell에서 로드 되지 않도록 PS7 경로가 제거 됩니다. `WinPSModulePath`Windows PowerShell을 시작할 때이 값이 사용 됩니다.

### <a name="starting-powershell-7-from-windows-powershell"></a>Windows PowerShell에서 PowerShell 7 시작

PowerShell 7 시작은 Windows PowerShell에서 추가한 경로를 상속 하는 것과 함께 그대로 계속 유지 됩니다. PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.

### <a name="starting-powershell-6-from-powershell-7"></a>PowerShell 7에서 PowerShell 6 시작

PowerShell Core 6은 `$env:PSModulePath` 를 덮어씁니다. 변경 내용이 없습니다.

### <a name="starting-powershell-7-from-powershell-6"></a>PowerShell 6에서 PowerShell 7 시작

Powershell 7 시작은 PowerShell Core 6이 추가 된 상속 경로를 추가 하 여 그대로 계속 유지 됩니다. PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.

## <a name="see-also"></a>참고 항목

- [about_Modules](about_Modules.md)
- [환경 메서드](/dotnet/api/system.environment)

