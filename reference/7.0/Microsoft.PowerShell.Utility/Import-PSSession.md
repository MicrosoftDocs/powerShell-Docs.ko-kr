---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: c64a59300cdaffe71de04c7843bf644df49530d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390119"
---
# Import-PSSession

## 개요
다른 세션의 명령을 현재 세션으로 가져옵니다.

## SYNTAX

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## 설명

`Import-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터의 PSSession에서 cmdlet, 함수 및 별칭과 같은 명령을 현재 세션으로 가져옵니다. `Get-Command`Cmdlet이 PSSession에서 찾을 수 있는 모든 명령을 가져올 수 있습니다.

명령을 사용 하 여 `Import-PSSession` Microsoft Exchange Server shell과 같은 사용자 지정 된 셸에서 또는 현재 세션에 있지 않은 Windows PowerShell 모듈 및 스냅인 또는 다른 요소를 포함 하는 세션에서 명령을 가져옵니다.

명령을 가져오려면 먼저 cmdlet을 사용 `New-PSSession` 하 여 PSSession을 만듭니다. 그런 다음 cmdlet을 사용 `Import-PSSession` 하 여 명령을 가져옵니다. 기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 가져옵니다. 모든 명령을 가져오려면 **AllowClobber** 매개 변수를 사용합니다.

가져온 명령은 세션의 다른 명령과 같은 방법으로 사용할 수 있습니다. 가져온 명령을 사용할 때 명령에서 가져온 부분은 암시적으로는 원래 있던 세션에서 실행됩니다. 그러나 원격 작업은 전적으로 Windows PowerShell에서 처리됩니다. 다른 세션(PSSession)에 대한 연결을 열어 두어야 하는 경우를 제외하면 원격 작업은 신경쓰지 않아도 됩니다. 다른 세션에 대한 연결을 닫으면 가져온 명령을 더 이상 사용할 수 없습니다.

가져온 명령은 로컬 명령 보다 실행 하는 데 더 오래 걸릴 수 있으므로는 `Import-PSSession` 가져온 모든 명령에 **AsJob** 매개 변수를 추가 합니다. 이 매개 변수는 명령을 Windows PowerShell 백그라운드 작업으로 실행할 수 있도록 합니다. 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md)를 참조하세요.

를 사용 하는 경우 `Import-PSSession` Windows PowerShell은 가져온 명령을 사용자의 세션에만 존재 하는 임시 모듈에 추가 하 고 해당 모듈을 나타내는 개체를 반환 합니다. 이후 세션에서 사용할 수 있는 영구 모듈을 만들려면 cmdlet을 사용 `Export-PSSession` 합니다.

이 `Import-PSSession` cmdlet은 Windows PowerShell의 암시적 원격 기능을 사용 합니다. 명령을 현재 세션으로 가져올 때 원래 세션이 나 원래 컴퓨터의 유사한 세션에서 암시적으로 실행 됩니다.

Windows PowerShell 3.0부터 cmdlet을 사용 `Import-Module` 하 여 원격 세션에서 현재 세션으로 모듈을 가져올 수 있습니다. 이 기능은 암시적 원격을 사용하며 를 사용 하 여 `Import-PSSession` 원격 세션에서 선택한 모듈을 현재 세션으로 가져오는 것과 같습니다.

## 예제

### 예제 1: PSSession에서 모든 명령 가져오기

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

이 명령은 현재 세션에 있는 명령과 이름이 같은 명령을 제외하고 Server01 컴퓨터의 PSSession에 있는 모든 명령을 현재 세션으로 가져옵니다.

**CommandName** 매개 변수를 사용하지 않으므로 가져온 명령에 필요한 모든 형식 지정 데이터도 가져옵니다.

### 예 2: 특정 문자열로 끝나는 명령 가져오기

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

이 명령은 "-test"로 끝나는 이름의 명령을 PSSession에서 로컬 세션으로 가져온 다음 가져온 cmdlet을 사용하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` PSSession을 만듭니다. PSSession을 `$S` 변수에 저장 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Import-PSSession` 의 PSSession에 있는 명령을 `$S` 현재 세션으로 가져옵니다. **CommandName** 매개 변수를 사용하여 Test 명사가 포함된 명령을 지정하고 **FormatTypeName** 매개 변수를 사용하여 Test 명령에 대한 형식 지정 데이터를 가져옵니다.

세 번째 및 네 번째 명령은 가져온 명령을 현재 세션에 사용합니다. 가져온 명령은 실제로 현재 세션에 추가되므로 로컬 구문을 사용하여 실행할 수 있습니다. 가져온 명령을 실행 하는 데 cmdlet을 사용할 필요는 없습니다 `Invoke-Command` .

### 예제 3: PSSession에서 cmdlet 가져오기

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

이 예제에서는 가져온 cmdlet을 로컬 cmdlet과 같은 방법으로 사용할 수 있음을 보여 줍니다.

이러한 명령은 Server01 컴퓨터의 PSSession에서 및 cmdlet을 가져오고 `New-Test` `Get-Test` `Set-Test` Server02 컴퓨터의 pssession에서 cmdlet을 가져옵니다.

이 cmdlet은 각기 다른 PSSession에서 가져온 것이지만 cmdlet 간에 개체를 파이프해도 오류가 발생하지 않습니다.

### 예제 4: 가져온 명령을 백그라운드 작업으로 실행

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

이 예제에서는 가져온 명령을 백그라운드 작업으로 실행하는 방법을 보여 줍니다.

가져온 명령은 로컬 명령 보다 실행 하는 데 더 오래 걸릴 수 있으므로는 `Import-PSSession` 가져온 모든 명령에 **AsJob** 매개 변수를 추가 합니다. **AsJob** 매개 변수를 사용하면 명령을 백그라운드 작업으로 실행할 수 있습니다.

첫 번째 명령은 Server01 컴퓨터에 PSSession을 만들고 PSSession 개체를 변수에 저장 합니다 `$S` .

두 번째 명령은를 사용 하 여 `Import-PSSession` 의 PSSession에서 현재 세션으로 테스트 cmdlet을 가져옵니다 `$S` .

세 번째 명령은 가져온 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `New-Test` `New-Test` 명령을 백그라운드 작업으로 실행 합니다. 이 명령은에서 반환 하는 작업 개체를 저장 `New-Test` `$batch` 합니다.

네 번째 명령은 cmdlet을 사용 하 여 `Receive-Job` 변수의 작업 결과를 가져옵니다 `$batch` .

### 예 5: Windows PowerShell 모듈에서 cmdlet 및 함수 가져오기

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

이 예제에서는 cmdlet 및 함수를 원격 컴퓨터의 Windows PowerShell 모듈에서 현재 세션으로 가져오는 방법을 보여 줍니다.

첫 번째 명령은 Server01 컴퓨터에 PSSession을 만든 다음 변수에 저장 합니다 `$S` .

두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Import-Module` 의 PSSession에서 명령을 실행 합니다 `$S` .

일반적으로이 모듈은 `Import-Module` Windows PowerShell 프로필의 명령으로 모든 세션에 추가 되지만 프로필은 pssession에서 실행 되지 않습니다.

세 번째 명령은의 **module** 매개 변수를 사용 하 여 `Import-PSSession` 모듈의 cmdlet 및 함수를 현재 세션으로 가져옵니다.

### 예제 6: 임시 파일에 모듈 만들기

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

이 예제에서는 `Import-PSSession` 디스크에서 임시 파일에 모듈을 만드는 방법을 보여 줍니다. 또한 현재 세션으로 가져오기 전에 모든 명령이 함수로 변환됨을 보여 줍니다.

이 명령은 cmdlet을 사용 하 여 `Import-PSSession` `Get-Date` Cmdlet 및 searchhelp 함수를 현재 세션으로 가져옵니다.

`Import-PSSession`Cmdlet은 임시 모듈을 나타내는 **Psmoduleinfo** 개체를 반환 합니다. **Path** 속성의 값은 `Import-PSSession` 스크립트 모듈 (.psm1) 파일을 임시 위치에 만들었음을 보여 줍니다. **ExportedFunctions** 속성은 `Get-Date` Cmdlet과 searchhelp 함수를 둘 다 함수로 가져왔으므로 표시 합니다.

### 예 7: 가져온 명령에 의해 숨겨진 명령 실행

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

이 예제에서는 가져온 명령에서 숨기는 명령을 실행하는 방법을 보여 줍니다.

첫 번째 명령은 `Get-Date` 변수의 PSSession에서 cmdlet을 가져옵니다 `$S` . 현재 세션에 cmdlet이 포함 되어 있으므로 `Get-Date` 명령에 **AllowClobber** 매개 변수가 필요 합니다.

두 번째 명령은 cmdlet의 **all** 매개 변수를 사용 하 여 `Get-Command` `Get-Date` 현재 세션에 있는 모든 명령을 가져옵니다. 출력은 세션에 원래 cmdlet과 함수가 포함 되어 있음을 보여 줍니다 `Get-Date` `Get-Date` . `Get-Date`함수는의 PSSession에서 가져온 cmdlet을 실행 `Get-Date` `$S` 합니다.

세 번째 명령은 명령을 실행 합니다 `Get-Date` . 함수는 cmdlet 보다 우선 하므로 Windows PowerShell에서 율리우스 날짜를 반환 하는 가져온 함수를 실행 합니다 `Get-Date` .

네 번째 및 다섯 번째 명령은 가져온 명령에서 숨기는 명령을 실행하는 데 정규화된 이름을 사용하는 방법을 보여 줍니다.

네 번째 명령은 원래 `Get-Date` cmdlet이 현재 세션에 추가 된 Windows PowerShell 스냅인의 이름을 가져옵니다.

다섯 번째 명령은 cmdlet의 스냅인 정규화 된 이름을 사용 하 여 `Get-Date` `Get-Date` 명령을 실행 합니다.

명령 우선 순위 및 숨겨진 명령에 대한 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.

### 예 8: 이름에 특정 문자열이 있는 명령 가져오기

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

이 명령은의 PSSession에 있는 항목의 이름이 포함 된 명령을 가져옵니다 `$S` . 명령에는 **CommandName** 매개 변수는 포함 되지만 **FormatTypeData** 매개 변수는 포함 되어 있지 않으므로 명령만 가져옵니다.

를 사용 하 여 `Import-PSSession` 원격 컴퓨터에서 명령을 실행 하 고 현재 세션에 명령에 대 한 형식 지정 데이터가 이미 있는 경우이 명령을 사용 합니다.

### 예 9: Module 매개 변수를 사용 하 여 세션으로 가져온 명령 검색

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

이 명령은의 **Module** 매개 변수를 사용 하 여 `Get-Command` 명령에 의해 세션으로 가져온 명령을 찾는 방법을 보여 줍니다 `Import-PSSession` .

첫 번째 명령은 cmdlet을 사용 하 여 `Import-PSSession` 변수의 PSSession에서 "bits"를 포함 하는 명령을 가져옵니다 `$S` . `Import-PSSession`명령은 임시 모듈을 반환 하 고,이 명령은 모듈을 변수에 저장 합니다 `$m` .

두 번째 명령은 cmdlet을 사용 하 여 `Get-Command` 변수에서 모듈에 의해 내보내지는 명령을 가져옵니다 `$M` .

**Module** 매개 변수는 모듈 이름에 사용되는 문자열 값을 사용합니다. 그러나 모듈 개체를 제출할 경우 Windows PowerShell은 모듈 이름을 반환하는 모듈 개체의 **ToString** 메서드를 사용합니다.

`Get-Command`명령은 "와 동일 합니다 `Get-Command $M.Name` .

## PARAMETERS

### -AllowClobber

현재 세션에 있는 명령과 이름이 동일한 경우에도이 cmdlet이 지정 된 명령을 가져오도록 지정 합니다.

현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령이 원래 명령을 숨기거나 바꿉니다. 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.

기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 동일한 명령을 가져오지 않습니다.

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

### -ArgumentList

지정 된 인수 (매개 변수 값)를 사용 하 여 생성 되는 명령 배열을 지정 합니다.

예를 들어 `Get-Item` 인증서 (Cert:)에서 명령의 변형을 가져오려면 드라이브의 PSSession에 `$S` 를 입력 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 합니다.

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

### -인증서

에서 만드는 임시 모듈에서 서식 파일 (* .Format.ps1xml) 또는 스크립트 모듈 파일 (. .psm1)에 서명 하는 데 사용 되는 클라이언트 인증서를 지정 합니다 `Import-PSSession` .

인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.

인증서를 찾으려면 cmdlet을 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 (Cert:)에서 cmdlet을 사용 합니다. 드라이브나. 인증서가 잘못되었거나 권한이 없을 경우 명령이 실패합니다.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

지정 된 이름이 나 이름 패턴을 사용 하 여 명령을 지정 합니다. 와일드카드가 지원됩니다. **CommandName** 또는 별칭, **이름** 을 사용 합니다.

기본적으로는 `Import-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외 하 고 세션에서 모든 명령을 가져옵니다. 이렇게 하면 가져온 명령이 세션의 명령을 숨기거나 바꾸지 않습니다. 다른 명령을 숨기거나 바꾸는 명령을 포함하여 모든 명령을 가져오려면 **AllowClobber** 매개 변수를 사용합니다.

**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다. 마찬가지로, **FormatTypeName** 매개 변수를 사용할 경우 **CommandName** 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

명령 개체의 유형을 지정 합니다. 기본값은 Cmdlet입니다. **CommandType** 또는 별칭 **Type** 을 사용합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 앤티앨리어스. 원격 세션에 있는 Windows PowerShell 별칭입니다.
- 모두. 원격 세션에 있는 cmdlet 및 함수입니다.
- 애플리케이션을 클릭합니다. `$env:path`.Txt, .exe 및 .dll 파일을 비롯 하 여 원격 세션의 Path 환경 변수 ()에 나열 된 경로에 Windows-PowerShell 파일 이외의 모든 파일.
- #A0. 원격 세션에 있는 cmdlet입니다. 기본값은 "Cmdlet"입니다.
- ExternalScript. 원격 세션의 Path 환경 변수 ()에 나열 된 경로에 있는 ps1 파일. `$env:path`
- 필터 및 함수 원격 세션에 있는 Windows PowerShell 함수입니다.
- 스크립트. 원격 세션에 있는 스크립트 블록입니다.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableNameChecking

이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.

기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 Windows PowerShell은 다음 경고 메시지를 표시 합니다.

"경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다. 자세한 내용을 보려면 Verbose 매개 변수를 사용 하 고, `Get-Verb` 승인 된 동사 목록을 보려면을 입력 합니다. "

이 메시지는 경고일 뿐입니다. 비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다. 메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.

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

### -FormatTypeName

지정 된 Microsoft .NET Framework 형식에 대 한 형식 지정 명령을 지정 합니다.
유형 이름을 입력합니다.
와일드카드가 지원됩니다.

이 매개 변수 값은 `Get-FormatData` 명령을 가져올 세션의 명령에서 반환 하는 형식의 이름 이어야 합니다. 원격 세션의 모든 형식 지정 데이터를 가져오려면를 입력 `*` 합니다.

명령에 **CommandName** 또는 **formattypename** 매개 변수가 포함 되어 있지 않으면 `Import-PSSession` `Get-FormatData` 원격 세션의 명령에서 반환 하는 모든 .NET Framework 형식에 대 한 형식 지정 명령을 가져옵니다.

**FormatTypeName** 매개 변수를 사용할 경우 **CommandName** 매개 변수를 사용하지 않으면 명령을 가져오지 않습니다.

마찬가지로, **CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 가져오지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -변수인 fullyqualifiedmodule

PowerShell SDK의 [ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) 의 설명 섹션에서 설명 하는 이름이 **ModuleSpecification** 개체 형식으로 지정 된 모듈을 지정 합니다. 예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}` 또는
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.

**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.

**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다. 두 매개 변수는 함께 사용할 수 없습니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -모듈

Windows PowerShell 스냅인 및 모듈에서 명령의 배열을 지정 합니다. 스냅인 및 모듈 이름을 입력합니다. 와일드카드는 사용할 수 없습니다.

`Import-PSSession` 스냅인에서 공급자를 가져올 수 없습니다.

자세한 내용은 [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) 및 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)을 참조하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -접두사

가져온 명령 이름의 명사에 대 한 접두사를 지정 합니다.

이 매개 변수를 사용하면 세션에 있는 서로 다른 명령의 이름이 같은 경우 발생할 수 있는 이름 충돌을 방지할 수 있습니다.

예를 들어, 접두사를 원격으로 지정 하 고 cmdlet을 가져오면이 `Get-Date` cmdlet은 세션에서로 알려져 `Get-RemoteDate` 있으며 원래 cmdlet과는 혼동 되지 않습니다 `Get-Date` .

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

### -Session

Cmdlet을 가져올 **PSSession** 을 지정 합니다. 세션 개체가 포함 된 변수를 입력 하거나 세션 개체를 가져오는 명령 (예: 또는 명령)을 `New-PSSession` 입력 `Get-PSSession` 합니다. 세션은 하나만 지정할 수 있습니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### System.object..

`Import-PSSession` 및 cmdlet이 반환 하는 것과 동일한 모듈 개체를 반환 `New-Module` `Get-Module` 합니다.
그러나 가져온 모듈은 임시 모듈이며 현재 세션에만 존재합니다. 디스크에 영구 모듈을 만들려면 cmdlet을 사용 `Export-PSSession` 합니다.

## 참고

- `Import-PSSession` 은 PowerShell 원격 인프라를 사용 합니다. 이 cmdlet을 사용하려면 WS-Management 원격 기능을 사용하도록 컴퓨터를 구성해야 합니다. 자세한 내용은 [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) 및 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)를 참조 하세요.
- `Import-PSSession` 변수 또는 PowerShell 공급자를 가져오지 않습니다.
- 현재 세션에 있는 명령과 이름이 같은 명령을 가져오는 경우 가져온 명령은 세션에 있는 별칭, 함수 및 cmdlet을 숨길 수 있으며 세션에 있는 함수 및 변수를 바꿀 수 있습니다. 이름 충돌을 방지하려면 **Prefix** 매개 변수를 사용합니다. 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.
- `Import-PSSession` 모든 명령을 가져오기 전에 함수로 변환 합니다. 그 결과 가져온 명령은 원래 명령 유형을 유지할 때의 동작과 다소 다르게 작동합니다. 예를 들어 PSSession에서 cmdlet을 가져온 다음 모듈 또는 스냅인에서 같은 이름의 cmdlet을 가져오는 경우 함수가 cmdlet보다 우선적으로 적용되기 때문에 항상 PSSession에서 가져온 cmdlet이 기본적으로 실행됩니다. 반대로 별칭을 같은 이름의 별칭이 있는 세션으로 가져오는 경우 별칭이 함수보다 우선적으로 적용되기 때문에 항상 원래 별칭이 사용됩니다. 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)를 참조하세요.
- `Import-PSSession` cmdlet을 사용 하 여 `Write-Progress` 명령 진행률을 표시 합니다. 명령이 실행되는 동안 진행률 표시줄을 확인할 수 있습니다.
- 가져올 명령을 찾기 위해에서 cmdlet을 `Import-PSSession` 사용 하 여 `Invoke-Command` `Get-Command` PSSession에서 명령을 실행 합니다. 명령에 대 한 형식 지정 데이터를 가져오기 위해 cmdlet을 사용 합니다 `Get-FormatData` . 명령을 실행할 때 이러한 cmdlet의 오류 메시지가 표시 될 수 있습니다 `Import-PSSession` . 또한,, `Import-PSSession` `Get-Command` `Get-FormatData` `Select-Object` 및 cmdlet을 포함 하지 않는 PSSession에서 명령을 가져올 수 없습니다 `Get-Help` .
- 가져온 명령의 경우 사용자 인터페이스를 통해 메모장 등의 프로그램을 시작할 수 없다는 점을 포함하여 다른 원격 명령과 동일한 제한이 적용됩니다.
- Windows PowerShell 프로필은 pssession에서 실행 되지 않으므로 프로필을 통해 세션에 추가 하는 명령은에서 사용할 수 없습니다 `Import-PSSession` . 프로필에서 명령을 가져오려면 명령을 `Invoke-Command` 가져오기 전에 명령을 사용 하 여 PSSession에서 프로필을 수동으로 실행 합니다.
- 에서 `Import-PSSession` 형식 지정 데이터를 가져오지 않는 경우에도에서 만드는 임시 모듈에 서식 파일을 포함할 수 있습니다. 명령이 형식 지정 데이터를 가져오지 않는 경우 만든 형식 지정 파일에 형식 지정 데이터가 포함되지 않습니다.
- 를 사용 하려면 `Import-PSSession` 현재 세션의 실행 정책을 제한 하거나 AllSigned 수 없습니다 .이는를 만드는 임시 모듈에 `Import-PSSession` 이러한 정책에서 금지 되는 서명 되지 않은 스크립트 파일이 포함 되어 있기 때문입니다. `Import-PSSession`로컬 컴퓨터에 대 한 실행 정책을 변경 하지 않고를 사용 하려면의 **Scope** 매개 변수를 사용 하 여 `Set-ExecutionPolicy` 단일 프로세스에 대 한 덜 제한적인 실행 정책을 설정 합니다.
- Windows PowerShell 2.0에서는 다른 세션에서 가져온 명령에 대한 도움말 항목에 **Prefix** 매개 변수를 사용하여 할당한 접두사가 포함되어 있지 않습니다. Windows PowerShell 2.0에서 가져온 명령에 대한 도움말을 가져오려면 접두사가 없는 원래 명령 이름을 사용합니다.

## 관련 링크

[Export-PSSession](Export-PSSession.md)
