---
ms.date: 09/13/2016
ms.topic: reference
title: 사용자 확인 요청
description: 사용자 확인 요청
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646311"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="bdb49-103">사용자 확인 요청</span><span class="sxs-lookup"><span data-stu-id="bdb49-103">Users Requesting Confirmation</span></span>

<span data-ttu-id="bdb49-104">`true` `SupportsShouldProcess` Cmdlet 특성 선언의 매개 변수에 값을 지정 하면 사용자가 `Confirm` 명령 프롬프트에서 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-104">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="bdb49-105">기본 환경에서 사용자는 매개 변수를 지정 `Confirm` 하거나 `"-Confirm:$true` [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 때 확인이 요청 되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-105">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="bdb49-106">이렇게 하면 높은 영향을 주는 작업에도 불구 하 고 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 확인 요청을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-106">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="bdb49-107">`Confirm`을 지정 하지 않으면 [](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `$ConfirmPreference` 기본 설정 변수가 `ConfirmImpact` Cmdlet 또는 공급자의 설정 보다 크거나 같은 경우에는 system.object를 호출 하 여 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-107">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="bdb49-108">의 기본 설정이 `$ConfirmPreference` 높습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-108">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="bdb49-109">따라서 기본 환경에서는 높은 영향을 주는 작업 요청 확인을 지정 하는 cmdlet 및 공급자만 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-109">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="bdb49-110">가 false 이거나가 지정 된 경우에는 System.object가 사용자에 게 `Confirm` 확인을 `"-Confirm:$false` 요청 하 고 [](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `$ConfirmPreference` shell 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-110">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdb49-111">설명</span><span class="sxs-lookup"><span data-stu-id="bdb49-111">Remarks</span></span>

- <span data-ttu-id="bdb49-112">를 지정 하는 cmdlet 및 공급자의 경우 `SupportsShouldProcess` `ConfirmImpact` 이러한 작업은 "중간 영향" 작업으로 처리 되며 기본적으로 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-112">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="bdb49-113">영향 수준이 기본 설정 변수의 기본 설정 보다 낮습니다 `$ConfirmPreference` .</span><span class="sxs-lookup"><span data-stu-id="bdb49-113">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="bdb49-114">사용자가 매개 변수를 지정 하는 경우 `Verbose` 확인 메시지를 표시 하지 않는 경우에도 작업에 대 한 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb49-114">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdb49-115">관련 항목</span><span class="sxs-lookup"><span data-stu-id="bdb49-115">See Also</span></span>

[<span data-ttu-id="bdb49-116">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="bdb49-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
