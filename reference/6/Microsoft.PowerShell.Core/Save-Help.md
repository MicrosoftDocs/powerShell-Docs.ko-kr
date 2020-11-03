---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 4b7e74d7b83dbf5128b30e1bbf2c51d69c3a235a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217170"
---
# Save-Help

## 개요
최신 도움말 파일을 다운로드하여 파일 시스템 디렉터리에 저장합니다.

## SYNTAX

### Path (기본값)

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### LiteralPath

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## 설명

**저장-도움말** Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 지정한 디렉터리에 저장 합니다.
이 기능을 통해 인터넷에 액세스할 수 없는 컴퓨터에서 도움말 파일을 업데이트할 수 있으며, 여러 컴퓨터에서 도움말 파일을 업데이트할 수 있습니다.

Windows PowerShell 3.0에서 **저장-도움말** 은 로컬 컴퓨터에 설치 된 모듈에 대해서만 작동 합니다.
원격 컴퓨터에서 모듈을 가져올 수도 있지만 PowerShell 원격을 사용 하 여 원격 컴퓨터에서 **Psmoduleinfo** 개체에 대 한 참조를 가져올 수도 있지만 **HelpInfoUri** 속성은 유지 되지 않으며 **저장-도움말이** 원격 모듈 도움말에 대해 작동 하지 않습니다.

Windows PowerShell 4.0에서 **HelpInfoUri** 속성은 PowerShell 원격 기능을 통해 유지 되며,이를 통해 원격 컴퓨터에 설치 된 모듈을 저장 하는 **데 도움이** 됩니다.
인터넷에 액세스할 수 없는 컴퓨터에서 Export-Clixml를 실행 하 고 인터넷에 액세스할 수 있는 컴퓨터에서 개체를 가져온 다음 **psmoduleinfo** 개체에서 **save Help** 를 실행 하 여 **psmoduleinfo** 개체를 디스크나 이동식 미디어에 저장할 수도 있습니다.
이동식 저장소 미디어 (예: USB 드라이브)를 사용 하 여 저장 된 도움말을 원격 컴퓨터로 전송할 수 있습니다.
Help **는 update-help를 실행 하** 여 원격 컴퓨터에 설치할 수 있습니다.
이 프로세스는 어떤 유형의 네트워크에도 액세스할 수 없는 컴퓨터에 도움말을 설치하는 데 사용할 수 있습니다.

저장 된 도움말 파일을 설치 하려면 Update-Help cmdlet을 실행 합니다.
*SourcePath* 매개 변수를 추가 하 여 도움말 파일을 저장 한 폴더를 지정 합니다.

매개 변수를 지정하지 않으면 **Save-Help** 명령은 세션의 모든 모듈과 컴퓨터에서 **PSModulePath** 환경 변수에 나열된 위치에 설치된 모듈에 대한 최신 도움말을 다운로드합니다.
이 작업은 경고 없이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 건너뜁니다.

**저장-도움말** cmdlet은 대상 폴더에 있는 도움말 파일의 버전을 확인 합니다.
최신 도움말 파일을 사용할 수 있는 경우이 cmdlet은 인터넷에서 최신 도움말 파일을 다운로드 한 다음 폴더에 저장 합니다.
**저장-도움말** cmdlet은 캐비닛 파일에서 도움말 파일을 추출 하 여 컴퓨터에 설치 하는 대신 다운로드 한 캐비닛 (.cab) 파일을 저장 하는 것을 제외 하 고는 Update-Help cmdlet과 똑같이 작동 합니다.

각 모듈에 대해 저장된 도움말은 도움말 정보(HelpInfo XML) 파일과 각 UI 문화권의 도움말 파일 캐비닛(.cab) 파일로 구성됩니다.
캐비닛 파일에서 도움말 파일을 추출할 필요는 없습니다.
**Update-help** cmdlet은 도움말 파일을 추출 하 고 안전성에 대 한 XML의 유효성을 검사 한 다음 모듈 폴더의 언어별 하위 폴더에 도움말 파일 및 도움말 정보 파일을 설치 합니다.

PowerShell 설치 폴더 ($pshome \Modules)의 모듈에 대 한 도움말 파일을 저장 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.
이러한 모듈에 대한 도움말 파일을 다운로드하려면 컴퓨터에서 Administrators 그룹의 구성원이어야 합니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: DhcpServer 모듈에 대 한 도움말 저장

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module, save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

이 예제에서는 로컬 컴퓨터에 **DhcpServer** 모듈 또는 DHCP 서버 역할을 설치 하지 않고 **DhcpServer** 모듈에 대 한 도움말을 인터넷에 연결 된 클라이언트 컴퓨터에서 **저장 하는** 세 가지 방법을 보여 줍니다.

### 예 2: DhcpServer 모듈에 대 한 도움말 설치

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

이 예제에서는 인터넷에 액세스할 수 없는 컴퓨터의 **DhcpServer** 모듈에 대해 예제 1에서 저장 한 도움말을 설치 하는 방법을 보여 줍니다.

### 예 3: 모든 모듈에 대 한 도움말 저장

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

이 명령은 로컬 컴퓨터에서 Windows용 UI 문화권 집합에 있는 모든 모듈에 대한 최신 도움말 파일을 다운로드합니다.
도움말 파일을 Server01\Fileshare01 폴더에 저장 합니다 \\ \\ .

### 예 4: 컴퓨터의 모듈에 대 한 도움말 저장

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

이 명령은 **ServerManager** 모듈에 대 한 최신 도움말 파일을 다운로드 한 다음 Server01\Fileshare01 폴더에 저장 \\ \\ 합니다.

모듈이 컴퓨터에 설치되면 모듈을 현재 세션으로 가져오지 않은 경우에도 *Module* 매개 변수 값으로 모듈 이름을 입력할 수 있습니다.

이 명령은 *Credential* 매개 변수를 사용하여 파일 공유에 쓸 수 있는 권한을 가진 사용자의 자격 증명을 제공합니다.

### 예 5: 다른 컴퓨터의 모듈에 대 한 도움말 저장

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

이러한 명령은 **Customsql** 모듈에 대 한 최신 도움말 파일을 다운로드 하 고 Server01\Fileshare01 폴더에 저장 합니다 \\ \\ .

**Customsql** 모듈이 컴퓨터에 설치 되어 있지 않기 때문에 시퀀스에는 Server02 컴퓨터에서 customsql 모듈에 대 한 module 개체를 가져온 다음 module 개체를 **cmdlet으로** 파이프 하는 Invoke-Command 명령이 포함 되어 있습니다.

모듈이 컴퓨터에 설치되어 있지 않으면 **Save-Help** 에는 최신 도움말 파일의 위치에 대한 정보를 포함하는 모듈 개체가 필요합니다.

### 예제 6: 여러 언어로 된 모듈에 대 한 도움말 저장

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

이 명령은 4 가지 UI 문화권의 PowerShell 핵심 모듈에 대 한 도움말을 저장 합니다.
이러한 로캘의 언어 팩을 컴퓨터에 설치할 필요는 없습니다.

**저장-도움말** 파일은 모듈 소유자가 인터넷에서 번역 된 파일을 사용할 수 있도록 하는 경우에만 다른 UI 문화권의 모듈에 대 한 도움말 파일을 다운로드할 수 있습니다.

### 예 7: 매일 한 번 이상 도움말 저장

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

이 명령은 컴퓨터에 설치된 모든 모듈을 대한 도움말을 저장합니다.
이 명령은 **Save help** cmdlet이 24 시간 마다 두 번 이상 도움말을 다운로드 하지 못하도록 하는 규칙을 재정의 하는 *Force* 매개 변수를 지정 합니다.

*Force* 매개 변수도 1gb 제한과 우회 버전 검사를 재정의 합니다.
따라서 버전이 대상 폴더의 버전 보다 최신 버전이 아닌 경우에도 파일을 다운로드할 수 있습니다.

이 명령은 **Save help** cmdlet을 사용 하 여 도움말 파일을 다운로드 하 여 지정 된 폴더에 저장 합니다.
*Force* 매개 변수는 매일 두 번 이상 **Save Help** 명령을 실행 해야 하는 경우에 필요 합니다.

## PARAMETERS

### -Credential

사용자 자격 증명을 지정 합니다. 이 cmdlet은 **DestinationPath** 매개 변수로 지정 된 파일 시스템 위치에 액세스할 수 있는 권한이 있는 사용자의 자격 증명을 사용 하 여 명령을 실행 합니다. 이 매개 변수는 **DestinationPath** 또는 **LiteralPath** 매개 변수가 명령에 사용 되는 경우에만 유효 합니다.

이 매개 변수를 사용 하면 `Save-Help` 원격 컴퓨터에서 **DestinationPath** 매개 변수를 사용 하는 명령을 실행할 수 있습니다. 명시적 자격 증명을 제공 하 여 원격 컴퓨터에서 명령을 실행 하 고 액세스 거부 오류가 발생 하거나 CredSSP 인증을 사용 하 여 자격 증명을 위임 하지 않고도 세 번째 컴퓨터의 파일 공유에 액세스할 수 있습니다.

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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DestinationPath

도움말 파일이 저장 되는 폴더의 경로를 지정 합니다.
파일 이름 또는 파일 이름 확장명은 지정하지 마세요.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 cmdlet은 하루에 한 번 제한을 따르지 않고 버전 검사를 건너뛰고 1gb 제한을 초과 하는 파일을 다운로드 함을 나타냅니다.

이 매개 변수를 지정하지 않으면 각 모듈에 대한 **Save-Help** 명령이 24시간마다 한 번만 허용되고, 다운로드는 모듈당 1GB의 압축되지 않은 콘텐츠로 제한되고, 모듈의 도움말 파일은 컴퓨터의 파일에 있는 버전보다 최신 버전일 경우에만 설치됩니다.

매일 한 번 제한은 도움말 파일을 호스트 하는 서버를 보호 하 고 PowerShell 프로필에 **저장-도움말** 명령을 추가 하는 것이 실용적입니다.

*Force* 매개 변수 없이 여러 ui 문화권의 모듈에 대 한 도움말을 저장 하려면 동일한 명령에 모든 ui 문화권을 포함 합니다 (예:).`Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -변수인 fullyqualifiedmodule

ModuleSpecification 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.
이 내용은 MSDN library의 [ModuleSpecification 생성자 (Hashtable)](https://msdn.microsoft.com/library/jj136290) 의 설명 섹션에 설명 되어 있습니다.
예를 들어 *변수인 fullyqualifiedmodule* 매개 변수는 @ {ModuleName = "ModuleName" 형식으로 지정 된 모듈 이름을 허용 합니다. ModuleVersion = "version_number"} 또는 @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}.
**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.

*모듈* 매개 변수와 동일한 명령에 *변수인 fullyqualifiedmodule* 매개 변수를 지정할 수 없습니다.

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

대상 폴더의 경로를 지정 합니다.
*DestinationPath* 매개 변수 값과 달리 *LiteralPath* 매개 변수의 값은 입력 한 대로 사용 됩니다.
어떠한 문자도 와일드카드 문자로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -모듈

이 cmdlet이 도움말을 다운로드 하는 모듈을 지정 합니다.
하나 이상의 모듈 이름 또는 이름 패턴를 쉼표로 구분 된 목록 또는 각 줄에 하나의 모듈 이름이 있는 파일에 입력 합니다.
와일드카드 문자를 사용할 수 있습니다.
Get-Module cmdlet에서 모듈 개체를 파이프로 파이프 하 여 **저장할** 수도 있습니다.

기본적으로 **Save-Help** 는 업데이트할 수 있는 도움말을 지원하며 로컬 컴퓨터에서 **PSModulePath** 환경 변수에 나열된 위치에 설치되어 있는 모든 모듈의 도움말을 다운로드합니다.

컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장 하려면 원격 컴퓨터에서 **import-module** 명령을 실행 합니다.
그런 다음 생성된 모듈 개체를 **Save-Help** cmdlet에 파이프하거나 모듈 개체를 *Module* 또는 *InputObject* 매개 변수 값으로 제출합니다.

지정한 모듈이 컴퓨터에 설치되어 있는 경우 모듈 이름 또는 모듈 개체를 입력할 수 있습니다.
모듈이 컴퓨터에 설치되지 않은 경우 모듈 개체(예: **Get-Module** cmdlet에 의해 반환되는 개체)를 입력해야 합니다.

**Save Help** Cmdlet의 *module* 매개 변수는 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.
**PSModulePath** 위치에 없는 모듈에 대 한 도움말을 저장 하려면 **저장-도움말** 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다.

"*" (모두)의 값은 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트 하려고 합니다.
여기에는 업데이트할 수 있는 도움말을 지원 하지 않는 모듈도 포함 됩니다.
이 값은 명령이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견 하면 오류를 생성할 수 있습니다.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UICulture

이 cmdlet이 업데이트 된 도움말 파일을 가져오는 UI 문화권 값을 지정 합니다.
하나 이상의 언어 코드 (예: es), culture 개체를 포함 하는 변수 또는 문화권 개체를 가져오는 명령 (예: Get-Culture 또는 Get-UICulture 명령)을 입력 합니다.

와일드카드 문자는 사용할 수 없습니다.
부분 언어 코드 (예: "de")를 지정 하지 마십시오.

기본적으로 **저장 도움말** 은 Windows 또는 대체 문화권에 대해 설정 된 UI 문화권의 도움말 파일을 가져옵니다.
*UICulture* 매개 변수를 지정 하는 경우 **Save-help** 는 대체 문화권이 아니라 지정 된 UI 문화권에 대 한 도움말만 찾습니다.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

이 cmdlet은 현재 사용자의 자격 증명을 사용 하 여 웹 다운로드를 포함 하 여 명령을 실행 함을 나타냅니다.
기본적으로 명령은 명시적 자격 증명 없이 실행됩니다.

이 매개 변수는 웹 다운로드에서 NTLM, 협상 또는 kerberos 기반 인증을 사용하는 경우에만 유효합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -범위

이 매개 변수는이 cmdlet에서 아무 작업도 수행 하지 않습니다.

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.object..

**Get-help** cmdlet의 module 개체를 **Save-Help** 의 *module* 매개 변수로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 모듈에 대 한 도움말을 $pshome \Modules 폴더에 저장 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다. 컴퓨터의 Administrators 그룹 구성원만 $pshome \Modules 폴더의 모듈에 대 한 도움말을 다운로드할 수 있습니다.
* 각 모듈에 대해 저장된 도움말은 도움말 정보(HelpInfo XML) 파일과 각 UI 문화권의 도움말 파일 캐비닛(.cab) 파일로 구성됩니다. 캐비닛 파일에서 도움말 파일을 추출할 필요는 없습니다. Update-Help cmdlet은 도움말 파일을 추출 하 고 XML의 유효성을 검사 한 다음 모듈 폴더의 언어별 하위 폴더에 도움말 파일 및 도움말 정보 파일을 설치 합니다.
* **Save-Help** cmdlet은 컴퓨터에 설치되지 않은 모듈에 대한 도움말을 저장할 수 있습니다. 그러나 도움말 파일이 module 폴더에 설치 되기 때문에 **update-help** cmdlet은 컴퓨터에 설치 된 모듈에 대해서만 업데이트 된 도움말 파일을 설치할 수 있습니다.
* **Save-Help** 에서 모듈에 대해 업데이트된 도움말 파일을 찾지 못하거나 지정된 언어의 업데이트된 도움말을 찾을 수 없는 경우 오류 메시지를 표시하지 않으면서 계속 자동으로 찾습니다. 명령으로 저장 된 파일을 보려면 *Verbose* 매개 변수를 지정 합니다.
* 모듈은 업데이트할 수 있는 도움말의 가장 작은 단위입니다. 모듈의 모든 cmdlet에 대 한 특정 cmdlet에 대 한 도움말은 저장할 수 없습니다. 특정 cmdlet이 포함 된 모듈을 찾으려면 Get-Command cmdlet과 함께 **ModuleName** 속성을 사용 합니다 (예:). `(Get-Command \<cmdlet-name\>).ModuleName`
* **Save-Help** 는 모든 모듈과 PowerShell 핵심 스냅인을 지원 합니다. 다른 스냅인은 지원 하지 않습니다.
* **업데이트-도움말** 및 **저장-도움말** cmdlet은 다음 포트를 사용 하 여 도움말 파일을 다운로드 합니다. HTTP의 경우 포트 80, HTTPS의 경우 포트 443
* **Update-Help** 및 **Save-Help** cmdlet은 Windows PE(Windows 사전 설치 환경)에서 지원되지 않습니다.

## 관련 링크

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Update-Help](Update-Help.md)
