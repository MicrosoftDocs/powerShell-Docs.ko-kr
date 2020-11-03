---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213570"
---
# Update-DscConfiguration

## 개요
끌어오기 서버에서 업데이트 된 구성을 확인 하 고 적용 합니다.

## SYNTAX

### ComputerNameSet (기본값)

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
`Update-DscConfiguration`Cmdlet은 끌어오기 서버에 연결 하 고, 노드가 노드의 최신 항목과 다른 경우 구성을 다운로드 한 후 컴퓨터에 구성을 적용 합니다.

이 cmdlet은 Microsoft 지원 라이브러리에서 [WINDOWS RT 8.1, Windows 8.1 및 Windows Server 2012 r 2에 대 한 11 월 2014 업데이트 롤업의](https://support.microsoft.com/kb/3000850) 일부로만 사용할 수 있습니다.

## 예제

### 예제 1: 구성 업데이트

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

이 명령을 실행 한 후 서버에서 등록 된 끌어오기 서비스에 연결 하 고, 할당 된 최신 구성을 다운로드 한 후 적용 합니다.
-Wait 및-Verbose 매개 변수는 선택 사항입니다.
대화형으로 작업 하는 경우 이러한 매개 변수를 결합 하면 구성 적용 시 진행률 및 성공 또는 실패에 대 한 실시간 피드백을 사용할 수 있습니다.

### 예제 2: CIM 세션을 통해 연결 하 여 구성 업데이트

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.
또한 암호를 입력하라는 메시지를 표시합니다.
자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.

두 번째 명령은 $Session에 저장 된 **CimSession** 에 지정 된 컴퓨터를 업데이트 합니다.
이 명령은 *Wait* 매개 변수를 지정 합니다.
현재 명령이 완료 될 때까지 콘솔에서 추가 명령을 허용 하지 않습니다.

## PARAMETERS

### -CimSession
원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.
[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.
기본값은 로컬 컴퓨터의 현재 세션입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
컴퓨터 이름 배열을 지정합니다.
Cmdlet은이 매개 변수가 지정 하는 컴퓨터에 구성 설정을 적용 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.
**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.
자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName
작업의 이름을 지정합니다.
이 매개 변수를 지정하면 cmdlet이 작업으로 실행되고 **Job** 개체를 반환합니다.

기본적으로 Windows PowerShell은 이름 JobN을 할당 합니다. 여기서 N은 정수입니다.

*Wait* 매개 변수를 지정하는 경우 이 매개 변수를 지정하지 마세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.
이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.
스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait
Cmdlet이 모든 구성 작업을 완료할 때까지 콘솔을 차단 함을 나타냅니다.

이 매개 변수를 지정하는 경우 *JobName* 매개 변수를 지정하지 마세요.

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

### -Confirm
cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
