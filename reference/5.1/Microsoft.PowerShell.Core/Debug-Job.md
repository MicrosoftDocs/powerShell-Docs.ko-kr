---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: d36d15194ce1d4a48a59ad8bb8621b3c9c1a74ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212113"
---
# Debug-Job

## 개요
실행 중인 백그라운드, 원격 또는 Windows PowerShell 워크플로 작업을 디버깅 합니다.

## SYNTAX

### JobParameterSet (기본값)

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobNameParameterSet

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobIdParameterSet

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobInstanceIdParameterSet

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**디버그-작업** cmdlet을 사용 하 여 작업 내에서 실행 되는 스크립트를 디버그할 수 있습니다.
이 cmdlet은 Windows PowerShell 워크플로 작업, 백그라운드 작업 및 원격 세션에서 실행 되는 작업을 디버그 하도록 디자인 되었습니다.
**디버그-작업** 은 실행 중인 작업 개체, 이름, ID 또는 인스턴스 ID를 입력으로 수락 하 고 실행 중인 스크립트에서 디버깅 세션을 시작 합니다.
Debugger **quit** 명령은 작업을 중지 하 고 스크립트를 실행 합니다.
Windows PowerShell 5.0부터 **끝내기** 명령은 디버거를 분리 하 고 작업을 계속 실행할 수 있도록 합니다.

## 예제

### 예제 1: 작업 ID로 작업 디버그

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

이 명령은 ID가 3 인 실행 중인 작업을 중단 합니다.

## PARAMETERS

### -Id
실행 중인 작업의 ID 번호를 지정 합니다.
작업의 ID 번호를 가져오려면 Get-Job cmdlet을 실행 합니다.

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId
실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.
작업의 *InstanceId* 를 가져오려면 다음 예제와 같이 **get job** cmdlet을 실행 하 고 결과를 **형식-** * cmdlet으로 파이프 합니다.

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Job
실행 중인 작업 개체를 지정 합니다.
이 매개 변수를 사용 하는 가장 간단한 방법은 디버깅할 실행 중인 작업을 반환 하는 **Get job** 명령의 결과를 저장 한 다음 변수를이 매개 변수 값으로 지정 하는 것입니다.

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
작업 이름을 지정 하 여 작업을 지정 합니다.
작업을 시작할 때 Invoke-Command 및 JobName와 같은 cmdlet에 *JobName* 매개 변수를 추가 하 여 작업 이름을 지정할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
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

### System.web. Remorererea 작업

## 출력

## 참고

## 관련 링크

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
