---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212378"
---
# New-IseSnippet

## 개요
Windows PowerShell ISE 코드 조각을 만듭니다.

## SYNTAX

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## 설명

`New-ISESnippet`Cmdlet은 Windows PowerShell ISE을 위한 다시 사용할 수 있는 텍스트 "조각"을 만듭니다. 조각을 사용하여 Windows PowerShell ISE의 스크립트 창 또는 명령 창에 텍스트를 추가할 수 있습니다. 이 cmdlet은 Windows PowerShell ISE에서만 사용할 수 있습니다.

Windows PowerShell 3.0부터 Windows PowerShell ISE에는 기본 제공 조각 컬렉션이 포함되어 있습니다. Cmdlet을 사용 하 여 `New-ISESnippet` 기본 제공 컬렉션에 추가할 고유한 코드 조각을 만들 수 있습니다. 조각 파일을 보고, 변경하며, 추가하고, 삭제하며, 공유하고, Windows PowerShell 모듈에 포함할 수 있습니다. Windows PowerShell ISE에서 코드 조각을 보려면 **편집** 메뉴에서 **코드 조각 시작** 을 선택 하거나 <kbd>ctrl</kbd> + <kbd>J</kbd>를 누릅니다.

`New-ISESnippet`Cmdlet은 `<Title>.Snippets.ps1xml` 지정한 제목을 사용 하 여 디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` . 작성 중인 모듈에 조각 파일을 포함하려면 모듈 디렉터리의 Snippets 하위 디렉터리에 조각 파일을 추가합니다.

실행 정책이 **제한** 되거나 **AllSigned** 세션에서 사용자가 만든 코드 조각을 사용할 수 없습니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: Comment-Based 도움말 코드 조각 만들기

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

이 명령은 Windows PowerShell ISE용 Comment-BasedHelp 조각을 만듭니다. `Comment-BasedHelp.snippets.ps1xml`사용자의 코드 조각 디렉터리에 이라는 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .

### 예제 2: 필수 코드 조각 만들기

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

이 예제에서는 Windows PowerShell ISE에 대 한 **필수** 라는 코드 조각을 만듭니다. 첫 번째 명령은 조각 텍스트를 변수에 저장 합니다 `$M` . 두 번째 명령은 cmdlet을 사용 하 여 `New-ISESnippet` 코드 조각을 만듭니다. 이 명령은 **Force** 매개 변수를 사용하여 이전 조각을 같은 이름으로 덮어씁니다.

### 예 3: 폴더의 필수 코드 조각을 대상 폴더로 복사

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

이 명령은 cmdlet을 사용 하 여 `Copy-Item` Server\Share 파일 공유에 배치 하는 폴더에서 **필수** 코드 조각을 복사 `New-ISESnippet` 합니다.

## PARAMETERS

### -작성자

코드 조각의 작성자를 지정 합니다. 작성자 필드는 조각 파일에 나타나지만 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타나지 않습니다.

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

### -CaretOffset

이 cmdlet이 커서를 배치할 조각 텍스트의 문자를 지정 합니다. 커서 위치를 나타내는 정수를 입력합니다. 여기서 "1"은 텍스트의 첫 번째 문자를 나타냅니다. 기본값 0(영)은 커서를 텍스트의 첫 번째 문자 바로 앞에 둡니다. 이 매개 변수는 조각 텍스트를 들여쓰지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

조각에 대 한 설명을 지정 합니다. 설명 값은 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타납니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 cmdlet이 같은 위치에 있는 동일한 이름의 조각 파일을 덮어쓰도록 지정 합니다. 기본적으로는 `New-ISESnippet` 파일을 덮어쓰지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -텍스트

조각을 선택할 때 추가되는 텍스트 값을 지정합니다. 조각 텍스트는 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타납니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

조각의 제목 또는 이름을 지정합니다. 제목은 조각 파일의 이름도 지정합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

`New-IseSnippet` types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다. 따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션에 이러한 조각을 추가할 수 없습니다. **Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.

`New-IseSnippet` **제한** 된 또는 **AllSigned** 세션에서 cmdlet을 사용 하는 경우 코드 조각이 만들어지지만 Windows PowerShell에서 새로 만든 코드 조각을 세션에 추가 하려고 할 때 오류 메시지가 나타납니다. 새 조각과 사용자가 만든 서명되지 않은 다른 조각을 사용하려면 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작합니다.

Windows PowerShell 실행 정책에 대한 자세한 내용은 about_Execution_Policies(영문)를 참조하세요.

- 코드 조각을 변경 하려면 조각 파일을 편집 합니다. Windows PowerShell ISE의 스크립트 창에서 조각 파일을 편집할 수 있습니다.
- 추가한 코드 조각을 삭제 하려면 조각 파일을 삭제 합니다.
- 기본 제공 코드 조각은 삭제할 수 없지만 "$psise를 사용 하 여 모든 기본 제공 코드 조각을 숨길 수 있습니다. Options. ShowDefaultSnippets = $false "명령입니다.
- 기본 제공 코드 조각과 동일한 이름을 가진 코드 조각을 만들 수 있습니다. 두 조각 모두 Windows PowerShell ISE의 조각 메뉴에 나타납니다.

## 관련 링크

[Get-IseSnippet](Get-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
