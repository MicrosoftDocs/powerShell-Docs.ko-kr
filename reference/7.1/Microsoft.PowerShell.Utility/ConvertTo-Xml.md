---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: 2e7ebe3a528095873dc7ba5ba0deba2905f531ee
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215857"
---
# ConvertTo-Xml

## 개요
개체의 XML 기반 표시를 만듭니다.

## SYNTAX

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## 설명

`ConvertTo-Xml`Cmdlet은 하나 이상의 .net 개체에 대 한 [XML 기반](/dotnet/api/system.xml.xmldocument) 표현을 만듭니다. 이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.

여러 개체를로 파이프 `ConvertTo-Xml` 하거나 **InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Xml` 모든 개체의 표현을 포함 하는 단일 메모리 내 XML 문서를 반환 합니다.

이 cmdlet은 결과 XML을 [export-clixml](./Export-Clixml.md) 를 사용 하 여 `Export-Clixml` 개체로 다시 가져올 수 있는 [CLI (공용 언어 인프라) xml](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 파일에 저장 한다는 점을 제외 하 고는 [Import-Clixml](./Import-Clixml.md)내보내기와 유사 합니다. `ConvertTo-Xml` XML 문서의 메모리 내 표현을 반환 하므로 PowerShell에서 계속 처리할 수 있습니다. `ConvertTo-Xml` 에는 개체를 CLI XML로 변환할 수 있는 옵션이 없습니다.

## 예제

### 예제 1: 날짜를 XML로 변환

```
PS C:\> Get-Date | ConvertTo-Xml
```

이 명령은 현재 날짜 ( **DateTime** 개체)를 XML로 변환 합니다.

### 예제 2: 프로세스를 XML로 변환

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

이 명령은 컴퓨터의 모든 프로세스를 나타내는 프로세스 개체를 XML 문서로 변환합니다. 개체는 수준 3까지 확장됩니다.

## PARAMETERS

### -As

출력 형식을 결정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 문자열.
단일 문자열을 반환합니다.
- 스트림입니다.
문자열의 배열을 반환합니다.
- 문서입니다.
**XmlDocument** 개체를 반환 합니다.

기본값은 Document입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -깊이

XML 표시에 포함되는 포함 개체 수준을 지정합니다. 기본값은 1입니다.

예를 들어 개체의 속성에 또 개체가 포함된 경우 포함 개체 속성의 XML 표시를 저장하려면 수준을 2로 지정해야 합니다.

Types.ps1xml 파일에서 개체 유형에 대한 기본값을 재정의할 수 있습니다. 자세한 내용은 about_Types.ps1xml을 참조하세요.

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

### -InputObject

변환할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를 **convertto-html** 로 파이프 할 수도 있습니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

개체 노드에서 Type 특성을 생략합니다.

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

### System.web. PSObject

모든 개체를 **convertto-html** 로 파이프 할 수 있습니다.

## 출력

### System.string 또는 System.Xml.Xml문서

*As* 매개 변수 값은 **convertto-html에서** 반환 하는 개체의 유형을 결정 합니다.

## 참고

## 관련 링크

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Export-Clixml](Export-Clixml.md)

[가져오기-날짜](Get-Date.md)

[Import-Clixml](Import-Clixml.md)

