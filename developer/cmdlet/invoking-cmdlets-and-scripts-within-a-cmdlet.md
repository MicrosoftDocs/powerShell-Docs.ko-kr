---
title: Cmdlet 및 Cmdlet 내에서 스크립트를 호출 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058881"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="d075d-102">Cmdlet 내에서 Cmdlet 및 호출</span><span class="sxs-lookup"><span data-stu-id="d075d-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="d075d-103">Cmdlet은 다른 cmdlet와 cmdlet의 메서드를 처리 된 입력 내의 스크립트에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="d075d-104">이 옵션을 사용 하면 코드를 다시 작성할 필요 없이 cmdlet에 기존 cmdlet 및 스크립트의 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="d075d-105">메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-105">The Invoke Method</span></span>

<span data-ttu-id="d075d-106">모든 cmdlet를 호출 하 여 기존 cmdlet을 호출할 수는 [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 와 같은 메서드를 처리 하는 입력에서 메서드를 [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)되는 cmdlet에 의해 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="d075d-107">그러나에서 직접 파생 되는 cmdlet에만 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="d075d-108">파생 되는 cmdlet를 호출할 수 없습니다는 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="d075d-109">합니다 [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드가 다음과 같은 변형을 합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="d075d-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 이 변형은 cmdlet 개체를 호출 하 고 "T" 형식 개체의 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="d075d-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 이 변형은 cmdlet 개체를 호출 하 고 강력한 형식의 emumerator를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="d075d-112">이 변형은 사용자를 컬렉션에 개체를 사용 하 여 사용자 지정 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="d075d-113">예</span><span class="sxs-lookup"><span data-stu-id="d075d-113">Examples</span></span>

|<span data-ttu-id="d075d-114">예제</span><span class="sxs-lookup"><span data-stu-id="d075d-114">Example</span></span>|<span data-ttu-id="d075d-115">설명</span><span class="sxs-lookup"><span data-stu-id="d075d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d075d-116">Cmdlet 내에서 Cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="d075d-117">이 예제에는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="d075d-118">Cmdlet 내에서 스크립트를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="d075d-119">이 예제에는 다른 cmdlet 내에서 cmdlet에 제공 되는 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d075d-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d075d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d075d-120">See Also</span></span>

<span data-ttu-id="d075d-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d075d-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
