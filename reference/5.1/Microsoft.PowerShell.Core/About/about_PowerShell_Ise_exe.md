---
description: PowerShell_Ise.exe 명령줄 도구를 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223338"
---
# <a name="about-powershell-iseexe"></a>PowerShell Ise.exe 정보

## <a name="short-description"></a>간단한 설명

PowerShell_Ise.exe 명령줄 도구를 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell_Ise.exe는 Windows PowerShell ISE (통합 스크립팅 환경) 세션을 시작 합니다. Cmd.exe 및 Windows PowerShell에서 실행할 수 있습니다.

PowerShell_ISE.exe를 실행 하려면 PowerShell_ISE.exe, PowerShell_ISE 또는 ISE를 입력 합니다.

## <a name="syntax"></a>SYNTAX

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a>PARAMETERS

### <a name="-file"></a>-File

Windows PowerShell ISE에서 지정 된 파일을 엽니다. 매개 변수 이름 ("-File")은 선택 사항입니다. 둘 이상의 파일을 나열 하려면 따옴표로 묶은 텍스트 문자열을 하나 입력 합니다. 문자열 내에서 파일 이름을 구분 하려면 쉼표를 사용 합니다.

다음은 그 예입니다. 

PowerShell_ISE-파일 "File1.ps1, File2.ps1, File3.xml".

Windows PowerShell에서는 파일 이름 사이에 공백을 사용할 수 있지만 Cmd.exe와 같은 다른 프로그램에서는 올바르게 해석 되지 않을 수도 있습니다.

이 매개 변수를 사용 하 여 Windows PowerShell 스크립트 파일 및 XML 파일을 비롯 한 모든 텍스트 파일을 열 수 있습니다.

### <a name="-mta"></a>-Mta

다중 스레드 아파트를 사용 하 여 Windows PowerShell ISE를 시작 합니다. 이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다. STA (단일 스레드 아파트)가 기본값입니다.

### <a name="-noprofile"></a>-NoProfile

Windows PowerShell 프로필을 실행 하지 않습니다. 기본적으로 Windows PowerShell 프로필은 모든 세션에서 실행 됩니다.

다른 프로필을 사용 하는 시스템에서 실행 되는 함수 및 스크립트와 같은 공유 콘텐츠를 작성 하는 경우이 매개 변수를 사용 하는 것이 좋습니다.
자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

### <a name="-help---"></a>-Help-?,/?

PowerShell_ISE.exe에 대 한 도움말을 표시 합니다.

## <a name="examples"></a>예제

이러한 명령은 Windows PowerShell ISE 시작 합니다. 이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

이러한 명령은 Windows PowerShell ISE에서 Get-Profile.ps1 스크립트를 엽니다.
이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

이 명령은 Windows PowerShell ISE에서 Get-Backups.ps1 및 Get-BackupInstance.ps1 스크립트를 엽니다. 둘 이상의 파일을 열려면 쉼표를 사용 하 여 파일 이름을 구분 하 고 전체 파일 이름 값을 따옴표로 묶습니다.

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

이 명령은 프로필 없이 Windows PowerShell ISE를 시작 합니다.

```
PS C:> ISE -NoProfile
```

이 명령은 PowerShell_ISE.exe에 대 한 도움말을 가져옵니다.

```
PS C:> ISE -help
```

## <a name="see-also"></a>참고 항목

[about_PowerShell.exe](about_PowerShell_exe.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)

[Windows PowerShell ISE (통합 스크립팅 환경)](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
