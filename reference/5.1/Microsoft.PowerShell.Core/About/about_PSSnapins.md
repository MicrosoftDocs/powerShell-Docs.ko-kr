---
description: Windows PowerShell 스냅인에 대해 설명 하 고이 스냅인을 사용 하 고 관리 하는 방법을 보여 줍니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222665"
---
# <a name="about-pssnapins"></a>PSSnapins 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell 스냅인에 대해 설명 하 고이 스냅인을 사용 하 고 관리 하는 방법을 보여 줍니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 스냅인은 Windows PowerShell 공급자 및 또는 cmdlet을 포함 하는 Microsoft .NET 프레임 워크 어셈블리입니다 \/ . Windows PowerShell에는 일련의 기본 스냅인이 포함 되어 있지만 사용자가 만들거나 다른 사용자가 가져온 공급자와 cmdlet을 포함 하는 스냅인을 추가 하 여 Windows PowerShell의 기능과 가치를 확장할 수 있습니다.

스냅인을 추가 하면 해당 스냅인에 포함 된 cmdlet 및 공급자가 현재 세션에서 즉시 사용할 수 있지만 변경 내용은 현재 세션에만 영향을 줍니다.

모든 이후 세션에 스냅인을 추가 하려면 Windows PowerShell 프로필에 저장 합니다. Export-Console cmdlet을 사용 하 여 스냅인 이름을 콘솔 파일에 저장 한 다음 이후 세션에서 사용할 수도 있습니다. 각각 서로 다른 스냅인 집합을 사용 하 여 여러 콘솔 파일을 저장할 수도 있습니다.

참고: windows powershell 스냅인 (PSSnapins)은 Windows powershell 3.0 및 Windows PowerShell 2.0에서 사용할 수 있습니다. 이후 버전에서 변경 되거나 사용할 수 없게 될 수 있습니다. Windows PowerShell cmdlet 및 공급자를 패키징하려면 모듈을 사용합니다. 모듈을 만들고 스냅인을 모듈로 변환 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.

### <a name="finding-snap-ins"></a>스냅인 찾기

컴퓨터의 Windows PowerShell 스냅인 목록을 가져오려면 다음을 입력 합니다.

```powershell
Get-PSSnapin
```

각 Windows PowerShell 공급자에 대 한 스냅인을 가져오려면 다음을 입력 합니다.

```powershell
Get-PSProvider | Format-List name, pssnapin
```

Windows PowerShell 스냅인에서 cmdlet 목록을 가져오려면 다음을 입력 합니다.

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a>스냅인 설치

기본 제공 스냅인이 시스템에 등록 되 고 Windows PowerShell을 시작할 때 기본 세션에 추가 됩니다. 그러나 다른 사용자가 만들거나 가져온 스냅인을 등록 한 다음 세션에 스냅인을 추가 해야 합니다.

### <a name="registering-a-snap-in"></a>스냅인 등록

Windows PowerShell 스냅인은 .dll 파일로 컴파일되는 .NET Framework 언어로 작성 된 프로그램입니다. 스냅인에서 공급자 및 cmdlet을 사용 하려면 먼저 스냅인을 등록 해야 합니다 (레지스트리에 추가).

대부분의 스냅인에는 .dll 파일을 등록 하는 설치 프로그램 (.exe 또는 .msi 파일)이 포함 되어 있습니다. 그러나 스냅인을 .dll 파일로 받는 경우 시스템에 등록할 수 있습니다. 자세한 내용은 MSDN library에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://go.microsoft.com/fwlink/?LinkID=143619) 을 참조 하십시오.

시스템에서 등록 된 모든 스냅인을 가져오거나 스냅인이 등록 되었는지 확인 하려면 다음을 입력 합니다.

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a>현재 세션에 스냅인 추가

현재 세션에 등록 된 스냅인을 추가 하려면 Add-PsSnapin cmdlet을 사용 합니다. 예를 들어 세션에 Microsoft SQL Server 스냅인을 추가 하려면 다음을 입력 합니다.

```powershell
Add-PSSnapin sql
```

명령이 완료 되 면 스냅인의 공급자 및 cmdlet을 세션에서 사용할 수 있습니다. 그러나 저장 하지 않는 한 현재 세션 에서만 사용할 수 있습니다.

### <a name="saving-the-snap-ins"></a>스냅인 저장

이후 Windows PowerShell 세션에서 스냅인을 사용 하려면 Windows PowerShell 프로필에 Add-PsSnapin 명령을 추가 합니다. 또는 스냅인 이름을 콘솔 파일로 내보냅니다.

프로필에 Add-PSSnapin 명령을 추가 하면 이후의 모든 Windows PowerShell 세션에서 사용할 수 있습니다. 세션에서 스냅인의 이름을 내보내는 경우 스냅인이 필요한 경우에만 내보내기 파일을 사용할 수 있습니다.

Windows PowerShell 프로필에 Add-PsSnapin 명령을 추가 하려면 프로필을 열고 명령을 붙여넣거나 입력 한 다음 프로필을 저장 합니다. 자세한 내용은 about_Profiles를 참조하세요.

콘솔 파일 (. .psc1)의 세션에서 스냅인을 저장 하려면 Export-Console cmdlet을 사용 합니다. 예를 들어 현재 세션 구성의 스냅인을 현재 디렉터리의 NewConsole 파일에 저장 하려면 다음을 입력 합니다.

```powershell
Export-Console NewConsole
```

자세한 내용은 내보내기-콘솔을 참조 하세요.

### <a name="opening-windows-powershell-with-a-console-file"></a>콘솔 파일을 사용 하 여 WINDOWS POWERSHELL 열기

스냅인이 포함 된 콘솔 파일을 사용 하려면 Cmd.exe의 명령 프롬프트나 다른 Windows PowerShell 세션에서 Windows PowerShell (PowerShell.exe)을 시작 합니다. PsConsoleFile 매개 변수를 사용 하 여 스냅인이 포함 된 콘솔 파일을 지정 합니다. 예를 들어 다음 명령은 NewConsole. .psc1 콘솔 파일을 사용 하 여 Windows PowerShell을 시작 합니다.

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

이제 세션에서 스냅인의 공급자 및 cmdlet을 사용할 수 있습니다.

### <a name="removing-a-snap-in"></a>스냅인 제거

현재 세션에서 Windows PowerShell 스냅인을 제거 하려면 Remove-PsSnapin cmdlet을 사용 합니다. 예를 들어 현재 세션에서 SQL Server 스냅인을 제거 하려면 다음을 입력 합니다.

```powershell
Remove-PSSnapin sql
```

이 cmdlet은 세션에서 스냅인을 제거 합니다. 스냅인은 여전히 로드 되지만 지원 되는 공급자 및 cmdlet은 더 이상 사용할 수 없습니다.

### <a name="built-in-commands"></a>기본 제공 명령

Windows powershell 2.0 및 windows powershell 3.0 이상의 이전 스타일 호스트 프로그램에서 windows PowerShell과 함께 설치 되는 기본 제공 명령은 모든 Windows PowerShell 세션에 자동으로 추가 되는 스냅인에 패키지 됩니다.

Windows PowerShell 3.0 부터는 InitialSessionState. Initialsessionstate.createdefault2 메서드를 사용 하 여 세션을 시작 하는 최신 스타일의 호스트 프로그램--기본 제공 명령이 모듈에 패키지 됩니다. 예외는 항상 스냅인으로 나타나는 Microsoft. PowerShell. Core입니다. 코어 스냅인은 기본적으로 모든 세션에 포함 됩니다. 기본 제공 모듈은 처음 사용할 때 자동으로 로드 됩니다.

참고: New-PSSession cmdlet을 사용 하 여 시작 된 세션을 포함 하 여 원격 세션은 기본 제공 명령이 스냅인에 패키지 된 이전 스타일의 세션입니다.

다음 스냅인 (또는 모듈)은 Windows PowerShell과 함께 설치 됩니다.

- Microsoft. PowerShell-Windows PowerShell의 기본 기능을 관리 하는 데 사용 되는 공급자 및 cmdlet을 포함 합니다. 여기에는 파일 시스템, 레지스트리, 별칭, 환경, 함수 및 변수 공급자와 Get-help, Get-help 및 Get 기록과 같은 기본 cmdlet이 포함 됩니다.

- Windows PowerShell 호스트에서 사용 하는 cmdlet (예: Start-Transcript 및 중지 기록)이 포함 되어 있습니다.

- Microsoft. 관리-Windows 기반 기능을 관리 하는 데 사용 되는 Get-Service 및 Get-ChildItem와 같은 cmdlet을 포함 합니다.

- Get-authenticodesignature-Acl, Get-및 Convertto-html와 같은 Windows PowerShell 보안을 관리 하는 데 사용 되는 인증서 공급자 및 cmdlet을 포함 합니다.

- Microsoft. PowerShell에는 개체 및 데이터를 조작 하는 데 사용 되는 cmdlet (예: Get Member, Write Host 및 Format-List)이 포함 되어 있습니다.

- Enable-wsmancredssp-Connect-WSMan 및와 같은 Windows 원격 관리 서비스를 관리 하는 WSMan 공급자 및 cmdlet을 포함 합니다.

## <a name="logging-snap-in-events"></a>스냅인 이벤트 로깅

Windows PowerShell 3.0부터 모듈 및 스냅인의 LogPipelineExecutionDetails 속성을 TRUE로 설정 하 여 Windows PowerShell 모듈 및 스냅인에서 cmdlet에 대 한 실행 이벤트를 기록할 수 있습니다. 자세한 내용은 [about_EventLogs](about_EventLogs.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Add-pssnapin](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[Add-pssnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[Add-pssnapin](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[Export-Console](xref:Microsoft.PowerShell.Core.Export-Console)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[about_Profiles](about_Profiles.md)

[about_Modules](about_Modules.md)

## <a name="keywords"></a>어

about_Snapins, about_Snap_ins, about_Snap 기능
