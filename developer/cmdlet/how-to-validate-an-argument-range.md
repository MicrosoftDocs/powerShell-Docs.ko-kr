---
title: 인수가 범위를 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859739"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="19962-102">인수 범위를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="19962-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="19962-103">이 예제에서는 Windows PowerShell 런타임이 cmdlet을 실행 하기 전에 매개 변수 인수의 최소 및 최대 값을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19962-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="19962-104">ValidateRange 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19962-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="19962-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 참조 하세요. [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)합니다.</span><span class="sxs-lookup"><span data-stu-id="19962-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="19962-106">인수가 범위를 유효성을 검사 하려면</span><span class="sxs-lookup"><span data-stu-id="19962-106">To validate an argument range</span></span>

- <span data-ttu-id="19962-107">다음 코드 에서처럼 ValidateRange 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19962-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="19962-108">0에서 5에 대 한 범위를 지정 하는이 예제는 `InputData` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="19962-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="19962-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [ValidateRange 특성 선언을](./validaterange-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="19962-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19962-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19962-110">See Also</span></span>

[<span data-ttu-id="19962-111">ValidateRange 특성 선언</span><span class="sxs-lookup"><span data-stu-id="19962-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

<span data-ttu-id="19962-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="19962-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
