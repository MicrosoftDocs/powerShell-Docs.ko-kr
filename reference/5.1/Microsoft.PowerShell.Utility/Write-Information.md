---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: e0f28393c95e2c0703c489d4691edcf883b4cb05
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224298"
---
# Write-Information

## 개요

PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.

## SYNTAX

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## 설명

`Write-Information`Cmdlet은 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정 합니다.

Windows PowerShell 5.0에는 새로운 구조화 된 정보 스트림이 도입 되었습니다. 이 스트림을 사용 하 여 스크립트와 해당 호출자 또는 호스트 응용 프로그램 간에 구조화 된 데이터를 전송할 수 있습니다.
`Write-Information` 스트림에 정보 메시지를 추가 하 고 PowerShell에서 명령에 대 한 정보 스트림 데이터를 처리 하는 방법을 지정할 수 있습니다. 정보 스트림은 `PowerShell.Streams` , 작업 및 예약 된 작업에 대해서도 작동 합니다.

> [!NOTE]
> 정보 스트림은 메시지에 "[Stream Name]:"을 접두사로 추가 하는 표준 규칙을 따르지 않습니다. 이는 간단 하 고 시각적으로 청결도 하기 위한 것입니다.

`$InformationPreference`기본 설정 변수 값은 사용자가 제공 하는 메시지를 `Write-Information` 스크립트 작업의 예상 지점에 표시할지 여부를 결정 합니다. 이 변수의 기본값은 이므로 `SilentlyContinue` 기본적으로 정보 메시지는 표시 되지 않습니다. 의 값을 변경 하지 않으려면 `$InformationPreference` `InformationAction` 일반 매개 변수를 명령에 추가 하 여 해당 값을 재정의할 수 있습니다. 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 및 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조 하세요.

> [!NOTE]
> Windows PowerShell 5.0부터 `Write-Host` 은이에 대 한 래퍼로,를 사용 하 여 `Write-Information` 출력을 `Write-Host` 정보 스트림으로 내보낼 수 있습니다. 이를 통해 이전 버전과의 호환성을 유지 하면서 **를 사용** 하 여 작성 된 데이터를 **캡처하거나** 제거할 수 있습니다 `Write-Host` . 자세한 내용은 [쓰기 호스트](Write-Host.md) 를 참조 하십시오.

`Write-Information` 는 또한 PowerShell 5.x에서 지원 되는 워크플로 활동입니다.

## 예제

### 예제 1: Get 결과에 대 한 정보 작성

이 예제에서는 `Get-WindowsFeature` ' p '로 시작 하는 이름 값이 있는 모든 기능을 찾기 위해 명령을 실행 한 후 정보 메시지 "기능을 가져왔습니다!"를 표시 합니다.
`$InformationPreference`변수가 여전히 기본값인로 설정 되어 있기 때문에 `SilentlyContinue` `InformationAction` 매개 변수를 추가 하 여 값을 재정의 하 `$InformationPreference` 고 메시지를 표시 합니다. `InformationAction`값은 Continue입니다. 즉, 메시지가 표시 되지만 스크립트나 명령이 아직 완료 되지 않았으면 계속 됩니다.

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### 예제 2: 정보 작성 및 태그

이 예제에서는 `Write-Information` 를 사용 하 여 사용자가 현재 명령 실행이 완료 된 후 다른 명령을 실행 해야 한다는 사실을 알 수 있습니다. 이 예에서는 정보 메시지에 태그 지침을 추가 합니다. 이 명령을 실행 한 후 정보 스트림을 검색 하 여 표시 되는 메시지에 대 한 지침을 검색 하면 여기에 지정 된 메시지가 결과 중 하나입니다.

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### 예제 3: 파일에 정보 쓰기

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

## PARAMETERS

### -MessageData

스크립트나 명령을 실행할 때 사용자에 게 표시 하려는 정보 메시지를 지정 합니다. 최상의 결과를 위해 정보 메시지를 큰따옴표로 묶습니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -태그

를 사용 하 여 정보 스트림에 추가한 메시지를 정렬 하 고 필터링 하는 데 사용할 수 있는 간단한 문자열을 지정 `Write-Information` 합니다. 이 매개 변수는의 **Tags** 매개 변수와 유사 하 게 작동 `New-ModuleManifest` 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### None

`Write-Information` 파이프 입력을 허용 하지 않습니다.

## 출력

### System.web. InformationRecord

## 참고

## 관련 링크

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

[Write-Output](Write-Output.md)
