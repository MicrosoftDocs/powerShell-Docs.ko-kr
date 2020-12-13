---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 코드의 특성
description: Cmdlet 코드의 특성
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653647"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="63f12-103">Cmdlet 코드의 특성</span><span class="sxs-lookup"><span data-stu-id="63f12-103">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="63f12-104">Windows PowerShell에서 제공 하는 공통 기능을 사용 하기 위해 cmdlet 코드에 정의 된 클래스 및 공용 속성은 특성으로 데코 레이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-104">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="63f12-105">예를 들어, 다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 **Get Proc** cmdlet이 구현 된 Microsoft .NET Framework 클래스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-105">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="63f12-106">이 cmdlet은이 문서의 예로 사용 되며 `Get-Process` Windows PowerShell에서 제공 하는 cmdlet과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-106">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="63f12-107">이러한 특성의 구현은 cmdlet 코드의 구현과 별개 이므로 메타 데이터로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-107">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="63f12-108">Windows PowerShell 런타임은 cmdlet을 실행할 때 특성을 인식 한 다음 각 특성에 대해 적절 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-108">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="63f12-109">이러한 특성에서 제공 하는 고유한 버전의 기능을 구현 하는 것이 좋지만 좋은 cmdlet 디자인에서는 이러한 일반적인 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f12-109">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="63f12-110">Cmdlet에서 선언할 수 있는 다양 한 특성에 대 한 자세한 내용은 [특성 형식](./attribute-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63f12-110">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63f12-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63f12-111">See Also</span></span>

[<span data-ttu-id="63f12-112">특성 유형</span><span class="sxs-lookup"><span data-stu-id="63f12-112">Attribute Types</span></span>](./attribute-types.md)

<span data-ttu-id="63f12-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="63f12-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
