---
description: PowerShell DSC (필요한 상태 구성) 기능에 대 한 간략 한 소개를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224889"
---
# <a name="about_desiredstateconfiguration"></a>about_DesiredStateConfiguration

## <a name="short-description"></a>간단한 설명

PowerShell DSC (필요한 상태 구성) 기능에 대 한 간략 한 소개를 제공 합니다.

## <a name="long-description"></a>자세한 설명

DSC는 소프트웨어 서비스에 대 한 구성 데이터를 배포 및 관리 하 고 이러한 서비스가 실행 되는 환경을 관리할 수 있도록 하는 PowerShell의 관리 플랫폼입니다.

DSC는 소프트웨어 환경의 상태를 구성 하는 방법을 선언적으로 지정 하는 데 사용할 수 있는 PowerShell 언어 확장, 새 cmdlet 및 리소스 집합을 제공 합니다. 또한 기존 구성을 유지하고 관리하는 수단을 제공합니다.

DSC는 PowerShell 4.0에서 도입 되었습니다.

DSC에 대 한 자세한 내용은 TechNet 라이브러리에서 [PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/overview) 를 참조 하세요.

## <a name="developing-dsc-resources-with-classes"></a>클래스를 사용 하 여 DSC 리소스 개발

PowerShell 5.0부터 클래스를 사용 하 여 DSC 리소스를 개발할 수 있습니다.
자세한 내용은 [about_Classes](about_Classes.md)및 Microsoft TechNet의 [PowerShell 클래스를 사용 하 여 사용자 지정 DSC 리소스 작성](/previous-versions//dn948461(v=technet.10)) 을 참조 하세요.

## <a name="using-dsc"></a>DSC 사용

DSC를 사용 하 여 환경을 구성 하려면 먼저 구성 키워드를 사용 하 여 PowerShell 스크립트 블록을 정의 하 고 그 뒤에 식별자를 사용 하 여 블록을 구분 합니다. 구성 블록 내에서 환경의 각 노드 (컴퓨터)에 대해 원하는 구성 상태를 지정 하는 노드 블록을 정의할 수 있습니다. 노드 블록은 Node 키워드를 사용 하 여 시작 하 고, 대상 컴퓨터의 이름은 변수가 될 수 있습니다. 컴퓨터 이름 뒤에는 노드 블록을 구분 하는 중괄호가 있습니다. 노드 블록 내에서 리소스 블록을 정의 하 여 특정 리소스를 구성할 수 있습니다. 리소스 블록은 리소스의 형식 이름으로 시작 하 여 다음 예제에 표시 된 것 처럼 블록을 구분 하는 중괄호 뒤에 해당 블록에 대해 지정 하려는 식별자가 나옵니다.

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

구성을 만들려면 PowerShell 함수를 호출 하는 것과 동일한 방식으로 구성 블록을 호출 합니다 .이 함수는 정의 된 것으로 예상 되는 매개 변수를 전달 합니다 (위 예제에서는 2 개). 예를 들어,이 경우는 다음과 같습니다.

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

그러면 지정 된 경로에 노드당 MOF 파일이 생성 됩니다. 이러한 MOF 파일은 각 노드에 대해 원하는 구성을 지정 합니다. 그런 다음, 다음 cmdlet을 사용 하 여 구성 MOF 파일을 구문 분석 하 고 각 노드를 해당 구성으로 보내고 이러한 구성을 적용 합니다. 클래스 기반 DSC 리소스에 대 한 별도의 MOF 파일을 만들 필요는 없습니다.

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a>DSC를 사용 하 여 구성 상태 유지 관리

DSC를 사용 하면 구성이 idempotent 됩니다. 즉, DSC를 사용 하 여 동일한 구성을 두 번 이상 시행 하는 경우 결과 구성 상태는 항상 동일 합니다. 따라서 환경의 모든 노드가 원하는 구성 상태에서 데이터베이스가 드리프트 수 있는 것으로 의심 되는 경우 동일한 DSC 구성을 다시 설정 하 여 다시 원하는 상태로 전환할 수 있습니다. 상태가 원하는 상태에서 데이터베이스가 드리프트 된 리소스만 처리 하도록 구성 스크립트를 수정할 필요는 없습니다.

다음 예에서는 지정 된 노드에 대 한 실제 구성 상태가 노드의 마지막 DSC 구성에서 데이터베이스가 드리프트 여부를 확인 하는 방법을 보여 줍니다. 이 예제에서는 로컬 컴퓨터의 구성을 확인 합니다.

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a>기본 제공 DSC 리소스

구성 스크립트에서 다음과 같은 기본 제공 리소스를 사용할 수 있습니다.

|속성                  |속성                                         |
|----------------------|---------------------------------------------------|
|파일                  |{DestinationPath, Attributes, Checksum, Content ...}|
|보관               |{Destination, Path, Checksum, Credential ...}       |
|Environment           |{Name, DependsOn, 확인, 경로 ...}                 |
|그룹                 |{GroupName, Credential, DependsOn, Description ...} |
|로그                   |{Message, DependsOn, PsDscRunAsCredential}         |
|패키지               |{Name, Path, ProductId, Arguments ...}              |
|레지스트리              |{Key, ValueName, DependsOn, 확인 ...}             |
|스크립트                |{GetScript, SetScript, TestScript, Credential ...}  |
|서비스               |{Name, 속성과 builtinaccount, Credential, 종속성 ...}|
|사용자                  |{UserName, DependsOn, Description, Disabled ...}    |
|WaitForAll            |{NodeName, Context.resourcename, DependsOn, PsDscRunAsC ...}|
|WaitForAny            |{NodeName, Context.resourcename, DependsOn, PsDscRunAsC ...}|
|WaitForSome           |{NodeCount, NodeName, Context.resourcename, DependsOn ...}  |
|WindowsFeature        |{Name, Credential, DependsOn, 확인 ...}           |
|WindowsOptionalFeature|{Name, DependsOn, 확인, LogLevel ...}             |
|WindowsProcess        |{Arguments, Path, Credential, DependsOn ...}        |

시스템에서 사용할 수 있는 DSC 리소스 목록을 가져오려면 cmdlet을 실행 `Get-DscResource` 합니다.

> [!NOTE]
> 7\.0 이전 PowerShell 버전에서 `Get-DscResource`는 클래스 기반 DSC 리소스를 찾지 않습니다.

이 항목의 예제에서는 파일 및 Add-windowsfeature 리소스를 사용 하는 방법을 보여 줍니다. 리소스에 사용할 수 있는 모든 속성을 보려면 PowerShell ISE의 구성 스크립트 내에서 리소스 키워드 (예: 파일)에 커서를 삽입 하 고 <kbd>ctrl</kbd> + <kbd>스페이스바</kbd> 를 누릅니다.

## <a name="find-more-resources"></a>추가 리소스 찾기

PowerShell 및 DSC 사용자 커뮤니티 및 Microsoft에서 만든 다른 많은 DSC 리소스를 다운로드 하 여 설치 하 고 알아볼 수 있습니다. [PowerShell 갤러리](https://www.powershellgallery.com/) 를 방문 하 여 사용 가능한 DSC 리소스를 찾아보고 알아보세요.

## <a name="see-also"></a>참고 항목

[PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/overview)

[기본 제공 PowerShell 필요한 상태 구성 리소스](/powershell/scripting/dsc/resources/resources)

[사용자 지정 PowerShell 필요한 상태 구성 리소스 빌드](/powershell/scripting/dsc/resources/authoringResource)
