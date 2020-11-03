---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ComputerMachinePassword 재설정
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214489"
---
# ComputerMachinePassword 재설정

## 개요
컴퓨터의 컴퓨터 계정 암호를 다시 설정합니다.

## SYNTAX

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명
**Reset-computermachinepassword** cmdlet은 컴퓨터가 도메인의 도메인 컨트롤러를 인증 하는 데 사용 하는 컴퓨터 계정 암호를 변경 합니다.
이 명령을 사용하여 로컬 컴퓨터의 암호를 다시 설정할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에 대 한 암호 다시 설정

```
PS C:\> Reset-ComputerMachinePassword
```

이 명령은 로컬 컴퓨터의 컴퓨터 암호를 다시 설정 합니다.
이 명령은 현재 사용자의 자격 증명으로 실행됩니다.

### 예 2: 지정 된 도메인 컨트롤러를 사용 하 여 로컬 컴퓨터의 암호 다시 설정

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

이 명령은 D C 01 도메인 컨트롤러를 사용 하 여 로컬 컴퓨터의 컴퓨터 암호를 다시 설정 합니다.
*Credential* 매개 변수를 사용 하 여 도메인에서 컴퓨터 암호를 다시 설정할 권한이 있는 사용자 계정을 지정 합니다.

### 예 3: 원격 컴퓨터에서 암호 다시 설정

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 원격 컴퓨터에서 **reset-computermachinepassword** 명령을 실행 합니다.

Windows PowerShell의 원격 명령에 대 한 자세한 내용은 about_Remote 및 **호출-명령** 을 참조 하세요.

## PARAMETERS

### -Credential
이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet에 의해 생성 된 개체)를 입력 합니다.
사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Server
이 cmdlet이 컴퓨터 계정 암호를 설정 하는 경우 사용할 도메인 컨트롤러의 이름을 지정 합니다.

이 매개 변수는 선택 사항입니다.
이 매개 변수를 생략하면 도메인 컨트롤러가 명령을 처리하도록 선택됩니다.

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

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

## 관련 링크

## 관련 링크
