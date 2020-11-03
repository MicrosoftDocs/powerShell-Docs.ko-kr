---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 2a30b8a86098a9d3ffdf8e48b092ac419d6b6e95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211977"
---
# New-Module

## 개요
메모리에만 있는 새 동적 모듈을 만듭니다.

## SYNTAX

### ScriptBlock (기본값)

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### 속성

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## 설명

`New-Module`Cmdlet은 스크립트 블록에서 동적 모듈을 만듭니다. 동적 모듈의 멤버(예: 함수 및 변수)는 세션에서 즉시 사용할 수 있어야 하며 세션을 닫을 때까지 사용할 수 있는 상태로 유지됩니다.

정적 모듈과 마찬가지로 동적 모듈의 cmdlet과 함수는 기본적으로 내보내고 변수와 별칭은 내보내지 않습니다. 그러나 Export-ModuleMember cmdlet 및의 매개 변수를 사용 하 여 기본값을 재정의할 수 있습니다 `New-Module` .

의 **AsCustomObject** 매개 변수를 사용 하 여 `New-Module` 동적 모듈을 사용자 지정 개체로 반환할 수도 있습니다. 함수와 같은 모듈 멤버는 세션으로 가져오는 대신 사용자 지정 개체의 스크립트 메서드로 구현됩니다.

동적 모듈은 메모리에만 있고 디스크에는 없습니다. 모든 모듈과 마찬가지로 동적 모듈의 멤버는 전역 범위의 하위인 개인 모듈 범위에서 실행됩니다. Get-Module은 동적 모듈을 가져올 수 없지만 Get-Command는 내보낸 멤버를 가져올 수 있습니다.

에서 동적 모듈을 사용할 수 있도록 하려면 `Get-Module` `New-Module` 명령을 import-module으로 파이프 하거나로 반환 되는 module 개체를 파이프 `New-Module` `Import-Module` 합니다. 이 작업은 동적 모듈을 목록에 추가 `Get-Module` 하지만 모듈을 디스크에 저장 하거나 영구적으로 설정 하지는 않습니다.

## 예제

### 예제 1: 동적 모듈 만들기

이 예에서는 라는 함수를 사용 하 여 새 동적 모듈을 만듭니다 `Hello` . 이 명령은 새 동적 모듈을 나타내는 모듈 개체를 반환합니다.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### 예 2: 동적 모듈과 Get-Module 및 Get-Command 사용

이 예에서는 cmdlet에서 동적 모듈을 반환 하지 않는 방법을 보여 줍니다 `Get-Module` . 이러한 멤버가 내보내는 멤버는 cmdlet에 의해 반환 됩니다 `Get-Command` .

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### 예제 3: 변수를 현재 세션으로 내보내기

이 예에서는 cmdlet을 사용 하 여 `Export-ModuleMember` 변수를 현재 세션으로 내보냅니다.
명령이 없으면 `Export-ModuleMember` 함수만 내보내집니다.

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

출력에는 변수와 함수 모두 세션으로 내보냈다고 나와 있습니다.

### 예 4: Get-Module에서 동적 모듈을 사용할 수 있도록 설정

이 예에서는 동적 모듈을로 파이프 하 여에서 동적 모듈을 사용할 수 있도록 설정 하는 방법을 보여 줍니다 `Get-Module` `Import-Module` .

`New-Module` cmdlet으로 파이프 되는 module 개체를 만듭니다 `Import-Module` . 의 **name** 매개 변수는 `New-Module` 모듈에 이름을 할당 합니다. `Import-Module`는 기본적으로 개체를 반환 하지 않으므로이 명령의 출력은 없습니다. `Get-Module`**GreetingModule** 를 현재 세션으로 가져왔습니다.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

`Get-Command`Cmdlet은 `Hello` 동적 모듈이 내보내는 함수를 보여 줍니다.

### 예 5: 내보낸 함수를 포함 하는 사용자 지정 개체 생성

이 예제에서는의 **AsCustomObject** 매개 변수를 사용 하 여 `New-Module` 내보낸 함수를 나타내는 스크립트 메서드를 포함 하는 사용자 지정 개체를 생성 하는 방법을 보여 줍니다.

`New-Module`Cmdlet은 및 라는 두 개의 함수를 사용 하 여 동적 모듈을 만듭니다 `Hello` `Goodbye` . **AsCustomObject** 매개 변수는 기본적으로 생성 되는 **psmoduleinfo** 개체 대신 사용자 지정 개체를 만듭니다 `New-Module` . 이 사용자 지정 개체는 변수에 저장 됩니다 `$m` .
`$m`변수에 할당 된 값이 없는 것으로 나타납니다.

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

`$m`Cmdlet에 파이프 하 여 `Get-Member` 사용자 지정 개체의 속성 및 메서드를 표시 합니다. 출력은 개체에 및 함수를 나타내는 스크립트 메서드가 있음을 보여 `Hello` 줍니다 `Goodbye` .
마지막으로 이러한 스크립트 메서드를 호출 하 고 결과를 표시 합니다.

### 예제 6: 스크립트 블록의 결과 가져오기

이 예에서는 **Returnresult** 매개 변수를 사용 하 여 모듈 개체를 요청 하는 대신 스크립트 블록의 실행 결과를 요청 합니다. 새 모듈의 스크립트 블록은 함수를 정의한 `SayHello` 다음 함수를 호출 합니다.

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETERS

### -ArgumentList

스크립트 블록으로 전달 되는 매개 변수 값인 인수 배열을 지정 합니다. **Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

이 cmdlet이 동적 모듈을 나타내는 사용자 지정 개체를 반환 함을 나타냅니다. 모듈 멤버는 사용자 지정 개체의 스크립트 메서드로 구현되지만 세션으로 가져오지 않습니다. 사용자 지정 개체를 변수에 저장하고 점 표기법을 사용하여 멤버를 호출할 수 있습니다.

모듈에 이름이 같은 멤버가 여러 개 있는 경우 (예: 이름이 인 함수 및 변수) 사용자 지정 개체에서 각 이름을 가진 하나의 멤버에만 액세스할 수 있습니다.

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

### -Cmdlet

이 cmdlet이 모듈에서 현재 세션으로 내보내는 cmdlet의 배열을 지정 합니다.
쉼표로 구분된 cmdlet 목록을 입력합니다. 와일드카드 문자를 사용할 수 있습니다. 기본적으로 모듈의 모든 cmdlet을 내보냅니다.

스크립트 블록에서 cmdlet을 정의할 수는 없지만 동적 모듈이 이진 모듈에서 cmdlet을 가져오는 경우 동적 모듈에 cmdlet이 포함될 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -함수

이 cmdlet이 모듈에서 현재 세션으로 내보내는 함수 배열을 지정 합니다.
쉼표로 구분된 함수 목록을 입력합니다. 와일드카드 문자를 사용할 수 있습니다. 기본적으로 모듈에 정의된 모든 함수를 내보냅니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

새 모듈의 이름을 지정합니다. 또한 모듈 이름을 New-Module로 파이프할 수 있습니다.

기본값은로 시작 하 여 `__DynamicModule_` 동적 모듈의 경로를 지정 하는 GUID가 뒤에 오는 자동 생성 된 이름입니다.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

이 cmdlet이 스크립트 블록을 실행 하 고 모듈 개체를 반환 하는 대신 스크립트 블록 결과를 반환 함을 나타냅니다.

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

### -ScriptBlock

동적 모듈의 내용을 지정합니다. 내용을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
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

### System.String

모듈 이름을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### PSCustomObject 또는 None 중에서 하나를 일치 하지 않습니다.

이 cmdlet은 기본적으로 **Psmoduleinfo** 개체를 생성 합니다. **AsCustomObject** 매개 변수를 사용 하는 경우 **PSCustomObject** 개체를 생성 합니다. **Returnresult** 매개 변수를 사용 하는 경우 동적 모듈의 스크립트 블록 평가 결과가 반환 됩니다.

## 참고

별칭으로를 참조할 수도 있습니다 `New-Module` `nmo` . 자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.

## 관련 링크

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[모듈 가져오기](Import-Module.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)
