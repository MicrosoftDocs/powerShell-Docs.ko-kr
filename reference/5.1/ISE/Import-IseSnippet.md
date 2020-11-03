---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212385"
---
# Import-IseSnippet

## 개요
ISE 조각을 현재 세션으로 가져옵니다.

## SYNTAX

### FromFolder (기본값)

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### FromModule

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## 설명

`Import-IseSnippet`Cmdlet은 다시 사용할 수 있는 텍스트 "조각"을 모듈 또는 디렉터리에서 현재 세션으로 가져옵니다. 코드 조각은 Windows PowerShell ISE에서 바로 사용할 수 있습니다. 이 cmdlet은 Windows PowerShell ISE (통합 스크립팅 환경) 에서만 작동 합니다.

가져온 조각을 보고 사용 하려면 Windows PowerShell ISE **편집** 메뉴에서 **코드 조각 시작** 을 클릭 하거나 <kbd>ctrl</kbd> + <kbd>J</kbd>를 누릅니다.

가져온 조각은 현재 세션에서만 사용할 수 있습니다. 코드 조각을 모든 Windows PowerShell ISE 세션으로 가져오려면 `Import-IseSnippet` Windows PowerShell 프로필에 명령을 추가 하거나 조각 파일을 로컬 코드 조각 디렉터리에 복사 `$home\Documents\WindowsPowershell\Snippets` 합니다.

코드 조각을 가져오려면 코드 조각 XML에서 Windows PowerShell ISE 코드 조각을 적절히 지정 하 고 Snippet.ps1XML 파일에 저장 해야 합니다. 적격 코드 조각을 만들려면 cmdlet을 사용 `New-IseSnippet` 합니다. `New-IseSnippet``<SnippetTitle>.Snippets.ps1xml`디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` . 조각을 Windows PowerShell 모듈의 Snippets 디렉터리나 다른 디렉터리로 이동하거나 복사할 수 있습니다.

`Get-IseSnippet`로컬 코드 조각 디렉터리에서 사용자가 만든 코드 조각을 가져오는 cmdlet은 가져온 조각을 가져오지 않습니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 디렉터리에서 조각 가져오기

이 예제에서는 디렉터리의 조각을 `\\Server01\Public\Snippets` 현재 세션으로 가져옵니다. **재귀** 매개 변수를 사용 하 여 조각 디렉터리의 모든 하위 디렉터리에서 조각을 가져옵니다.

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### 예제 2: 모듈에서 조각 가져오기

이 예제에서는 **SnippetModule** 모듈에서 조각을 가져옵니다. 명령이 실행 될 때 **SnippetModule** 모듈을 사용자의 세션으로 가져오지 않은 경우에도이 명령은 **ListAvailable** 매개 변수를 사용 하 여 코드 조각을 가져옵니다.

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### 예제 3: 모듈의 조각 찾기

이 예제에서는 PSModulePath 환경 변수에 설치 된 모든 모듈의 조각을 가져옵니다.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### 예제 4: 모든 모듈 코드 조각 가져오기

이 예제에서는 설치 된 모든 모듈의 모든 조각을 현재 세션으로 가져옵니다. 일반적으로 코드 조각이 있는 모듈은 `Import-IseSnippet` 모듈을 가져올 때 cmdlet을 사용 하 여이를 가져오기 때문에 다음과 같은 명령을 실행할 필요가 없습니다.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### 예 5: 모든 모듈 조각 복사

이 예제에서는 설치 된 모든 모듈의 조각 파일을 현재 사용자의 조각 디렉터리에 복사 합니다. 현재 세션에만 영향을 주는 가져온 조각과 달리 복사된 조각은 모든 Windows PowerShell ISE 세션에서 사용할 수 있습니다.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## PARAMETERS

### -ListAvailable

이 cmdlet은 모듈을 현재 세션으로 가져오지 않은 경우에도 컴퓨터에 설치 된 모듈에서 조각을 가져옵니다. 이 매개 변수를 생략 하 고 **module** 매개 변수에 지정 된 모듈을 현재 세션으로 가져오지 않은 경우 모듈에서 코드 조각을 가져오지 못했습니다.

이 매개 변수는 **Module** 매개 변수가 명령에 사용된 경우에만 유효합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -모듈

지정된 모듈의 조각을 현재 세션으로 가져옵니다. 와일드카드 문자는 지원되지 않습니다.

이 매개 변수는와 같은 모듈 경로에 있는 코드 조각 하위 디렉터리에 있는 Snippet.ps1xml 파일에서 조각을 가져옵니다 `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .

이 매개 변수는 모듈 작성자가 시작 스크립트(예: 모듈 매니페스트의 **ScriptsToProcess** 키에 지정된 스크립트)에 사용하도록 설계되었습니다. 모듈의 조각은 모듈을 사용 하 여 자동으로 가져오지 않지만 명령을 사용 하 여 가져올 수 있습니다 `Import-IseSnippet` .

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

이 cmdlet이 조각을 가져오는 조각 디렉터리의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -재귀

이 cmdlet은 **Path** 매개 변수 값의 모든 하위 디렉터리에서 조각을 가져오도록 지정 합니다.

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

### 없음

이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.

## 출력

### 없음

이 cmdlet은 출력을 생성하지 않습니다.

## 참고

- `Get-IseSnippet`가져온 코드 조각은 cmdlet을 사용 하 여 가져올 수 없습니다. `Get-IseSnippet` 디렉터리의 조각만 가져옵니다 `$home\Documents\WindowsPowerShell\Snippets` .
- `Import-IseSnippet`**ISESnippetCollection** 개체의 **Load** 정적 메서드를 사용 합니다. Windows PowerShell ISE 개체 모델에서 코드 조각의 **Load** 메서드를 사용할 수도 있습니다. `$psISE.CurrentPowerShellTab.Snippets.Load()`
- `New-IseSnippet`Cmdlet은 types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다. 따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션으로 이러한 조각을 로드할 수 없습니다. **Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.

  Cmdlet에서 반환 하는 서명 되지 않은 사용자 생성 코드 조각을 사용 하려면 `Import-IseSnippet` 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작 합니다.

  Windows PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)(영문)를 참조하세요.

## 관련 링크

[Get-IseSnippet](Get-IseSnippet.md)

[New-IseSnippet](New-IseSnippet.md)
