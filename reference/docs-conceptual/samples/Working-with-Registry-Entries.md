---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 레지스트리 항목 작업
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086037"
---
# <a name="working-with-registry-entries"></a>레지스트리 항목 작업

레지스트리 항목은 키의 속성이어서 직접 검색할 수 없으므로 레지스트리 항목으로 작업할 경우 약간 다른 방법으로 접근해야 합니다.

## <a name="listing-registry-entries"></a>레지스트리 항목 나열

다양한 방법으로 레지스트리 항목을 검사할 수 있습니다. 가장 간단한 방법은 속성 이름을 키와 연결하는 것입니다. 예를 들어 레지스트리 키 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`의 항목 이름을 보려면 `Get-Item`을 사용합니다. 레지스트리 키에는 키에 있는 레지스트리 항목의 목록인 "Property" 제네릭 이름을 가진 속성이 있습니다.
다음 명령은 Property 속성을 선택하고 목록에 표시되도록 항목을 확장합니다.

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

레지스트리 항목을 읽기 쉽게 보려면 `Get-ItemProperty`를 사용합니다.

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

키의 Windows PowerShell 관련 속성은 모두 "PS" 접두사가 붙어 있습니다(예: **PSPath**, **PSParentPath**, **PSChildName** 및 **PSProvider**).

`*.*` 표기법을 사용하여 현재 위치를 나타낼 수 있습니다. 먼저 `Set-Location`을 사용하여 **CurrentVersion** 레지스트리 컨테이너로 변경할 수 있습니다.

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

또는 기본 제공 HKLM PSDrive를 `Set-Location`과 함께 사용할 수 있습니다.

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

그런 다음, 현재 위치에 `*.*` 표기법을 사용하여 전체 경로를 지정하지 않고 속성을 나열할 수 있습니다.

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

경로 확장은 파일 시스템에서와 동일하게 작동하므로 이 위치에서 `Get-ItemProperty -Path ..\Help`를 사용하여 `HKLM:\SOFTWARE\Microsoft\Windows\Help`에 대한 **ItemProperty** 목록을 가져올 수 있습니다.

## <a name="getting-a-single-registry-entry"></a>단일 레지스트리 항목 가져오기

레지스트리 키에서 특정 항목을 검색하려면 여러 가지 방법 중 하나를 사용할 수 있습니다. 이 예제에서는 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`에서 **DevicePath**의 값을 찾습니다.

`Get-ItemProperty`를 사용하면서, **Path** 매개 변수를 사용하여 키의 이름을 지정하고, **Name** 매개 변수를 사용하여 **DevicePath** 항목의 이름을 지정합니다.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

이 명령은 표준 Windows PowerShell 속성과 **DevicePath** 속성을 반환합니다.

> [!NOTE]
> `Get-ItemProperty`에는 **Filter**, **Include** 및 **Exclude** 매개 변수가 있지만 속성 이름을 기준으로 필터링하는 데 사용할 수 없습니다. 이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목이 아닙니다. 레지스트리 항목은 항목 속성입니다.

다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다. reg.exe에 대한 도움말을 보려면 명령 프롬프트에 `reg.exe /?`를 입력합니다. DevicePath 항목을 찾으려면 다음 명령에 표시된 대로 reg.exe를 사용합니다.

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

**WshShell** COM 개체를 사용하여 일부 레지스트리 항목을 찾을 수도 있습니다. 이 방법은 대규모 이진 데이터나 “\\”와 같은 문자를 포함하는 레지스트리 항목 이름에는 사용할 수 없습니다. \\ 구분 기호를 사용하여 속성 이름을 항목 경로에 추가합니다.

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>단일 레지스트리 항목 설정

레지스트리 키에서 특정 항목을 변경하려면 여러 가지 방법 중 하나를 사용할 수 있습니다. 이 예제에서는 `HKEY_CURRENT_USER\Environment` 아래의 **Path** 항목을 수정합니다. **Path** 항목은 실행 파일을 찾는 위치를 지정합니다.

1. `Get-ItemProperty`를 사용하여 **Path** 항목의 현재 값을 검색합니다.
2. `;`으로 구분하여 새 값을 추가합니다.
3. 지정된 키, 항목 이름 및 값과 함께 `Set-ItemProperty`를 사용하여 레지스트리 항목을 수정합니다.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> `Set-ItemProperty`에는 **Filter**, **Include** 및 **Exclude** 매개 변수가 있지만 속성 이름을 기준으로 필터링하는 데 사용할 수 없습니다. 이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목(항목 속성)이 아닙니다.

다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다. reg.exe에 대한 도움말을 보려면 명령 프롬프트에서 **reg.exe /?** 를 입력합니다.
.

다음 예제에서는 위 예제에 추가된 경로를 제거하여 **Path** 항목을 변경합니다.
`Get-ItemProperty`는 `reg query`에서 반환된 문자열을 구문 분석할 필요가 없도록 현재 값을 검색하는 데 사용됩니다. **SubString** 및 **LastIndexOf** 메서드는 **Path** 항목에 추가된 마지막 경로를 검색하는 데 사용됩니다.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>새 레지스트리 항목 만들기

“PowerShellPath”라는 새 항목을 **CurrentVersion** 키에 추가하려면 키 경로, 항목 이름, 항목 값과 함께 `New-ItemProperty`를 사용합니다. 이 예제에서는 Windows PowerShell의 설치 디렉터리 경로를 저장하는 Windows PowerShell 변수 값 `$PSHome`을 사용합니다.

다음 명령을 사용하여 새 항목을 키에 추가할 수 있습니다. 이 명령은 새 항목에 대한 정보도 반환합니다.

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType**은 다음 표에서 **Microsoft.Win32.RegistryValueKind** 열거형 멤버의 이름이어야 합니다.

|PropertyType 값|의미|
|----------------------|-----------|
|이진|이진 데이터|
|Dword|유효한 UInt32 숫자|
|ExpandString|동적으로 확장되는 환경 변수를 포함할 수 있는 문자열|
|MultiString|다중 행 문자열|
|문자열|임의의 문자열 값|
|Qword|8바이트 이진 데이터|

> [!NOTE]
> **Path** 매개 변수에 대한 값의 배열을 지정하여 여러 위치에 레지스트리 항목을 추가할 수 있습니다.

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

**Force** 매개 변수를 `New-ItemProperty` 명령에 추가하여 기존 레지스트리 항목 값을 덮어쓸 수도 있습니다.

## <a name="renaming-registry-entries"></a>레지스트리 항목 이름 바꾸기

**PowerShellPath** 항목의 이름을 “PSHome”으로 바꾸려면 `Rename-ItemProperty`를 사용합니다.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

이름을 바꾼 값을 표시하려면 **PassThru** 매개 변수를 명령에 추가합니다.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>레지스트리 항목 삭제

PSHome 및 PowerShellPath 레지스트리 항목을 모두 삭제하려면 `Remove-ItemProperty`를 사용합니다.

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
