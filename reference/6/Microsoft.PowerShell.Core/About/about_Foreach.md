---
description: 항목 컬렉션의 모든 항목을 트래버스하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: b5f09785fbf1fa8c3c14d287efc7cf5fed2d18eb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221626"
---
# <a name="about-foreach"></a>ForEach 정보

## <a name="short-description"></a>간단한 설명
항목 컬렉션의 모든 항목을 트래버스하는 데 사용할 수 있는 언어 명령을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`Foreach`문 (루프 라고도 함)은 `Foreach` 항목 컬렉션의 일련의 값을 단계별로 실행 (반복) 하는 언어 구문입니다.

트래버스할 가장 간단 하 고 가장 일반적인 컬렉션 형식은 배열입니다.
루프 내에서 `Foreach` 배열의 각 항목에 대해 하나 이상의 명령을 실행 하는 것이 일반적입니다.

## <a name="syntax"></a>구문

다음은 구문을 보여 줍니다 `ForEach` .

```
foreach ($<item> in $<collection>){<statement list>}
```

`ForEach`괄호 안에 있는 문의 부분은 변수와 반복할 컬렉션을 나타냅니다. PowerShell `$<item>` 은 루프가 실행 될 때 변수를 자동으로 만듭니다 `Foreach` . 루프를 반복 하기 전에 변수는 컬렉션의 값으로 설정 됩니다.
문 뒤의 블록에는 `Foreach` `{<statement list>}` 컬렉션의 각 항목에 대해 실행할 명령 집합이 포함 되어 있습니다.

### <a name="examples"></a>예

예를 들어 `Foreach` 다음 예제의 루프는 배열의 값을 표시 합니다 `$letterArray` .

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

이 예제에서는 `$letterArray` 배열이 생성 되 고 문자열 값,, 및를 사용 하 여 초기화 됩니다 `"a"` `"b"` `"c"` `"d"` . `Foreach`문이 처음 실행 될 때 `$letter` 변수는 ()의 첫 번째 항목으로 설정 `$letterArray` `"a"` 됩니다. 그런 다음 cmdlet을 사용 하 여 `Write-Host` 문자 a를 표시 합니다. 다음 번에 루프를 통해를로 `$letter` 설정 `"b"` 합니다. 루프에서 `Foreach` 문자 d를 표시 한 후 PowerShell은 루프를 종료 합니다.

`Foreach`PowerShell 명령 프롬프트에서 명령으로 실행 하려면 전체 문이 한 줄에 표시 되어야 합니다. `Foreach`대신 ps1 스크립트 파일에 명령을 추가 하는 경우 전체 문이 한 줄에 표시 되지 않아도 됩니다.

`Foreach` 문을 항목 컬렉션을 반환 하는 cmdlet과 함께 사용할 수도 있습니다. 다음 예에서는 Foreach 문이 cmdlet에 의해 반환 되는 항목 목록을 단계별로 안내 합니다 `Get-ChildItem` .

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

문을 사용 하 여 반환 되는 결과를 제한 하 여 예제를 구체화할 수 있습니다 `If` . 다음 예제에서 `Foreach` 문은 이전 예제와 동일한 반복 작업을 수행 하지만, `If` 결과를 100 kb 보다 큰 파일로 제한 하는 문을 추가 합니다.

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

이 예에서 `Foreach` 루프는 변수의 속성을 사용 하 여 `$file` 비교 작업을 수행 `$file.length -gt 100KB` 합니다 (). 변수는 cmdlet에서 반환 되는 `$file` 개체의 모든 속성을 포함 합니다 `Get-ChildItem` . 따라서 단순히 파일 이름 이상의 이름을 반환할 수 있습니다.
다음 예제에서 PowerShell은 문 목록 내에서의 길이와 마지막 액세스 시간을 반환 합니다.

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

이 예에서는 문 목록에서 단일 명령을 실행 하는 것으로 제한 되지 않습니다.

루프 외부에서 변수를 사용 하 `Foreach` 고 루프 내에서 변수를 증가 시킬 수도 있습니다. 다음 예제에서는 크기가 100 KB를 초과 하는 파일 수를 계산 합니다.

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

위의 예제에서 `$i` 변수는 루프 외부로 설정 되 `0` 고, 발견 된 각 파일에 대 한 루프 내에서 100 보다 큰 변수가 증가 합니다. 루프가 종료 되 면 `If` 문은의 값을 평가 하 여 `$i` 100 KB를 초과 하는 모든 파일의 수를 표시 합니다. 또는 100 KB 이상의 파일이 없다는 메시지를 표시 합니다.

이전 예제에서는 파일 길이 결과의 형식을 지정 하는 방법도 보여 줍니다.

```powershell
($file.length / 1024).ToString("F0")
```

값은 1024로 나뉘어 결과를 바이트 대신 킬로바이트 단위로 표시 하 고 결과 값은 고정 소수점 서식 지정자를 사용 하 여 형식 지정 된 후 결과에서 10 진수 값을 제거 합니다. 0을 지정 하면 형식 지정자에 소수 자릿수가 표시 되지 않습니다.

다음 예제에서 정의 된 함수는 PowerShell 스크립트 및 스크립트 모듈을 구문 분석 하 고 내에 포함 된 함수의 위치를 반환 합니다. 이 예제에서는 메서드를 사용 하는 방법 `MoveNext` (루프에서와 유사 하 게 작동 함 `skip X` `For` )과 `Current` `$foreach` foreach 스크립트 블록 내의 변수 속성을 사용 하는 방법을 보여 줍니다. 예제 함수는 여러 줄에 걸쳐 있는 함수 정의가 비정상적 이거나 일관 되지 않은 경우에도 스크립트에서 함수를 찾을 수 있습니다.

자세한 내용은 [열거자 사용](about_Automatic_Variables.md#using-enumerators)을 참조 하세요.

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
