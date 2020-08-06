---
title: 인수의 길이를 확인 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, example
ms.openlocfilehash: aa0545def6d9628f6b41090a425f0c5af25f6ad7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784081"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="c8a67-102">인수 길이 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="c8a67-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="c8a67-103">이 예에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수 인수의 문자 수 (길이)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8a67-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="c8a67-104">ValidateLength 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a67-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="c8a67-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8a67-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="c8a67-106">인수 길이를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="c8a67-106">To validate the argument length</span></span>

- <span data-ttu-id="c8a67-107">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a67-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="c8a67-108">이 예에서는 인수의 길이는 0 자에서 10 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a67-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="c8a67-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8a67-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8a67-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8a67-110">See Also</span></span>

[<span data-ttu-id="c8a67-111">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="c8a67-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="c8a67-112">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="c8a67-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
