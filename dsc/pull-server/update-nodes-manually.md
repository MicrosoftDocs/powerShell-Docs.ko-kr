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
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="a6302-103">끌어오기 서버에서 노드 업데이트</span><span class="sxs-lookup"><span data-stu-id="a6302-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="a6302-104">아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="a6302-105">끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="a6302-106">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="a6302-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a6302-107">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="a6302-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a6302-108">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a6302-109">이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="a6302-110">노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.</span><span class="sxs-lookup"><span data-stu-id="a6302-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="a6302-111">Update-dscconfiguration cmdlet을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="a6302-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="a6302-112">PowerShell 5.0부터 합니다 [Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, LCM 구성 끌어오기 서버에서 해당 구성을 업데이트 하는 노드를 강제로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="a6302-113">호출 CIMMethod를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="a6302-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="a6302-114">PowerShell 4.0에서는 여전히 수동으로 적용할 수 있습니다 사용 하 여 해당 구성을 업데이트 하려면 끌어오기 클라이언트가 [Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="a6302-115">다음 예제에서는 지정 된 자격 증명을 사용 하 여 CIM 세션을 만든 적절 한 CIM 메서드를 호출 하며 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6302-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="a6302-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6302-116">See Also</span></span>

[<span data-ttu-id="a6302-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="a6302-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
