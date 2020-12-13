---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 특성
description: Cmdlet 특성
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653519"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="dded5-103">Cmdlet 특성</span><span class="sxs-lookup"><span data-stu-id="dded5-103">Cmdlet Attributes</span></span>

<span data-ttu-id="dded5-104">Windows PowerShell은 사용자 코드 내에서 해당 기능을 구현 하지 않고 cmdlet에 일반적인 기능을 추가 하는 데 사용할 수 있는 여러 특성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-104">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="dded5-105">여기에는 cmdlet 클래스로 Microsoft .NET Framework 클래스를 식별 하는 Cmdlet 특성, cmdlet에서 반환 되는 .NET Framework 형식을 지정 하는 OutputType 특성, cmdlet 매개 변수로 공용 속성을 식별 하는 매개 변수 특성 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-105">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dded5-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="dded5-106">In This Section</span></span>

<span data-ttu-id="dded5-107">[Cmdlet 코드의 특성](./attributes-in-cmdlet-code.md) Cmdlet 코드에서 특성을 사용 하는 경우의 이점을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-107">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="dded5-108">[특성 유형](./attribute-types.md) Cmdlet 클래스를 데코레이팅 할 수 있는 다양 한 특성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-108">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="dded5-109">[별칭 특성 선언](./alias-attribute-declaration.md) Cmdlet 매개 변수 이름에 대 한 별칭을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-109">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="dded5-110">[Cmdlet 특성 선언](./cmdlet-attribute-declaration.md) .NET Framework 클래스를 cmdlet으로 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-110">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="dded5-111">[자격 증명 특성 선언](./credential-attribute-declaration.md) 문자열 입력을 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 로 변환 하기 위한 지원을 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-111">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="dded5-112">[OutputType 특성 선언](./outputtype-attribute-declaration.md) Cmdlet에서 반환 되는 .NET Framework 유형을 지정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-112">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="dded5-113">[매개 변수 특성 선언](./parameter-attribute-declaration.md) Cmdlet의 매개 변수를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-113">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="dded5-114">[Validatecount 특성 선언](./validatecount-attribute-declaration.md) 매개 변수에 허용 되는 인수 수를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-114">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="dded5-115">[ValidateLength 특성 선언](./validatelength-attribute-declaration.md) 매개 변수 인수의 길이 (문자 수)를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-115">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="dded5-116">[ValidatePattern 특성 선언](./validatepattern-attribute-declaration.md) 매개 변수 인수에 대 한 올바른 패턴을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-116">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="dded5-117">[ValidateRange 특성 선언](./validaterange-attribute-declaration.md) 매개 변수 인수의 올바른 범위를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-117">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="dded5-118">[ValidateSet 특성 선언](./validateset-attribute-declaration.md) 매개 변수 인수에 사용할 수 있는 값을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dded5-118">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="dded5-119">참조</span><span class="sxs-lookup"><span data-stu-id="dded5-119">Reference</span></span>

<span data-ttu-id="dded5-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="dded5-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
