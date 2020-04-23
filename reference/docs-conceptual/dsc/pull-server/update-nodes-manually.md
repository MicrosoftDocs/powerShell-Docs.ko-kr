---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버에서 노드 업데이트
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500669"
---
# <a name="update-nodes-from-a-pull-server"></a>끌어오기 서버에서 노드 업데이트

아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다. 끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다. 노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기**(v5)를 통해 LCM에 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Update-DSCConfiguration cmdlet 사용

PowerShell 5.0부터, [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet은 노드가 LCM에 구성된 끌어오기 서버에서 해당 구성을 업데이트하도록 합니다.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Invoke-CIMMethod 사용

PowerShell 4.0에서는 [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod)를 사용하여 수동으로 끌어오기 클라이언트가 해당 구성을 업데이트하도록 할 수 있습니다. 다음 예제에서는 지정된 자격 증명을 사용하여 CIM 세션을 만들고, 적절한 CIM 메서드를 호출하고, 세션을 제거합니다.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>참고 항목

[PerformRequiredConfigurationChecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
