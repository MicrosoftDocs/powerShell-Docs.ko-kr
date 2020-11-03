---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: 8d99f861a9cbdc72d30975275c49c6cd5bde2bed
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211329"
---
# Export-ModuleMember

## 개요
내보내는 모듈 멤버를 지정합니다.

## SYNTAX

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## 설명

**Export-modulemember** cmdlet은 스크립트 모듈 (.psm1) 파일 또는 New-Module cmdlet을 사용 하 여 만든 동적 모듈에서 내보낸 모듈 멤버를 지정 합니다.
모듈 멤버에는 cmdlet, 함수, 변수 및 별칭이 포함 됩니다.
이 cmdlet은 스크립트 모듈 파일이나 동적 모듈에서만 사용할 수 있습니다.

스크립트 모듈에 **export-modulemember** 명령이 포함 되어 있지 않으면 스크립트 모듈의 함수 및 별칭을 내보내고 변수는 내보내지 않습니다.
스크립트 모듈에 **export-modulemember** 명령이 포함 된 경우 **export-modulemember** 명령에 지정 된 멤버만 내보내집니다.
**Export-modulemember** 를 사용 하 여 스크립트 모듈이 다른 모듈에서 가져오는 멤버를 표시 하지 않거나 내보낼 수도 있습니다.

**Export-modulemember** 명령은 선택 사항 이지만 모범 사례입니다.
명령에서 기본값을 확인하는 경우에도 모듈 작성자의 의도를 보여 줍니다.

## 예제

### 예제 1: 스크립트 모듈에서 함수 및 별칭 내보내기

```powershell
Export-ModuleMember -Function * -Alias *
```

이 명령은 스크립트 모듈에 정의 된 모든 함수 및 별칭을 내보냅니다.

### 예제 2: 특정 별칭 및 함수 내보내기

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

이 명령은 스크립트 모듈에 정의된 별칭 3개와 함수 3개를 내보냅니다.

이 명령 형식을 사용하여 모듈 멤버의 이름을 지정할 수 있습니다.

### 예제 3: 멤버 없음 내보내기

```powershell
Export-ModuleMember
```

이 명령은 스크립트 모듈에 정의된 멤버를 내보내지 않도록 지정합니다.

모듈 멤버를 내보내지 않도록 하지만 멤버를 숨기지는 않습니다.
사용자는 모듈 멤버를 읽고 복사하거나 호출 연산자(&)를 사용하여 내보내 지지 않는 모듈 멤버를 호출할 수 있습니다.

### 예제 4: 특정 변수 내보내기

```powershell
Export-ModuleMember -Variable increment
```

이 명령은 스크립트 모듈에서 $increment 변수만 내보내고
다른 멤버는 내보내지 않습니다.

모듈의 함수를 내보내는 것 외에도 변수를 내보내려는 경우 **export-modulemember** 명령에는 모든 함수의 이름과 변수의 이름이 포함 되어야 합니다.

### 예 5: 여러 내보내기 명령

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

이 명령은 스크립트 모듈 (.psm1) 파일에서 여러 **export-modulemember** 명령이 해석 되는 방법을 보여 줍니다.

함수 3개와 별칭 1개를 만든 다음 함수 2개와 별칭을 내보냅니다.

**Export-modulemember** 명령이 없으면 세 가지 함수와 별칭을 모두 내보냅니다.
**Export-modulemember** 명령을 사용 하면 **새 테스트** 및 **시작-테스트** 함수 및 STT 별칭을 내보낼 수 있습니다.

### 예제 6: 동적 모듈에서 멤버 내보내기

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

이 명령은 **새 모듈** cmdlet을 사용 하 여 만든 동적 모듈에서 Export-ModuleMember를 사용 하는 방법을 보여 줍니다.

이 예에서는 **export-modulemember** 를 사용 하 여 동적 모듈에서 Hi와 **SayHello** 함수를 모두 내보냅니다.

### 예제 7: 단일 명령에서 함수 선언 및 내보내기

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

이 예에는 함수를 **Export** 선언 하거나 변수를 만든 다음 `Export-ModuleMember` 함수 또는 변수에 대 한 명령을 작성 하는 Export 라는 함수가 포함 되어 있습니다.
이 함수를 사용하면 하나의 명령으로 함수 또는 변수를 선언하고 내보낼 수 있습니다.

**Export** 함수를 사용 하려면 스크립트 모듈에 포함 합니다.
함수를 내보내려면 `Export` **function** 키워드 앞에를 입력 합니다.

변수를 내보내려면 다음 형식을 사용하여 변수를 선언하고 변수 값을 설정합니다.

`Export variable <variable-name> <value>`

예제의 명령은 올바른 형식을 보여 줍니다.
이 예제에서는 **새-테스트** 함수 및 $Interval 변수만 내보냅니다.

## PARAMETERS

### -별칭

스크립트 모듈 파일에서 내보내는 별칭을 지정합니다.
별칭 이름을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Cmdlet

스크립트 모듈 파일에서 내보내는 cmdlet을 지정합니다.
cmdlet 이름을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

스크립트 모듈 파일에서 cmdlet을 만들 수는 없지만 이진 모듈의 cmdlet을 스크립트 모듈로 가져온 다음 스크립트 모듈에서 다시 내보낼 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -함수

스크립트 모듈 파일에서 내보내는 함수를 지정합니다.
함수 이름을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.
함수 이름 문자열을 **export-modulemember** 로 파이프 할 수도 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Variable

스크립트 모듈 파일에서 내보내는 변수를 지정합니다.
달러 기호 없이 변수 이름을 입력 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 함수 이름 문자열을 파이프 하 여 사용할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 내보낸 멤버 목록에서 멤버를 제외 하려면 다른 모든 멤버를 나열 하지만 제외 하려는 멤버를 생략 하는 **export-modulemember** 명령을 추가 합니다.

## 관련 링크

[Get-Module](Get-Module.md)

[모듈 가져오기](Import-Module.md)

[Remove-Module](Remove-Module.md)
