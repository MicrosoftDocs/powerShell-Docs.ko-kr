---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212778"
---
# Remove-PSSnapin

## 개요
현재 세션에서 Windows PowerShell 스냅인을 제거합니다.

## SYNTAX

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Add-pssnapin** cmdlet은 현재 세션에서 Windows PowerShell 스냅인을 제거 합니다.
이 cmdlet을 사용 하 여 windows PowerShell에 추가 된 스냅인을 제거할 수 있습니다 .이 cmdlet을 사용 하 여 Windows PowerShell과 함께 설치 된 스냅인을 제거할 수 없습니다.

현재 세션에서 스냅인을 제거 하면 스냅인이 여전히 로드 되지만 스냅인의 cmdlet 및 공급자는 세션에서 더 이상 사용할 수 없습니다.

## 예제

### 예제 1: 스냅인 제거

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

이 명령은 현재 세션에서 **Microsoft Exchange** 스냅인을 제거 합니다.
명령이 완료되면 스냅인이 지원하는 cmdlet 및 공급자를 세션에서 사용할 수 없습니다.

### 예제 2: 파이프라인에서 이름을 사용 하 여 스냅인 제거

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

이 명령은 현재 세션에서 smp로 시작 하는 이름을 가진 Windows PowerShell 스냅인을 제거 합니다.

이 명령은 **add-pssnapin** cmdlet을 사용 하 여 스냅인을 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 결과를 **add-pssnapin** cmdlet으로 보내면이 cmdlet이 결과를 세션에서 제거 합니다.
명령이 완료되면 스냅인이 지원하는 cmdlet 및 공급자를 세션에서 더 이상 사용할 수 없습니다.

개체를 **add-pssnapin** 에 파이프 하면 개체 이름이 *name 매개 변수와* 연결 됩니다 .이 매개 변수는 **name** 속성을 가진 파이프라인의 개체를 허용 합니다.

### 예제 3: 이름을 사용 하 여 스냅인 제거

```
PS C:\> Remove-PSSnapin -Name *event*
```

이 명령은 이벤트를 포함 하는 이름이 있는 모든 Windows PowerShell 스냅인을 제거 합니다.

## PARAMETERS

### -Name
현재 세션에서 제거할 Windows PowerShell 스냅인의 이름을 지정합니다.
와일드카드 문자(*)를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru
스냅인을 나타내는 개체를 반환 합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### PSSnapInInfo.
스냅인 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, PSSnapInInfo
이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 스냅인을 나타내는 **PSSnapInInfo** 개체를 생성 합니다.
기본적으로 **add-pssnapin** 은 출력을 생성 하지 않습니다.

## 참고

* **Add-pssnapin** 는 세션에서 스냅인을 제거 하기 전에 Windows PowerShell의 버전을 확인 하지 않습니다. 스냅인을 제거할 수 없는 경우 경고가 표시되고 명령이 실패합니다.
* **Add-pssnapin** 는 현재 세션에만 영향을 줍니다. Add-PSSnapin 명령을 Windows PowerShell 프로필에 추가한 경우 이후 세션에서 스냅인을 제거하려면 이 명령을 삭제해야 합니다. 지침을 보려면을 입력 `Get-Help about_Profiles` 합니다.

## 관련 링크

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)
