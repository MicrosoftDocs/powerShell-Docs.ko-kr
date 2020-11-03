---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215490"
---
# Enable-ComputerRestore

## 개요
지정된 파일 시스템 드라이브에서 시스템 복원 기능을 사용하도록 설정합니다.

## SYNTAX

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Enable computerrestore** cmdlet은 하나 이상의 파일 시스템 드라이브에서 시스템 복원 기능을 설정 합니다.
그 결과 Restore-Computer cmdlet 같은 도구를 사용하여 컴퓨터를 이전 상태로 복원할 수 있습니다.

시스템 복원은 이 기능을 사용할 수 있는 모든 드라이브에서 기본적으로 사용하도록 설정되지만 Disable-ComputerRestore cmdlet을 사용하는 등의 방법으로 사용하지 않도록 설정할 수 있습니다.
드라이브에서 시스템 복원을 사용하도록 설정하거나 다시 사용하도록 설정하려면 먼저 또는 동시에 시스템 드라이브에서 시스템 복원을 사용하도록 설정해야 합니다.
각 드라이브의 시스템 복원 상태를 찾으려면 Rstrui.exe를 사용합니다.

시스템 복원 지점과 ComputerRestore cmdlet은 Windows 7, Windows Vista 및 Windows XP와 같은 클라이언트 운영 체제에서만 지원됩니다.

## 예제

### 예 1: 지정한 드라이브에서 시스템 복원을 사용 하도록 설정

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

이 명령은 로컬 컴퓨터의 C: 드라이브에서 시스템 복원을 사용하도록 설정합니다.

### 예 2: 여러 드라이브에서 시스템 복원 사용

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

이 명령은 로컬 컴퓨터의 C: 및 D: 드라이브에서 시스템 복원을 사용하도록 설정합니다.

## PARAMETERS

### -드라이브
파일 시스템 드라이브를 지정합니다.
하나 이상의 파일 시스템 드라이브 문자를 입력 합니다. 여기에는 각각 콜론과 백슬래시가 오고 따옴표 (예: C:\)로 묶여 있습니다. 또는 D:\.
이 매개 변수는 필수적 요소입니다.

드라이브가 로컬 컴퓨터에 매핑되어 있는 경우에도 이 cmdlet을 사용하여 원격 네트워크 드라이브에서 시스템 복원을 사용하도록 설정할 수 없으며 외부 드라이브와 같이 시스템 복원에 사용할 수 없는 드라이브에서는 시스템 복원을 사용하도록 설정할 수 없습니다.

드라이브에서 시스템 복원을 사용하도록 설정하려면 미리 또는 동시에 시스템 드라이브에서 시스템 복원을 사용하도록 설정해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
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

### 없음
이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* Windows Vista 이상 버전에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.

  시스템 복원에 적합 한 파일 시스템 드라이브를 찾으려면 제어판의 시스템에서 시스템 보호 탭을 참조 하세요. Windows PowerShell에서이 탭을 열려면를 입력 `SystemPropertiesProtection` 합니다.

  이 cmdlet은 WMI(Windows Management Instrumentation) (WMI) **SystemRestore** 클래스를 사용 합니다.

*

## 관련 링크

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)
