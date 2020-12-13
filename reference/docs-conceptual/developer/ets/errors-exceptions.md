---
ms.date: 07/09/2020
ms.topic: reference
title: 확장 유형 시스템에서 발생 하는 오류 및 예외
description: 확장 유형 시스템에서 발생 하는 오류 및 예외
ms.openlocfilehash: 295c16ad9abb67b0c4967bf32125bfc7ee0a35da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652485"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a><span data-ttu-id="fb374-103">확장 유형 시스템에서 발생 하는 오류 및 예외</span><span class="sxs-lookup"><span data-stu-id="fb374-103">Errors and exceptions in the Extended Type System</span></span>

<span data-ttu-id="fb374-104">오류는 형식 데이터를 초기화 하는 동안 그리고 **PSObject** 개체의 멤버에 액세스 하거나 **languageprimitives.physicalhash** 와 같은 유틸리티 클래스 중 하나를 사용 하는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-104">Errors can occur in ETS during the initialization of type data and when accessing a member of an **PSObject** object or using one of the utility classes such as **LanguagePrimitives**.</span></span>

## <a name="runtime-errors"></a><span data-ttu-id="fb374-105">런타임 오류</span><span class="sxs-lookup"><span data-stu-id="fb374-105">Runtime errors</span></span>

<span data-ttu-id="fb374-106">한 가지 예외를 제외 하 고, 캐스팅할 때 런타임에 **ExtendedTypeSystemException** 에서 throw 되는 모든 예외는 **ExtendedTypeSystemException** 클래스에서 파생 된 예외 또는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-106">With one exception, when casting, all exceptions thrown from ETS during runtime are either an **ExtendedTypeSystemException** exception or an exception derived from the **ExtendedTypeSystemException** class.</span></span> <span data-ttu-id="fb374-107">이렇게 하면 스크립트 개발자가 스크립트의 문을 사용 하 여 이러한 예외를 트래핑할 수 있습니다 `Trap` .</span><span class="sxs-lookup"><span data-stu-id="fb374-107">This allows script developers to trap these exceptions using the `Trap` statement in their script.</span></span>

## <a name="errors-getting-member-values"></a><span data-ttu-id="fb374-108">멤버 값을 가져오는 중 오류 발생</span><span class="sxs-lookup"><span data-stu-id="fb374-108">Errors getting member values</span></span>

<span data-ttu-id="fb374-109">GetValueInvocationException 멤버 (속성, 메서드 또는 매개 변수가 있는 속성)의 값을 가져올 때 발생 하는 모든 오류는 **Getvalueexception** 또는  exception을 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-109">All errors that occur when getting the value of an ETS member (property, method, or parameterized property) cause a **GetValueException** or **GetValueInvocationException** exception to be thrown.</span></span>
<span data-ttu-id="fb374-110">오류가 발생 했음을 인식 하면 **Getvalueexception** 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-110">When ETS recognizes that an error occurred a **GetValueException** exception is thrown.</span></span> <span data-ttu-id="fb374-111">참조 된 멤버의 기본 getter가 오류가 발생 한 것을 인식 하는 경우 get 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **GetValueInvocationException** 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-111">When the underlying getter of a referenced member recognizes that an error occurred, a **GetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the get invocation error.</span></span>

## <a name="errors-setting-member-values"></a><span data-ttu-id="fb374-112">오류 설정 멤버 값</span><span class="sxs-lookup"><span data-stu-id="fb374-112">Errors setting member values</span></span>

<span data-ttu-id="fb374-113">SetValueInvocationException 속성 값을 설정할 때 발생 하는 모든 오류는 **Setvalueexception** 또는  exception을 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-113">All errors that occur when setting the value of an ETS property cause a **SetValueException** or **SetValueInvocationException** exception to be thrown.</span></span> <span data-ttu-id="fb374-114">오류가 발생 했음을 인식 하면 **Setvalueexception** 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-114">When ETS recognizes that an error occurred a **SetValueException** exception is thrown.</span></span> <span data-ttu-id="fb374-115">참조 된 속성의 기본 setter가 오류가 발생 한 것을 인식 하면 set 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **SetValueInvocationException** 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-115">When the underlying setter of a referenced property recognizes that an error occurred, a **SetValueInvocationException** exception is thrown that may or may not include the inner exception that caused the set invocation error.</span></span>

## <a name="errors-invoking-a-method"></a><span data-ttu-id="fb374-116">메서드를 호출 하는 오류</span><span class="sxs-lookup"><span data-stu-id="fb374-116">Errors invoking a method</span></span>

<span data-ttu-id="fb374-117">MethodInvocationException 메서드를 호출할 때 발생 하는 모든 오류는 **MethodException** 또는  예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-117">All errors that occur when invoking an ETS method cause a **MethodException** or **MethodInvocationException** exception to be thrown.</span></span> <span data-ttu-id="fb374-118">**MethodException** 에서 오류가 발생 한 것으로 인식 되 면 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-118">When ETS recognizes that an error occurred a **MethodException** exception is thrown.</span></span> <span data-ttu-id="fb374-119">참조 된 메서드에서 오류가 발생 한 것을 인식 하면 호출 오류를 발생 시킨 내부 예외를 포함 하거나 포함 하지 않을 수 있는 **MethodInvocationException** 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-119">When the referenced method recognizes that an error occurred, a **MethodInvocationException** exception is thrown that may or may not include the inner exception that caused the invocation error.</span></span>

## <a name="casting-errors"></a><span data-ttu-id="fb374-120">캐스팅 오류</span><span class="sxs-lookup"><span data-stu-id="fb374-120">Casting errors</span></span>

<span data-ttu-id="fb374-121">잘못 된 캐스팅을 시도 하면 **PSInvalidCastException** 이 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-121">When an invalid cast is attempted, an **PSInvalidCastException** is thrown.</span></span> <span data-ttu-id="fb374-122">이 예외는 **InvalidCastException** 에서 파생 되기 때문에 스크립트에서 직접 트랩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-122">Because this exception derives from **System.InvalidCastException**, it is not able to be directly trapped from script.</span></span> <span data-ttu-id="fb374-123">캐스팅을 시도 하는 엔터티는 **이를** **PSInvalidCastException** 로 래핑하여 스크립트에서 트래핑할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-123">Be aware that the entity attempting the cast would need to wrap **PSInvalidCastException** in an **PSRuntimeException** for this to be trappable by scripts.</span></span> <span data-ttu-id="fb374-124">**PSPropertySet**, **psmemberset**, **psmemberset** 또는 **ReadOnlyPSMemberInfoCollection ' 1** 의 멤버의 값을 설정 하려고 하면 **NotSupportedException** 이 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-124">If an attempt is made to set the value of an **PSPropertySet**, **PSMemberSet**, **PSMethodInfo**, or a member of the **ReadOnlyPSMemberInfoCollection\`1**, a **NotSupportedException** is thrown.</span></span>

## <a name="common-runtime-errors"></a><span data-ttu-id="fb374-125">일반적인 런타임 오류</span><span class="sxs-lookup"><span data-stu-id="fb374-125">Common runtime errors</span></span>

<span data-ttu-id="fb374-126">발생 하는 다른 모든 일반적인 런타임 오류는 특정 예외 형식이 추가로 없는 **ExtendedTypeSystemException** exception 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-126">Any other common runtime errors that occur are of type **ExtendedTypeSystemException** exception with no additional specific exception types.</span></span>

## <a name="initialization-errors"></a><span data-ttu-id="fb374-127">초기화 오류</span><span class="sxs-lookup"><span data-stu-id="fb374-127">Initialization errors</span></span>

<span data-ttu-id="fb374-128">를 초기화할 때 오류가 발생할 수 있습니다 `types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="fb374-128">Errors may occur when initializing `types.ps1xml`.</span></span> <span data-ttu-id="fb374-129">일반적으로 이러한 오류는 PowerShell 런타임이 시작 될 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-129">Typically, these errors are displayed when the PowerShell runtime starts.</span></span> <span data-ttu-id="fb374-130">그러나 모듈이 로드 될 때 표시 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb374-130">However, they can also be displayed when a module is loaded.</span></span>
