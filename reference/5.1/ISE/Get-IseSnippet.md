---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218105"
---
# Get-IseSnippet

## 개요
사용자가 만든 조각을 가져옵니다.

## SYNTAX

```
Get-IseSnippet [<CommonParameters>]
```

## 설명

`Get-IseSnippet`Cmdlet은 사용자가 만든 재사용 가능한 텍스트 조각을 포함 하는 types.ps1xml 파일을 가져옵니다. Windows PowerShell ISE (통합 스크립팅 환경) 에서만 작동 합니다.

Cmdlet을 사용 하 여 `New-IseSnippet` 코드 조각을 만들 때는 `New-IseSnippet` `<SnippetTitle>.Snippets.ps1xml` 디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .
`Get-IseSnippet` 조각 디렉터리의 조각 파일을 가져옵니다.

이 cmdlet은 cmdlet을 통해 모듈에서 가져온 코드 조각 또는 조각을 기본으로 가져오지 않습니다 `Import-IseSnippet` .

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 모든 사용자 정의 코드 조각 가져오기

이 예제에서는 코드 조각 디렉터리의 모든 사용자 정의 조각을 가져옵니다.

```powershell
Get-IseSnippet
```

### 예제 2: 원격 컴퓨터의 모든 사용자 정의 조각을 공유 디렉터리에 복사

이 예제에서는 원격 컴퓨터 그룹의 사용자가 만든 모든 조각을 공유 코드 조각 디렉터리에 복사 합니다.

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

`Invoke-Command``Get-IseSnippet`파일의 컴퓨터에서 실행 됩니다 `Servers.txt` . 파이프라인 연산자 ( `|` )는 조각 파일을 cmdlet으로 전송 하 여 `Copy-Item` **Destination** 매개 변수로 지정 된 디렉터리에 복사 합니다.

### 예제 3: 로컬 컴퓨터에 각 조각의 제목 및 텍스트 표시

이 예제에서는 및 cmdlet을 사용 하 여 `Get-IseSnippet` `Select-Xml` 로컬 컴퓨터에 있는 각 조각의 제목과 텍스트를 표시 합니다.

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### 예제 4: 세션의 모든 조각에 대 한 제목 및 설명 표시

이 예제에서는 기본 제공 조각, 사용자 정의 조각 및 가져온 조각을 포함 하 여 세션에 있는 모든 조각의 제목 및 설명을 표시 합니다.

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

`$PSISE`변수는 Windows PowerShell ISE 호스트 프로그램을 나타냅니다. 변수의 **Currentpowershelltab** 속성은 `$PSISE` 현재 세션을 나타냅니다. **Snippets** 속성은 현재 세션의 조각을 나타냅니다.

`$PSISE.CurrentPowerShellTab.Snippets`이 명령은 cmdlet과 달리 코드 조각을 나타내는 **new-isesnippet** 개체를 반환 합니다. `Get-IseSnippet` `Get-IseSnippet` 조각 파일을 나타내는 파일 개체 (System.web)를 반환 합니다.

`Format-Table`Cmdlet은 테이블에 있는 코드 조각의 **displaytitle** 및 **Description** 속성을 표시 합니다.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### System.object

이 cmdlet은 조각 파일을 나타내는 file 개체를 반환 합니다.

## 참고

* `New-IseSnippet`Cmdlet은 types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다. 따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션에 이러한 조각을 추가할 수 없습니다. **Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.

  Cmdlet에서 반환 하는 서명 되지 않은 사용자 생성 코드 조각을 사용 하려면 `Get-IseSnippet` 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작 합니다.

  Windows PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)(영문)를 참조하세요.

## 관련 링크

[New-IseSnippet](New-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
