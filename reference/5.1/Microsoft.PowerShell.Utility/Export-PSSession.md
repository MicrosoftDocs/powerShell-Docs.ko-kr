---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 11533a9b127dc6d088258392c0e142bfbe5c070c
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388028"
---
# Export-PSSession

## 개요

다른 세션에서 명령을 내보내고 PowerShell 모듈에 저장 합니다.

## SYNTAX

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## 설명

`Export-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터의 다른 PowerShell 세션 (PSSession)에서 cmdlet, 함수, 별칭 및 기타 명령 유형을 가져온 후 PowerShell 모듈에 저장 합니다. 모듈의 명령을 현재 세션에 추가 하려면 cmdlet을 사용 `Import-Module` 합니다.

`Import-PSSession`다른 PSSession의 명령을 현재 세션으로 가져오는와 달리는 `Export-PSSession` 모듈에 명령을 저장 합니다. 현재 세션으로 가져오지 않습니다.

명령을 내보내려면 cmdlet을 사용 `New-PSSession` 하 여 내보낼 명령이 포함 된 PSSession을 만듭니다. 그런 다음 cmdlet을 사용 `Export-PSSession` 하 여 명령을 내보냅니다.

명령 이름 충돌을 방지 하기 위해의 기본값은 `Export-PSSession` 현재 세션에 있는 명령을 제외한 모든 명령을 내보내는 것입니다. **CommandName** 매개 변수를 사용 하 여 내보낼 명령을 지정할 수 있습니다.

`Export-PSSession`Cmdlet은 PowerShell의 암시적 원격 기능을 사용 합니다. 명령을 현재 세션으로 가져올 때 원래 세션이 나 원래 컴퓨터의 유사한 세션에서 암시적으로 실행 됩니다.

## 예제

### 예제 1: PSSession에서 명령 내보내기

이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 새 PSSession을 만듭니다. 현재 세션에 있는 명령을 제외한 모든 명령을 로컬 컴퓨터의 Server01 라는 모듈로 내보냅니다. 내보내기에는 명령에 대 한 형식 지정 데이터가 포함 됩니다.

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

`New-PSSession`명령은 Server01 컴퓨터에 PSSession을 만듭니다. PSSession은 변수에 저장 됩니다 `$S` . `Export-PSSession`명령은 `$S` 변수의 명령과 형식 지정 데이터를 Server01 모듈로 내보냅니다.

### 예제 2: Get 및 Set 명령 내보내기

이 예에서는 `Get` `Set` 서버에서 및 명령을 모두 내보냅니다.

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

이러한 명령은 `Get` `Set` 원격 컴퓨터에 있는 Microsoft exchange Server 스냅인의 및 명령을 `$PSHOME\Modules` 로컬 컴퓨터의 디렉터리에 있는 Exchange 모듈로 내보냅니다.
모듈을 디렉터리에 배치 `$PSHOME\Modules` 하면 컴퓨터의 모든 사용자가 액세스할 수 있습니다.

### 예 3: 원격 컴퓨터에서 명령 내보내기

이 예제에서는 원격 컴퓨터의 PSSession에서 cmdlet을 내보내 로컬 컴퓨터의 모듈에 저장 합니다. 모듈의 cmdlet을 사용할 수 있도록 현재 세션에 추가 합니다.

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

`New-PSSession`이 명령은 Server01 컴퓨터에 PSSession을 만들어 변수에 저장 합니다 `$S` . `Export-PSSession`명령은의 PSSession에서 이름이 테스트로 시작 하는 cmdlet을 `$S` 로컬 컴퓨터의 testcmdlets 모듈로 내보냅니다.

`Remove-PSSession`Cmdlet은 `$S` 현재 세션에서 PSSession을 삭제 합니다. 이 명령은 세션에서 가져온 명령을 사용 하기 위해 PSSession이 활성화 되지 않아도 됨을 보여 줍니다. `Import-Module`Cmdlet은 testcmdlets 모듈의 cmdlet을 현재 세션에 추가 합니다. 언제 든 지 모든 세션에서 명령을 실행할 수 있습니다.

`Get-Help`Cmdlet은 이름이 Test로 시작 하는 cmdlet에 대 한 도움말을 가져옵니다. 모듈의 명령이 현재 세션에 추가 된 후에는 및 cmdlet을 사용 하 여 `Get-Help` `Get-Command` 가져온 명령에 대해 알아볼 수 있습니다. `Test-Files`Cmdlet을 Server01 컴퓨터에서 내보낸 후 세션에 추가 했습니다. `Test-Files`Cmdlet은 명령을 가져온 컴퓨터의 원격 세션에서 실행 됩니다. PowerShell은 TestCmdlets 모듈에 저장 된 정보를 통해 세션을 만듭니다.

### 예 4: 현재 세션의 Export 및 변경이 명령

이 예에서는 변수에 저장 된 명령을 현재 세션으로 내보냅니다.

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

이 `Export-PSSession` 명령은 변수의 PSSession에 있는 모든 명령과 형식 지정 데이터를 `$S` 현재 세션으로 내보냅니다. **AllowClobber** 매개 변수는 현재 세션에 있는 명령과 이름이 같은 명령을 포함 합니다.

### 예 5: 닫힌 PSSession에서 명령 내보내기

이 예제에서는 내보낸 명령을 만든 PSSession을 닫을 때 특별 한 옵션을 사용 하 여 내보낸 명령을 실행 하는 방법을 보여 줍니다.

모듈을 가져올 때 원래 원격 세션이 닫히면 모듈은 원래 컴퓨터에 연결 되는 열려 있는 원격 세션을 사용 합니다. 원본 컴퓨터에 대 한 현재 세션이 없는 경우 모듈은 세션을 다시 설정 합니다.

원격 세션에서 특수 한 옵션을 사용 하 여 내보낸 명령을 실행 하려면 모듈을 가져오기 전에 이러한 옵션으로 원격 세션을 만들어야 합니다. Cmdlet에 `New-PSSession` **sessionoption** 매개 변수를 사용 합니다.

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

`New-PSSessionOption`Cmdlet은 **Pssessionoption** 개체를 만든 다음이 개체를 `$Options` 변수에 저장 합니다. `New-PSSession`명령은 Server01 컴퓨터에 PSSession을 만듭니다.
**Sessionoption** 매개 변수는에 저장 된 개체를 사용 합니다 `$Options` . 세션은 변수에 저장 됩니다 `$S` .

`Export-PSSession`Cmdlet은의 PSSession에서 `$S` Server01 모듈로 명령을 내보냅니다.
`Remove-PSSession`Cmdlet은 변수의 PSSession을 삭제 합니다 `$S` .

`New-PSSession`Cmdlet은 Server01 컴퓨터에 연결 하는 새 PSSession을 만듭니다. **Sessionoption** 매개 변수는에 저장 된 개체를 사용 합니다 `$Options` . `Import-Module`Cmdlet은 Server01 모듈에서 명령을 가져옵니다. 모듈의 명령은 Server01 컴퓨터의 PSSession에서 실행 됩니다.

## PARAMETERS

### -AllowClobber

현재 세션에 있는 명령과 이름이 같더라도 지정한 명령을 내보냅니다.

현재 세션에 있는 명령과 이름이 같은 명령을 내보내는 경우 내보낸 명령은 원래 명령을 숨기 거 나 바꿉니다. 자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)를 참조하세요.

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

지정한 인수(매개 변수 값)를 사용하여 생성된 명령 변형을 내보냅니다.

예를 들어 `Get-Item` 인증서 (Cert:)에서 명령의 변형을 내보내려면 드라이브의 PSSession에 `$S` 를 입력 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 합니다.

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

에서 만드는 모듈의 형식 파일 (* .Format.ps1xml) 또는 스크립트 모듈 파일 (. .psm1)에 서명 하는 데 사용 되는 클라이언트 인증서를 지정 합니다 `Export-PSSession` . 인증서가 포함된 변수를 입력하거나 인증서를 가져오는 명령 또는 식을 입력합니다.

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

지정한 이름 또는 이름 패턴을 가진 명령만 내보냅니다. 와일드카드가 지원됩니다. **CommandName** 또는 별칭, **이름** 을 사용 합니다.

기본적으로는 `Export-PSSession` 현재 세션에 있는 명령과 이름이 같은 명령을 제외한 모든 명령을 PSSession에서 내보냅니다. 그러면 명령이 현재 세션의 명령으로 숨겨지거나 대체 되지 않습니다. 다른 명령을 숨기 거 나 바꾸는 명령을 포함 하 여 모든 명령을 내보내려면 **AllowClobber** 매개 변수를 사용 합니다.

**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 내보내지 않습니다. 마찬가지로, **Formattypename** 매개 변수를 사용 하는 경우 **CommandName** 매개 변수를 사용 하지 않으면 명령을 내보내지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

지정한 유형의 명령 개체만 내보냅니다. **CommandType** 또는 별칭 **Type** 을 사용합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 앤티앨리어스. 현재 세션의 모든 PowerShell 별칭입니다.
- 모두. 모든 명령 유형입니다. 와 동일 합니다 `Get-Command -Name *` .
- 애플리케이션을 클릭합니다. `$env:path`.Txt, .exe 및 .dll 파일을 비롯 하 여 Path 환경 변수 ()에 나열 된 경로에 있는 PowerShell 파일 이외의 모든 파일
- #A0. 현재 세션에 있는 cmdlet입니다. 기본값은 Cmdlet입니다.
- 구성 PowerShell 구성. 자세한 내용은 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)를 참조 하세요.
- ExternalScript. Path 환경 변수 ()에 나열 된 경로에 있는 모든 ps1 파일 `$env:path`
- 필터 및 함수 모든 PowerShell 함수입니다.
- 스크립트. 현재 세션에 있는 스크립트 블록입니다.
- 워크플로. PowerShell 워크플로입니다. 자세한 내용은 [about_Workflows](../PSWorkflow/About/about_Workflows.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `UTF8`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.
- `BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.
- `Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다.
- `OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.
- `Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.
- `UTF7` 는 u t f-7을 사용 합니다.
- `UTF8` 는 u t f-8을 사용 합니다.
- `UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

파일에 읽기 전용 특성이 있어도 하나 이상의 기존 출력 파일을 덮어씁니다.

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

지정한 Microsoft .NET Framework 유형에 대한 형식 지정 명령만 내보냅니다. 유형 이름을 입력합니다. 기본적으로는 `Export-PSSession` **system.object** 네임 스페이스에 없는 모든 .NET Framework 형식에 대 한 형식 지정 명령을 내보냅니다.

이 매개 변수 값은 `Get-FormatData` 명령을 가져올 세션의 명령에서 반환 하는 형식의 이름 이어야 합니다. 원격 세션의 모든 형식 지정 데이터를 가져오려면를 입력 `*` 합니다.

**Formattypename** 매개 변수를 사용 하는 경우 **CommandName** 매개 변수를 사용 하지 않으면 명령을 내보내지 않습니다.

**CommandName** 매개 변수를 사용 하는 경우 **formattypename** 매개 변수를 사용 하지 않으면 명령에 대 한 형식 지정 파일을 내보내지 않습니다.

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

**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다. [ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션을 참조 하세요.

예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다. **모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다. 두 매개 변수는 함께 사용할 수 없습니다.

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

지정 된 PowerShell 스냅인 및 모듈의 명령만 내보냅니다. 스냅인 및 모듈 이름을 입력합니다. 와일드카드는 사용할 수 없습니다.

자세한 내용은 `Import-Module` 및 [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)을 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

에서 만든 모듈의 선택적 경로와 이름을 지정 합니다 `Export-PSSession` . 기본 경로는 `$home\Documents\WindowsPowerShell\Modules`입니다. 이 매개 변수는 필수적 요소입니다.

모듈 하위 디렉터리 또는를 만드는 파일이 이미 있는 경우 `Export-PSSession` 명령이 실패 합니다. 기존 파일을 덮어쓰려면 **Force** 매개 변수를 사용 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

명령을 내보낼 원본 PSSession을 지정합니다. 세션 개체 또는 세션 개체를 가져오는 명령 (예: 명령)을 포함 하는 변수를 입력 `Get-PSSession` 합니다. 이 매개 변수는 필수적 요소입니다.

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

개체를에 연결할 수 없습니다 `Export-PSSession` .

## 출력

### System.object

`Export-PSSession` 만든 모듈을 구성 하는 파일 목록을 반환 합니다.

## 참고

`Export-PSSession` 은 PowerShell 원격 인프라를 사용 합니다. 이 cmdlet을 사용하려면 원격 기능을 사용하도록 컴퓨터를 구성해야 합니다. 자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.

`Export-PSSession`를 사용 하 여 PowerShell 공급자를 내보낼 수는 없습니다.

내보낸 명령은 명령을 내보낸 원본 PSSession에서 암시적으로 실행됩니다. 원격으로 명령을 실행 하는 방법에 대 한 자세한 내용은 PowerShell에서 전체적으로 처리 됩니다. 내보낸 명령은 로컬 명령과 동일한 방식으로 실행할 수 있습니다.

`Export-ModuleMember` 내보내는 모듈에서 PSSession에 대 한 정보를 캡처하고 저장 합니다. 모듈을 가져올 때 명령이 내보내진 PSSession이 닫혀 있고 동일한 컴퓨터에 대 한 활성 PSSession이 없을 경우 모듈의 명령에서 PSSession을 다시 만들려고 시도 합니다. PSSession을 다시 만들지 못한 경우 내보낸 명령이 실행 되지 않습니다.

모듈에서 캡처 및 저장 하는 세션 정보에는 `Export-ModuleMember` `$PSSessionOption` 기본 설정 변수에 지정 하거나, 또는 Cmdlet의 **sessionoption** 매개 변수를 사용 하는 것과 같은 세션 옵션이 포함 되어 있지 않습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` . 모듈을 가져올 때 원본 PSSession이 닫혀 있을 경우 모듈은 동일한 컴퓨터에 대한 다른 PSSession을 사용합니다(사용 가능한 경우). 가져온 명령을 올바르게 구성된 세션에서 실행하려면 모듈을 가져오기 전에 원하는 옵션으로 PSSession을 만듭니다.

내보낼 명령을 찾기 위해는 cmdlet을 `Export-PSSession` 사용 하 여 `Invoke-Command` `Get-Command` PSSession에서 명령을 실행 합니다. 명령에 대 한 형식 지정 데이터를 가져오고 저장 하기 위해 `Get-FormatData` 및 cmdlet을 사용 `Export-FormatData` 합니다. `Invoke-Command` `Get-Command` `Get-FormatData` 명령을 실행할 때,, 및의 `Export-FormatData` 오류 메시지가 표시 될 수 있습니다 `Export-PSSession` . 또한는,, `Export-PSSession` 및 cmdlet을 포함 하지 않는 세션에서 명령을 내보낼 수 없습니다 `Get-Command` `Get-FormatData` `Select-Object` `Get-Help` .

`Export-PSSession` cmdlet을 사용 하 여 `Write-Progress` 명령 진행률을 표시 합니다. 명령이 실행되는 동안 진행률 표시줄을 확인할 수 있습니다.

내보낸 명령의 경우 사용자 인터페이스를 통해 메모장 등의 프로그램을 시작할 수 없다는 점을 포함하여 다른 원격 명령과 동일한 제한이 적용됩니다.

PowerShell 프로필은 pssession에서 실행 되지 않으므로 프로필을 통해 세션에 추가 하는 명령은에서 사용할 수 없습니다 `Export-PSSession` . 프로필에서 명령을 내보내려면 명령을 사용 하 여 명령을 `Invoke-Command` 내보내기 전에 PSSession에서 프로필을 수동으로 실행 합니다.

`Export-PSSession`명령에서 형식 지정 데이터를 가져오지 않는 경우에도에서 만드는 모듈에 서식 파일이 포함 될 수 있습니다. 명령이 형식 지정 데이터를 가져오지 않는 경우 만든 형식 지정 파일에 형식 지정 데이터가 포함되지 않습니다.

## 관련 링크

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[모듈 가져오기](../Microsoft.PowerShell.Core/Import-Module.md)

[Import-PSSession](Import-PSSession.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
