---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5e76a15e8f2dcacc7f973cbc46d057bb92c3ad41
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217234"
---
# Get-Command

## 개요
모든 명령을 가져옵니다.

## SYNTAX

### CmdletSet (기본값)

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [<CommonParameters>]
```

## 설명

`Get-Command`Cmdlet은 cmdlet, 별칭, 함수, 필터, 스크립트 및 응용 프로그램을 포함 하 여 컴퓨터에 설치 된 모든 명령을 가져옵니다. `Get-Command` 다른 세션에서 가져온 명령 및 PowerShell 모듈에서 명령을 가져옵니다. 현재 세션으로 가져온 명령만 가져오려면 **ListImported** 매개 변수를 사용합니다.

매개 변수가 없으면 `Get-Command` 컴퓨터에 설치 된 모든 cmdlet, 함수 및 별칭을 가져옵니다. `Get-Command *``$env:Path`응용 프로그램 명령 유형에 나열 되는 Path 환경 변수 ()에 있는 모든 비 PowerShell 파일을 포함 하는 모든 명령 유형을 가져옵니다.

`Get-Command` 와일드 카드 문자 없이 명령의 정확한 이름을 사용 하면 명령을 즉시 사용할 수 있도록 명령이 포함 된 모듈을 자동으로 가져옵니다. 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다. 자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

`Get-Command` 도움말 항목에서 정보를 가져오는와는 달리 명령 코드에서 직접 데이터를 가져옵니다 `Get-Help` .

Windows PowerShell 5.0부터 cmdlet의 결과에는 `Get-Command` 기본적으로 **버전** 열이 표시 됩니다. 새 **버전** 속성이 **commandinfo** 클래스에 추가 되었습니다.

## 예제

### 예제 1: cmdlet, 함수 및 별칭 가져오기

이 명령은 컴퓨터에 설치 된 PowerShell cmdlet, 함수 및 별칭을 가져옵니다.

```powershell
Get-Command
```

### 예 2: 현재 세션의 명령 가져오기

이 명령은 **ListImported** 매개 변수를 사용하여 현재 세션의 명령만 가져옵니다.

```powershell
Get-Command -ListImported
```

### 예제 3: cmdlet 가져오기 및 순서 대로 표시

이 명령은 모든 cmdlet을 가져오고 cmdlet 이름에 포함된 명사의 사전순으로 정렬한 다음 명사 기반 그룹으로 표시합니다. 이 표시를 사용하여 특정 작업에 대한 cmdlet을 찾을 수 있습니다.

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### 예제 4: 모듈의 명령 가져오기

이 명령은 **Module** 매개 변수를 사용 하 여 microsoft Powershell. Security 및 Microsoft. powershell 모듈에서 명령을 가져옵니다.

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### 예 5: cmdlet에 대 한 정보 가져오기

이 명령은 cmdlet에 대 한 정보를 가져옵니다 `Get-AppLockerPolicy` . 또한 **AppLocker** 모듈의 모든 명령을 현재 세션에 추가하는 **AppLocker** 모듈을 가져옵니다.

```powershell
Get-Command Get-AppLockerPolicy
```

모듈을 자동으로 가져올 때 효과는 Import-Module cmdlet을 사용 하는 것과 같습니다.
모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다. 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다. 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

### 예제 6: cmdlet의 구문 가져오기

이 명령은 **Argumentlist** 및 **구문** 매개 변수를 사용 하 여 `Get-ChildItem` Cert: 드라이브에서 사용 되는 cmdlet의 구문을 가져옵니다. Cert: 드라이브는 인증서 공급자가 세션에 추가 하는 PowerShell 드라이브입니다.

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

출력에 표시 된 구문과 **Args** ( **argumentlist** ) 매개 변수를 생략할 때 표시 되는 구문을 비교 하면 **인증서 공급자** 가 동적 매개 변수 **codesigningcert** 를 cmdlet에 추가 하는 것을 알 수 있습니다 `Get-ChildItem` .

인증서 공급자에 대 한 자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.

### 예 7: 동적 매개 변수 가져오기

이 예제의 명령은 함수를 사용 하 여 `Get-DynamicParameters` Certificate `Get-ChildItem` : 드라이브에서 사용 되는 경우 인증서 공급자가 cmdlet에 추가 하는 동적 매개 변수를 가져옵니다.

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

`Get-DynamicParameters`이 예제의 함수는 cmdlet의 동적 매개 변수를 가져옵니다. 이전 예의 방법 대신 이 방법을 사용할 수 있습니다. 다른 cmdlet 또는 공급자가 동적 매개 변수를 cmdlet에 추가할 수 있습니다.

### 예 8: 모든 형식의 모든 명령 가져오기

이 명령은 **Path** 환경 변수 ()의 경로에 있는 실행 파일을 포함 하 여 로컬 컴퓨터에 있는 모든 형식의 명령을 모두 가져옵니다 `$env:path` .

```powershell
Get-Command *
```

각 파일에 대한 **FileInfo** 개체(System.IO.FileInfo)가 아니라 **ApplicationInfo** 개체(System.Management.Automation.ApplicationInfo)를 반환합니다.

### 예제 9: 매개 변수 이름 및 유형을 사용 하 여 cmdlet 가져오기

이 명령은 이름이 Auth를 포함 하 고 형식이 **Authenticationmechanism** 인 매개 변수가 있는 cmdlet을 가져옵니다.

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

이러한 명령을 사용하여 사용자 인증에 사용되는 메서드를 지정할 수 있는 cmdlet을 찾을 수 있습니다.

**ParameterType** 매개 변수는 이름이 유사한 경우에도 **AuthenticationMechanism** 값을 사용하는 매개 변수와 **AuthenticationLevel** 매개 변수를 사용하는 매개 변수를 구분합니다.

### 예 10: 별칭 가져오기

이 예에서는 별칭과 함께 cmdlet을 사용 하는 방법을 보여 줍니다 `Get-Command` .

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

일반적으로 cmdlet 및 함수에 사용 되지만은 `Get-Command` 스크립트, 함수, 별칭 및 실행 파일도 가져옵니다.

이 명령의 출력은 별칭에 대한 **Name** 속성 값의 특수 보기를 표시합니다. 보기에는 별칭과 전체 명령 이름이 표시됩니다.

### 예 11: 메모장 명령의 모든 인스턴스 가져오기

이 예에서는 cmdlet의 **all** 매개 변수를 사용 하 여 `Get-Command` 로컬 컴퓨터에 있는 "Notepad" 명령의 모든 인스턴스를 표시 합니다.

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

**All** 매개 변수는 세션에 동일한 이름을 가진 명령이 두 개 이상 있는 경우에 유용합니다.

Windows PowerShell 3.0부터 기본적으로 세션에 동일한 이름의 명령이 여러 개 포함 된 경우는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다. **All** 매개 변수를 사용 하 여 `Get-Command` 지정 된 이름의 모든 명령을 가져오고 실행 우선 순위에 따라 반환 합니다. 목록의 첫 번째 명령이 아닌 명령을 실행하려면 명령의 정규화된 경로를 입력합니다.

명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.

### 예 12: cmdlet이 포함 된 모듈의 이름 가져오기

이 명령은 cmdlet이 시작 된 모듈의 이름을 가져옵니다 `Get-Date` .
명령에서 모든 명령의 **ModuleName** 속성을 사용합니다.

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

이 명령 형식은 세션으로 가져오지 않은 경우에도 PowerShell 모듈의 명령에 대해 작동 합니다.

### 예제 13: 출력 형식이 있는 cmdlet 및 함수 가져오기

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

이 명령은 출력 유형이 있는 cmdlet 및 함수와 반환하는 개체 유형을 가져옵니다.

명령의 첫 번째 부분에서 모든 cmdlet을 가져옵니다.
파이프라인 연산자 (|)가 cmdlet에 cmdlet을 보냅니다 .이 cmdlet은 `Where-Object` **OutputType** 속성이 채워지는 항목만 선택 합니다.
다른 파이프라인 연산자는 선택한 cmdlet 개체를 cmdlet으로 전송 합니다 `Format-List` . 그러면이 cmdlet에서 각 cmdlet의 이름과 출력 유형을 목록으로 표시 합니다.

cmdlet 코드에서 cmdlet의 **OutputType** 특성을 정의하는 경우에만 **CommandInfo** 개체의 **OutputType** 속성에 null이 아닌 값이 포함됩니다.

### 예 14: 특정 개체 유형을 입력으로 사용 하는 cmdlet 가져오기

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

이 명령은 네트워크 어댑터 개체를 입력으로 사용하는 cmdlet을 찾습니다. 이 명령을 사용하여 임의 명령이 반환하는 개체 유형을 허용하는 cmdlet을 찾을 수 있습니다.

명령에서 모든 개체의 **PSTypeNames** 내부 속성을 사용합니다. 이 속성은 개체를 설명하는 유형을 가져옵니다. 네트워크 어댑터 컬렉션의 **PSTypeNames** 속성이 아니라 네트워크 어댑터의 **PSTypeNames** 속성을 가져오기 위해 명령에서 배열 표기법을 사용하여 cmdlet이 반환하는 첫 번째 네트워크 어댑터를 가져옵니다.

### 예 15: 유사 항목 일치를 사용 하 여 명령 가져오기

이 예제에서 명령 이름에는 의도적으로 오타가 있습니다.
이 cmdlet은 스위치를 사용 하 여 가장 일치 하는 `-UseFuzzyMatching` 항목이 `Get-Command` 시스템의 다른 기본 명령 뒤에 나오는 것으로 확인 되었습니다.

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## PARAMETERS

### -All

이 cmdlet은 이름이 같은 동일한 형식의 명령을 포함 하 여 모든 명령을 가져옵니다. 기본적으로는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.

PowerShell에서 여러 명령의 이름이 동일한 경우 실행할 명령을 선택 하는 데 사용 하는 방법에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.
이름 충돌로 인해 기본적으로 실행 되지 않는 모듈의 정규화 된 명령 이름 및 실행 명령에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

Windows PowerShell 2.0에서는 `Get-Command` 기본적으로 모든 명령을 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

인수의 배열을 지정 합니다. 이 cmdlet은 지정 된 매개 변수 ("인수")와 함께 사용할 경우 cmdlet 또는 함수에 대 한 정보를 가져옵니다. **ArgumentList** 의 별칭은 **Args** 입니다.

다른 특정 매개 변수가 사용 되는 경우에만 사용할 수 있는 동적 매개 변수를 검색 하려면 **Argumentlist** 값을 동적 매개 변수를 트리거하는 매개 변수로 설정 합니다.

공급자가 cmdlet에 추가 하는 동적 매개 변수를 검색 하려면 **Argumentlist** 매개 변수의 값을 공급자 드라이브의 경로 (예: WSMan:, HKLM: 또는 Cert:)로 설정 합니다. 명령이 PowerShell 공급자 cmdlet 인 경우 각 명령에 하나의 경로만 입력 합니다. 공급자 cmdlet은 **Argumentlist** 값의 첫 번째 경로에 대 한 동적 매개 변수만 반환 합니다. 공급자 cmdlet에 대 한 자세한 내용은 [about_Providers](About/about_Providers.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

이 cmdlet이 가져오는 명령의 유형을 지정 합니다. 명령 유형을 하나 이상 입력합니다. **CommandType** 또는 별칭 **Type** 을 사용합니다. 기본적으로 `Get-Command` 모든 cmdlet, 함수 및 별칭을 가져옵니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 앤티앨리어스. 모든 PowerShell 명령의 별칭을 가져옵니다. 자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.
- 모두. 모든 명령 유형을 가져옵니다. 이 매개 변수 값은에 해당 합니다 `Get-Command *` .
- 애플리케이션을 클릭합니다. .Txt, .exe 및 .dll 파일을 비롯 하 여 **Path** 환경 변수 ($env:p a)에 나열 된 경로에서 PowerShell이 아닌 파일을 가져옵니다. **Path** 환경 변수에 대 한 자세한 내용은 about_Environment_Variables를 참조 하세요.
- #A0. 모든 cmdlet을 가져옵니다.
- ExternalScript. **Path** 환경 변수($env:path)에 나열된 경로에 있는 모든 .ps1 파일을 가져옵니다.
- 필터 및 함수 모든 PowerShell 고급 및 단순 함수와 필터를 가져옵니다.
- 스크립트. 모든 스크립트 블록을 가져옵니다. PowerShell 스크립트 (ps1 파일)를 가져오려면 ExternalScript 값을 사용 합니다.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -변수인 fullyqualifiedmodule

[ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 **설명** 섹션에서 설명 하는 **ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.
예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.

**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다. 두 매개 변수는 함께 사용할 수 없습니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListImported

이 cmdlet은 현재 세션의 명령만 가져옵니다.

PowerShell 3.0부터 시작 하 여 기본적으로 `Get-Command` 현재 세션의 명령을 포함 하 여 모든 설치 된 명령을 가져옵니다. PowerShell 2.0에서는 현재 세션의 명령만 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -모듈

모듈의 배열을 지정 합니다. 이 cmdlet은 지정 된 모듈에서 가져온 명령을 가져옵니다.
모듈 또는 모듈 개체의 이름을 입력 합니다.

이 매개 변수는 문자열 값을 사용 하지만이 매개 변수의 값은 및 cmdlet이 반환 하는 개체와 같은 **Psmoduleinfo** 개체 일 수도 있습니다 `Get-Module` `Import-PSSession` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

이름 배열을 지정합니다. 이 cmdlet은 지정 된 이름의 명령만 가져옵니다. 이름 또는 이름 패턴을 입력합니다. 와일드카드 문자를 사용할 수 있습니다.

동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용합니다. 두 명령의 이름이 같은 경우 기본적으로 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -명사

명령 명사 배열을 지정 합니다. 이 cmdlet은 지정 된 명사를 포함 하는 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다. 명사 또는 명사 패턴을 하나 이상 입력합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ParameterName

매개 변수 이름 배열을 지정 합니다. 이 cmdlet은 세션에서 지정 된 매개 변수가 있는 명령을 가져옵니다. 매개 변수 이름 또는 매개 변수 별칭을 입력 합니다. 와일드카드 문자가 지원됩니다.

**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -ParameterType

매개 변수 이름 배열을 지정 합니다. 이 cmdlet은 세션에서 지정 된 유형의 매개 변수가 있는 명령을 가져옵니다. 매개 변수 유형의 전체 이름이나 부분 이름을 입력합니다. 와일드카드 문자가 지원됩니다.

**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

이 cmdlet이 명령 정보를 표시 함을 나타냅니다.

이 매개 변수는 Windows PowerShell 5.0에서 도입 되었습니다.

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

### -구문

이 cmdlet은 명령에 대해 다음과 같은 지정 된 데이터만 가져옵니다.

- 별칭. 표준 이름을 가져옵니다.
- Cmdlet. 구문을 가져옵니다.
- 함수 및 필터. 함수 정의를 가져옵니다.
- 스크립트 및 응용 프로그램 또는 파일입니다. 경로와 파일 이름을 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

가져올 명령 수를 지정 합니다. 이 매개 변수를 사용하여 명령의 출력을 제한할 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseFuzzyMatching

명령을 찾을 때 유사 일치 알고리즘을 사용 함을 나타냅니다. 가장 일치 하는 항목에서 가장 일치 하는 항목으로 출력 순서가 가장 큽니다. 와일드 카드 문자를 포함할 수 있는 명령을 일치 시 키 려 고 하므로 유사 항목 일치에 와일드 카드를 사용 하면 안 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -동사

명령 동사의 배열을 지정 합니다. 이 cmdlet은 지정 된 동사가 포함 된 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다. 동사 또는 동사 패턴을 하나 이상 입력합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

이 cmdlet에 명령 이름을 파이프 하 여 사용할 수 있습니다.

## 출력

### System.web. CommandInfo

이 cmdlet은 **Commandinfo** 클래스에서 파생 된 개체를 반환 합니다. 반환 되는 개체의 유형은 가져오는 명령의 유형에 따라 달라 집니다 `Get-Command` .

### System.management.automation.aliasinfo.

별칭을 나타냅니다.

### System.object 정보입니다.

응용 프로그램 및 파일을 나타냅니다.

### System.object..

cmdlet을 나타냅니다.

### System.object를 관리 합니다.

함수와 필터를 나타냅니다.

## 참고

* 세션에서 이름이 같은 명령을 둘 이상 사용할 수 있는 경우 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 반환 합니다. 실행 순서에 나열 된 것과 동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용 합니다. 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)를 참조하세요.
* 모듈을 자동으로 가져올 때 효과는 cmdlet을 사용 하는 것과 같습니다 `Import-Module` . 모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다.
  모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다. 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

## 관련 링크

[Export-PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get-Help](Get-Help.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)
