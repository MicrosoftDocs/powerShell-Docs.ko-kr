---
title: 확인을 요청 하는 사용자 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369252"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="b282d-102">사용자 확인 요청</span><span class="sxs-lookup"><span data-stu-id="b282d-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="b282d-103">Cmdlet 특성 선언의 `SupportsShouldProcess` 매개 변수에 `true` 값을 지정 하면 사용자는 명령 프롬프트에서 `Confirm` 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="b282d-104">기본 환경에서 사용자는 `Confirm` 매개 변수를 지정 하거나 `"-Confirm:$true`를 지정 하 여 확인이 요청 될 때 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="b282d-105">이렇게 하면 높은 영향을 주는 작업에도 불구 하 고 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 확인 요청을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="b282d-106">`Confirm` 지정 되지 않은 경우 `$ConfirmPreference` 기본 설정 변수가 Cmdlet 또는 공급자의 `ConfirmImpact` 설정 보다 크거나 같은 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="b282d-107">`$ConfirmPreference`의 기본 설정은 높습니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="b282d-108">따라서 기본 환경에서는 높은 영향을 주는 작업 요청 확인을 지정 하는 cmdlet 및 공급자만 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="b282d-109">`Confirm` false 이거나 `"-Confirm:$false` 지정 된 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 가 사용자의 확인을 요청 하 고 `$ConfirmPreference` shell 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="b282d-110">설명</span><span class="sxs-lookup"><span data-stu-id="b282d-110">Remarks</span></span>

- <span data-ttu-id="b282d-111">`SupportsShouldProcess`를 지정 하지만 `ConfirmImpact`하지 않는 cmdlet 및 공급자의 경우 이러한 작업은 "중간 영향" 작업으로 처리 되며 기본적으로 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="b282d-112">영향 수준이 `$ConfirmPreference` 기본 설정 변수의 기본 설정 보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="b282d-113">사용자가 `Verbose` 매개 변수를 지정 하는 경우 확인 메시지를 표시 하지 않는 경우에도 작업에 대 한 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b282d-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b282d-114">관련 항목</span><span class="sxs-lookup"><span data-stu-id="b282d-114">See Also</span></span>

<span data-ttu-id="b282d-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b282d-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
