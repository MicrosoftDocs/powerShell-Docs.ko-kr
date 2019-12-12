---
title: 인수 개수를 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365532"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="02d4b-102">인수 개수를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="02d4b-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="02d4b-103">이 예제에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수가 허용 하는 인수 개수 (개수)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="02d4b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="02d4b-104">이 유효성 검사 규칙은 ValidateCount 특성을 선언 하 여 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02d4b-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="02d4b-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="02d4b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="02d4b-106">인수 개수를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="02d4b-106">To validate an argument count</span></span>

- <span data-ttu-id="02d4b-107">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="02d4b-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="02d4b-108">이 예에서는 매개 변수에서 인수를 하나 또는 3 개까지 허용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02d4b-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="02d4b-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="02d4b-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02d4b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02d4b-110">See Also</span></span>

[<span data-ttu-id="02d4b-111">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="02d4b-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

<span data-ttu-id="02d4b-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="02d4b-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
