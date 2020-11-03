---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93220033"
---
# Get-Clipboard

## 개요
현재 Windows 클립보드 항목을 가져옵니다.

## SYNTAX

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## 설명

`Get-Clipboard`Cmdlet은 현재 Windows 클립보드 항목을 가져옵니다. 텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .

## 예제

### 예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시

이 예제에서는 브라우저에서 이미지를 마우스 오른쪽 단추로 클릭 하 고 **복사** 작업을 선택 했습니다. 다음 명령은 클립보드에 저장 된 이미지의 링크를 URL로 표시 합니다.

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### 예 2: 특정 형식으로 클립보드의 내용 가져오기

이 예제에서는 Windows에서 클립보드에 파일을 복사 하 고 <kbd>Ctrl + C</kbd>를 눌러 파일을 클립보드에 복사 Explorerby. 다음 명령을 사용 하 여 클립보드의 내용을 파일 목록으로 액세스할 수 있습니다.

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## PARAMETERS

### -형식

클립보드의 형식 또는 형식을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 텍스트
- FileDropList
- 이미지
- 오디오

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Raw

클립보드의 전체 내용을 가져옵니다. 여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.

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

### -TextFormatType

클립보드의 텍스트 데이터 서식 유형을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 텍스트
- UnicodeText
- 형식
- Html
- CommaSeparatedValue

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

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

### System.string, System.string, System.string, System.web. 이미지를 클릭 합니다.

## 참고

## 관련 링크

[Set-Clipboard](Set-Clipboard.md)
