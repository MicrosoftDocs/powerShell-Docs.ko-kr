---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 82721b3d079c795e0ce6fcae1fba0eab93344b52
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605222"
---
# Get-Help

## 개요
PowerShell 명령 및 개념에 대 한 정보를 표시 합니다.

## SYNTAX

### AllUsersView (기본값)

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 예

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 매개 변수

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 온라인

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## 설명

`Get-Help`Cmdlet은 cmdlet, 함수, CIM(Common Information Model) (CIM) 명령, 워크플로, 공급자, 별칭 및 스크립트를 포함 하 여 PowerShell 개념 및 명령에 대 한 정보를 표시 합니다.

PowerShell cmdlet에 대 한 도움말을 보려면을 입력 하 고 `Get-Help` cmdlet 이름 (예:)을 입력 `Get-Help Get-Process` 합니다.

PowerShell의 개념 도움말 문서는 **about_Comparison_Operators** 와 같은 **about_** 시작 합니다. 모든 **about_** 문서를 보려면을 입력 `Get-Help about_*` 합니다. 특정 아티클을 보려면 `Get-Help about_<article-name>` 와 같은를 입력 `Get-Help about_Comparison_Operators` 합니다.

PowerShell 공급자에 대 한 도움말을 보려면를 입력 한 `Get-Help` 다음 공급자 이름을 입력 합니다. 예를 들어 인증서 공급자에 대 한 도움말을 보려면을 입력 `Get-Help Certificate` 합니다.

`help` `man` 한 번에 하나의 텍스트 화면을 표시 하는 또는를 입력할 수도 있습니다. 와 `<cmdlet-name> -?` 동일 `Get-Help` 하지만 cmdlet에 대해서만 작동 하는 또는입니다.

`Get-Help` 컴퓨터의 도움말 파일에서 표시 하는 도움말 콘텐츠를 가져옵니다. 도움말 파일이 없으면에는 `Get-Help` cmdlet에 대 한 기본 정보만 표시 됩니다. 일부 PowerShell 모듈에는 도움말 파일이 포함 되어 있습니다. PowerShell 3.0 부터는 Windows 운영 체제와 함께 제공 되는 모듈에 도움말 파일이 포함 되지 않습니다. PowerShell 3.0의 모듈에 대 한 도움말 파일을 다운로드 하거나 업데이트 하려면 cmdlet을 사용 합니다 `Update-Help` .

Microsoft Docs에서 PowerShell 도움말 문서를 온라인으로 볼 수도 있습니다. 온라인 버전의 도움말 파일을 가져오려면와 같은 **online** 매개 변수를 사용 `Get-Help Get-Process -Online` 합니다. 모든 PowerShell 설명서를 읽으려면 Microsoft Docs [Powershell 설명서](/powershell)를 참조 하세요.

`Get-Help`다음에 도움말 아티클의 정확한 이름을 입력 하거나 도움말 문서에 고유한 단어를 입력 하는 경우 `Get-Help` 문서 내용이 표시 됩니다. 명령 별칭의 정확한 이름을 지정 하는 경우는 `Get-Help` 원래 명령에 대 한 도움말을 표시 합니다. 여러 도움말 문서 제목에 표시 되는 단어 또는 단어 패턴을 입력 하는 경우 `Get-Help` 일치 하는 타이틀의 목록이 표시 됩니다. 도움말 문서 제목에 표시 되지 않는 텍스트를 입력 하면에서 해당 `Get-Help` 텍스트를 포함 하는 문서 목록을 표시 합니다.

`Get-Help` 지원 되는 모든 언어 및 로캘에 대 한 도움말 문서를 볼 수 있습니다. `Get-Help` 는 먼저 Windows에 대해 설정 된 로캘, 부모 로캘 (예: pt의 경우 **pt** **-BR**)에서 도움말 파일을 찾은 다음 대체 (fallback) 로캘로 검색 합니다. PowerShell 3.0부터 `Get-Help` 대체 로캘에 대 한 도움말을 찾을 수 없는 경우는 오류 메시지를 반환 하거나 자동 생성 된 도움말을 표시 하기 전에 영어, **en-us** 에서 도움말 문서를 찾습니다.

명령 구문 다이어그램에 표시 되는 기호에 대 한 자세한 내용은 `Get-Help` [about_Command_Syntax](./About/about_Command_Syntax.md)를 참조 하세요.
**필수** 및 **위치** 와 같은 매개 변수 특성에 대 한 자세한 내용은 [about_Parameters](./About/about_Parameters.md)를 참조 하세요.

>[!NOTE]
> PowerShell 3.0 및 PowerShell 4.0에서는 `Get-Help` 모듈을 현재 세션으로 가져오지 않은 경우 모듈의 문서 **에 대 한 정보** 를 찾을 수 없습니다. 이것은 알려진 문제입니다. 모듈의 문서 **에 대 한 자세한** 내용을 보려면 cmdlet을 사용 `Import-Module` 하거나 모듈에 포함 된 cmdlet을 실행 하 여 모듈을 가져옵니다.

## 예제

### 예제 1: cmdlet에 대 한 기본 도움말 정보 표시

이 예에서는 cmdlet에 대 한 기본 도움말 정보를 표시 `Format-Table` 합니다.

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` 는 cmdlet의 가장 간단 하 고 기본적인 구문입니다 `Get-Help` . **Name** 매개 변수를 생략할 수 있습니다.

구문은 `<cmdlet-name> -?` cmdlet에 대해서만 작동 합니다.

### 예제 2: 한 번에 한 페이지씩 기본 정보 표시

이 예에서는 cmdlet에 대 한 기본 도움말 정보 `Format-Table` 를 한 번에 한 페이지씩 표시 합니다.

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` 는 `Get-Help` 내부적으로 cmdlet을 실행 하 고 결과를 한 번에 한 페이지씩 표시 하는 함수입니다.

`man` 는 함수에 대 한 별칭입니다 `help` .

`Get-Help Format-Table` 개체를 파이프라인 아래로 보냅니다. `Out-Host -Paging` 파이프라인에서 출력을 수신 하 고 한 번에 한 페이지씩 표시 합니다. 자세한 내용은 [Out-Host](Out-Host.md)를 참조 하세요.

### 예제 3: cmdlet에 대 한 추가 정보 표시

이 예에서는 cmdlet에 대 한 자세한 도움말 정보 `Format-Table` 를 표시 합니다.

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

**Detailed** 매개 변수는 매개 변수 설명 및 예제를 포함 하는 도움말 문서의 자세히 보기를 표시 합니다.

**Full** 매개 변수는 매개 변수 설명, 예제, 입력 및 출력 개체 형식, 추가 메모를 포함 하는 도움말 문서 전체 보기를 표시 합니다.

**자세히** 및 **전체** 매개 변수는 컴퓨터에 도움말 파일이 설치 된 명령에만 적용 됩니다. 이 매개 변수는 개념 (**about_**) 도움말 문서에는 적용 되지 않습니다.

### 예제 4: 매개 변수를 사용 하 여 cmdlet의 선택 된 부분 표시

이 예에서는 cmdlet 도움말의 선택 된 부분을 표시 `Format-Table` 합니다.

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

**예제** 매개 변수는 도움말 파일의 **NAME** 및 **개요** 섹션과 모든 예제를 표시 합니다. 예제 **매개 변수는 스위치** 매개 변수 이므로 예제 번호를 지정할 수 없습니다.

**매개** 변수 매개 변수는 지정 된 매개 변수에 대 한 설명만 표시 합니다. 별표 ( `*` ) 와일드 카드 문자만 지정 하면 모든 매개 변수에 대 한 설명이 표시 됩니다.
**매개** 변수가 **GroupBy** 와 같은 매개 변수 이름을 지정 하는 경우 해당 매개 변수에 대 한 정보가 표시 됩니다.

이러한 매개 변수는 개념 (**about_**) 도움말 문서에는 적용 되지 않습니다.

### 예 5: 온라인 버전의 도움말 표시

이 예에서는 `Format-Table` 기본 웹 브라우저에서 cmdlet에 대 한 도움말 문서의 온라인 버전을 표시 합니다.

```powershell
Get-Help Format-Table -Online
```

### 예 6: 도움말 시스템에 대 한 도움말 표시

`Get-Help`매개 변수가 없는 cmdlet은 PowerShell 도움말 시스템에 대 한 정보를 표시 합니다.

```powershell
Get-Help
```

### 예 7: 사용 가능한 도움말 문서 표시

이 예제에서는 컴퓨터에서 사용할 수 있는 모든 도움말 문서의 목록을 표시 합니다.

```powershell
Get-Help *
```

### 예 8: 개념 문서 목록 표시

이 예제에서는 PowerShell 도움말에 포함 된 개념 문서의 목록을 표시 합니다. 이러한 모든 문서는 **about_** 문자로 시작 합니다. 특정 도움말 파일을 표시 하려면를 입력 `Get-Help \<about_article-name\>` 합니다 (예:) `Get-Help about_Signing` .

컴퓨터에 도움말 파일이 설치 된 개념 문서만 표시 됩니다. PowerShell 3.0에서 도움말 파일을 다운로드 하 고 설치 하는 방법에 대 한 자세한 내용은 [update-help](Update-Help.md)를 참조 하세요.

```powershell
Get-Help about_*
```

### 예 9: cmdlet 도움말에서 단어 검색

이 예제에서는 cmdlet 도움말 문서에서 단어를 검색 하는 방법을 보여 줍니다.

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` 는 **전체** 매개 변수를 사용 하 여에 대 한 도움말 정보를 가져옵니다 `Add-Member` . **MamlCommandHelpInfo** 개체가 파이프라인으로 전송 됩니다. `Out-String`**Stream** 매개 변수를 사용 하 여 개체를 문자열로 변환 합니다. `Select-String`**Pattern** 매개 변수를 사용 하 여 **export-clixml** 에 대 한 문자열을 검색 합니다.

### 예 10: 단어를 포함 하는 문서 목록 표시

이 예에서는 **remoting** 이라는 단어를 포함 하는 문서의 목록을 표시 합니다.

문서 제목에 나타나지 않는 단어를 입력 하면에 `Get-Help` 해당 단어가 포함 된 문서 목록이 표시 됩니다.

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### 예 11: 공급자별 도움말 표시

이 예제에서는에 대 한 공급자별 도움말을 가져오는 두 가지 방법을 보여 줍니다 `Get-Item` . 이러한 명령은 `Get-Item` PowerShell SQL Server 공급자의 **DataCollection** 노드에서 cmdlet을 사용 하는 방법을 설명 하는 도움말을 가져옵니다.

첫 번째 예에서는 `Get-Help` **path** 매개 변수를 사용 하 여 SQL Server 공급자의 경로를 지정 합니다.
공급자의 경로가 지정 되었으므로 모든 경로 위치에서 명령을 실행할 수 있습니다.

두 번째 예제에서는를 사용 하 여 `Set-Location` SQL Server 공급자의 경로로 이동 합니다. 해당 위치에서 **경로** 매개 변수는 `Get-Help` 공급자 관련 도움말을 가져오는 데 필요 하지 않습니다.

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### 예 12: 스크립트에 대 한 도움말 표시

이 예제에서는에 대 한 도움말을 가져옵니다 `MyScript.ps1 script` . 함수 및 스크립트에 대 한 도움말을 작성 하는 방법에 대 한 자세한 내용은 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)를 참조 하세요.

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETERS

### -범주

지정된 범주 및 해당 별칭의 항목에 대한 도움말만 표시합니다. 개념 문서는 **HelpFile** 범주에 있습니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- Alias
- Cmdlet
- 공급자
- 일반
- FAQ
- 용어
- HelpFile
- ScriptCommand
- 함수
- Assert
- ExternalScript
- 모두
- DefaultHelp
- 워크플로
- DscResource
- 인스턴스
- Configuration

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -구성 요소

지정 된 구성 요소 값 (예: **Exchange**)을 사용 하 여 명령을 표시 합니다. 구성 요소 이름을 입력합니다.
와일드카드 문자를 사용할 수 있습니다. 이 매개 변수는 개념 (**About_**) 도움말의 표시에 영향을 주지 않습니다.

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

### -Detailed

매개 변수 설명과 예를 기본 도움말 표시에 추가합니다. 이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다. 개념 (**About_**) 도움말의 표시에는 영향을 주지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Examples

이름, 개요 및 예만 표시합니다. 예제만 표시 하려면을 입력 `(Get-Help \<cmdlet-name\>).Examples` 합니다.

이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다. 개념 (**About_**) 도움말의 표시에는 영향을 주지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

Cmdlet에 대 한 전체 도움말 문서를 표시 합니다. **전체** 에는 매개 변수 설명 및 특성, 예제, 입력 및 출력 개체 형식, 추가 참고 사항이 포함 됩니다.

이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다. 개념 (**About_**) 도움말의 표시에는 영향을 주지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -기능

지정된 기능이 있는 항목에 대한 도움말을 표시합니다. 기능을 입력하세요. 와일드카드 문자를 사용할 수 있습니다. 이 매개 변수는 개념 (**About_**) 도움말의 표시에 영향을 주지 않습니다.

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

지정된 명령 또는 개념에 대한 도움말을 가져옵니다. Cmdlet, 함수, 공급자, 스크립트 또는 워크플로의 이름을 입력 합니다 (예:). 예를 들어와 같은 `Get-Member` 개념 문서 이름 `about_Objects` 또는 별칭을 입력 `ls` 합니다. Cmdlet 및 공급자 이름에 와일드 카드 문자를 사용할 수 있지만 와일드 카드 문자를 사용 하 여 함수 도움말 및 스크립트 도움말 문서의 이름을 찾을 수는 없습니다.

환경 변수에 나열 된 경로에 없는 스크립트에 대 한 도움말을 보려면 `$env:Path` 스크립트의 경로와 파일 이름을 입력 합니다.

도움말 아티클의 정확한 이름을 입력 하면에서 `Get-Help` 문서 내용을 표시 합니다.

여러 도움말 문서 제목에 표시 되는 단어 또는 단어 패턴을 입력 하는 경우 `Get-Help` 일치 하는 타이틀의 목록이 표시 됩니다.

도움말 문서 제목과 일치 하지 않는 텍스트를 입력 하면에서 해당 `Get-Help` 텍스트를 포함 하는 문서 목록을 표시 합니다.

과 같은 개념 문서의 이름은 영어가 `about_Objects` 아닌 PowerShell 버전 에서도 영어로 입력 해야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Online

온라인 버전의 도움말 문서를 기본 브라우저에 표시 합니다. 이 매개 변수는 cmdlet, 함수, 워크플로 및 스크립트 도움말 문서에 대해서만 사용할 수 있습니다. **Online** 매개 변수는 `Get-Help` 원격 세션에서 사용할 수 없습니다.

작성 하는 도움말 문서에서이 기능을 지 원하는 방법에 대 한 자세한 내용은 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)및 [온라인 도움말 지원](/powershell/scripting/developer/module/supporting-online-help)및 [PowerShell Cmdlet에 대 한 도움말 작성](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

###  매개 변수

지정된 매개 변수에 대한 자세한 설명만 표시합니다. 와일드카드가 지원됩니다. 이 매개 변수는 개념 (**About_**) 도움말의 표시에 영향을 주지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

지정된 공급자 경로에서 cmdlet이 작동하는 방식을 설명하는 도움말을 가져옵니다. PowerShell 공급자 경로를 입력 하십시오.

이 매개 변수는 지정 된 PowerShell 공급자 경로에서 cmdlet이 작동 하는 방식을 설명 하는 cmdlet 도움말 아티클의 사용자 지정 된 버전을 가져옵니다. 이 매개 변수는 공급자 cmdlet에 대 한 도움말과 공급자가 해당 도움말 파일에 공급자 cmdlet 도움말 아티클의 사용자 지정 버전을 포함 하는 경우에만 적용 됩니다. 이 매개 변수를 사용하려면 공급자를 포함하는 모듈에 대한 도움말 파일을 설치합니다.

공급자 경로에 대 한 사용자 지정 cmdlet 도움말을 보려면 공급자 경로 위치로 이동 하 여 `Get-Help` 명령을 입력 하거나 경로 위치에서의 **path** 매개 변수를 사용 `Get-Help` 하 여 공급자 경로를 지정 합니다. 도움말 문서의 공급자 도움말 섹션에서 온라인으로 사용자 지정 cmdlet 도움말을 찾을 수도 있습니다.

PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](./About/about_Providers.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Role

지정된 사용자 역할에 맞게 사용자 지정된 도움말을 표시합니다. 역할을 입력하세요. 와일드카드 문자를 사용할 수 있습니다.

사용자가 조직에서 수행하는 역할을 입력합니다. 일부 cmdlet은 이 매개 변수 값을 기반으로 해당 도움말 파일에서 서로 다른 텍스트를 표시합니다. 이 매개 변수는 핵심 cmdlet의 도움말에는 영향을 주지 않습니다.

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

### -ShowWindow

도움말 항목을 더 쉽게 읽을 수 있도록 창에 표시합니다. 이 창에는 도움말 항목에서 선택한 섹션만 표시 하는 옵션을 비롯 하 여 표시 옵션을 설정할 수 있는 **찾기** 검색 기능 및 **설정** 상자가 포함 되어 있습니다.

**ShowWindow** 매개 변수는 명령 (cmdlet, 함수, CIM 명령, 스크립트) 및 개념 **관련** 문서에 대 한 도움말 항목을 지원 합니다. 공급자 도움말은 지원하지 않습니다.

이 매개 변수는 PowerShell 7.0에서 다시 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

파이프라인에서로 개체를 보낼 수 없습니다 `Get-Help` .

## 출력

### ExtendedCmdletHelpInfo

`Get-Help`도움말 파일이 없는 명령에서를 실행 하는 경우는 자동 `Get-Help` 생성 된 도움말을 나타내는 **ExtendedCmdletHelpInfo** 개체를 반환 합니다.

### System.String

개념 도움말 문서를 가져오는 경우이를 `Get-Help` 문자열로 반환 합니다.

### MamlCommandHelpInfo

도움말 파일이 있는 명령이 표시 되 면는 `Get-Help` **MamlCommandHelpInfo** 개체를 반환 합니다.

## 참고

PowerShell 3.0에는 도움말 파일이 포함 되어 있지 않습니다. 에서 읽는 도움말 파일을 다운로드 하 여 설치 하려면 `Get-Help` cmdlet을 사용 합니다 `Update-Help` . Cmdlet을 사용 하 여 `Update-Help` PowerShell과 함께 제공 되는 핵심 명령과 설치 하는 모듈에 대 한 도움말 파일을 다운로드 하 고 설치할 수 있습니다. 또한 이 cmdlet으로 도움말 파일을 업데이트하여 컴퓨터의 도움말이 오래되지 않도록 할 수 있습니다.

[Windows Powershell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)부터 powershell 온라인에서 제공 되는 명령에 대 한 도움말 문서를 읽을 수도 있습니다.

`Get-Help` Windows 운영 체제에 대해 설정 된 로캘 또는 해당 로캘의 대체 언어로 도움말을 표시 합니다. 기본 또는 대체 로캘에 대 한 도움말 파일이 없는 경우는 `Get-Help` 컴퓨터에 도움말 파일이 없는 것 처럼 동작 합니다. 다른 로캘에 대 한 도움말을 보려면 제어판의 **국가** 및 **언어** 를 사용 하 여 설정을 변경 합니다. Windows 10, **설정**, **시간 & 언어** 입니다.

도움말의 전체 보기에는 매개 변수에 대 한 정보 테이블이 포함 되어 있습니다. 이 테이블에는 다음 필드가 포함되어 있습니다.

- **필수**. 매개 변수가 필수(true)인지 선택 사항(false)인지를 나타냅니다.

- **위치**. 매개 변수의 이름이 지정 되었는지 아니면 위치 (숫자) 인지를 나타냅니다. 위치 매개 변수는 명령에서 지정된 위치에 표시해야 합니다.

- **명명** 됨은 매개 변수 이름이 필요 하지만 매개 변수가 명령의 아무 곳에 나 나타날 수 있음을 나타냅니다.

- **Numeric** 은 매개 변수 이름이 선택 사항 이지만 이름을 생략 하면 숫자에 지정 된 자리에 매개 변수가 있어야 함을 나타냅니다. 예를 들어는 `2` 매개 변수 이름이 생략 된 경우 매개 변수가 명령에서 두 번째 또는 유일한 명명 되지 않은 매개 변수 여야 함을 나타냅니다. 매개 변수 이름을 사용할 경우에는 해당 매개 변수를 명령에서 어느 위치에든 표시할 수 있습니다.

- **기본값** 입니다. 명령에 매개 변수를 포함 하지 않는 경우 PowerShell에서 사용 하는 매개 변수 값 또는 기본 동작입니다.

- 파이프라인 입력을 허용 합니다. 파이프라인을 통해 매개 변수에 개체를 보낼 수 있는지 (true) 또는 불가능 (false) 여부를 나타냅니다. **속성 이름으로** 파이프라인 개체에 매개 변수 이름과 이름이 같은 속성이 있어야 함을 의미 합니다.

- **와일드 카드 문자를 허용** 합니다. 매개 변수 값에 별표 ( `*` ) 또는 물음표 ()와 같은 와일드 카드 문자를 포함할 수 있는지 여부를 나타냅니다 `?` .

## 관련 링크

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[업데이트 가능한 도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)

[Update-Help](Update-Help.md)

[설명 기반 도움말 항목 작성](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[PowerShell cmdlet에 대한 도움말 작성](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

