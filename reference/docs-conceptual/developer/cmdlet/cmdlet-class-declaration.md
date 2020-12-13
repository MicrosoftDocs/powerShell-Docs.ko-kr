---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 클래스 선언
description: Cmdlet 클래스 선언
ms.openlocfilehash: 854b0a4ca9f6c87c4fad3b71ee726beade585e02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653505"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="0112a-103">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="0112a-103">Cmdlet Class Declaration</span></span>

<span data-ttu-id="0112a-104">Microsoft .NET Framework 클래스는 cmdlet 특성을 클래스의 메타 데이터로 지정 하 **여 cmdlet으로** 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-104">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="0112a-105">**Cmdlet** 특성은 모든 cmdlet에 대해 유일 하 게 필요한 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-105">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="0112a-106">**Cmdlet** 특성을 지정 하는 경우 사용자에 대해 cmdlet을 식별 하는 동사 및 명사 쌍을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-106">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="0112a-107">그리고 cmdlet이 지 원하는 Windows PowerShell 기능을 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-107">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="0112a-108">**Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0112a-108">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0112a-109">**Cmdlet** 특성은 [system.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-109">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="0112a-110">이 클래스의 속성은 특성을 선언할 때 사용 되는 선언 매개 변수에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-110">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="0112a-111">명사</span><span class="sxs-lookup"><span data-stu-id="0112a-111">Nouns</span></span>

<span data-ttu-id="0112a-112">Cmdlet의 명사는 cmdlet이 작동 하는 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-112">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="0112a-113">명사는 다른 cmdlet에서 cmdlet을 구별 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-113">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="0112a-114">Cmdlet 이름의 명사는 특정 해야 하며, *서버* 와 같은 일반적인 명사의 경우 리소스를 다른 비슷한 리소스와 구별 하는 짧은 접두사를 추가 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-114">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="0112a-115">예를 들어 접두사가 포함 된 명사를 포함 하는 cmdlet 이름은 `Get-SQLServer` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-115">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="0112a-116">특정 명사를 보다 일반적인 동사로 조합 하면 사용자가 해당 작업으로 cmdlet을 빠르게 찾은 다음 불필요 한 cmdlet 이름 중복을 방지 하는 동시에 해당 리소스에서 cmdlet을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-116">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="0112a-117">Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0112a-117">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="0112a-118">동사</span><span class="sxs-lookup"><span data-stu-id="0112a-118">Verbs</span></span>

<span data-ttu-id="0112a-119">동사를 지정 하는 경우 개발 지침을 사용 하려면 Windows PowerShell에서 제공 하는 미리 정의 된 동사 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-119">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="0112a-120">이러한 미리 정의 된 동사 중 하나를 사용 하 여 작성 하는 cmdlet과 Microsoft와 다른 사용자가 작성 한 cmdlet 간에 일관성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-120">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="0112a-121">예를 들어 "Get" 동사는 데이터를 검색 하는 cmdlet에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-121">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="0112a-122">동사에 대 한 지침에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0112a-122">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="0112a-123">Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0112a-123">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="0112a-124">Windows PowerShell 기능 지원</span><span class="sxs-lookup"><span data-stu-id="0112a-124">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="0112a-125">**Cmdlet** 특성을 사용 하면 Cmdlet이 Windows PowerShell에서 제공 하는 몇 가지 일반적인 기능을 지원 하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-125">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="0112a-126">여기에는 사용자 피드백 확인 (ShouldProcess 기능 지원)과 같은 일반적인 기능 및 트랜잭션에 대 한 지원이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-126">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="0112a-127">트랜잭션에 대 한 지원은 Windows PowerShell 2.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-127">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="0112a-128">**Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0112a-128">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="0112a-129">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="0112a-129">Cmdlet Class Definition</span></span>

<span data-ttu-id="0112a-130">다음 코드는 GetProc cmdlet 클래스에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-130">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="0112a-131">파스칼식 대/소문자가 사용 되 고 클래스 이름에 cmdlet의 동사와 명사가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-131">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="0112a-132">파스칼식 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="0112a-132">Pascal Casing</span></span>

<span data-ttu-id="0112a-133">Cmdlet의 이름을 사용할 때는 파스칼식 대/소문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-133">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="0112a-134">예를 들어 `Get-Item` 및 `Get-ItemProperty` cmdlet은 cmdlet의 이름을 지정할 때 대/소문자를 사용 하는 올바른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0112a-134">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="0112a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0112a-135">See Also</span></span>

[<span data-ttu-id="0112a-136">System.object. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="0112a-136">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="0112a-137">CmdletAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="0112a-137">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="0112a-138">Cmdlet 동사 이름</span><span class="sxs-lookup"><span data-stu-id="0112a-138">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

<span data-ttu-id="0112a-139">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="0112a-139">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="0112a-140">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0112a-140">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
