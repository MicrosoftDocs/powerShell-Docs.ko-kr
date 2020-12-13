---
ms.date: 09/13/2016
ms.topic: reference
title: 인수 길이 유효성을 검사하는 방법
description: 인수 길이 유효성을 검사하는 방법
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652634"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="c16f7-103">인수 길이 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="c16f7-103">How to Validate the Argument Length</span></span>

<span data-ttu-id="c16f7-104">이 예에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수 인수의 문자 수 (길이)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c16f7-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="c16f7-105">ValidateLength 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c16f7-105">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="c16f7-106">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c16f7-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="c16f7-107">인수 길이를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="c16f7-107">To validate the argument length</span></span>

- <span data-ttu-id="c16f7-108">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c16f7-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="c16f7-109">이 예에서는 인수의 길이는 0 자에서 10 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c16f7-109">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="c16f7-110">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c16f7-110">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c16f7-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c16f7-111">See Also</span></span>

[<span data-ttu-id="c16f7-112">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="c16f7-112">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

<span data-ttu-id="c16f7-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="c16f7-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
