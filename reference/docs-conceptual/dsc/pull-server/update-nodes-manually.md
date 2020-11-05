---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버에서 노드 업데이트
description: 이 문서에서는 끌어오기 서버에서 DSC 관리 노드를 업데이트하는 방법을 설명합니다.
ms.openlocfilehash: 7256a0e1fdfaa8e56150c4f7299640bc95b82cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656758"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="aee7b-104">끌어오기 서버에서 노드 업데이트</span><span class="sxs-lookup"><span data-stu-id="aee7b-104">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="aee7b-105">아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="aee7b-106">끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="aee7b-107">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="aee7b-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="aee7b-108">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="aee7b-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="aee7b-109">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="aee7b-110">이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="aee7b-111">노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기** (v5)를 통해 LCM에 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="aee7b-112">Update-DSCConfiguration cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="aee7b-112">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="aee7b-113">PowerShell 5.0부터, [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet은 노드가 LCM에 구성된 끌어오기 서버에서 해당 구성을 업데이트하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-113">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="aee7b-114">Invoke-CIMMethod 사용</span><span class="sxs-lookup"><span data-stu-id="aee7b-114">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="aee7b-115">PowerShell 4.0에서는 [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod)를 사용하여 수동으로 끌어오기 클라이언트가 해당 구성을 업데이트하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-115">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="aee7b-116">다음 예제에서는 지정된 자격 증명을 사용하여 CIM 세션을 만들고, 적절한 CIM 메서드를 호출하고, 세션을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="aee7b-116">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="aee7b-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aee7b-117">See Also</span></span>

[<span data-ttu-id="aee7b-118">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="aee7b-118">PerformRequiredConfigurationChecks</span></span>](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
