---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: 노드 다시 부팅
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680743"
---
# <a name="reboot-a-node"></a>노드 다시 부팅

> [!NOTE]
> 이 항목에서는 노드를 다시 부팅 하는 방법을 설명 합니다. 찾기가 성공 하려면 다시 부팅 순서에서를 **ActionAfterReboot** 및 **RebootNodeIfNeeded** LCM 설정을 올바르게 구성 해야 합니다.
> 로컬 구성 관리자 설정에 대 한 내용은 참조 하세요 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md), 또는 [구성 로컬 구성 관리자 (v4)](../managing-nodes/metaConfig4.md)합니다.

노드 다시 부팅할 수에서 리소스를 내에서 사용 하 여는 `$global:DSCMachineStatus` 플래그입니다. 이 플래그 설정 `1` 에 `Set-TargetResource` 함수 후 노드를 직접 다시 부팅 하도록 LCM을 강제로 합니다 **설정** 현재 리소스의 메서드. 이 플래그를 사용 하는 **xPendingReboot** 리소스 검색을 다시 부팅이 보류 중인 경우 DSC 외부입니다.

프로그램 [구성을](configurations.md) 노드를 다시 부팅 해야 하는 단계를 수행할 수 있습니다. 와 같은 작업을 포함할 수 없습니다이:

- Windows: 업데이트
- 소프트웨어 설치
- 파일의 이름을 바꿉니다.
- 컴퓨터 이름 바꾸기

합니다 **xPendingReboot** 리소스는 다시 부팅이 보류 중인 경우를 확인 하려면 특정 컴퓨터 위치를 확인 합니다. 노드는 DSC 외부에서 다시 부팅 해야 하는 경우는 **xPendingReboot** 리소스 집합을 `$global:DSCMachineStatus` 플래그를 `1` 강제로 다시 부팅 되 고, 보류 중 상태를 해결 합니다.

> [!NOTE]
> 모든 DSC 리소스는 LCM에서이 플래그를 설정 하 여 노드를 다시 부팅을 지시할 수는 `Set-TargetResource` 함수입니다. 자세한 내용은 [MOF 사용 하 여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceMOF.md)합니다.

## <a name="syntax"></a>구문

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>속성

| 속성 | 설명 |
| --- | --- |
| 이름| 구성 내에서 리소스의 인스턴스당 고유 해야 하는 필수 매개 변수입니다.|
| SkipComponentBasedServicing | 구성 요소 기반 서비스 구성 요소에 의해 트리거되는 Skip 재부팅 합니다. |
| SkipWindowsUpdate | Windows 업데이트에 의해 트리거되는 Skip 재부팅 합니다.|
| SkipPendingFileRename | 보류 중인 파일 이름 바꾸기 다시 부팅을 건너뜁니다. |
| SkipCcmClientSDK | ConfigMgr 클라이언트에 의해 트리거되는 Skip 재부팅 합니다. |
| SkipComputerRename | Skip은 컴퓨터 이름을 변경 하 여 트리거된 다시 부팅 합니다. |
| PSDSCRunAsCredential | V5에서 지원 합니다. 지정된 된 사용자로 리소스를 실행합니다. |
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. 자세한 내용은 참조 하세요. [DependsOn 사용](resource-depends-on.md)|

## <a name="example"></a>예제

다음 예제에서는 Microsoft Exchange를 사용 하 여 설치 합니다 [xExchange](https://github.com/PowerShell/xExchange) 리소스입니다.
전체 설치를 **xPendingReboot** 리소스는 노드를 다시 부팅 하는 데 사용 됩니다.

> [!NOTE]
> 이 예제에는 포리스트에 Exchange server를 추가할 권한이 있는 계정의 자격 증명이 필요 합니다. 자격 증명을 사용 하 여 DSC에 대 한 자세한 내용은 참조 하세요. [DSC에서 자격 증명 처리](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> 이 예제에서는 재부팅을 허용 하 고 다시 부팅 한 후 구성을 계속 하려면 로컬 Configuration Manager 구성 했다고 가정 합니다.

## <a name="where-to-download"></a>다운로드 위치

다음 위치에서 또는 PowerShell 갤러리를 사용 하 여이 항목에서 사용 하는 리소스를 다운로드할 수 있습니다.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
