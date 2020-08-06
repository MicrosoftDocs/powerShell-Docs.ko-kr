---
title: 확장 유형 시스템 클래스 멤버
ms.date: 07/09/2020
ms.openlocfilehash: 24a57b7fd0b3db47d0d7138859aa0502ca9016f0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786274"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="c0647-102">확장 유형 시스템 클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="c0647-102">Extended Type System class members</span></span>

<span data-ttu-id="c0647-103">**PSMemberTypes** 열거형에 의해 정의 되는 형식을 가진 여러 종류의 멤버를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-103">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="c0647-104">이러한 멤버 형식에는 각각 고유한 CLR 형식으로 정의 되는 속성, 메서드, 멤버 및 멤버 집합이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-104">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="c0647-105">예를 들어, **참고 속성** 은 고유한 **psnoteproperty** 형식으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-105">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="c0647-106">이러한 개별 CLR 형식에는 [Psmemberinfo 클래스](/dotnet/api/system.management.automation.psmemberinfo)에서 상속 되는 고유한 속성과 공용 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-106">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="c0647-107">PSMemberInfo 클래스</span><span class="sxs-lookup"><span data-stu-id="c0647-107">The PSMemberInfo class</span></span>

<span data-ttu-id="c0647-108">**Psmemberinfo** 클래스는 모든 멤버 형식에 대 한 기본 클래스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-108">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="c0647-109">이 클래스는 모든 멤버 CLR 형식에 대 한 다음 기본 속성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-109">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="c0647-110">**Name** 속성: 멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-110">**Name** property: The name of the member.</span></span> <span data-ttu-id="c0647-111">이 이름은 기본 개체에서 정의 하거나, 적용 된 멤버나 확장 멤버가 노출 될 때 PowerShell에서 정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-111">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="c0647-112">**Value** 속성: 특정 멤버에서 반환 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-112">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="c0647-113">각 멤버 형식은 해당 멤버 값을 처리 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-113">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="c0647-114">**TypeNameOfValue** Property: value 속성에 의해 반환 되는 값의 CLR 형식 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-114">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="c0647-115">멤버 액세스</span><span class="sxs-lookup"><span data-stu-id="c0647-115">Accessing members</span></span>

<span data-ttu-id="c0647-116">멤버 컬렉션은 **PSObject** 개체의 **멤버**, **메서드**및 **속성** 속성을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-116">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="c0647-117">속성 속성</span><span class="sxs-lookup"><span data-stu-id="c0647-117">ETS properties</span></span>

<span data-ttu-id="c0647-118">속성은 속성으로 처리 될 수 있는 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-118">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="c0647-119">기본적으로 식의 왼쪽에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-119">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="c0647-120">별칭 속성, 코드 속성, PowerShell 속성, 메모 속성 및 스크립트 속성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-120">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="c0647-121">이러한 속성 유형에 대 한 자세한 내용은 속성 [속성](properties.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0647-121">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="c0647-122">메서드</span><span class="sxs-lookup"><span data-stu-id="c0647-122">ETS methods</span></span>

<span data-ttu-id="c0647-123">인수는 인수를 사용 하 고 결과를 반환할 수 있으며 식의 왼쪽에 표시 될 수 없는 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-123">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="c0647-124">여기에는 코드 메서드, PowerShell 메서드 및 스크립트 메서드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0647-124">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="c0647-125">이러한 메서드 형식에 대 한 자세한 [내용은 메서드를 참조 하세요](methods.md).</span><span class="sxs-lookup"><span data-stu-id="c0647-125">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
