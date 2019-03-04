---
title: Cmdlet 특성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853919"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="69a18-102">Cmdlet 특성</span><span class="sxs-lookup"><span data-stu-id="69a18-102">Cmdlet Attributes</span></span>

<span data-ttu-id="69a18-103">Windows PowerShell 공통 기능을 사용자 고유의 코드 내에서 해당 기능을 구현 하지 않고 cmdlet을 추가 하는 데 사용할 수 있는 몇 가지 특성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="69a18-104">여기에 cmdlet 클래스, cmdlet, cmdlet으로 공용 속성을 식별 하는 매개 변수 특성에서 반환 되는.NET Framework 형식 지정 하는 OutputType 특성으로 Microsoft.NET Framework 클래스를 식별 하는 Cmdlet 특성 매개 변수 및 기타 정보</span><span class="sxs-lookup"><span data-stu-id="69a18-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="69a18-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="69a18-105">In This Section</span></span>

<span data-ttu-id="69a18-106">[Cmdlet 코드의 특성이](./attributes-in-cmdlet-code.md) cmdlet 코드에서 특성을 사용 하는 혜택에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="69a18-107">[특성 유형을](./attribute-types.md) 데코레이팅하는 cmdlet 클래스는 다른 특성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="69a18-108">[별칭 특성 선언은](./alias-attribute-declaration.md) cmdlet 매개 변수 이름에 대 한 별칭을 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="69a18-109">[Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md) cmdlet를.NET Framework 클래스를 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="69a18-110">[특성 선언을 자격 증명](./credential-attribute-declaration.md) 문자열 입력에 변환에 대 한 지원을 추가 하는 방법에 설명 합니다는 [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="69a18-111">[OutputType 특성 선언](./outputtype-attribute-declaration.md) cmdlet에서 반환 되는.NET Framework 형식 지정 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="69a18-112">[매개 변수 특성 선언](./parameter-attribute-declaration.md) cmdlet의 매개 변수를 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="69a18-113">[ValidateCount 특성 선언을](./validatecount-attribute-declaration.md) 인수의 개수 매개 변수의 수를 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="69a18-114">[ValidateLength 특성 선언을](./validatelength-attribute-declaration.md) 매개 변수 인수의 문자에서 길이 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="69a18-115">[ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md) 매개 변수 인수에 대 한 유효한 패턴을 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="69a18-116">[ValidateRange 특성 선언을](./validaterange-attribute-declaration.md) 매개 변수 인수에 대 한 유효한 범위를 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="69a18-117">[ValidateSet 특성 선언을](./validateset-attribute-declaration.md) 매개 변수 인수에 대 한 가능한 값을 정의 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a18-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="69a18-118">참조</span><span class="sxs-lookup"><span data-stu-id="69a18-118">Reference</span></span>

<span data-ttu-id="69a18-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="69a18-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
