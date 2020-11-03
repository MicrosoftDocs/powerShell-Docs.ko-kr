---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 541059691e794591e85a8321a4507ed8838bcb4a
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "93219129"
---
# Update-Help

## 개요
최신 도움말 파일을 다운로드하여 컴퓨터에 설치합니다.

## SYNTAX

### Path (기본값)

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Update-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 컴퓨터에 설치 합니다. 변경 내용을 적용 하려면 PowerShell을 다시 시작 하지 않아도 됩니다. Cmdlet을 사용 `Get-Help` 하 여 새 도움말 파일을 즉시 볼 수 있습니다.

`Update-Help` 컴퓨터에 있는 도움말 파일의 버전을 확인 합니다. 모듈에 대 한 도움말 파일이 없거나 도움말 파일이 오래 된 경우에서 `Update-Help` 최신 도움말 파일을 다운로드 합니다. 도움말 파일은 인터넷 또는 파일 공유에서 다운로드 하 여 설치할 수 있습니다.

매개 변수를 사용 하지 않으면는 `Update-Help` 세션 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다. 현재 세션에 설치 되어 있지만 로드 되지 않은 모듈은 포함 됩니다. PowerShell 모듈은 환경 변수에 나열 된 위치에 저장 됩니다 `$env:PSModulePath` . 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조하세요.

**Module** 매개 변수를 사용 하 여 특정 모듈에 대 한 도움말 파일을 업데이트할 수 있습니다. **UICulture** 매개 변수를 사용 하 여 여러 언어 및 로캘로 도움말 파일을 다운로드 합니다.

인터넷에 연결 되지 않은 컴퓨터 에서도를 사용할 수 있습니다 `Update-Help` . 먼저, cmdlet을 사용 `Save-Help` 하 여 인터넷에서 도움말 파일을 다운로드 하 고 인터넷에 연결 되지 않은 시스템에서 액세스할 수 있는 공유 폴더에 저장 합니다. 그런 다음의 **SourcePath** 매개 변수를 사용 `Update-Help` 하 여 공유에서 업데이트 된 도움말 파일을 다운로드 하 고 컴퓨터에 설치 합니다.

PowerShell 프로필에 cmdlet을 추가 하 여 도움말 업데이트를 자동화할 수 있습니다 `Update-Help` . 기본적으로는 `Update-Help` 각 컴퓨터에서 하루에 한 번만 실행 됩니다. 매일 한 번이라는 제한을 재정의하려면 **Force** 매개 변수를 사용합니다.

`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다.

> [!IMPORTANT]
> `Update-Help` PowerShell 6.0 및 아래에서 관리 권한이 필요 합니다.
> PowerShell 6.1 이상에서는 기본 **범위** 를로 설정 `CurrentUser` 합니다.
> PowerShell 6.1 이전에는 **범위** 매개 변수를 사용할 수 없습니다.
>
> PowerShell 핵심 모듈에 대 한 도움말 파일을 업데이트 하려면 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.
>
> Powershell Core 모듈을 비롯 하 여 powershell 설치 디렉터리 ()의 모듈에 대 한 도움말 파일을 다운로드 하거나 업데이트 하려면 `$PSHOME\Modules` **관리자 권한으로 실행** 옵션을 사용 하 여 powershell을 시작 합니다.
> 예: `Start-Process pwsh.exe -Verb RunAs`

## 예제

### 예 1: 모든 모듈에 대 한 도움말 파일 업데이트

`Update-Help`Cmdlet은 업데이트할 수 있는 도움말을 지 원하는 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다. 운영 체제에서 UI (사용자 인터페이스) 문화권 언어를 설정 합니다.

```powershell
Update-Help
```

### 예 2: 지정 된 모듈에 대 한 도움말 파일 업데이트

`Update-Help`이 cmdlet은 **Microsoft PowerShell** 로 시작 하는 모듈 이름에 대해서만 도움말 파일을 업데이트 합니다.

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### 예 3: 다른 언어에 대 한 도움말 파일 업데이트

이 `Update-Help` cmdlet은 모든 모듈에 대해 일본어 (ja-jp) 및 영어 (en-us) 도움말 파일을 업데이트 합니다.

모듈에서 지정 된 UI 문화권에 대 한 도움말 파일을 제공 하지 않으면 모듈 및 UI 문화권에 대 한 오류 메시지가 표시 됩니다. 이 예제에서 오류 메시지는 모듈 **Microsoft. PowerShell** 에 대 한 **ja-jp** 도움말 파일을 찾을 수 없음을 나타냅니다.

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### 예제 4: 파일 공유에서 여러 컴퓨터에 대 한 도움말 파일 업데이트

이 예제에서 업데이트 된 도움말 파일은 인터넷에서 다운로드 되 고 파일 공유에 저장 됩니다. 파일 공유에 액세스 하 고 업데이트를 설치할 수 있는 권한이 있는 사용자 자격 증명이 필요 합니다. 파일 공유를 사용 하는 경우 방화벽으로 보호 되거나 인터넷에 연결 되지 않은 컴퓨터를 업데이트 하는 것이 가능 합니다.

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

`Save-Help`명령은 업데이트할 수 있는 도움말을 지 원하는 모든 모듈에 대 한 최신 도움말 파일을 다운로드 합니다.
**DestinationPath** 매개 변수는 파일 공유에 파일을 저장 합니다 `\\Server01\Share\PSHelp` . **Credential** 매개 변수는 파일 공유에 액세스할 수 있는 권한을 가진 사용자를 지정 합니다.

`Invoke-Command`Cmdlet은 `Update-Help` 여러 컴퓨터에서 원격 명령을 실행 합니다. **ComputerName** 매개 변수는 **Servers.txt** 파일에서 원격 컴퓨터의 목록을 가져옵니다. **ScriptBlock** 매개 변수는 `Update-Help` 명령을 실행 하 고 **SourcePath** 매개 변수를 사용 하 여 업데이트 된 도움말 파일을 포함 하는 파일 공유를 지정 합니다. **Credential** 매개 변수는 파일 공유에 액세스 하 고 원격 명령을 실행할 수 있는 사용자를 지정 합니다 `Update-Help` .

### 예 5: 업데이트 된 도움말 파일 목록 가져오기

`Update-Help`Cmdlet은 지정 된 모듈에 대 한 도움말을 업데이트 합니다. 이 cmdlet은 **Verbose** 일반 매개 변수를 사용 하 여 업데이트 된 도움말 파일의 목록을 표시 합니다. **자세한 정보** 표시를 사용 하 여 특정 모듈에 대 한 모든 도움말 파일 또는 도움말 파일의 출력을 볼 수 있습니다.

**Verbose** 매개 변수를 사용 하지 않으면 `Update-Help` 명령 결과를 표시 하지 않습니다. **Verbose** 매개 변수 출력은 도움말 파일이 업데이트 되었는지 또는 최신 버전이 설치 되어 있는지 확인 하는 데 유용 합니다.

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### 예제 6: 업데이트할 수 있는 도움말을 지 원하는 모듈 찾기

이 예제에서는 업데이트할 수 있는 도움말을 지 원하는 모듈을 나열 합니다. 이 명령은 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다. **HelpInfoUri** 속성에는 cmdlet이 실행 될 때 리디렉션되는 주소가 포함 되어 있습니다 `Update-Help` .

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### 예 7: 업데이트 된 도움말 파일 인벤토리

이 예제에서 스크립트는 `Get-UpdateHelpVersion.ps1` 각 모듈 및 해당 버전 번호에 대해 업데이트할 수 있는 도움말 파일의 인벤토리를 만듭니다.

스크립트는 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다. 업데이트할 수 있는 도움말을 지 원하는 모듈의 경우 스크립트는 도움말 정보 파일 (* helpinfo.xml)을 찾고 구문 분석 하 여 최신 버전 번호를 찾습니다.

이 스크립트는 **PSCustomObject** 클래스 및 해시 테이블을 사용 하 여 사용자 지정 출력 개체를 만듭니다.

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETERS

### -Credential

**SourcePath** 로 지정 된 파일 시스템 위치에 액세스할 수 있는 권한이 있는 사용자의 자격 증명을 지정 합니다. 이 매개 변수는 **SourcePath** 또는 **LiteralPath** 매개 변수가 명령에 사용된 경우에만 유효합니다.

**Credential** 매개 변수를 사용 하면 `Update-Help` 원격 컴퓨터에서 **SourcePath** 매개 변수를 사용 하 여 명령을 실행할 수 있습니다. 명시적 자격 증명을 제공 하 여 원격 컴퓨터에서 명령을 실행 하 고 액세스 거부 오류가 발생 하거나 CredSSP 인증을 사용 하 여 자격 증명을 위임 하지 않고도 세 번째 컴퓨터의 파일 공유에 액세스할 수 있습니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 cmdlet은 하루에 한 번만 수행 하 고, 버전 검사를 건너뛰고, 1gb 제한을 초과 하는 파일을 다운로드 함을 나타냅니다.

이 매개 변수를 사용 하지 않으면은 `Update-Help` 24 시간 마다 한 번만 실행 됩니다. 다운로드는 모듈 별로 압축 되지 않은 1gb로 제한 되며, 도움말 파일은 컴퓨터의 기존 파일 보다 최신 버전인 경우에만 설치 됩니다.

매일 한 번 제한은 도움말 파일을 호스트 하는 서버를 보호 하 고, 반복 되는 `Update-Help` 연결 또는 다운로드의 리소스 비용을 들이지 않고 PowerShell 프로필에 명령을 추가 하는 것이 실용적입니다.

**Force** 매개 변수 없이 여러 UI 문화권의 모듈에 대한 도움말을 업데이트하려면 동일한 명령에 모든 UI 문화권을 포함합니다. 예:

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -변수인 fullyqualifiedmodule

**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.
이러한 모듈은 [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션에 설명 되어 있습니다.

예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

또는

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.

**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.

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

### -LiteralPath

인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일에 대 한 폴더를 지정 합니다. Cmdlet을 사용 하 **SourcePath** 여 `Save-Help` 디렉터리에 도움말 파일을 다운로드 한 경우이 매개 변수 또는 SourcePath를 사용 합니다.

또는 cmdlet과 같은 디렉터리 개체를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .

**SourcePath** 의 값과 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -모듈

지정된 모듈에 대한 도움말을 업데이트합니다. 쉼표로 구분 된 목록에 하나 이상의 모듈 이름 또는 이름 패턴을 입력 하거나 각 줄에 하나의 모듈 이름을 나열 하는 파일을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다. Cmdlet에서 cmdlet으로 모듈 파이프라인을 만들 수 있습니다 `Get-Module` `Update-Help` .

지정 하는 모듈은 컴퓨터에 설치 해야 하지만 현재 세션으로 가져올 필요는 없습니다. 환경 변수에 나열 된 위치에 설치 된 모듈 또는 세션의 모든 모듈을 지정할 수 있습니다 `$env:PSModulePath` .

값 `*` (모두)은 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트 하려고 시도 합니다.
업데이트할 수 있는 도움말을 지원 하지 않는 모듈은 포함 되어 있습니다. 이 값은 명령이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견 하면 오류를 생성할 수 있습니다. 대신 `Update-Help` 매개 변수 없이 실행 합니다.

Cmdlet의 **module** 매개 변수는 `Update-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다. 위치에 없는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Update-Help` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -재귀

지정 된 디렉터리에 있는 도움말 파일에 대 한 재귀 검색을 수행 합니다. 이 매개 변수는 명령에서 **SourcePath** 매개 변수를 사용 하는 경우에만 유효 합니다.

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

### -범위

도움말이 업데이트 되는 시스템 범위를 지정 합니다. **AllUsers** 범위의 업데이트에는 Windows 시스템에 대 한 관리 권한이 필요 합니다. `-Scope`매개 변수는 PowerShell Core 버전 6.1에서 도입 되었습니다.

**CurrentUser** 는 PowerShell 6.1 이상에서 도움말 파일에 대 한 기본 범위입니다. **AllUsers** 를 지정 하 여 모든 사용자에 대 한 도움말을 설치 하거나 업데이트할 수 있습니다. Unix 시스템에서 `sudo` 모든 사용자에 대 한 도움말을 업데이트 하려면 권한이 필요 합니다. `sudo pwsh -c Update-Help`

사용 가능한 값은

- CurrentUser
- AllUsers

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePath

가 `Update-Help` 인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일을 가져오는 파일 시스템 폴더를 지정 합니다. 폴더의 경로를 입력 합니다. 파일 이름 또는 파일 이름 확장명을 지정 하지 마세요. 또는 cmdlet의 폴더와 같은 폴더를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .

기본적으로는 `Update-Help` 업데이트 된 도움말 파일을 인터넷에서 다운로드 합니다. Cmdlet **SourcePath** 을 사용 `Save-Help` 하 여 업데이트 된 도움말 파일을 디렉터리에 다운로드 한 경우 SourcePath를 사용 합니다.

**SourcePath** 의 기본값을 지정 하려면 **그룹 정책** , **컴퓨터 구성** 으로 이동 하 여 **update-help에 대 한 기본 원본 경로를 설정** 합니다. 이 그룹 정책 설정은 사용자가를 사용 하 여 `Update-Help` 인터넷에서 도움말 파일을 다운로드 하지 못하도록 합니다.
자세한 내용은 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)를 참조하세요.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

`Update-Help`에서 업데이트 된 도움말 파일을 가져오는 데 사용 하는 UI 문화권 값을 지정 합니다. 하나 이상의 언어 코드 (예: **es)** , culture 개체를 포함 하는 변수 또는 문화권 개체를 가져오는 명령 (예: 또는 명령)을 입력 `Get-Culture` `Get-UICulture` 합니다. 와일드 카드 문자를 사용할 수 없으며 **de** 와 같은 부분 언어 코드를 제출할 수 없습니다.

기본적으로는 `Update-Help` 운영 체제에 대해 설정 된 UI 문화권의 도움말 파일을 가져옵니다. **UICulture** 매개 변수를 지정 하는 경우는 `Update-Help` 지정 된 UI 문화권에 대 한 도움말만 찾습니다.

> [!NOTE]
> Ubuntu 18.04에서 기본 로캘 설정을 인식할 수 `C.UTF.8` 없는 UI 문화권이 아닌로 변경 했습니다. `Update-Help` 와 같은 지원 되는 로캘에서이 매개 변수를 사용 하지 않는 한 자동으로 도움말 다운로드에 실패 `en-US` 합니다. 지원 되지 않는 값을 사용 하는 모든 플랫폼에서 발생할 수 있습니다.

**UICulture** 매개 변수를 사용하는 명령은 모듈이 지정된 UI 문화권에 대한 도움말 파일을 제공하는 경우에 성공합니다. 지정 된 UI 문화권이 지원 되지 않기 때문에 명령이 실패 하면 오류 메시지가 표시 됩니다.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

에서 `Update-Help` 현재 사용자의 자격 증명을 사용 하 여 인터넷 다운로드를 포함 하 여 명령을 실행 함을 나타냅니다. 기본적으로 명령은 명시적 자격 증명 없이 실행됩니다.

이 매개 변수는 웹 다운로드에서 NTLM (NT LAN Manager), 협상 또는 Kerberos 기반 인증을 사용 하는 경우에만 적용 됩니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.io.directoryinfo

디렉터리 경로를로 파이프 할 수 있습니다 `Update-Help` .

### System.object..

Cmdlet에서로 모듈 개체를 파이프 할 수 있습니다 `Get-Module` `Update-Help` .

## 출력

### 없음

`Update-Help` 는 출력을 생성 하지 않습니다.

## 참고

Powershell과 함께 설치 되는 명령 또는 디렉터리의 모듈을 포함 하는 PowerShell 핵심 모듈에 대 한 도움말을 업데이트 하려면 `$PSHOME\Modules` **관리자 권한으로 실행** 하는 옵션을 사용 하 여 powershell을 시작 합니다.

컴퓨터의 Administrators 그룹 구성원만 PowerShell 핵심 모듈에 대 한 도움말, PowerShell과 함께 설치 되는 명령, 폴더의 모듈에 대 한 도움말을 업데이트할 수 있습니다 `$PSHOME\Modules` . 도움말 파일을 업데이트할 수 있는 권한이 없는 경우 온라인으로 도움말 파일을 읽을 수 있습니다. 예들 들어 `Get-Help Update-Help -Online`입니다.

모듈은 업데이트할 수 있는 도움말의 가장 작은 단위입니다. 특정 cmdlet에 대 한 도움말을 업데이트할 수 없습니다. 특정 cmdlet이 포함 된 모듈을 찾으려면 cmdlet의 **ModuleName** 속성 (예:)을 사용 `Get-Command` `(Get-Command Update-Help).ModuleName` 합니다.

도움말 파일이 모듈 디렉터리에 설치 되어 있기 때문에 `Update-Help` cmdlet은 컴퓨터에 설치 된 모듈에 대해서만 업데이트 된 도움말 파일을 설치할 수 있습니다. 그러나 cmdlet은 `Save-Help` 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장할 수 있습니다.

에서 `Update-Help` 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 없거나 지정 된 언어로 업데이트 된 도움말을 찾을 수 없는 경우 오류 메시지를 표시 하지 않고 자동으로 계속 됩니다. 세부적인 상태 및 진행 상황을 보려면 **Verbose** 매개 변수를 사용합니다.

`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다. 이전 버전의 PowerShell에서는 작동 하지 않습니다. Windows powershell 2.0 및 Windows PowerShell 3.0이 모두 있는 컴퓨터에서 `Update-Help` Windows powershell 3.0 세션의 cmdlet을 사용 하 여 도움말 파일을 다운로드 하 고 업데이트 합니다. 도움말 파일은 Windows PowerShell 2.0 및 Windows PowerShell 3.0에서 모두 사용할 수 있습니다.

`Update-Help`및 `Save-Help` cmdlet은 다음 포트를 사용 하 여 도움말 파일을 다운로드 합니다. HTTP의 경우 포트 80, HTTPS의 경우 포트 443

`Update-Help` 모든 모듈과 PowerShell 핵심 스냅인을 지원 합니다. 다른 스냅인은 지원 하지 않습니다.

환경 변수에 나열 되지 않은 위치에 있는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 모듈을 현재 세션으로 가져온 다음 `Update-Help` 명령을 실행 합니다. `Update-Help`매개 변수 없이 실행 하거나 **module** 매개 변수를 사용 하 여 모듈 이름을 지정 합니다. 및 cmdlet의 **module** 매개 변수는 `Update-Help` `Save-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.

모듈은 업데이트할 수 있는 도움말을 지원할 수 있습니다. 작성 하는 모듈에서 업데이트할 수 있는 도움말을 지 원하는 방법에 대 한 지침은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.

`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.

## 관련 링크

[Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Get-UICulture](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Start-Job](Start-Job.md)

[Save-Help](Save-Help.md)
