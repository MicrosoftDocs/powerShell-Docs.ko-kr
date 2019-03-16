---
title: 확인 메시지 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059476"
---
# <a name="confirmation-messages"></a><span data-ttu-id="05e66-102">확인 메시지</span><span class="sxs-lookup"><span data-stu-id="05e66-102">Confirmation Messages</span></span>

<span data-ttu-id="05e66-103">여기는의 변형에 따라 표시 될 수 있는 다양 한 확인 메시지를 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 고 [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 이라고 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05e66-104">확인을 요청 하는 방법을 보여 주는 샘플 코드를 보려면 [요청 확인 하는 방법을](./how-to-request-confirmations.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="05e66-105">리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-105">Specifying the Resource</span></span>

<span data-ttu-id="05e66-106">호출 하 여 변경할 수에 있는 리소스를 지정할 수는 [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="05e66-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="05e66-107">이 예에서 사용 하 여 리소스를 제공한는 `target` Windows PowerShell에서 하는 메서드 및 작업의 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="05e66-108">다음 메시지에 "MyResource" 텍스트는 실행 하는 리소스 이며 작업 호출을 수행 하는 명령의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="05e66-109">사용자가 선택 **Yes** 또는 **모두 예** 확인 요청 (표시 된 대로 다음 예제의)를 호출 하는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)메서드 설정 되는 두 번째 확인 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="05e66-110">작업 및 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="05e66-111">변경 되려고 할 리소스 및 명령을 호출 하 여 수행 하는 작업을 지정할 수는 [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="05e66-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="05e66-112">이 예에서 사용 하 여 리소스를 제공한 합니다 `target` 매개 변수 및 사용 하 여 작업을 `target` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="05e66-113">다음 메시지에 "MyResource" 텍스트는 실행 하는 리소스 이며 "MyAction" 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="05e66-114">사용자가 선택 **예** 하거나 **모두 예** 이전 메시지에 대 한 호출에는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드를 수행 하는 원인을 두 번째 확인 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05e66-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="05e66-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05e66-115">See Also</span></span>

<span data-ttu-id="05e66-116">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="05e66-116">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
