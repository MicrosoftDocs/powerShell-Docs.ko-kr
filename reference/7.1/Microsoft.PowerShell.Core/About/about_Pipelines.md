---
description: PowerShell에서 파이프라인으로 명령 결합
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: ca933e7e130959ef725d760d859ca43b99bdfc76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222025"
---
# <a name="about-pipelines"></a>파이프라인 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 파이프라인으로 명령 결합

## <a name="long-description"></a>자세한 설명입니다.

파이프라인은 파이프라인 연산자 ( `|` ) (ASCII 124)로 연결 되는 일련의 명령입니다. 각 파이프라인 연산자는 이전 명령의 결과를 다음 명령으로 보냅니다.

첫 번째 명령의 출력은 처리를 위해 두 번째 명령에 대 한 입력으로 보낼 수 있습니다. 그리고 해당 출력을 다른 명령으로 보낼 수도 있습니다. 결과는 일련의 간단한 명령으로 구성 된 복잡 한 명령 체인 또는 _파이프라인_ 입니다.

예를 들면 다음과 같습니다.

```powershell
Command-1 | Command-2 | Command-3
```

이 예제에서는 `Command-1` 를 내보내는 개체가로 보내집니다 `Command-2` .
`Command-2` 개체를 처리 하 고로 보냅니다 `Command-3` . `Command-3` 개체를 처리 하 고 파이프라인으로 보냅니다. 파이프라인에 명령이 더 이상 없으므로 결과가 콘솔에 표시 됩니다.

파이프라인에서 명령은 왼쪽에서 오른쪽 순서로 처리 됩니다. 처리는 단일 작업으로 처리 되 고 출력은 생성 될 때 표시 됩니다.

다음은 간단한 예제입니다. 다음 명령은 메모장 프로세스를 가져온 다음 중지 합니다.

예를 들면 다음과 같습니다.

```powershell
Get-Process notepad | Stop-Process
```

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 메모장 프로세스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보내면이 `Stop-Process` Cmdlet이 메모장 프로세스를 중지 합니다. `Stop-Process`지정 된 프로세스가 파이프라인을 통해 전송 되기 때문에이 명령에는 프로세스를 지정 하기 위한 **이름** 또는 **ID** 매개 변수가 없습니다.

이 파이프라인 예제에서는 현재 디렉터리에 있는 텍스트 파일을 가져오고, 1만 바이트 보다 긴 파일만 선택 하 고, 길이를 기준으로 정렬 하 고, 테이블에 있는 각 파일의 이름과 길이를 표시 합니다.

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

이 파이프라인은 지정 된 순서 대로 4 개의 명령으로 구성 됩니다. 다음 그림에서는 파이프라인의 다음 명령에 전달 되는 각 명령의 출력을 보여 줍니다.

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>파이프라인 사용

대부분의 PowerShell cmdlet은 파이프라인을 지원 하도록 설계 되었습니다. 대부분의 경우 **Get** cmdlet의 결과를 동일한 명사의 다른 cmdlet으로 _파이프_ 할 수 있습니다.
예를 들어 cmdlet의 출력을 `Get-Service` 또는 cmdlet으로 파이프 할 수 `Start-Service` 있습니다 `Stop-Service` .

이 예제 파이프라인은 컴퓨터에서 WMI 서비스를 시작 합니다.

```powershell
Get-Service wmi | Start-Service
```

또 다른 예로 `Get-Item` PowerShell 레지스트리 공급자 내 또는의 출력을 `Get-ChildItem` cmdlet으로 파이프 할 수 있습니다 `New-ItemProperty` . 이 예제에서는 값이 **8124** 인 **noofemployees** 라는 새 레지스트리 항목을 **MyCompany** 레지스트리 키에 추가 합니다.

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

,,, 및와 같은 유틸리티 cmdlet은 대부분 `Get-Member` `Where-Object` `Sort-Object` `Group-Object` `Measure-Object` 파이프라인 에서만 거의 사용 됩니다. 모든 개체 유형을 이러한 cmdlet으로 파이프 할 수 있습니다. 이 예에서는 각 프로세스에서 열린 핸들 수를 기준으로 컴퓨터의 모든 프로세스를 정렬 하는 방법을 보여 줍니다.

```powershell
Get-Process | Sort-Object -Property handles
```

,,, 및와 같은 개체를 형식 지정, 내보내기 및 출력 cmdlet으로 파이프 할 수 있습니다 `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` `Out-File` .

이 예에서는 cmdlet을 사용 하 여 `Format-List` 프로세스 개체의 속성 목록을 표시 하는 방법을 보여 줍니다.

```powershell
Get-Process winlogon | Format-List -Property *
```

약간의 연습을 통해 간단한 명령을 파이프라인으로 결합 하 여 시간을 절약 하 고 입력 한 다음 스크립팅을 보다 효율적으로 만들 수 있습니다.

## <a name="how-pipelines-work"></a>파이프라인 작동 방법

이 섹션에서는 입력 개체가 cmdlet 매개 변수에 바인딩되어 파이프라인 실행 중에 처리 되는 방법에 대해 설명 합니다.

### <a name="accepts-pipeline-input"></a>파이프라인 입력 허용

파이프라인을 지원 하려면 수신 cmdlet에 파이프라인 입력을 허용 하는 매개 변수가 있어야 합니다. `Get-Help`명령을 **Full** 또는 **Parameter** 옵션과 함께 사용 하 여 파이프라인 입력을 허용 하는 cmdlet의 매개 변수를 확인 합니다.

예를 들어 파이프라인 입력을 허용 하는 cmdlet의 매개 변수를 확인 하려면 `Start-Service` 다음을 입력 합니다.

```powershell
Get-Help Start-Service -Full
```

또는

```powershell
Get-Help Start-Service -Parameter *
```

Cmdlet에 대 한 도움말에서는 `Start-Service` **InputObject** 및 **Name** 매개 변수만 파이프라인 입력을 허용 한다는 것을 보여 줍니다.

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

파이프라인을 통해 개체를로 보내면 `Start-Service` PowerShell에서 개체를 **InputObject** 및 **Name** 매개 변수와 연결 하려고 시도 합니다.

### <a name="methods-of-accepting-pipeline-input"></a>파이프라인 입력을 허용 하는 메서드

Cmdlet 매개 변수는 다음 두 가지 방법 중 하나로 파이프라인 입력을 허용할 수 있습니다.

- **Byvalue** : 매개 변수는 예상 되는 .net 유형과 일치 하거나 해당 형식으로 변환할 수 있는 값을 허용 합니다.

  예를 들어의 **Name** 매개 변수는 `Start-Service` 값으로 파이프라인 입력을 허용 합니다. 문자열로 변환할 수 있는 문자열 개체 또는 개체를 사용할 수 있습니다.

- **Bypropertyname** : 매개 변수는 입력 개체에 매개 변수와 이름이 같은 속성이 있는 경우에만 입력을 허용 합니다.

  예를 들어의 Name 매개 변수는 `Start-Service` **name** 속성이 있는 개체를 허용할 수 있습니다. 개체의 속성을 나열 하려면로 파이프 `Get-Member` 합니다.

일부 매개 변수는 값 이나 속성 이름을 사용 하 여 개체를 받아들일 수 있으므로 파이프라인에서 더 쉽게 입력할 수 있습니다.

### <a name="parameter-binding"></a>매개 변수 바인딩

한 명령에서 다른 명령으로 개체를 파이프 하면 PowerShell에서 파이프 된 개체를 수신 cmdlet의 매개 변수와 연결 하려고 시도 합니다.

PowerShell의 매개 변수 바인딩 구성 요소는 다음 기준에 따라 입력 개체를 cmdlet 매개 변수와 연결 합니다.

- 매개 변수는 파이프라인의 입력을 허용 해야 합니다.
- 매개 변수는 전송 되는 개체의 형식 또는 필요한 형식으로 변환할 수 있는 형식을 수락 해야 합니다.
- 매개 변수가 명령에 사용 되지 않았습니다.

예를 들어 `Start-Service` cmdlet은 많은 매개 변수를 포함 하지만, **이름** 및 **InputObject** 는 파이프라인 입력을 허용 합니다. **Name** 매개 변수는 문자열을 사용 하 고 **InputObject** 매개 변수는 서비스 개체를 사용 합니다. 따라서 문자열, 서비스 개체 및 개체를 문자열 또는 서비스 개체로 변환할 수 있는 속성으로 파이프 할 수 있습니다.

PowerShell은 매개 변수 바인딩을 최대한 효율적으로 관리 합니다. PowerShell이 특정 매개 변수에 바인딩되도록 제안 하거나 강제할 수 없습니다. PowerShell에서 파이프 된 개체를 바인딩할 수 없는 경우 명령이 실패 합니다.

바인딩 오류 문제 해결에 대 한 자세한 내용은이 문서의 뒷부분에 나오는 [파이프라인 오류 조사](#investigating-pipeline-errors) 를 참조 하세요.

### <a name="one-at-a-time-processing"></a>일회성 (일회성) 처리

개체를 명령으로 파이프 하는 것은 명령의 매개 변수를 사용 하 여 개체를 제출 하는 것과 매우 비슷합니다. 파이프라인 예제를 살펴보겠습니다. 이 예제에서는 파이프라인을 사용 하 여 서비스 개체의 테이블을 표시 합니다.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

기능적으로의 **InputObject** 매개 변수를 사용 하 여 개체 컬렉션을 제출 하는 것과 같습니다 `Format-Table` .

예를 들어 **InputObject** 매개 변수를 사용 하 여 전달 된 변수에 서비스 컬렉션을 저장할 수 있습니다.

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

또는 **InputObject** 매개 변수에 명령을 포함할 수 있습니다.

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

그러나 중요 한 차이점이 있습니다. 여러 개체를 명령으로 파이프 하면 PowerShell에서 한 번에 하나씩 명령에 개체를 보냅니다. 명령 매개 변수를 사용 하는 경우 개체는 단일 배열 개체로 전송 됩니다. 이러한 사소한 차이로 인해 상당한 결과가 발생 합니다.

파이프라인을 실행 하는 경우 PowerShell은 인터페이스를 구현 하는 모든 형식을 자동으로 열거 `IEnumerable` 하 고 파이프라인을 통해 한 번에 하나씩 멤버를 보냅니다. 예외는입니다 .이 경우에는 `[hashtable]` 메서드를 호출 해야 `GetEnumerator()` 합니다.

다음 예제에서는 배열과 해시 테이블을 cmdlet으로 파이프 하 여 `Measure-Object` 파이프라인에서 받은 개체 수를 계산 합니다. 배열에 여러 멤버가 있고 해시 테이블에 여러 개의 키-값 쌍이 있습니다. 배열에 한 번에 하나씩만 열거 됩니다.

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

마찬가지로, cmdlet에서 cmdlet으로 여러 프로세스 개체를 파이프 하는 경우 `Get-Process` `Get-Member` PowerShell은 각 프로세스 개체를 한 번에 하나씩로 보냅니다 `Get-Member` . `Get-Member` 프로세스 개체의 .NET 클래스 (형식)와 해당 속성 및 메서드를 표시 합니다.

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` 중복을 제거 하므로 개체가 모두 동일한 형식이 면 하나의 개체 유형만 표시 됩니다.

그러나의 **InputObject** 매개 변수를 사용 하는 경우은 (는) `Get-Member` `Get-Member` 단일 단위로 **시스템 진단** 개체의 배열을 받습니다. 개체의 배열 속성을 표시 합니다. (System.string 형식 이름 뒤의 배열 기호 ()를 적어둡니다 `[]` .) **System.Object**

예를 들면 다음과 같습니다.

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

이 결과는 의도 한 것과 다를 수 있습니다. 그러나 이해 한 후에는 사용할 수 있습니다. 예를 들어 모든 배열 개체에는 **Count** 속성이 있습니다. 이를 사용 하 여 컴퓨터에서 실행 되는 프로세스 수를 계산할 수 있습니다.

예를 들면 다음과 같습니다.

```powershell
(Get-Process).count
```

파이프라인으로 전송 되는 개체는 한 번에 하나씩 배달 된다는 점을 기억해 야 합니다.

## <a name="investigating-pipeline-errors"></a>파이프라인 오류 조사

PowerShell에서 파이프 된 개체를 수신 cmdlet의 매개 변수와 연결할 수 없는 경우 명령이 실패 합니다.

다음 예제에서는 레지스트리 키 간에 레지스트리 항목을 이동 하려고 합니다. `Get-Item`Cmdlet은 대상 경로를 가져온 다음 cmdlet에 파이프 합니다 `Move-ItemProperty` . `Move-ItemProperty`명령은 이동할 레지스트리 항목의 현재 경로 및 이름을 지정 합니다.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

명령이 실패 하 고 PowerShell에서 다음과 같은 오류 메시지를 표시 합니다.

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

조사 하려면 cmdlet을 사용 `Trace-Command` 하 여 PowerShell의 매개 변수 바인딩 구성 요소를 추적 합니다. 다음 예제에서는 파이프라인이 실행 되는 동안 매개 변수 바인딩을 추적 합니다. **PSHost** 매개 변수는 콘솔에 추적 결과를 표시 하 고 **FilePath** 매개 변수는 나중에 참조할 수 있도록 추적 결과를 `debug.txt` 파일로 보냅니다.

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

추적 결과는 긴 하지만 cmdlet에 바인딩되는 값을 표시 한 `Get-Item` 다음 cmdlet에 바인딩되는 명명 된 값을 표시 합니다 `Move-ItemProperty` .

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

마지막으로 경로를의 **대상** 매개 변수에 바인딩하려는 시도가 실패 한 것을 보여 줍니다 `Move-ItemProperty` .

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

Cmdlet을 사용 `Get-Help` 하 여 **Destination** 매개 변수의 특성을 볼 수 있습니다.

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

결과는 **대상** 에서 파이프라인 입력만 "속성 이름"으로 사용 함을 보여 줍니다. 따라서 파이프 된 개체에는 **Destination** 이라는 속성이 있어야 합니다.

`Get-Member`에서 들어오는 개체의 속성을 보려면를 사용 `Get-Item` 합니다.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

출력은 항목이 **대상** 속성이 없는 **Microsoft Win32 RegistryKey** 개체 임을 보여 줍니다. 명령이 실패 한 이유를 설명 하는입니다.

**Path** 매개 변수는 이름이 나 값을 기준으로 파이프라인 입력을 허용 합니다.

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

명령을 수정 하려면 cmdlet에서 대상을 지정 하 `Move-ItemProperty` 고를 사용 `Get-Item` 하 여 이동 하려는 항목의 **경로** 를 가져와야 합니다.

예를 들면 다음과 같습니다.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>내장 선 연속

앞서 설명한 것 처럼 파이프라인은 `|` 일반적으로 단일 줄로 작성 된 파이프라인 연산자 ()로 연결 되는 일련의 명령입니다. 그러나 가독성을 위해 PowerShell을 사용 하면 파이프라인을 여러 줄로 분할할 수 있습니다.
파이프 연산자가 줄의 마지막 토큰이 면 PowerShell 파서는 다음 줄을 현재 명령에 조인 하 여 파이프라인 생성을 계속 합니다.

예를 들어 다음 한 줄 파이프라인이 있습니다.

```powershell
Command-1 | Command-2 | Command-3
```

다음과 같이 작성할 수 있습니다.

```powershell
Command-1 |
  Command-2 |
    Command-3
```

후속 줄의 선행 공백은 중요 하지 않습니다. 들여쓰기는 가독성을 향상 시킵니다.

PowerShell 7은 줄의 시작 부분에 파이프라인 문자를 사용 하 여 파이프라인의 연속에 대 한 지원을 추가 합니다. 다음 예에서는이 새 기능을 사용 하는 방법을 보여 줍니다.

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> 셸에서 대화형으로 작업 하는 경우 <kbd>Ctrl</kbd>V를 사용 하 여 붙여 넣는 경우에만 줄의 시작 부분에 파이프라인을 사용 하 여 코드를 붙여 + <kbd>V</kbd> 넣습니다.
> 붙여넣기 작업을 마우스 오른쪽 단추로 클릭 하면 한 번에 하나씩 줄이 삽입 됩니다. 줄이 파이프라인 문자로 끝나지 않으므로 PowerShell은 입력을 완료 한 것으로 간주 하 고 입력 한 대로 해당 줄을 실행 합니다.

## <a name="see-also"></a>참고 항목

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)

