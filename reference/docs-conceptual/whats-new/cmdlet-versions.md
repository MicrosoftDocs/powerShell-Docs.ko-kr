---
ms.date: 02/03/2020
keywords: powershell,core
title: 모듈 및 cmdlet의 릴리스 기록
ms.openlocfilehash: e421201d74da2cc74b1bd57529fb3c3e5245ecae
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995448"
---
# <a name="release-history-of-modules-and-cmdlets"></a>모듈 및 cmdlet의 릴리스 기록

이 문서에서는 다양한 버전의 PowerShell과 함께 제공되는 모듈 및 cmdlet을 나열합니다. 릴리스 정보에 있는 내용에 대한 요약이 제공되며 자세한 내용은 다음 릴리스 정보에서 찾을 수 있습니다.

- [PowerShell Core 6.2의 새로운 기능](what-s-new-in-powershell-core-62.md)
- [PowerShell Core 6.1의 새로운 기능](what-s-new-in-powershell-core-61.md)
- [PowerShell Core 6.0의 새로운 기능](what-s-new-in-powershell-core-60.md)
- [PowerShell Core 6.0의 호환성이 손상되는 변경](breaking-changes-ps6.md)
- [PowerShell Core 6.0의 알려진 문제](known-issues-ps6.md)

진행 중인 작업입니다. 이 정보를 최신 상태로 유지할 수 있도록 도와주세요.

## <a name="module-release-history"></a>모듈 릴리스 기록

|         모듈 이름/PS 버전          |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Windows만 해당 |
| 2\.0에 도입된 ISE                   | &check; |         |         |         | Windows만 해당 |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Windows만 해당 |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | Windows만 해당 |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | Windows만 해당 |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | Windows만 해당 |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WsMan.Management                | &check; | &check; | &check; | &check; | Windows만 해당 |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Windows만 해당 |
| PSReadline 1.x                            | &check; |         |         |         | Windows만 해당 |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Windows만 해당 |
| PSWorkflow                                | &check; |         |         |         | Windows만 해당 |
| PSWorkflowUtility                         | &check; |         |         |         | Windows만 해당 |
| ThreadJob                                 |         | &check; | &check; | &check; |              |

## <a name="cmdlet-release-history"></a>Cmdlet 릴리스 기록

### <a name="cimcmdlets"></a>CimCmdlets

|         Cmdlet 이름         |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-CimClass                | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-CimSession              | &check; | &check; | &check; | &check; | Windows만 해당 |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Windows만 해당 |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Windows만 해당 |
| New-CimInstance             | &check; | &check; | &check; | &check; | Windows만 해당 |
| New-CimSession              | &check; | &check; | &check; | &check; | Windows만 해당 |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Windows만 해당 |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Windows만 해당 |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Windows만 해당 |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Windows만 해당 |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Windows만 해당 |

### <a name="ise-introduced-in-20"></a>2\.0에 도입된 ISE

|    Cmdlet 이름    |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Windows만 해당 |
| Import-IseSnippet | &check; |      |       |       | Windows만 해당 |
| New-IseSnippet    | &check; |      |       |       | Windows만 해당 |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Cmdlet 이름    |   5.1   |   6.x   |   7.0   |   7.1   | 참고 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Cmdlet 이름            |   5.1   |   6.x   |   7.0   |   7.1   |            참고            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Windows만 해당               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Windows만 해당               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Windows만 해당               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Windows만 해당               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Windows만 해당               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Windows만 해당               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Windows만 해당               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | 6\.2에 추가된 Linux 지원 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | 6\.2에 추가된 Linux 지원 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Windows만 해당               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | 6\.2에 추가된 Linux 지원 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Windows만 해당               |
| Get-Verb                          | &check; |         |         |         | Windows만 해당               |
| 모듈 가져오기                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Windows만 해당               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Windows만 해당               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Windows만 해당               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Windows만 해당               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Windows만 해당               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Windows만 해당               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Windows만 해당               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Windows만 해당               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Cmdlet 이름   |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Windows만 해당 |
| Get-Counter    | &check; |         | &check; | &check; | Windows만 해당 |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Windows만 해당 |
| Import-Counter | &check; |         |         |         | Windows만 해당 |
| New-WinEvent   | &check; | &check; | &check; | &check; | Windows만 해당 |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Cmdlet 이름    |   5.1   |   6.x   |   7.0   |   7.1   | 참고 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Cmdlet 이름       |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Windows만 해당 |
| Disable-LocalUser       | &check; |      |       |       | Windows만 해당 |
| Enable-LocalUser        | &check; |      |       |       | Windows만 해당 |
| Get-LocalGroup          | &check; |      |       |       | Windows만 해당 |
| Get-LocalGroupMember    | &check; |      |       |       | Windows만 해당 |
| Get-LocalUser           | &check; |      |       |       | Windows만 해당 |
| New-LocalGroup          | &check; |      |       |       | Windows만 해당 |
| New-LocalUser           | &check; |      |       |       | Windows만 해당 |
| Remove-LocalGroup       | &check; |      |       |       | Windows만 해당 |
| Remove-LocalGroupMember | &check; |      |       |       | Windows만 해당 |
| Remove-LocalUser        | &check; |      |       |       | Windows만 해당 |
| Rename-LocalGroup       | &check; |      |       |       | Windows만 해당 |
| Rename-LocalUser        | &check; |      |       |       | Windows만 해당 |
| Set-LocalGroup          | &check; |      |       |       | Windows만 해당 |
| Set-LocalUser           | &check; |      |       |       | Windows만 해당 |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Cmdlet 이름          |   5.1   |   6.x   |   7.0   |   7.1   |               참고               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Windows만 해당                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Windows만 해당                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Windows만 해당                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Windows만 해당                     |
| Complete-Transaction          | &check; |         |         |         | Windows만 해당                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Windows만 해당                     |
| Enable-ComputerRestore        | &check; |         |         |         | Windows만 해당                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | macOS에서는 지원되지 않음           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Windows만 해당                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Windows만 해당                     |
| Get-EventLog                  | &check; |         |         |         | Windows만 해당                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Windows만 해당                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Windows만 해당                     |
| Get-WmiObject                 | &check; |         |         |         | Windows만 해당                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Windows만 해당                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Windows만 해당                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Windows만 해당                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Windows만 해당                     |
| New-WebServiceProxy           | &check; |         |         |         | Windows만 해당                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Windows만 해당                     |
| Remove-Computer               | &check; |         |         |         | Windows만 해당                     |
| Remove-EventLog               | &check; |         |         |         | Windows만 해당                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Windows만 해당                     |
| Remove-WmiObject              | &check; |         |         |         | Windows만 해당                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| ComputerMachinePassword 재설정 | &check; |         |         |         | Windows만 해당                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Restore-Computer              | &check; |         |         |         | Windows만 해당                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Windows만 해당                     |
| Show-ControlPanelItem         | &check; |         |         |         | Windows만 해당                     |
| Show-EventLog                 | &check; |         |         |         | Windows만 해당                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Start-Transaction             | &check; |         |         |         | Windows만 해당                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | 7\.0에 추가된 Linux/macOS 지원 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Windows만 해당                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Windows만 해당                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Windows만 해당                     |
| Use-Transaction               | &check; |         |         |         | Windows만 해당                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Linux/macOS에서 작동하지 않음     |
| Write-EventLog                | &check; |         |         |         | Windows만 해당                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Cmdlet 이름        |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Windows만 해당 |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Cmdlet 이름         |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Windows만 해당 |
| Invoke-OperationValidation | &check; |      |       |       | Windows만 해당 |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Cmdlet 이름        |   5.1   |   6.x   |   7.0   |   7.1   |                  참고                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Linux/macOS에서 **Unrestricted** 반환 |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Linux/macOS에 해당되지 않음             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Windows만 해당                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Windows만 해당                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet 이름        |   5.1   |   6.x   |   7.0   |   7.1   |                   참고                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Linux/macOS에서 사용할 수 있는 이벤트 원본이 없음 |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Linux/macOS에서 사용할 수 있는 이벤트 원본이 없음 |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Linux/macOS에서 사용할 수 있는 이벤트 원본이 없음 |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Linux/macOS에서 사용할 수 있는 이벤트 원본이 없음 |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | 7\.0에서 macOS에 대한 지원 추가            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Linux/macOS에서 사용할 수 있는 이벤트 원본이 없음 |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WsMan.Management

|      Cmdlet 이름       |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Windows만 해당 |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Windows만 해당 |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Windows만 해당 |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Windows만 해당 |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Windows만 해당 |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Windows만 해당 |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Windows만 해당 |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Windows만 해당 |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Windows만 해당 |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Windows만 해당 |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Windows만 해당 |
| Test-WSMan             | &check; | &check; | &check; | &check; | Windows만 해당 |

### <a name="packagemanagement"></a>PackageManagement

|       Cmdlet 이름        |   5.1   |   6.x   |   7.0   |   7.1   | 참고 |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet 이름           |   5.1   |   6.x   |   7.0   |   7.1   | 참고 |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet 이름                 |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| Convertto-html-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Windows만 해당 |
| Enable-DscDebug                            | &check; |         |         |         | Windows만 해당 |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Windows만 해당 |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Windows만 해당 |
| Get DscLocalConfigurationManager           | &check; |         |         |         | Windows만 해당 |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Windows만 해당 |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Windows만 해당 |
| Restore-DscConfiguration                   | &check; |         |         |         | Windows만 해당 |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Windows만 해당 |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Windows만 해당 |
| Stop-DscConfiguration                      | &check; |         |         |         | Windows만 해당 |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Windows만 해당 |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Windows만 해당 |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet 이름          |   5.1   |   6.x   |   7.0   |   7.1   |     참고     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Windows만 해당 |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Windows만 해당 |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Windows만 해당 |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | Windows만 해당 |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | Windows만 해당 |

### <a name="psreadline"></a>PSReadline

|         Cmdlet 이름         |   5.1   |   6.x   |   7.0   |   7.1   | 참고 |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet 이름       |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Windows만 해당 |
| Disable-JobTrigger      | &check; |      |       |       | Windows만 해당 |
| Disable-ScheduledJob    | &check; |      |       |       | Windows만 해당 |
| Enable-JobTrigger       | &check; |      |       |       | Windows만 해당 |
| Enable-ScheduledJob     | &check; |      |       |       | Windows만 해당 |
| Get-JobTrigger          | &check; |      |       |       | Windows만 해당 |
| Get-ScheduledJob        | &check; |      |       |       | Windows만 해당 |
| Get-ScheduledJobOption  | &check; |      |       |       | Windows만 해당 |
| New-JobTrigger          | &check; |      |       |       | Windows만 해당 |
| New-ScheduledJobOption  | &check; |      |       |       | Windows만 해당 |
| Register-ScheduledJob   | &check; |      |       |       | Windows만 해당 |
| Remove-JobTrigger       | &check; |      |       |       | Windows만 해당 |
| Set-JobTrigger          | &check; |      |       |       | Windows만 해당 |
| Set-ScheduledJob        | &check; |      |       |       | Windows만 해당 |
| Set-ScheduledJobOption  | &check; |      |       |       | Windows만 해당 |
| Unregister-ScheduledJob | &check; |      |       |       | Windows만 해당 |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Cmdlet 이름          |   5.1   | 6.x  |  7.0  |  7.1  |     참고     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Windows만 해당 |
| New-PSWorkflowSession         | &check; |      |       |       | Windows만 해당 |
| Invoke-AsWorkflow             | &check; |      |       |       | Windows만 해당 |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet 이름   |  5.1  |   6.x   |   7.0   |   7.1   | 참고 |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; |      |
