---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 8e0c1057a4117eb60cdc8ec494470dacaca78699
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2020
ms.locfileid: "93217930"
---
# Read-Host

## 개요
콘솔에서 입력 줄을 읽습니다.

## SYNTAX

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## 설명

`Read-Host`Cmdlet은 콘솔에서 입력 줄을 읽습니다. 이 cmdlet을 사용하여 사용자에게 입력하라는 메시지를 표시할 수 있습니다. 입력을 보안 문자열로 저장할 수 있으므로 이 cmdlet을 사용하여 암호 등의 보안 데이터와 공유 데이터를 입력하라는 메시지를 사용자에게 표시할 수 있습니다.

## 예제

### 예제 1: 콘솔 입력을 변수에 저장

이 예에서는 "age를 입력 하십시오." 문자열을 프롬프트로 표시 합니다. 값을 입력 하 고 Enter 키를 누르면 값이 변수에 저장 됩니다 `$Age` .

```powershell
$Age = Read-Host "Please enter your age"
```

### 예제 2: 콘솔 입력을 보안 문자열로 저장

이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다. 값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다. Enter 키를 누르면 값이 변수에 **SecureString** 개체로 저장 됩니다 `$pwd_secure_string` .

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## PARAMETERS

### -AsSecureString

Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다. 이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **SecureString** 개체 ( **system.web** )입니다.

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

### -Prompt

프롬프트 텍스트를 지정합니다.
문자열을 입력합니다.
문자열에 공백이 포함되어 있으면 따옴표로 묶습니다.
PowerShell은 입력 한 텍스트에 콜론 ()을 추가 `:` 합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.string 또는 System.object

**Assecurestring** 매개 변수를 사용 하는 경우은 `Read-Host` **SecureString** 을 반환 합니다. 그러지 않으면 문자열이 반환됩니다.

## 참고

## 관련 링크

[Clear-Host](../microsoft.powershell.core/clear-host.md)

[Get-Host](Get-Host.md)

[Write-Host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
