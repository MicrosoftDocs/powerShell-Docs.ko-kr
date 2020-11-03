---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 19871bcfd1e045ab30bfef0dc88aa42a4c4aecf4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216393"
---
# Out-Default

## 개요
출력을 기본 포맷터와 기본 출력 cmdlet으로 보냅니다.

## SYNTAX

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

PowerShell `Out-Default` 은 모든 파이프라인의 끝에 자동으로 추가 됩니다. `Out-Default` 개체 스트림을 서식 지정 하 고 출력 하는 방법을 결정 합니다. 개체 스트림이 문자열 스트림이 면가 `Out-Default` `Out-Host` 호스트에서 제공 하는 적절 한 api를 호출 하는에 직접 파이프 합니다. 개체 스트림에 문자열이 없는 경우는 `Out-Default` 개체를 검사 하 여 수행할 작업을 결정 합니다.
먼저 개체 유형을 확인 하 고이 개체 유형에 대해 등록 된 _뷰가_ 있는지 여부를 확인 합니다.

PowerShell은 `Update-FormatData` 모든 사용자가 개체 유형에 대 한 뷰를 등록할 수 있는 XML 스키마 및 메커니즘 (cmdlet)을 정의 합니다. 모든 개체 유형에 대해 **넓은** , **목록** , **테이블** 또는 **사용자 지정** 뷰를 지정할 수 있습니다. 보기는 표시할 속성과 표시 되는 방법을 지정 합니다. 뷰가 등록 된 경우 사용할 포맷터를 정의 합니다. 따라서 등록 된 뷰가 **테이블** 뷰가 면에서 개체를 `Out-Default` 로 스트리밍합니다 `Format-Table | Out-Host` . `Format-Table` 개체를 형식 지정 레코드의 스트림으로 변환 하 고 (뷰 정의의 데이터로 구동), `Out-Host` 형식 지정 레코드를 호스트 인터페이스에 대 한 호출로 변환 합니다.

## 예제

### 예 1

이 cmdlet은 최종 사용자가 직접 실행할 수는 없지만 일 수 있습니다.

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETERS

### -InputObject

cmdlet에 대한 입력을 허용합니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -성적 증명서

출력을 PowerShell의 기록 서비스로 보낼지 여부를 결정 합니다.

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

## 출력

## 참고

## 관련 링크

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1xml](About/about_Format.ps1xml.md)

[PowerShell 서식 지정 및 출력의 작동 방식](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)
