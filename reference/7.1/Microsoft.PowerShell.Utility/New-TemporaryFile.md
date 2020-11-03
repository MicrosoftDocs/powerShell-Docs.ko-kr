---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 406675d8bde1b6b9a28913c09d5374393705f93b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217385"
---
# New-TemporaryFile

## 개요
임시 파일을 만듭니다.

## SYNTAX

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

이 cmdlet은 스크립트에서 사용할 수 있는 임시 파일을 만듭니다.

`New-TemporaryFile`Cmdlet은 파일 이름 확장명이 인 빈 파일을 만듭니다 `.tmp` .
이 cmdlet은 파일의 이름을 `tmp<NNNN>.tmp` 로 `<NNNN>` 바꿉니다. 여기서는 임의의 16 진수입니다.
Cmdlet은 **임시** 폴더에 파일을 만듭니다.

이 cmdlet은 [path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) 메서드를 사용 하 여 **임시** 폴더를 찾습니다. 이 메서드는 다음 순서로 환경 변수가 있는지 확인 하 고 찾은 첫 번째 경로를 사용 합니다.

- Windows 플랫폼에서:

  1. TMP 환경 변수로 지정 된 경로입니다.
  1. TEMP 환경 변수로 지정 된 경로입니다.
  1. USERPROFILE 환경 변수로 지정 된 경로입니다.
  1. Windows 디렉터리입니다.

- Windows가 아닌 플랫폼에서: TMPDIR 환경 변수에 지정 된 경로를 사용 합니다.

## 예제

### 예제 1: 임시 파일 만들기

```powershell
$TempFile = New-TemporaryFile
```

이 명령은 `.tmp` 임시 폴더에 파일을 생성 한 다음 해당 파일에 대 한 참조를 `$TempFile` 변수에 저장 합니다. 스크립트에서 나중에이 파일을 사용할 수 있습니다.

## PARAMETERS

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

## 출력

### System.object

이 cmdlet은 임시 파일을 나타내는 **FileInfo** 개체를 반환 합니다.

## 참고

## 관련 링크

