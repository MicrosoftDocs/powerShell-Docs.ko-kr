---
title: 인수의 길이를 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365492"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="1f1ce-102">인수 길이 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="1f1ce-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="1f1ce-103">이 예에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수 인수의 문자 수 (길이)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="1f1ce-104">ValidateLength 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="1f1ce-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="1f1ce-106">인수 길이를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="1f1ce-106">To validate the argument length</span></span>

- <span data-ttu-id="1f1ce-107">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="1f1ce-108">이 예에서는 인수의 길이는 0 자에서 10 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="1f1ce-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f1ce-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f1ce-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f1ce-110">See Also</span></span>

[<span data-ttu-id="1f1ce-111">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="1f1ce-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

<span data-ttu-id="1f1ce-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="1f1ce-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
