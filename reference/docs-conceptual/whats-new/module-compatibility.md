---
title: PowerShell 7 모듈 호환성
ms.date: 02/03/2020
ms.openlocfilehash: 273e25e3b7cd48e09b63e50c34ed0b98a4e766f0
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565066"
---
# <a name="powershell-7-module-compatibility"></a>PowerShell 7 모듈 호환성

이 문서에는 Microsoft에서 게시한 PowerShell 모듈의 목록이 포함되어 있습니다. 이러한 모듈은 다양한 Microsoft 제품 및 서비스에 대한 관리와 지원을 제공합니다. 각 모듈은 PowerShell 7에서 기본적으로 작동하도록 업데이트되었거나 PowerShell 7과의 호환성이 테스트되었습니다. 추가로 모듈을 식별하고 테스트하면 이 목록에 새로운 정보가 업데이트됩니다.

특정 모듈에 공유할 정보 또는 문제가 있는 경우 [WindowsCompatibility 리포지토리](https://github.com/PowerShell/WindowsCompatibility)에 문제를 제출하세요.

## <a name="windows-management-modules"></a>Windows 관리 모듈

Windows 관리 모듈은 Windows 버전 및 해당 버전에 대해 모듈이 패키징된 방식에 따라 다양한 방법으로 설치됩니다.

Windows Server에서는 관리자 권한으로 [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) cmdlet에서 기능 이름을 사용합니다. 다음은 그 예입니다.

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

Windows 10에서는 Windows 관리 모듈이 **Windows 선택적 기능** 또는 **Windows 기능**으로 제공됩니다. **관리자 권한으로 실행**을 사용하여 관리자 권한 세션에서 다음 명령을 실행해야 합니다.

- Windows 선택적 기능:

  선택적 기능 목록을 가져오려면 다음 명령을 실행합니다.

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  기능을 설치하려면

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  자세한 내용은 다음을 참조하세요.

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- Windows 기능:

  Windows 기능 목록을 가져오려면 다음 명령을 실행합니다.

  ```powershell
  Get-WindowsCapability -online
  ```

  기능 패키지의 이름은 `~~~~0.0.1.0`으로 끝납니다. 기능을 설치하려면 전체 이름을 사용해야 합니다.

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  자세한 내용은 다음을 참조하세요.

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>모듈 목록

| 모듈 이름                        | 상태                               | 지원되는 OS                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | 기본적으로 호환                  | RSAT-AD-PowerShell이 있는 Windows Server 1809 이상 버전<br>Rsat.ActiveDirectory.DS-LDS.Tools가 있는 Windows 10 1809 이상 버전 |
| ADFS                               | 호환성 계층으로 테스트되지 않음    |                                    |
| AppBackgroundTask                  | 기본적으로 호환                  | Windows 10 1903 이상 버전                   |
| AppLocker                          | 호환성 계층으로 테스트되지 않음    |                                    |
| AppvClient                         | 호환성 계층으로 테스트되지 않음    |                                    |
| Appx                               | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전 |
| AssignedAccess                     | 기본적으로 호환                  | Windows 10 1809 이상 버전                   |
| BestPractices                      | 호환성 계층으로 테스트되지 않음    |                                    |
| BitLocker                          | 기본적으로 호환                  | BitLocker가 있는 Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전 |
| BitsTransfer                       | 기본적으로 호환                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | 호환성 계층으로 테스트되지 않음    |                                        |
| BranchCache                        | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전 |
| CimCmdlets                         | 기본적으로 호환                  | PowerShell 7에 기본 제공 |
| ClusterAwareUpdating               | 호환성 계층으로 테스트되지 않음    |                         |
| ConfigCI                           | 호환성 계층으로 테스트되지 않음    |                         |
| Defender                           | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전  |
| DeliveryOptimization               | 기본적으로 호환                  | Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전  |
| DFSN                               | 기본적으로 호환                  | FS-DFS-Namespace가 있는 Windows Server 1809 이상 버전<br>Rsat.FailoverCluster.Management.Tools가 있는 Windows 10 1809 이상 버전 |
| DFSR                               | 호환성 계층으로 테스트되지 않음    |                                   |
| DhcpServer                         | 호환성 계층으로 테스트되지 않음    |                                   |
| DirectAccessClientComponents       | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전  |
| Dism                               | 기본적으로 호환                  | Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전  |
| DnsClient                          | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전  |
| DnsServer                          | 기본적으로 호환                  | DNS 또는 RSAT-DNS-Server가 있는 Windows Server 1809 이상 버전<br>Rsat.Dns.Tools가 있는 Windows 10 1809 이상 버전 |
| EventTracingManagement             | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전  |
| FailoverClusters                   | 호환성 계층으로 테스트되지 않음    |                                  |
| FailoverClusterSet                 | 호환성 계층으로 테스트되지 않음    |                                  |
| FileServerResourceManager          | 기본적으로 호환                  | FS-Resource-Manager가 있는 Windows Server 1809 이상 버전 |
| GroupPolicy                        | 호환성 계층으로 테스트되지 않음    |                                               |
| HgsClient                          | 기본적으로 호환                  | Hyper-V 또는 RSAT-Shielded-VM-Tools가 있는 Windows Server 1903 이상 버전<br>Rsat.Shielded.VM.Tools가 있는 Windows 10 1903 이상 버전 |
| HgsDiagnostics                     | 기본적으로 호환                  | Hyper-V 또는 RSAT-Shielded-VM-Tools가 있는 Windows Server 1809 이상 버전<br>Rsat.Shielded.VM.Tools가 있는 Windows 10 1809 이상 버전 |
| Hyper-V                            | 기본적으로 호환                  | Hyper-V-PowerShell이 있는 Windows Server 1809 이상 버전<br>Microsoft-Hyper-V-Management-PowerShell이 있는 Windows 10 1809 이상 버전 |
| IISAdministration                  | 호환성 계층으로 테스트되지 않음    |                                               |
| International                      | 기본적으로 호환                  | Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전      |
| IpamServer                         | 호환성 계층으로 테스트되지 않음    |                                               |
| iSCSI                              | 호환성 계층으로 테스트되지 않음    |                                               |
| IscsiTarget                        | 호환성 계층으로 테스트되지 않음    |                                               |
| ISE                                | 호환성 계층으로 테스트되지 않음    |                                               |
| Kds                                | 기본적으로 호환                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.PowerShell.Diagnostics   | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.PowerShell.Host          | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.PowerShell.LocalAccounts | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| Microsoft.PowerShell.Management    | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.PowerShell.ODataUtils    | 호환성 계층으로 테스트되지 않음    |                                               |
| Microsoft.PowerShell.Security      | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.PowerShell.Utility       | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| Microsoft.WSMan.Management         | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| MMAgent                            | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| MPIO                               | 기본적으로 호환                  | Multipath-IO가 있는 Windows Server 1809 이상 버전        |
| MsDtc                              | 호환성 계층으로 테스트되지 않음    |                                               |
| NetAdapter                         | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetConnection                      | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetEventPacketCapture              | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetLbfo                            | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetLldpAgent                       | 호환성 계층으로 테스트되지 않음    |                                               |
| NetNat                             | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetQos                             | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetSecurity                        | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetSwitchTeam                      | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetTCPIP                           | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetWNV                             | 호환성 계층으로 테스트되지 않음    |                                               |
| NetworkConnectivityStatus          | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetworkController                  | 호환성 계층으로 테스트되지 않음    |                                               |
| NetworkControllerDiagnostics       | 호환성 계층으로 테스트되지 않음    |                                               |
| NetworkLoadBalancingClusters       | 호환성 계층으로 테스트되지 않음    |                                               |
| NetworkSwitchManager               | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NetworkTransition                  | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| NFS                                | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Rsat.ServerManager.Tools가 있는 Windows 10 1809 이상 버전 |
| PackageManagement                  | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| PcsvDevice                         | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| PersistentMemory                   | 호환성 계층으로 테스트되지 않음    |                                               |
| PKI                                | 호환성 계층으로 테스트되지 않음    |                                               |
| PnpDevice                          | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| PowerShellGet                      | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| PrintManagement                    | 기본적으로 호환                  | Print-Services가 있는 Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전  |
| ProcessMitigations                 | 기본적으로 호환                  | Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전      |
| 프로비전                       | 호환성 계층으로 테스트되지 않음    |                                               |
| PSDesiredStateConfiguration        | 부분적으로                            | PowerShell 7에 기본 제공                       |
| PSDiagnostics                      | 기본적으로 호환                  | PowerShell 7에 기본 제공                       |
| PSScheduledJob                     | 호환성 계층에서 작동하지 않음 | PowerShell 5.1에 기본 제공                     |
| PSWorkflow                         | 호환성 계층으로 테스트되지 않음    |                                               |
| PSWorkflowUtility                  | 호환성 계층으로 테스트되지 않음    |                                               |
| RemoteAccess                       | 호환성 계층으로 테스트되지 않음    |                                               |
| RemoteDesktop                      | 호환성 계층으로 테스트되지 않음    |                                               |
| ScheduledTasks                     | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| SecureBoot                         | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| ServerCore                         | 호환성 계층으로 테스트되지 않음    |                                               |
| ServerManager                      | 호환성 계층으로 테스트되지 않음    |                                               |
| ServerManagerTasks                 | 호환성 계층으로 테스트되지 않음    |                                               |
| ShieldedVMDataFile                 | 기본적으로 호환                  | RSAT-Shielded-VM-Tools가 있는 Windows Server 1903 이상 버전<br>Rsat.Shielded.VM.Tools가 있는 Windows 10 1903 이상 버전 |
| ShieldedVMProvisioning             | 기본적으로 호환                  | HostGuardian이 있는 Windows Server 1809 이상 버전<br>HostGuardian이 있는 Windows 10 1809 이상 버전  |
| ShieldedVMTemplate                 | 기본적으로 호환                  | RSAT-Shielded-VM-Tools가 있는 Windows Server 1809 이상 버전<br>Rsat.Shielded.VM.Tools가 있는 Windows 10 1809 이상 버전 |
| SmbShare                           | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| SmbWitness                         | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| SMISConfig                         | 기본적으로 호환                  | WindowsStorageManagementService가 있는 Windows Server 1903 이상 버전 |
| sms                                | 호환성 계층으로 테스트되지 않음    |                                               |
| SoftwareInventoryLogging           | 기본적으로 호환                  | Windows Server 1809 이상 버전                          |
| StartLayout                        | 기본적으로 호환                  | Desktop Experience가 있는 Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전 |
| 스토리지                            | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| StorageBusCache                    | 호환성 계층으로 테스트되지 않음    |                                               |
| StorageMigrationService            | 호환성 계층으로 테스트되지 않음    |                                               |
| StorageQOS                         | 기본적으로 호환                  | RSAT-Clustering-PowerShell이 있는 Windows Server 1809 이상 버전<br>Rsat.FailoverCluster.Management.Tools가 있는 Windows 10 1809 이상 버전 |
| StorageReplica                     | 호환성 계층으로 테스트되지 않음    |                                               |
| SyncShare                          | 기본적으로 호환                  | FS-SyncShareService가 있는 Windows Server 1809 이상 버전 |
| SystemInsights                     | 호환성 계층으로 테스트되지 않음    |                                               |
| TLS                                | 호환성 계층으로 테스트되지 않음    |                                               |
| TroubleshootingPack                | 기본적으로 호환                  | Windows 10 1903 이상 버전                              |
| TrustedPlatformModule              | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| UEV                                | 기본적으로 호환                  | Windows Server ??Future version of Server with Desktop Experience??<br>Windows 10 1903 이상 버전 |
| UpdateServices                     | 호환성 계층에서 작동하지 않음 |                                               |
| VpnClient                          | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| Wdac                               | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| WebAdministration                  | 호환성 계층으로 테스트되지 않음    |                                               |
| WHEA                               | 기본적으로 호환                  | Windows Server 1903 이상 버전<br>Windows 10 1903 이상 버전      |
| WindowsDeveloperLicense            | 기본적으로 호환                  | Desktop Experience가 있는 Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전 |
| WindowsErrorReporting              | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전      |
| WindowsSearch                      | 기본적으로 호환                  | Windows 10 1903 이상 버전                              |
| WindowsServerBackup                | 기본적으로 호환                  | Windows-Server-Backup이 있는 Windows Server 19H2 |
| WindowsUpdate                      | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전       |
| WindowsUpdateProvider              | 기본적으로 호환                  | Windows Server 1809 이상 버전<br>Windows 10 1809 이상 버전       |
