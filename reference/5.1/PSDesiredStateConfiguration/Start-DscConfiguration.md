---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215289"
---
# Start-DscConfiguration

## 개요
구성을 노드에 적용합니다.

## SYNTAX

### ComputerNameAndPathSet (기본값)

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimSessionAndPathSet

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Start-DscConfiguration** cmdlet은 노드에 구성을 적용합니다.
*UseExisting* 매개 변수와 함께 사용 하는 경우 대상 컴퓨터의 기존 구성이 적용 됩니다.
컴퓨터 이름을 지정 하거나 CIM(Common Information Model) (CIM) 세션을 사용 하 여 구성을 적용할 컴퓨터를 지정 합니다.

기본적으로 이 cmdlet은 작업을 만들고 **Job** 개체를 반환합니다.
백그라운드 작업에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help about_Jobs` .
이 cmdlet을 대화형으로 사용하려면 *Wait* 매개 변수를 지정합니다.

구성 설정을 적용할 때 cmdlet이 수행하는 작업의 세부 정보를 보려면 *Verbose* 매개 변수를 지정합니다.

## 예제

### 예제 1: 구성 설정 적용

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

이 명령은 C:\DSC\Configurations\에 설정이 있는 모든 컴퓨터에 해당 폴더의 구성 설정을 적용합니다.
또한 배포된 각 대상 노드에 대한 **Job** 개체를 반환합니다.

### 예제 2: 구성 설정 적용 및 구성이 완료 될 때까지 대기

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

이 명령은 C:\DSC\Configurations\의 구성을 로컬 컴퓨터에 적용합니다.
또한 배포된 각 대상 노드(이 경우 로컬 컴퓨터만 해당)에 대한 **Job** 개체를 반환합니다.
이 예에서는 *Verbose* 매개 변수를 지정 합니다.
따라서 명령이 진행 됨에 따라 콘솔에 메시지를 보냅니다.
이 명령에는 *Wait* 매개 변수가 포함 됩니다.
따라서 명령이 모든 구성 작업을 완료할 때까지 콘솔을 사용할 수 없습니다.

### 예제 3: CIM 세션을 사용 하 여 구성 설정 적용

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

이 예제에서는 지정한 컴퓨터에 구성 설정을 적용합니다.
또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.
또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.

첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.
또한 암호를 입력하라는 메시지를 표시합니다.
자세한 내용을 보려면 `Get-Help NewCimSession`를 입력하십시오.

두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터에 C:\wom\configurations\의 구성 설정을 적용 합니다.
이 예제에서는 $Session 변수에 이름이 $Server01인 컴퓨터에 대한 CIM 세션만 포함되어 있습니다.
명령이 구성을 적용합니다.
또한 구성된 각 컴퓨터에 대한 **Job** 개체를 만듭니다.

## PARAMETERS

### -CimSession
원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.
[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.
기본값은 로컬 컴퓨터의 현재 세션입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
컴퓨터 이름 배열을 지정합니다.
이 매개 변수는 *Path* 매개 변수의 구성 문서를 포함 하는 컴퓨터를 배열에 지정 된 것으로 제한 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
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
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
대상 컴퓨터에서 현재 실행 되 고 있는 구성 작업을 중지 하 고 새 Start-Configuration 작업을 시작 합니다.
로컬 Configuration Manager의 **Refreshmode** 속성이 **Pull** 로 설정 되어 있으면이 매개 변수를 지정 하면 **푸시** 로 변경 됩니다.

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

### -Path
구성 설정 파일이 포함된 폴더의 파일 경로를 지정합니다.
이 cmdlet은 지정 된 경로에 설정 파일이 있는 컴퓨터에 이러한 구성 설정을 게시 하 고 적용 합니다.
각 대상 노드에는 다음 형식의 설정 파일이 있어야 합니다. NetBIOS 이름. mof.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
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

### -UseExisting
이 cmdlet이 기존 구성을 적용 함을 나타냅니다.
Start-dscconfiguration cmdlet Publish-DscConfiguration을 사용 하 여 **Start-DscConfiguration** 또는 게시를 사용 하 여 대상 컴퓨터에 구성이 있을 수 있습니다.

이 cmdlet에 대해이 매개 변수를 지정 하기 전에 [Windows PowerShell 5.0의 새로운 기능](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50) 정보를 검토 하십시오.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
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

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/overview)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)
