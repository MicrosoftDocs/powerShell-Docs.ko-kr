---
title: 인수 패턴의 유효성을 검사 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067776"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="f26c1-102">인수 패턴 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="f26c1-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="f26c1-103">이 예제에서는 Windows PowerShell 런타임이 cmdlet을 실행 하기 전에 매개 변수 인수의 문자 패턴을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f26c1-104">ValidatePattern 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f26c1-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 참조 하세요. [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)합니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="f26c1-106">인수 패턴의 유효성을 검사 하려면</span><span class="sxs-lookup"><span data-stu-id="f26c1-106">To validate an argument pattern</span></span>

- <span data-ttu-id="f26c1-107">다음 코드에 표시 된 것과 같이 유효성 검사 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="f26c1-108">이 예제에서는 각 숫자에 0 ~ 9의 값이 있는 4 자리 숫자로, 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="f26c1-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f26c1-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f26c1-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f26c1-110">See Also</span></span>

[<span data-ttu-id="f26c1-111">ValidatePattern 특성 선언</span><span class="sxs-lookup"><span data-stu-id="f26c1-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

<span data-ttu-id="f26c1-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f26c1-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
