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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067222"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="db7ee-102">사용자 확인 요청</span><span class="sxs-lookup"><span data-stu-id="db7ee-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="db7ee-103">값을 지정 하는 경우 `true` 에 대 한 합니다 `SupportsShouldProcess` Cmdlet 특성 선언의 매개 변수를 사용자 지정할 수는 `Confirm` 명령 프롬프트 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="db7ee-104">기본 환경에서 사용자 지정할 수 있습니다는 `Confirm` 매개 변수 또는 `"-Confirm:$true` 확인 요청 되는 때를 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="db7ee-105">이 건너뜁니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 영향력이 높은 작업에 대해서도 확인 요청을 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="db7ee-106">경우 `Confirm` 지정 하지 않으면를 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 하는 경우 확인을 요청 합니다 `$ConfirmPreference` 기본 설정 변수가 보다 크거나 같은 `ConfirmImpact` 설정는 cmdlet 또는 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="db7ee-107">기본 설정인 `$ConfirmPreference` 높음입니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="db7ee-108">따라서 기본 환경만 cmdlet 및 공급자 영향력이 높은 작업을 지정 하는 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="db7ee-109">경우 `Confirm` 이 false 이거나 `"-Confirm:$false` 지정 된 경우를 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 사용자 로부터 확인을 요청 하는 호출 및 `$ConfirmPreference` 셸 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="db7ee-110">설명</span><span class="sxs-lookup"><span data-stu-id="db7ee-110">Remarks</span></span>

- <span data-ttu-id="db7ee-111">지정 하는 cmdlet 및 공급자에 대 한 `SupportsShouldProcess`, 아닌 `ConfirmImpact`, "중간 영향" 작업으로 이러한 동작을 처리 하 고 기본적으로 메시지 표시 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="db7ee-112">기본 설정을 보다 낮은 해당 영향 수준입니다는 `$ConfirmPreference` 기본 설정 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="db7ee-113">사용자 지정 하는 경우는 `Verbose` 매개 변수를 알림이 표시 됩니다 작업의 확인을 묻지 않습니다 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7ee-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="db7ee-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db7ee-114">See Also</span></span>

<span data-ttu-id="db7ee-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="db7ee-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
