---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388827"
---
# Add-PSSnapin

## 개요
하나 이상의 Windows PowerShell 스냅인을 현재 세션에 추가합니다.

## SYNTAX

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## 설명

`Add-PSSnapin`Cmdlet은 등록 된 Windows PowerShell 스냅인을 현재 세션에 추가 합니다. 스냅인이 추가되고 나면 현재 세션에서 스냅인이 지원하는 공급자와 cmdlet을 사용할 수 있습니다.

모든 향후 Windows PowerShell 세션에 스냅인을 추가 하려면 `Add-PSSnapin` Windows powershell 프로필에 명령을 추가 합니다. 자세한 내용은 [about_Profiles](about/about_Profiles.md)를 참조 하세요.

Windows PowerShell 3.0부터는 Windows PowerShell에 포함되는 핵심 명령이 모듈에 패키지됩니다. 단, 스냅인(PSSnapin)인 **Microsoft.PowerShell.Core** 는 예외입니다.
기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다. 모듈은 처음 사용할 때 자동으로 가져오며 Import-Module cmdlet을 사용 하 여 가져올 수 있습니다.

## 예제

### 예제 1: 스냅인 추가

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

이 명령은 Microsoft Exchange 및 Active Directory 스냅인을 현재 세션에 추가합니다.

### 예제 2: 등록 된 모든 스냅인 추가

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

이 명령은 등록된 모든 Windows PowerShell 스냅인을 세션에 추가합니다. **등록 된 매개 변수와 함께** Get-PSSnapin cmdlet을 사용 하 여 등록 된 각 스냅인을 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)는 결과를에 전달 하 여 `Add-PSSnapin` 세션에 추가 합니다. **PassThru** 매개 변수는 추가 된 각 스냅인을 나타내는 개체를 반환 합니다.

### 예제 3: 스냅인 등록 및 추가

첫 번째 명령은 Windows PowerShell과 함께 설치 된 스냅인을 포함 하는 현재 세션에 추가 된 스냅인을 가져옵니다. 이 예제에서 ManagementFeatures는 반환되지 않습니다. 이는 ManagementFeatures가 세션에 추가되지 않았음을 나타냅니다.

두 번째 명령은 세션에 이미 추가 된 스냅인을 포함 하 여 시스템에 등록 된 스냅인을 가져옵니다. Windows PowerShell과 함께 설치 된 스냅인은 포함 되지 않습니다. 이 경우 명령은 스냅인을 반환 하지 않습니다. 이는 ManagementFeatures 스냅인이 시스템에 등록 되지 않았음을 나타냅니다.

세 번째 명령은 .NET Framework에서 Installutil.exe 도구의 경로에 대 한 별칭을 만듭니다.

네 번째 명령은 Installutil.exe 도구를 사용 하 여 스냅인을 등록 합니다. 명령은 ManagementCmdlets.dll의 경로, 파일 이름 또는 스냅인의 모듈 이름을 지정 합니다.

다섯 번째 명령은 두 번째 명령과 동일합니다. 이번에는 이 명령을 사용하여 ManagementCmdlets 스냅인이 등록되었는지 확인합니다.

여섯 번째 명령은 cmdlet을 사용 하 여 `Add-PSSnapin` ManagementFeatures 스냅인을 세션에 추가 합니다. 이 명령은 파일 이름이 아니라 스냅인의 이름인 ManagementFeatures를 지정합니다.

스냅인이 세션에 추가 되었는지 확인 하기 위해 일곱 번째 명령은 Get-Command cmdlet의 **Module** 매개 변수를 사용 합니다. 이 명령은 스냅인이나 모듈에서 세션에 추가한 항목을 표시합니다.

Cmdlet이 반환 하는 개체의 **add-pssnapin** 속성을 사용 하 여 `Get-Command` cmdlet이 시작 된 스냅인 또는 모듈을 찾을 수도 있습니다. 여덟 번째 명령은 점 표기법을 사용 하 여 Set-Alias cmdlet의 Add-pssnapin 속성 값을 찾습니다.

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

이 예제에서는 시스템에서 스냅인을 등록한 다음 세션에 추가하는 프로세스를 보여 줍니다. ManagementCmdlets.dll 이라는 파일에 구현 된 가상의 스냅인 인 ManagementFeatures를 사용 합니다.

## PARAMETERS

### -Name

스냅인의 이름을 지정 합니다. AssemblyName 또는 ModuleName이 아닌 이름입니다. 와일드카드가 지원됩니다.

시스템에서 등록 된 스냅인의 이름을 찾으려면를 입력 `Get-PSSnapin -Registered` 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

이 cmdlet이 추가 된 각 스냅인을 나타내는 개체를 반환 함을 나타냅니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음 또는 PSSnapInInfo

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 스냅인을 나타내는 PSSnapInInfo 개체를 반환 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- Windows PowerShell 3.0부터 Windows PowerShell과 함께 설치된 핵심 명령이 모듈에 패키지됩니다. Windows PowerShell 2.0 및 이후 버전의 Windows PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 (PSSnapins)으로 패키지 됩니다. 예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다. 또한 New-PSSession cmdlet에서 시작한 것과 같은 원격 세션은 코어 스냅인을 포함 하는 이전 스타일의 세션입니다.

  핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2)를 참조 하세요.

- 스냅인에 대 한 자세한 내용은 [about_PSSnapins](About/about_PSSnapins.md) 및 [Windows PowerShell 스냅인을 만드는 방법](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)을 참조 하세요.
- `Add-PSSnapin` 현재 세션에만 스냅인을 추가 합니다. 모든 Windows PowerShell 세션에 스냅인을 추가하려면 스냅인을 Windows PowerShell 프로필에 추가합니다. 자세한 내용은 about_Profiles를 참조하세요.
- Microsoft .NET Framework 설치 유틸리티를 사용 하 여 등록 된 모든 스냅인을 추가할 수 있습니다. 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.
- 컴퓨터에 등록 된 스냅인 목록을 가져오려면를 입력 `Get-PSSnapin -Registered` 합니다.
- 스냅인을 추가 하기 전에는 `Add-PSSnapin` 스냅인의 버전을 확인 하 여 현재 버전의 Windows PowerShell과 호환 되는지 확인 합니다. 스냅인이 버전 확인에 실패하면 Windows PowerShell에서 오류를 보고합니다.

## 관련 링크

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
