---
title: Cmdlet 클래스 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 0de49d979c31b0e8d111323a2e1899d97868ec3f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978715"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="7504c-102">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="7504c-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="7504c-103">Microsoft .NET Framework 클래스는 cmdlet 특성을 클래스의 메타 데이터로 지정 하 **여 cmdlet으로** 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="7504c-104">**Cmdlet** 특성은 모든 cmdlet에 대해 유일 하 게 필요한 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="7504c-105">**Cmdlet** 특성을 지정 하는 경우 사용자에 대해 cmdlet을 식별 하는 동사 및 명사 쌍을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="7504c-106">그리고 cmdlet이 지 원하는 Windows PowerShell 기능을 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="7504c-107">**Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7504c-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7504c-108">**Cmdlet** 특성은 [system.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="7504c-109">이 클래스의 속성은 특성을 선언할 때 사용 되는 선언 매개 변수에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="7504c-110">명사</span><span class="sxs-lookup"><span data-stu-id="7504c-110">Nouns</span></span>

<span data-ttu-id="7504c-111">Cmdlet의 명사는 cmdlet이 작동 하는 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="7504c-112">명사는 다른 cmdlet에서 cmdlet을 구별 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="7504c-113">Cmdlet 이름의 명사는 특정 해야 하며, *서버*와 같은 일반적인 명사의 경우 리소스를 다른 비슷한 리소스와 구별 하는 짧은 접두사를 추가 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="7504c-114">예를 들어 접두사가 포함 된 명사를 포함 하는 cmdlet 이름은 `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="7504c-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="7504c-115">특정 명사를 보다 일반적인 동사로 조합 하면 사용자가 해당 작업으로 cmdlet을 빠르게 찾은 다음 불필요 한 cmdlet 이름 중복을 방지 하는 동시에 해당 리소스에서 cmdlet을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="7504c-116">Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7504c-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="7504c-117">동사</span><span class="sxs-lookup"><span data-stu-id="7504c-117">Verbs</span></span>

<span data-ttu-id="7504c-118">동사를 지정 하는 경우 개발 지침을 사용 하려면 Windows PowerShell에서 제공 하는 미리 정의 된 동사 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="7504c-119">이러한 미리 정의 된 동사 중 하나를 사용 하 여 작성 하는 cmdlet과 Microsoft와 다른 사용자가 작성 한 cmdlet 간에 일관성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="7504c-120">예를 들어 "Get" 동사는 데이터를 검색 하는 cmdlet에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="7504c-121">동사에 대 한 지침에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7504c-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="7504c-122">Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7504c-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="7504c-123">Windows PowerShell 기능 지원</span><span class="sxs-lookup"><span data-stu-id="7504c-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="7504c-124">**Cmdlet** 특성을 사용 하면 Cmdlet이 Windows PowerShell에서 제공 하는 몇 가지 일반적인 기능을 지원 하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="7504c-125">여기에는 사용자 피드백 확인 (ShouldProcess 기능 지원)과 같은 일반적인 기능 및 트랜잭션에 대 한 지원이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="7504c-126">트랜잭션에 대 한 지원은 Windows PowerShell 2.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="7504c-127">**Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7504c-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="7504c-128">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="7504c-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="7504c-129">다음 코드는 GetProc cmdlet 클래스에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="7504c-130">파스칼식 대/소문자가 사용 되 고 클래스 이름에 cmdlet의 동사와 명사가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="7504c-131">파스칼식 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="7504c-131">Pascal Casing</span></span>

<span data-ttu-id="7504c-132">Cmdlet의 이름을 사용할 때는 파스칼식 대/소문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="7504c-133">예를 들어 `Get-Item` 및 `Get-ItemProperty` cmdlet은 cmdlet의 이름을 지정할 때 대/소문자를 사용 하는 올바른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7504c-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="7504c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7504c-134">See Also</span></span>

[<span data-ttu-id="7504c-135">System.object. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="7504c-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="7504c-136">CmdletAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="7504c-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="7504c-137">Cmdlet 동사 이름</span><span class="sxs-lookup"><span data-stu-id="7504c-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

<span data-ttu-id="7504c-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="7504c-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="7504c-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7504c-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
