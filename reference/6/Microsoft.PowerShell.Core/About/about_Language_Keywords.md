---
description: PowerShell 스크립트 언어의 키워드에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 5e624feacd63bf4be4af4b31ae9879c3ab2e54c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221545"
---
# <a name="about-language-keywords"></a>언어 키워드 정보

## <a name="short-description"></a>간단한 설명
PowerShell 스크립트 언어의 키워드에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell에는 다음과 같은 언어 키워드가 있습니다. 자세한 내용은 키워드에 대 한 about 항목과 표 다음에 나오는 정보를 참조 하세요.

키워드     | 참조
---         | ---
시작       | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
중단       | [about_Break](about_Break.md), [about_Trap](about_Trap.md)
Catch       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
클래스       | [about_Classes](about_Classes.md)
계속    | [about_Continue](about_Continue.md), [about_Trap](about_Trap.md)
데이터        | [about_Data_Sections](about_Data_Sections.md)
정의      | 나중에 사용하도록 예약되어 있습니다.
수행          | [about_Do](about_Do.md), [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Else        | [about_If](about_If.md)
그렇지      | [about_If](about_If.md)
끝         | [about_Functions](about_Functions.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
열거형        | [about_Enum](about_Enum.md)
종료        | [이 항목에 설명 되어 있습니다.](#exit)
Assert      | [about_Functions](about_Functions.md)
Finally     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
For         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
보낸 사람        | 나중에 사용하도록 예약되어 있습니다.
함수    | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
숨김      | [about_Hidden](about_Hidden.md)
조건          | [about_If](about_If.md)
In(다음 안에)          | [about_ForEach](about_ForEach.md)
매개 변수       | [about_Functions](about_Functions.md)
프로세스     | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
반환 값      | [about_Return](about_Return.md)
정적      | [about_Classes](about_Classes.md)
스위치      | [about_Switch](about_Switch.md)
Throw       | [about_Throw](about_Throw.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Trap        | [about_Trap](about_Trap.md), [about_Break](about_Break.md), [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
시도해 보기         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
발생할       | [about_Do](about_Do.md)
사용       | [about_Using](about_Using.md), [about_Classes](about_Classes.md)
Var         | 나중에 사용하도록 예약되어 있습니다.
While       | [about_While](about_While.md), [about_Do](about_Do.md)

언어 키워드

### <a name="begin"></a>시작

`DynamicParam`, 및 키워드와 함께 함수 본문의 한 부분을 지정 합니다 `Process` `End` . `Begin`문 목록은 파이프라인에서 개체를 수신 하기 전에 한 번 실행 됩니다.

구문

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>중단

스크립트에서 루프가 종료 되도록 합니다.

구문

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>Catch

함께 제공 된 Try 문 목록에서 오류가 발생 하는 경우 실행할 문 목록을 지정 합니다. 오류 유형에는 대괄호가 필요 합니다. 두 번째 대괄호 쌍은 오류 유형이 optional 임을 나타냅니다.

구문

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>클래스

PowerShell에서 새 클래스를 지정 합니다.

구문

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>계속

스크립트를 실행 하 여 루프의 실행을 중지 하 고 조건으로 돌아갑니다. 조건을 충족 하는 경우 스크립트는 루프를 다시 시작 합니다.

구문

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>데이터

스크립트에서는 스크립트 논리에서 데이터를 격리 하는 섹션을 정의 합니다. `If`문과 몇 가지 제한 된 명령만 포함할 수 있습니다.

구문

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>수행

`While` `Until` 루프 구문으로 또는 키워드와 함께 사용 됩니다. PowerShell은에서 사용 하는 루프와 달리 문 목록을 한 번 이상 실행 `While` 합니다.

`While` 구문:

```Syntax
do {<statement list>} while (<condition>)
```

`Until` 구문:

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

`Begin`, 및 키워드와 함께 함수 본문의 한 부분을 지정 합니다 `Process` `End` . 동적 매개 변수는 런타임에 추가 됩니다.

구문

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Else

키워드와 함께 사용 되어 `If` 기본 문 목록을 지정 합니다.

구문

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>그렇지

`If` `Else` 추가 조건을 지정 하기 위해 및 키워드와 함께 사용 됩니다. `Else`키워드는 선택 사항입니다.

구문

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>끝

`DynamicParam`, 및 키워드와 함께 함수 본문의 한 부분을 지정 합니다 `Begin` `End` . `End`문 목록은 파이프라인에서 모든 개체를 받은 후 한 번 실행 됩니다.

구문

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>열거형

`enum` 는 열거형을 선언 하는 데 사용 됩니다. 열거자 목록 이라고 하는 명명 된 레이블 집합으로 구성 된 고유 형식입니다.

구문

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>종료

PowerShell에서 스크립트나 PowerShell 인스턴스를 종료 하도록 합니다.

구문

```Syntax
exit
exit <exitcode>
```

File 매개 변수와 함께를 사용 하는 경우 스크립트를 `pwsh` **File** `.ps1` 실행 하는 동안 발생 하는 오류 또는 예외를 처리 하기 위한 지침을 스크립트 파일 자체에 포함 해야 합니다. `exit`문을 사용 하 여 스크립트의 실행 후 상태를 나타내야 합니다.

Windows에서는와 사이의 숫자가 모두 `[int]::MinValue` `[int]::MaxValue` 허용 됩니다.

Unix에서는와 사이의 양수만 `[byte]::MinValue` `[byte]::MaxValue` 사용할 수 있습니다. `-1`부터 까지의 음수는 `-255` 256을 더하여 긍정 숫자로 자동으로 변환 됩니다. 예를 들어 `-2` 는로 변환 됩니다 `254` .

PowerShell에서 `exit` 문은 변수의 값을 설정 `$LASTEXITCODE` 합니다. Windows 명령 셸 (cmd.exe)에서 exit 문은 환경 변수의 값을 설정 합니다 `%ERRORLEVEL%` .

숫자가 아니거나 플랫폼별 범위를 벗어난 인수는의 값으로 변환 됩니다 `0` .

다음 예에서는 스크립트 파일에를 추가 하 여 오류 수준 변수 값을 4로 설정 합니다 `exit 4` `test.ps1` .

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>pwsh -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

을 실행 하 `pwsh.exe -File <path to a script>` 고 스크립트 파일이 명령을 사용 하 여 종료 되는 경우 `exit` 종료 코드는 명령에 사용 되는 숫자 인수로 설정 됩니다 `exit` . 스크립트에 문이 없으면 스크립트를 `exit` `0` 오류 없이 완료 하거나 `1` 스크립트가 처리 되지 않은 예외에서 종료 될 때 종료 코드는 항상입니다.

### <a name="filter"></a>Assert

각 입력 개체에 대해 문 목록이 한 번씩 실행 되는 함수를 지정 합니다. 프로세스 블록만 포함 하는 함수와 동일한 효과를 가집니다.

구문

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>Finally

Try 및 Catch와 연결 된 after 문으로 실행 되는 문 목록을 정의 합니다. `Finally` `CTRL+C` 스크립트를 유지 하거나 스크립트에서 Exit 키워드를 사용 하는 경우에도 문 목록이 실행 됩니다.

구문

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>For

조건을 사용 하 여 루프를 정의 합니다.

구문

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

컬렉션의 각 멤버를 사용 하 여 루프를 정의 합니다.

구문

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>보낸 사람

나중에 사용하기 위해 예약되어 있습니다.

### <a name="function"></a>함수

재사용 가능한 코드의 명명 된 문 목록을 만듭니다. 함수가 속한 범위의 이름을 지정할 수 있습니다. 키워드를 사용 하 여 하나 이상의 명명 된 매개 변수를 지정할 수 있습니다 `Param` . 함수 문 목록 내에 `DynamicParam` ,, `Begin` `Process` 및 `End` 문 목록을 포함할 수 있습니다.

구문

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

또한 문 목록 외부에서 함수 이름 뒤에 하나 이상의 매개 변수를 정의 하는 옵션이 있습니다.

구문

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>조건

조건부를 정의 합니다.

구문

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>숨김

Cmdlet의 기본 결과 `Get-Member` 와 IntelliSense 및 탭 완성 결과에서 클래스 멤버를 숨깁니다.

구문

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>In(다음 안에)

`ForEach`컬렉션의 각 멤버를 사용 하는 루프를 만들기 위해 문에 사용 됩니다.

구문

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

공유 PowerShell 세션에서 워크플로 명령을 실행 합니다. 이 키워드는 PowerShell 워크플로에서만 유효 합니다.

구문

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

`InlineScript`키워드는 `InlineScript` 공유 표준 (비 워크플로) 세션에서 명령을 실행 하는 활동을 나타냅니다. 키워드를 사용 하 여 `InlineScript` 워크플로에서 유효 하지 않은 명령을 실행 하 고 데이터를 공유 하는 명령을 실행할 수 있습니다. 기본적으로 InlineScript 스크립트 블록의 명령은 별도의 프로세스에서 실행 됩니다.

자세한 내용은 [워크플로에서 PowerShell 명령 실행](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11))을 참조 하세요.

### <a name="param"></a>매개 변수

함수에서 매개 변수를 정의 합니다.

구문

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>프로세스

`DynamicParam`, 및 키워드와 함께 함수 본문의 부분을 지정 합니다 `Begin` `End` . `Process`문 목록이 파이프라인에서 입력을 받으면 `Process` 문 목록이 파이프라인의 각 요소에 대해 한 번씩 실행 됩니다. 파이프라인에서 개체를 제공 하지 않는 경우 `Process` 문 목록이 실행 되지 않습니다. 명령이 파이프라인의 첫 번째 명령이 면 `Process` 문 목록이 한 번 실행 됩니다.

구문

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>반환 값

PowerShell에서 스크립트나 함수와 같은 현재 범위를 유지 하 고 선택적 식을 출력에 기록 합니다.

구문

```Syntax
return [<expression>]
```

### <a name="static"></a>정적

가 정의 된 클래스의 모든 인스턴스에 공통적으로 정의 된 속성이 나 메서드를 지정 합니다.

`Class`사용 예제는를 참조 하세요.

### <a name="switch"></a>스위치

여러 조건을 확인 하려면 `Switch` 문을 사용 합니다. `Switch`문은 일련의 `If` 문과 동일 하지만 더 간단 합니다.

`Switch`문은 각 조건과 선택적 동작을 나열 합니다. 조건이 가져오는 경우 작업이 수행 됩니다.

구문 1:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

구문 2:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Throw

개체를 오류로 throw 합니다.

구문

```Syntax
throw [<object>]
```

### <a name="trap"></a>Trap

오류가 발생 한 경우 실행할 문 목록을 정의 합니다. 오류 유형에는 대괄호가 필요 합니다. 두 번째 대괄호 쌍은 오류 유형이 optional 임을 나타냅니다.

구문

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>시도해 보기

문이 실행 되는 동안 오류를 확인할 문 목록을 정의 합니다. 오류가 발생 하는 경우 PowerShell은 또는 문에서 계속 실행 됩니다 `Catch` `Finally` . 오류 유형에는 대괄호가 필요 합니다. 두 번째 대괄호 쌍은 오류 유형이 optional 임을 나타냅니다.

구문

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>발생할

문 `Do` 목록이 한 번 이상 실행 되는 루핑 구문으로 문에서 사용 됩니다.

구문

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>사용

세션에서 사용 되는 네임 스페이스를 나타낼 수 있습니다. 클래스 및 멤버를 입력 하려면 더 작은 입력이 필요 합니다. 모듈의 클래스를 포함할 수도 있습니다.

구문 #1:

```Syntax
using namespace <.Net-framework-namespace>
```

구문 #2:

```Syntax
using module <module-name>
```

### <a name="while"></a>While

`while`문은 문이 실행 되기 전에 조건이 테스트 되는 루핑 구문입니다. 조건이 FALSE 이면 문이 실행 되지 않습니다.

문 구문:

```Syntax
while (<condition>) {
   <statements>
 }
```

문에서 사용 되는 경우 `Do` `while` 는 문 목록이 한 번 이상 실행 되는 루핑 구문의 일부입니다.

Do 루프 구문:

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>참고 항목

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)
