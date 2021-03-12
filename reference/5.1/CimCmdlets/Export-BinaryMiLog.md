---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194357"
---
# Export-BinaryMiLog

## 개요
개체 또는 개체의 이진 인코딩된 표현을 만들어 파일에 저장 합니다.

## SYNTAX

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## 설명

`Export-BinaryMILog`Cmdlet은 개체 또는 개체의 이진 기반 표현을 만들어 파일에 저장 합니다. 그런 다음 cmdlet을 사용 하 여 `Import-BinaryMiLog` 해당 파일의 내용을 기반으로 저장 된 개체를 다시 만들 수 있습니다.

이 cmdlet은 `Import-Clixml` `Export-BinaryMILog` 결과 개체를 이진 인코딩 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.

## 예제

### 예제 1-CimInstances의 이진 표현 만들기

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

이 명령은 Path 매개 변수로 지정 된 이진 MI 로그 파일에 **CimInstances** 를 내보냅니다. 이 파일을 가져와서 **CimInstances** 를 다시 만드는 방법에 대 한 자세한 내용은 Import-BinaryMiLog의 예제를 참조 하세요.

## PARAMETERS

### -InputObject

이 cmdlet에 대한 입력을 지정합니다. 이 매개 변수를 사용하거나 이 cmdlet에 입력을 파이프할 수 있습니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path

개체의 이진 표현을 저장할 파일의 경로를 지정 합니다. **Path** 매개 변수는 와일드 카드 및 상대 경로를 지원 합니다. 이 cmdlet은 경로가 둘 이상의 파일로 확인 될 경우 오류를 생성 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Ciminstance 개체로.

## 출력

### System.Object

## 참고

## 관련 링크

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)
