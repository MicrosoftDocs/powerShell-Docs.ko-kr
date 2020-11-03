---
description: PowerShell에서 업데이트할 수 있는 도움말 시스템에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: cf528451e17ecdfd7fa53f99ed29a5d6d4abf075
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220826"
---
# <a name="about-updatable-help"></a>업데이트할 수 있는 도움말 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 업데이트할 수 있는 도움말 시스템에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 PowerShell cmdlet 및 개념에 대 한 최신 도움말 항목에 액세스할 수 있는 여러 가지 방법을 제공 합니다.

PowerShell 3.0에 도입 된 업데이트할 수 있는 도움말 시스템은 명령줄에서 읽을 수 있도록 로컬 컴퓨터에 항상 최신 도움말 항목을 제공 하도록 설계 되었습니다. 최신 도움말 파일을 사용할 수 있게 될 때마다 도움말 파일을 다운로드 하 여 설치 하 고 업데이트 하는 것이 쉽습니다.

엔터프라이즈의 여러 컴퓨터와 인터넷에 액세스할 수 없는 컴퓨터에 대 한 업데이트 된 도움말을 제공 하기 위해 업데이트할 수 있는 도움말을 사용 하 여 도움말 파일을 파일 시스템 디렉터리 또는 파일 공유로 다운로드 한 다음 파일 공유에서 도움말 파일을 설치할 수 있습니다.

PowerShell 4.0에서 **HelpInfoUri** 속성은 Windows PowerShell 원격을 통해 유지 됩니다 .이를 통해 `Save-Help` 원격 컴퓨터에 설치 된 모듈에 대해 작업을 수행할 수 있지만, 로컬 컴퓨터에 반드시 설치 해야 하는 것은 아닙니다. 인터넷에 액세스할 수 없는 컴퓨터에서를 실행 하 여 **psmoduleinfo** 개체를 디스크 또는 이동식 미디어 (예: USB 드라이브)에 저장 하 `Export-Clixml` 고, 인터넷에 액세스할 수 있는 컴퓨터에서 **psmoduleinfo** 개체를 가져온 다음, `Save-Help` **psmoduleinfo** 개체에서 실행할 수 있습니다. 저장 된 도움말은 이동식 미디어를 사용 하 여 원격으로 연결 되지 않은 컴퓨터에 복사 된 다음를 실행 하 여 설치할 수 있습니다 `Update-Help` . 이러한 기능 향상을 `Save-Help` 통해 어떤 종류의 네트워크 액세스가 없는 컴퓨터에 도움말을 설치할 수 있습니다. 새 기능을 사용 하는 방법에 대 한 예제는 `Save-Help` 이 항목의 [파일 공유에서 도움말을 업데이트 하는 방법](#how-to-update-help-from-a-file-share) 을 참조 하십시오.

업데이트할 수 있는 도움말은 컴퓨터에 도움말 파일이 없는 경우에도 최신 도움말 항목에 대 한 온라인 액세스와 cmdlet에 대 한 기본 도움말도 지원 합니다.

PowerShell 3.0에는 도움말 파일이 함께 제공 되지 않습니다. 업데이트할 수 있는 도움말 기능을 사용 하면 기본적으로 PowerShell 및 모든 Windows 모듈에 포함 된 모든 명령에 대 한 도움말 파일을 설치할 수 있습니다.

## <a name="updatable-help-cmdlets"></a>업데이트할 수 있는 도움말 cmdlet

- `Update-Help`: 인터넷 또는 파일 공유에서 최신 도움말 파일을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.

- `Save-Help`: 인터넷에서 최신 도움말 파일을 다운로드 하 여 파일 시스템 디렉터리 또는 파일 공유에 저장 합니다. 컴퓨터에 도움말 파일을 설치 하려면를 사용 `Update-Help` 합니다.

- `Get-Help`: 명령줄에 도움말 항목을 표시 합니다. 컴퓨터의 도움말 파일에서 도움말을 가져옵니다. 도움말 파일이 없는 cmdlet 및 함수에 대해 자동 생성 된 도움말을 표시 합니다. 기본 인터넷 브라우저에서 cmdlet, 함수, 스크립트 및 워크플로에 대 한 온라인 도움말 항목을 엽니다.

## <a name="auto-generated-help-help-without-help-files"></a>자동 생성 된 도움말: 도움말 파일이 없는 도움말

컴퓨터의 cmdlet, 함수 또는 워크플로에 대 한 도움말 파일이 없으면 `Get-Help` cmdlet에서 자동 생성 된 도움말을 표시 하 고 도움말 파일을 다운로드 하거나 온라인으로 읽을 지 묻는 메시지를 표시 합니다.

자동 생성 된 도움말에는 구문과 별칭이 포함 되며, 업데이트할 수 있는 도움말 cmdlet을 사용 하 여 온라인 도움말 항목에 액세스 하는 방법을 설명 하는 설명이 포함 됩니다.

예를 들어 다음 명령은 cmdlet에 대 한 기본 도움말을 가져옵니다 `Get-Culture` . `Get-Help`컴퓨터에 도움말 파일이 없으면 출력에 표시 되는 내용이 표시 됩니다.

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>모듈에 대 한 도움말 파일

업데이트할 수 있는 도움말의 가장 작은 단위는 모듈에 대 한 도움말입니다. 모듈 도움말에는 모듈의 모든 cmdlet, 함수, 워크플로, 공급자, 스크립트 및 개념에 대 한 도움말이 포함 되어 있습니다. 현재 세션으로 가져오지 않은 경우에도 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트할 수 있습니다.

전체 모듈에 대 한 도움말을 업데이트할 수 있지만 개별 cmdlet에 대 한 도움말을 업데이트할 수는 없습니다.

특정 cmdlet이 포함 된 모듈을 찾으려면 다음 명령 형식을 사용 합니다.

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

예를 들어 cmdlet이 포함 된 모듈을 찾으려면 `Set-ExecutionPolicy` 다음을 입력 합니다.

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

특정 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.

```powershell
Update-Help -Module <ModuleName>
```

예를 들어 Set-ExecutionPolicy cmdlet을 포함 하는 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>업데이트할 수 있는 도움말에 대 한 사용 권한

디렉터리의 모듈에 대 한 도움말을 업데이트 하려면 `$pshome/Modules` 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.

관리자 그룹의 구성원이 아닌 경우 이러한 모듈에 대 한 도움말을 업데이트할 수 없습니다. 그러나 인터넷에 액세스할 수 있는 경우 온라인 도움말을 볼 수 있습니다.

디렉터리의 모듈 또는 디렉터리의 다른 하위 디렉터리에 있는 모듈에 대 한 도움말을 업데이트 `$home/Documents/PowerShell/Modules` `$home` 하려면 특별 한 권한이 필요 하지 않습니다.

`Update-Help`및 cmdlet에는 `Save-Help` 현재 사용자의 명시적 자격 증명을 제공 하는 **UseDefaultCredentials** 매개 변수가 있습니다. 이 매개 변수는 보안 인터넷 위치에 액세스 하기 위한 것입니다.

`Update-Help`또한 및 `Save-Help` cmdlet에는 원격 컴퓨터에서 명령을 실행 하 고 세 번째 컴퓨터의 파일 공유에 액세스할 수 있는 **자격 증명** 매개 변수가 있습니다. **Credential** 매개 변수는의 SourcePath 또는 **LiteralPath** 매개 변수와 `Update-Help` 의 **DestinationPath** 또는 **LiteralPath** 매개 변수를 사용 하는 경우에만 유효 합니다 `Save-Help` .

## <a name="how-to-install-and-update-help-files"></a>도움말 파일을 설치 하 고 업데이트 하는 방법

처음으로 도움말 파일을 다운로드 하 여 설치 하거나 컴퓨터에서 도움말 파일을 업데이트 하려면 cmdlet을 사용 합니다 `Update-Help` .

`Update-Help`Cmdlet은 다음 작업을 포함 하 여 모든 하드 작업을 수행 합니다.

- 업데이트할 수 있는 도움말을 지 원하는 모듈을 결정 합니다.
- 각 모듈이 업데이트할 수 있는 도움말 파일을 저장 하는 인터넷 위치를 찾습니다.
- 컴퓨터의 각 모듈에 대 한 도움말 파일을 각 모듈에서 사용할 수 있는 최신 도움말 파일과 비교 합니다.
- 인터넷에서 새 파일을 다운로드 합니다.
- 도움말 파일 패키지를의 래핑을 해제.
- 파일이 유효한 도움말 파일 인지 확인 합니다.
- 모듈 디렉터리의 언어별 하위 디렉터리에 도움말 파일을 설치 합니다.

새 도움말 항목에 액세스 하려면 cmdlet을 사용 합니다 `Get-Help` . PowerShell을 다시 시작할 필요는 없습니다.

업데이트할 수 있는 도움말을 지 원하는 컴퓨터의 모든 모듈에 대 한 도움말을 설치 하거나 업데이트 하려면 다음을 입력 합니다.

```powershell
Update-Help
```

특정 모듈에 대 한 도움말을 업데이트 하려면의 **모듈** 매개 변수를 추가 `Update-Help` 합니다. 모듈 이름에 와일드 카드 문자를 사용할 수 있습니다.

예를 들어 ServerManager 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.

```powershell
Update-Help -Module ServerManager
```

매개 변수가 없으면 `Update-Help` 세션의 모든 모듈 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말을 업데이트 합니다. 포함 하려면 모듈을 PSModulePath 환경 변수 값에 나열 된 디렉터리에 설치 해야 합니다. "Get-help-ListAvailable" 명령에 의해 반환 되는 모듈 이기도 합니다.

**Module** 매개 변수 값이 `*` (all) 이면에서 `Update-Help` 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 비롯 하 여 설치 된 모든 모듈에 대 한 도움말을 업데이트 하려고 시도 합니다. 이 명령은 일반적으로 cmdlet이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견할 때 많은 오류를 생성 합니다.

## <a name="how-to-update-help-from-a-file-share"></a>파일 공유에서 도움말을 업데이트 하는 방법

인터넷에 연결 되지 않은 컴퓨터를 지원 하거나 엔터프라이즈에서 도움말 업데이트를 제어 하거나 간소화 하려면 cmdlet을 사용 `Save-Help` 합니다. 이 `Save-Help` cmdlet은 인터넷에서 도움말 파일을 다운로드 하 여 지정한 파일 시스템 디렉터리에 저장 합니다.

`Save-Help` 지정 된 디렉터리에 있는 도움말 파일을 각 모듈에서 사용할 수 있는 최신 도움말 파일과 비교 합니다. 모듈에 대 한 도움말 파일이 나 최신 도움말 파일을 디렉터리에 사용할 수 없는 경우이 `Save-Help` cmdlet은 인터넷에서 새 파일을 다운로드 합니다. 그러나 도움말 파일은 래핑을 해제 하거나 설치 하지 않습니다.

파일 시스템 디렉터리에 저장 된 도움말 파일에서 컴퓨터의 도움말 파일을 설치 하거나 업데이트 하려면 cmdlet의 **SourcePath** 매개 변수를 사용 합니다 `Update-Help` . `Update-Help`Cmdlet은 최신 도움말 파일을 식별 하 고의 래핑을 해제 및 유효성을 검사 한 다음 모듈 디렉터리의 언어별 하위 디렉터리에 설치 합니다.

예를 들어 디렉터리에 설치 된 모든 모듈에 대 한 도움말을 저장 하려면 `\\Server\Share` 다음을 입력 합니다.

```powershell
Save-Help -DestinationPath \\Server\Share
```

그런 다음 디렉터리에서 도움말을 업데이트 하려면 `\\Server\Share` 다음을 입력 합니다.

```powershell
Update-Help -SourcePath \\Server\Share
```

다음 예에서는를 사용 하 여 `Save-Help` 로컬 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장 하는 방법을 보여 줍니다. 이 예에서는 관리자가를 실행 `Save-Help` 하 여 로컬 컴퓨터에 DhcpServer 모듈 또는 DHCP 서버 역할을 설치 하지 않고 인터넷에 연결 된 클라이언트 컴퓨터에서 DhcpServer 모듈에 대 한 도움말을 저장 합니다.

옵션 1:을 실행 `Invoke-Command` 하 여 원격 모듈의 **psmoduleinfo** 개체를 가져온 다음 변수에 저장 하 `$m` 고 변수를 `Save-Help` 모듈 이름으로 지정 하 여 **psmoduleinfo** 개체에서 실행 합니다 `$m` .

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

옵션 2: DHCP 서버 모듈을 실행 하는 컴퓨터에서 대상으로 하는 PSSession을 열고, 모듈에 대 한 **Psmoduleinfo** 개체를 가져오고, 변수에 저장 한 `$m` 후 `Save-Help` 변수에 저장 된 개체에서를 실행 합니다 `$m` .

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

옵션 3: DHCP 서버 모듈을 실행 하는 컴퓨터에서 대상으로 하는 CIM 세션을 열고 모듈의 **Psmoduleinfo** 개체를 가져온 다음 변수에 저장 된 `$m` `Save-Help` 개체에서 실행 합니다 `$m` .

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

다음 예에서는 관리자가 네트워크에 액세스할 수 없는 컴퓨터에 DHCP 서버 모듈에 대 한 도움말을 설치 합니다.

먼저를 실행 `Export-Clixml` 하 여 **Psmoduleinfo** 개체를 공유 폴더 또는 이동식 미디어로 내보냅니다.

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

다음으로, 인터넷에 액세스할 수 있는 컴퓨터에 이동식 미디어를 전송 하 고를 사용 하 여 **Psmoduleinfo** 개체를 가져옵니다 `Import-Clixml` . `Save-Help`을 실행 하 여 가져온 DhcpServer 모듈 **Psmoduleinfo** 개체에 대 한 도움말을 저장 합니다.

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

마지막으로, 네트워크에 액세스할 수 없는 컴퓨터에 이동식 미디어를 다시 전송 하 고를 실행 하 여 도움말을 설치 `Update-Help` 합니다.

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

매개 변수가 없으면 `Save-Help` 세션의 모든 모듈 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말을 다운로드 합니다. 포함 하려면 모듈을 `$env:PSModulePath` 로컬 컴퓨터 또는 도움말을 저장할 원격 컴퓨터의 환경 변수 값에 나열 된 디렉터리에 설치 해야 합니다. 이는 명령을 실행 하 여 반환 되는 모듈 이기도 `Get-Help -ListAvailable` 합니다.

## <a name="how-to-update-help-files-in-different-languages"></a>다른 언어로 도움말 파일을 업데이트 하는 방법

기본적으로 `Update-Help` 및 cmdlet은 `Save-Help` 로컬 컴퓨터의 Windows에 대해 설정 된 UI 문화권 및 언어에 대 한 도움말을 다운로드 합니다. 지정 된 모듈에 대 한 도움말 파일을 로컬 UI 문화권에서 사용할 수 없는 `Update-Help` 경우 `Save-Help` Windows 언어 대체 규칙을 사용 하 여 지원 되는 최상의 언어를 찾습니다.

그러나 및 cmdlet의 **UICulture** 매개 변수를 사용 `Update-Help` 하 여 `Save-Help` 사용 가능한 모든 UI 문화권에서 도움말 파일을 다운로드 하 고 설치할 수 있습니다.

예를 들어 세션의 모든 모듈에 대 한 최신 도움말 파일을 일본어 (Ja-jp)와 프랑스어 (fr-fr)로 저장 하려면 다음을 입력 합니다.

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

모듈에 대 한 도움말 파일을 지정한 언어로 사용할 수 없는 경우 `Update-Help` 및 `Save-Help` cmdlet은 각 모듈의 도움말이 제공 되는 언어를 나열 하는 오류 메시지를 반환 하므로 사용자 요구에 가장 적합 한 대체 항목을 선택할 수 있습니다.

> [!NOTE]
> 현재, 업데이트 가능한 도움말 콘텐츠는 영어 (en-us)로만 게시 됩니다. 일부 비 Windows 시스템에서는 **UICulture** 매개 변수를 사용 하 여 콘텐츠를 명시적으로 요청 해야 합니다 `en-US` .

## <a name="how-to-use-online-help"></a>온라인 도움말을 사용 하는 방법

로컬 컴퓨터에서 도움말 파일을 업데이트 하지 않거나 업데이트할 수 없는 경우에도 최신 도움말 파일을 온라인으로 가져올 수 있습니다.

Cmdlet 또는 함수에 대 한 온라인 도움말 항목을 열려면 cmdlet의 **online** 매개 변수를 사용 합니다 `Get-Help` .

예를 들어 다음 명령은 `Get-Job` 기본 인터넷 브라우저에서 cmdlet에 대 한 온라인 도움말 항목을 엽니다.

```powershell
Get-Help Get-Job -Online
```

스크립트에 대 한 온라인 도움말을 보려면 **온라인** 매개 변수와 스크립트의 전체 경로를 사용 합니다.

**Online** 매개 변수는 About 토픽에서 작동 하지 않습니다. Powershell 언어에 대 한 도움말 항목을 포함 하 여 PowerShell에 대 한 정보 항목을 보려면 [Powershell 정보 항목](about.md)을 참조 하세요.

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>인터넷 다운로드를 최소화 하거나 차단 하는 방법

인터넷에 연결 되지 않은 사용자에 게 업데이트할 수 있는 도움말을 제공 하 고 인터넷 다운로드를 최소화 하려면 cmdlet을 사용 합니다 `Save-Help` . 인터넷에서 도움말을 다운로드 하 여 네트워크 공유에 저장 합니다. 그런 다음 `Update-Help` 모든 컴퓨터에서 명령을 실행 하는 그룹 정책 설정 또는 예약 된 작업을 만듭니다. Cmdlet의 **SourcePath** 매개 변수 값을 `Update-Help` 네트워크 공유로 설정 합니다.

인터넷에 액세스할 수 있는 사용자가 인터넷에서 업데이트할 수 있는 도움말을 다운로드 하지 못하게 하려면 **update-help에 대 한 기본 원본 경로 설정** 그룹 정책 설정을 사용 합니다.

이 그룹 정책 설정은 지정 하는 파일 시스템 위치를 사용 하 여 모든 영향을 받는 컴퓨터의 모든 명령에 **SourcePath** 매개 변수를 암시적으로 추가 합니다 `Update-Help` . 사용자는 **sourcepath** 매개 변수를 명시적으로 사용 하 여 다른 파일 시스템 위치를 지정할 수 있지만 **sourcepath** 매개 변수를 제외 하 고 인터넷에서 도움말을 다운로드할 수 없습니다.

> [!NOTE]
> **컴퓨터 구성** 및 **사용자 구성** 아래에는 **update-help에 대 한 기본 원본 경로 설정** 그룹이 표시 됩니다. 그러나 **컴퓨터 구성** 에서 정책 설정만 적용 됩니다. **사용자 구성** 에서 정책 설정은 무시 됩니다.

자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)를 참조하세요.

## <a name="how-to-update-help-for-non-standard-modules"></a>비표준 모듈에 대 한 도움말을 업데이트 하는 방법

Cmdlet의 **ListAvailable** 매개 변수에서 반환 되지 않은 모듈에 대 한 도움말을 업데이트 하거나 저장 하려면 `Get-Module` 또는 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Update-Help` `Save-Help` . 원격 컴퓨터에서 명령을 실행 하기 전에 `Save-Help` 원격 컴퓨터에 연결 된 현재 세션 또는 스크립트 블록으로 모듈을 가져옵니다 `Invoke-Command` .

모듈이 현재 세션에 있는 경우 `Update-Help` `Save-Help` 매개 변수 없이 또는 cmdlet을 실행 하거나 module 매개 변수를 사용 **Module** 하 여 모듈 이름을 지정 합니다.

및 cmdlet의 **모듈** 매개 변수에는 `Update-Help` `Save-Help` 모듈 이름만 사용할 수가 있습니다. 모듈 파일에 대 한 경로를 허용 하지 않습니다.

이 방법을 사용 하 여 cmdlet의 **ListAvailable** 매개 변수 `Get-Module` (예: 환경 변수에 나열 되지 않은 위치에 설치 된 모듈 또는 제대로 구성 되지 않은 모듈)에 대 한 도움말을 업데이트 하거나 저장할 수 `$env:PSModulePath` 있습니다. 모듈 디렉터리에 basename가 디렉터리 이름과 동일한 파일이 하나 이상 포함 되어 있지 않습니다.

## <a name="how-to-support-updatable-help"></a>업데이트할 수 있는 도움말을 지 원하는 방법

모듈을 작성 하는 경우 모듈에 대 한 온라인 도움말 및 업데이트할 수 있는 도움말을 지원할 수 있습니다. 자세한 내용은 Microsoft Docs에서 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/help/supporting-updatable-help) 및 [온라인 도움말 지원](/powershell/scripting/developer/module/supporting-online-help) 을 참조 하세요.

PowerShell 스냅인 또는 주석 기반 도움말에서 업데이트할 수 있는 도움말을 사용할 수 없습니다.

## <a name="remarks"></a>설명

`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.

## <a name="see-also"></a>참고 항목

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
