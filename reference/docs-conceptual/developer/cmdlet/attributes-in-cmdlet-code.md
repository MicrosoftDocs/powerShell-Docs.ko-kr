---
title: Cmdlet 코드의 특성 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774918"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="a8506-102">Cmdlet 코드의 특성</span><span class="sxs-lookup"><span data-stu-id="a8506-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="a8506-103">Windows PowerShell에서 제공 하는 공통 기능을 사용 하기 위해 cmdlet 코드에 정의 된 클래스 및 공용 속성은 특성으로 데코 레이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="a8506-104">예를 들어, 다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 **Get Proc** cmdlet이 구현 된 Microsoft .NET Framework 클래스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="a8506-105">이 cmdlet은이 문서의 예로 사용 되며 `Get-Process` Windows PowerShell에서 제공 하는 cmdlet과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="a8506-106">이러한 특성의 구현은 cmdlet 코드의 구현과 별개 이므로 메타 데이터로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="a8506-107">Windows PowerShell 런타임은 cmdlet을 실행할 때 특성을 인식 한 다음 각 특성에 대해 적절 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="a8506-108">이러한 특성에서 제공 하는 고유한 버전의 기능을 구현 하는 것이 좋지만 좋은 cmdlet 디자인에서는 이러한 일반적인 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8506-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="a8506-109">Cmdlet에서 선언할 수 있는 다양 한 특성에 대 한 자세한 내용은 [특성 형식](./attribute-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8506-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8506-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8506-110">See Also</span></span>

[<span data-ttu-id="a8506-111">특성 유형</span><span class="sxs-lookup"><span data-stu-id="a8506-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="a8506-112">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a8506-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
