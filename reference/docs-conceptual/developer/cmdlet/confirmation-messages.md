---
title: 확인 메시지 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8f8192f6ed96b1eeb22e3b28ce1366eee8e7c16a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782194"
---
# <a name="confirmation-messages"></a><span data-ttu-id="d4465-102">확인 메시지</span><span class="sxs-lookup"><span data-stu-id="d4465-102">Confirmation Messages</span></span>

<span data-ttu-id="d4465-103">다음은 호출 되는 [시스템](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 의 변형에 따라 표시 될 수 있는 다양 한 확인 메시지입니다 .이 메시지 [는를 호출](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4465-104">확인을 요청 하는 방법을 보여 주는 샘플 코드는 확인 [을 요청 하는 방법](./how-to-request-confirmations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4465-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="d4465-105">리소스 지정</span><span class="sxs-lookup"><span data-stu-id="d4465-105">Specifying the Resource</span></span>

<span data-ttu-id="d4465-106">변경할 리소스를 지정할 수 있습니다 .이 [작업은 %2 a?를 호출 하 여 변경할 수 있습니다. Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="d4465-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="d4465-107">이 경우 메서드의 매개 변수를 사용 하 여 리소스를 제공 합니다 `target` .이 작업은 Windows PowerShell을 통해 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="d4465-108">다음 메시지에서 "MyResource" 텍스트는 사용 되는 리소스 이며 작업은 호출을 수행 하는 명령 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d4465-109">사용자가 다음 예제와 같이 확인 요청에 대해 모두 **예** 또는 예를 선택 **하** 는 경우에는 두 번째 확인 메시지가 표시 되는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="d4465-110">작업 및 리소스 지정</span><span class="sxs-lookup"><span data-stu-id="d4465-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="d4465-111">변경할 리소스와 해당 명령이 수행할 작업 (... n a m a. %2?)을 지정할 수 있습니다. [ Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드.</span><span class="sxs-lookup"><span data-stu-id="d4465-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="d4465-112">이 경우 매개 변수를 사용 하 여 리소스를 제공 하 `target` 고 매개 변수를 사용 하 여 작업을 수행 합니다 `target` .</span><span class="sxs-lookup"><span data-stu-id="d4465-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="d4465-113">다음 메시지에서 "MyResource" 라는 텍스트는 수행 되는 리소스 이며 "Myresource"은 수행 되는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d4465-114">사용자가 이전 메시지에 대해 **모두** **예** 또는 예를 선택 하는 경우에는 두 번째 확인 메시지가 표시 되는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4465-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="d4465-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4465-115">See Also</span></span>

[<span data-ttu-id="d4465-116">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d4465-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
