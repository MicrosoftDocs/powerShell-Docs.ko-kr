---
description: 고급 함수에서 매개 변수 집합을 정의 하 고 사용 하는 방법을 설명 합니다.
title: about_Parameter_Sets
Locale: en-US
ms.date: 01/05/2021
ms.openlocfilehash: 6163fd7e3e2d4493dc6f751599ac500fa4524f9e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194215"
---
# <a name="about-parameter-sets"></a>매개 변수 집합 정보

## <a name="short-description"></a>간단한 설명
고급 함수에서 매개 변수 집합을 정의 하 고 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell은 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대해 다른 작업을 수행할 수 있는 단일 함수를 작성할 수 있도록 합니다. 매개 변수 집합을 사용 하면 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다. 사용자가 지정한 매개 변수를 기반으로 다른 정보를 반환 하는 데 사용 됩니다.

## <a name="parameter-set-requirements"></a>매개 변수 집합 요구 사항

모든 매개 변수 집합에는 다음 요구 사항이 적용 됩니다.

- 각 매개 변수 집합은 고유한 매개 변수 조합을 포함 해야 합니다. 가능 하면 고유한 매개 변수 중 하나 이상이 필수 매개 변수 여야 합니다.

- 여러 위치 매개 변수를 포함 하는 매개 변수 집합은 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다. 두 위치 매개 변수는 같은 위치를 지정할 수 없습니다.

- 집합에 있는 하나의 매개 변수만 `ValueFromPipeline` 값을 사용 하 여 키워드를 선언할 수 있습니다 `true` . 여러 매개 변수는 `ValueFromPipelineByPropertyName` 값을 사용 하 여 키워드를 정의할 수 있습니다 `true` .

- 매개 변수에 대 한 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.

> [!NOTE]
> 매개 변수 집합은 32 개로 제한 됩니다.

## <a name="default-parameter-sets"></a>기본 매개 변수 집합

여러 매개 변수 집합을 정의 하는 경우 `DefaultParameterSetName` **cmdletbinding** 특성의 키워드는 기본 매개 변수 집합을 지정 합니다.
PowerShell은 명령에 제공 된 정보를 기반으로 사용할 매개 변수 집합을 확인할 수 없을 때 기본 매개 변수 집합을 사용 합니다. **Cmdletbinding** 특성에 대 한 자세한 내용은 [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)를 참조 하세요.

## <a name="declaring-parameter-sets"></a>매개 변수 집합 선언

매개 변수 집합을 만들려면 매개 변수 `ParameterSetName` 집합의 모든 매개 변수에 대 **한 매개 변수** 특성의 키워드를 지정 해야 합니다. 여러 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 **매개 변수** 특성을 추가 합니다.

매개 **변수 특성을** 사용 하면 매개 변수 집합 마다 매개 변수를 다르게 정의할 수 있습니다. 예를 들어 매개 변수를 한 집합에서 필수로 정의 하 고 다른 집합에서는 선택적으로 정의할 수 있습니다. 그러나 각 매개 변수 집합은 하나 이상의 고유 매개 변수를 포함 해야 합니다.

매개 변수 집합 이름이 할당 되지 않은 매개 변수는 모든 매개 변수 집합에 속합니다.

### <a name="example"></a>예

다음 예제 함수는 텍스트 파일의 숫자 줄, 문자 및 단어 수를 계산 합니다. 매개 변수를 사용 하 여 반환할 값과 측정 하려는 파일을 지정할 수 있습니다. 다음 네 가지 매개 변수 집합이 정의 되어 있습니다.

- 경로
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

각 매개 변수 집합은 고유한 매개 변수 또는 고유한 매개 변수 조합을 포함 해야 합니다. `Path`및 `PathAll` 매개 변수 집합은 매우 유사 하지만 **All** 매개 변수는 `PathAll` 매개 변수 집합에 대해 고유 합니다. `LiteralPath`및 매개 변수 집합에도 마찬가지입니다 `LiteralPathAll` . `PathAll`및 매개 변수 집합에 모두 `LiteralPathAll` 매개 변수가 있는 경우에도 **Path** 및 **LiteralPath** 매개 변수는이를 구분 합니다. 

사용은 `Get-Command -Syntax` 각 매개 변수 집합의 구문을 보여 줍니다. 그러나 매개 변수 집합의 이름은 표시 되지 않습니다. 다음 예에서는 각 매개 변수 집합에 사용할 수 있는 매개 변수를 보여 줍니다.

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>작업 중인 매개 변수 집합

이 예제에서는 `PathAll` 매개 변수 집합을 사용 합니다.

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
