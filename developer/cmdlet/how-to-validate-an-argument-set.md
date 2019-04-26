---
title: 인수 집합을 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067721"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="9a8d9-102">인수 집합을 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="9a8d9-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="9a8d9-103">이 예제에서는 Windows PowerShell 런타임이 cmdlet을 실행 하기 전에 매개 변수 인수를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="9a8d9-104">이 유효성 검사 규칙 매개 변수 인수에 대 한 유효한 값 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="9a8d9-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 참조 하세요. [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)합니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="9a8d9-106">인수 집합의 유효성을 검사 하려면</span><span class="sxs-lookup"><span data-stu-id="9a8d9-106">To validate an argument set</span></span>

- <span data-ttu-id="9a8d9-107">다음 코드 에서처럼 ValidateSet 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="9a8d9-108">가능한 값 집합을 지정 하는이 예제는 `UserName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="9a8d9-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [ValidateSet 특성 선언을](./validateset-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9a8d9-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a8d9-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a8d9-110">See Also</span></span>

[<span data-ttu-id="9a8d9-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="9a8d9-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="9a8d9-112">ValidateSet 특성 선언</span><span class="sxs-lookup"><span data-stu-id="9a8d9-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

<span data-ttu-id="9a8d9-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9a8d9-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
