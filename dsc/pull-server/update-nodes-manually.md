---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버에서 노드 업데이트
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402151"
---
# <a name="update-nodes-from-a-pull-server"></a>끌어오기 서버에서 노드 업데이트

아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다. 끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다. 이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다. 노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Update-dscconfiguration cmdlet을 사용 하 여

PowerShell 5.0부터 합니다 [Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, LCM 구성 끌어오기 서버에서 해당 구성을 업데이트 하는 노드를 강제로 수행 합니다.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>호출 CIMMethod를 사용 하 여

PowerShell 4.0에서는 여전히 수동으로 적용할 수 있습니다 사용 하 여 해당 구성을 업데이트 하려면 끌어오기 클라이언트가 [Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)합니다. 다음 예제에서는 지정 된 자격 증명을 사용 하 여 CIM 세션을 만든 적절 한 CIM 메서드를 호출 하며 세션을 제거 합니다.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>참고 항목

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
