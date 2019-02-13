---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 레지스트리 항목 작업
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681543"
---
# <a name="working-with-registry-entries"></a>레지스트리 항목 작업

레지스트리 항목은 키의 속성이어서 직접 검색할 수 없으므로 레지스트리 항목으로 작업할 경우 약간 다른 방법으로 접근해야 합니다.

### <a name="listing-registry-entries"></a>레지스트리 항목 나열

다양한 방법으로 레지스트리 항목을 검사할 수 있습니다. 가장 간단한 방법은 속성 이름을 키와 연결하는 것입니다. 예를 들어, 레지스트리 키 항목의 이름을 표시 하려면 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`를 사용 하 여 `Get-Item`입니다. 레지스트리 키에는 키에 있는 레지스트리 항목의 목록인 "Property" 제네릭 이름을 가진 속성이 있습니다.
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

좀 더 읽기 쉬운 형태로 레지스트리 항목을 보려면를 사용 하 여 `Get-ItemProperty`:

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

"`*.*`." 표기법을 사용하여 현재 위치를 나타낼 수 있습니다. 사용할 수 있습니다 `Set-Location` 로 변경 하는 **CurrentVersion** 레지스트리 컨테이너로 첫 번째:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

또는 사용 하 여 기본 제공 HKLM PSDrive를 사용할 수 있습니다 `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

그런 다음 현재 위치에 "`*.*`." 표기법을 사용하여 전체 경로를 지정하지 않고 속성을 나열할 수 있습니다.

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

이 위치에서 얻을 수 있도록 파일 시스템 내에서 동일 하 게 경로 확장 작동 합니다 **ItemProperty** 에 대 한 목록 `HKLM:\SOFTWARE\Microsoft\Windows\Help` 사용 하 여 `Get-ItemProperty -Path ..\Help`입니다.

### <a name="getting-a-single-registry-entry"></a>단일 레지스트리 항목 가져오기

레지스트리 키에서 특정 항목을 검색하려면 여러 가지 방법 중 하나를 사용할 수 있습니다. 이 예제에서는 값을 찾습니다 **DevicePath** 에서 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`합니다.

사용 하 여 `Get-ItemProperty`를 사용 합니다 **경로** 키의 이름을 지정 하려면 매개 변수 및 **이름** 의 이름을 지정 하려면 매개 변수를 **DevicePath** 항목입니다.

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
> 하지만 `Get-ItemProperty` 에 **필터**, **Include**, 및 **제외** 매개 변수 속성 이름별으로 필터링 할 사용할 수 없습니다. 이러한 매개 변수 항목 경로 및 없습니다 레지스트리 항목 레지스트리 키를 참조 하십시오. 항목 속성에는 레지스트리 항목입니다.

다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다. Reg.exe 사용 하 여 도움말에 대 한 입력 `reg.exe /?` 명령 프롬프트에서. DevicePath 항목을 찾으려면 다음 명령에 표시된 대로 reg.exe를 사용합니다.

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

**WshShell COM** 개체를 사용하여 일부 레지스트리 항목을 찾을 수도 있습니다. 이 방법은 대규모 이진 데이터나 "\\"와 같은 문자를 포함하는 레지스트리 항목 이름에는 사용할 수 없습니다. \\ 구분 기호를 사용하여 속성 이름을 항목 경로에 추가합니다.

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>단일 레지스트리 항목을 설정합니다.

레지스트리 키에서 특정 항목을 변경 하려는 경우에 여러 가지 방법 중 하나를 사용할 수 있습니다. 이 예제를 수정 합니다 **경로** 아래 항목 `HKEY_CURRENT_USER\Environment`합니다. 합니다 **경로** 항목 실행 파일을 찾을 위치를 지정 합니다.

1. 현재 값을 검색 합니다 **경로** 사용 하 여 항목 `Get-ItemProperty`합니다.
2. 새 값을 사용 하 여 구분 추가 `;`합니다.
3. 사용 하 여 `Set-ItemProperty` 와 지정 된 키, 항목 이름, 레지스트리 항목을 수정 하는 값입니다.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> 하지만 `Set-ItemProperty` 에 **필터**, **Include**, 및 **제외** 매개 변수 속성 이름별으로 필터링 할 사용할 수 없습니다. 이러한 매개 변수를 레지스트리 키(항목 경로)라고 하며 레지스트리 항목(항목 속성)이 아닙니다.

다른 옵션으로 Reg.exe 명령줄 도구를 사용합니다. reg.exe에 대한 도움말을 보려면 명령 프롬프트에서 **reg.exe /?** 를 입력합니다.
.

다음 예제에서는 변경 된 **경로** 위의 예제에 추가 된 경로 제거 하 여 항목입니다.
`Get-ItemProperty` 반환 된 문자열을 구문 분석할 필요가 없도록 하려면 현재 값을 검색 하는 여전히 `reg query`합니다. **SubString** 및 **LastIndexOf** 메서드에 추가 된 마지막 경로 검색 하는 데 사용 됩니다는 **경로** 항목입니다.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>새 레지스트리 항목 만들기

"PowerShellPath" 라는 새 항목을 추가 하는 **CurrentVersion** 키를 사용 하 여 `New-ItemProperty` 키, 항목 이름, 항목의 값을 경로 사용 하 여 합니다. 예를 들어 Windows PowerShell 변수 값 수행 됩니다 `$PSHome`, Windows powershell 설치 디렉터리의 경로를 저장 하는 합니다.

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

추가 하 여 기존 레지스트리 항목 값을 덮어쓸 수도 있습니다는 **Force** 매개 변수를 `New-ItemProperty` 명령입니다.

### <a name="renaming-registry-entries"></a>레지스트리 항목 이름 바꾸기

이름을 바꾸려면 합니다 **PowerShellPath** "PSHome"를 사용 하 여 항목 `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

이름을 바꾼 값을 표시하려면 **PassThru** 매개 변수를 명령에 추가합니다.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>레지스트리 항목 삭제

PSHome 및 PowerShellPath 레지스트리 항목을 삭제 하려면 사용 하 여 `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
