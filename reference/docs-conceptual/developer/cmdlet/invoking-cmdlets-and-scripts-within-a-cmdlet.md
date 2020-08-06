---
title: Cmdlet에서 cmdlet 및 스크립트 호출 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d5f76242c02763c41b81215bbb031e19869066a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786580"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="29ef7-102">Cmdlet 내에서 Cmdlet 및 호출</span><span class="sxs-lookup"><span data-stu-id="29ef7-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="29ef7-103">Cmdlet은 cmdlet의 입력 처리 메서드 내에서 다른 cmdlet 및 스크립트를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="29ef7-104">이렇게 하면 코드를 다시 작성할 필요 없이 cmdlet에 기존 cmdlet 및 스크립트의 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="29ef7-105">Invoke 메서드</span><span class="sxs-lookup"><span data-stu-id="29ef7-105">The Invoke Method</span></span>

<span data-ttu-id="29ef7-106">모든 cmdlet은 cmdlet에 의해 재정의 되는 입력 처리 메서드 (예: [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)) 내에서 [system.xml 메서드를](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 호출 하 여 기존 cmdlet을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="29ef7-107">그러나 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 직접 파생 되는 cmdlet만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="29ef7-108">[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 된 cmdlet을 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="29ef7-109">System.object.. n a m. [Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드에는 다음과 같은 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="29ef7-110">[System.object를 호출](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 합니다 .이 변형은 cmdlet 개체를 호출 하 고 "T" 형식 개체의 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="29ef7-111">Emumerator cmdlet 개체를 호출 하 고 강력한 형식의를 반환 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)</span><span class="sxs-lookup"><span data-stu-id="29ef7-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="29ef7-112">이 변형을 사용 하면 사용자가 컬렉션의 개체를 사용 하 여 사용자 지정 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="29ef7-113">예</span><span class="sxs-lookup"><span data-stu-id="29ef7-113">Examples</span></span>

|<span data-ttu-id="29ef7-114">예제</span><span class="sxs-lookup"><span data-stu-id="29ef7-114">Example</span></span>|<span data-ttu-id="29ef7-115">설명</span><span class="sxs-lookup"><span data-stu-id="29ef7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29ef7-116">Cmdlet에서 cmdlet 호출</span><span class="sxs-lookup"><span data-stu-id="29ef7-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="29ef7-117">이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="29ef7-118">Cmdlet 내에서 스크립트 호출</span><span class="sxs-lookup"><span data-stu-id="29ef7-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="29ef7-119">이 예에서는 다른 cmdlet 내에서 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ef7-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="29ef7-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29ef7-120">See Also</span></span>

[<span data-ttu-id="29ef7-121">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="29ef7-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
