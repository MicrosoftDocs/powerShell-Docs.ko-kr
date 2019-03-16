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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055090"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="fb8e8-102">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="fb8e8-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="fb8e8-103">Microsoft.NET Framework 클래스를 지정 하 여 cmdlet으로 선언 된 **Cmdlet** 클래스에 대 한 메타 데이터 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="fb8e8-104">(합니다 **Cmdlet** 특성은 모든 cmdlet에 대 한 필수 속성).</span><span class="sxs-lookup"><span data-stu-id="fb8e8-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="fb8e8-105">지정 하는 경우는 **Cmdlet** 특성인 cmdlet이 사용자를 식별 하는 동사-명사 쌍을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="fb8e8-106">및 cmdlet에서 지 원하는 Windows PowerShell 기능을 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="fb8e8-107">지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fb8e8-108">**Cmdlet** 특성은 정의한 합니다 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="fb8e8-109">이 클래스의 속성 특성을 선언 하는 경우 사용 되는 선언 매개 변수와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="fb8e8-110">명사</span><span class="sxs-lookup"><span data-stu-id="fb8e8-110">Nouns</span></span>

<span data-ttu-id="fb8e8-111">Cmdlet의 명사는 cmdlet이 적용 되는 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="fb8e8-112">명사는 다른 cmdlet에서 cmdlet을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="fb8e8-113">Cmdlet 이름의 명사 해야 특정 및 일반 명사의 경우와 같은 *server*를 유사한 다른 리소스에서 리소스를 구분할 수 있는 짧은 접두사를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="fb8e8-114">예를 들어는 접두사가 포함 된 명사를 포함 하는 cmdlet 이름 `Get-SQLServer`합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="fb8e8-115">보다 일반적인 동사와 특정 명사를 조합 작업에 의해 cmdlet를 빠르게 찾은 후 불필요 한 cmdlet 이름 중복을 방지 하는 동안 해당 리소스에서 cmdlet을 식별 한 다음 사용자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="fb8e8-116">Cmdlet 이름에 사용할 수 없는 특수 문자의 목록을 참조 하세요 [개발 지침 필요한](./required-development-guidelines.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="fb8e8-117">동사</span><span class="sxs-lookup"><span data-stu-id="fb8e8-117">Verbs</span></span>

<span data-ttu-id="fb8e8-118">동사를 지정 하는 경우 개발 지침 미리 정의 된 Windows PowerShell에서 제공 되는 동사 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="fb8e8-119">이러한 미리 정의 된 동사 중 하나를 사용 하 여 작성 하는 cmdlet 및 다른 사용자가 Microsoft에서 작성 된 cmdlet 간에 일관성을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="fb8e8-120">예를 들어, 데이터를 검색 하는 cmdlet에 대 한 "Get" 동사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="fb8e8-121">동사에 대 한 지침에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="fb8e8-122">Cmdlet 이름에 사용할 수 없는 특수 문자의 목록을 참조 하세요 [개발 지침 필요한](./required-development-guidelines.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="fb8e8-123">Windows PowerShell 기능을 지 원하는</span><span class="sxs-lookup"><span data-stu-id="fb8e8-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="fb8e8-124">합니다 **Cmdlet** 특성 또한 cmdlet Windows PowerShell에서 제공 하는 일반적인 기능 중 일부를 지원 하는지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="fb8e8-125">사용자에 게 피드백 확인 (ShouldProcess 기능에 대 한 지원 이라고 함) 등의 일반적인 기능에 대 한 지원 및 트랜잭션에 대 한 지원이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="fb8e8-126">(트랜잭션에 대 한 지원이 Windows PowerShell 2.0에서 도입 되었습니다).</span><span class="sxs-lookup"><span data-stu-id="fb8e8-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="fb8e8-127">지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="fb8e8-128">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="fb8e8-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="fb8e8-129">다음 코드는 GetProc cmdlet 클래스에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="fb8e8-130">파스칼식 대/소문자 구분 되 고 클래스의 이름을 동사와 cmdlet의 명사를 포함 하는 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="fb8e8-131">파스칼식 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="fb8e8-131">Pascal Casing</span></span>

<span data-ttu-id="fb8e8-132">Cmdlet에 이름을 지정할 때 사용 하 여 파스칼식 대/소문자 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="fb8e8-133">예를 들어 합니다 `Get-Item` 및 `Get-ItemProperty` cmdlet cmdlet를 명명할 때 대/소문자를 사용 하는 올바른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb8e8-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb8e8-134">See Also</span></span>

[<span data-ttu-id="fb8e8-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="fb8e8-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="fb8e8-136">CmdletAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="fb8e8-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="fb8e8-137">Cmdlet 동사 이름</span><span class="sxs-lookup"><span data-stu-id="fb8e8-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

<span data-ttu-id="fb8e8-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fb8e8-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="fb8e8-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fb8e8-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
