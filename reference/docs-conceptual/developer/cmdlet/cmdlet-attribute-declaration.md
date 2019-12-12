---
title: Cmdlet 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363542"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="4d99c-102">Cmdlet 특성 선언</span><span class="sxs-lookup"><span data-stu-id="4d99c-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="4d99c-103">Cmdlet 특성은 Microsoft .NET Framework 클래스를 cmdlet으로 식별 하 고 cmdlet을 호출 하는 데 사용 되는 동사와 명사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d99c-104">구문</span><span class="sxs-lookup"><span data-stu-id="4d99c-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="4d99c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4d99c-105">Parameters</span></span>

<span data-ttu-id="4d99c-106">`VerbName` ([system.string](/dotnet/api/System.String))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="4d99c-107">Cmdlet 동사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="4d99c-108">이 동사는 cmdlet이 수행 하는 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="4d99c-109">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md) 및 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d99c-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="4d99c-110">`NounName` ([system.string](/dotnet/api/System.String))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="4d99c-111">Cmdlet 명사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="4d99c-112">이 명사는 cmdlet이 작동 하는 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="4d99c-113">Cmdlet 명사에 대 한 자세한 내용은 [Cmdlet 선언](./cmdlet-class-declaration.md) 및 강력 하 게 권장 되는 [개발 지침](./strongly-encouraged-development-guidelines.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d99c-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="4d99c-114">`SupportsShouldProcess` ([system.string](/dotnet/api/System.Boolean)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="4d99c-115">`True` cmdlet은 시스템을 변경 하는 작업을 수행 하기 전에 사용자에 게 메시지를 표시 하는 방법을 제공 하는 cmdlet을 제공 하는 system.servicemodel [프로세스](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드에 대 한 호출을 지원함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="4d99c-116">`False`기본값은 cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 것을 지원 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="4d99c-117">확인 요청에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d99c-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="4d99c-118">`ConfirmImpact` ([system.string](/dotnet/api/System.Management.Automation.ConfirmImpact)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="4d99c-119">Cmdlet에 대 한 호출을 통해 cmdlet의 동작을 확인 하는 시기를 지정 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="4d99c-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="4d99c-120">Cmdlet (기본적으로 Medium)의 기능 (기본값)이 `$ConfirmPreference` 변수의 값 보다 크거나 같은 경우에만 [ [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ]를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="4d99c-121">이 매개 변수는 `SupportsShouldProcess` 매개 변수가 지정 된 경우에만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="4d99c-122">`DefaultParameterSetName` ([system.string](/dotnet/api/System.String)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="4d99c-123">사용할 매개 변수 집합을 확인할 수 없는 경우 Windows PowerShell 런타임에서 사용 하려는 기본 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="4d99c-124">각 매개 변수의 고유한 매개 변수를 필수 매개 변수로 설정 하 여이 상황을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="4d99c-125">기본 매개 변수 집합 이름이 지정 된 경우에도 Windows PowerShell에서 기본 매개 변수 집합을 사용할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="4d99c-126">Windows PowerShell 런타임에서는 단순히 개체 유형을 기반으로 하는 매개 변수 집합을 구분할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="4d99c-127">예를 들어 문자열을 파일 경로로 사용 하는 하나의 매개 변수 집합을 사용 하 고 **FileInfo** 개체를 직접 사용 하는 다른 집합을 사용 하는 경우 Windows PowerShell은 cmdlet에 전달 된 값에 따라 사용할 매개 변수 집합을 확인할 수 없으며 기본 매개 변수 집합을 사용 하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="4d99c-128">이 경우 기본 매개 변수 설정 이름을 지정 하는 경우에도 Windows PowerShell에서 모호한 매개 변수 설정 오류 메시지를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="4d99c-129">`SupportsTransactions` ([system.string](/dotnet/api/System.Boolean)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="4d99c-130">`True` cmdlet을 트랜잭션 내에서 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="4d99c-131">`True` 지정 된 경우 Windows PowerShell 런타임은 cmdlet의 매개 변수 목록에 `UseTransaction` 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="4d99c-132">`False`기본값은 트랜잭션 내에서 cmdlet을 사용할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d99c-133">설명</span><span class="sxs-lookup"><span data-stu-id="4d99c-133">Remarks</span></span>

- <span data-ttu-id="4d99c-134">동사와 명사는 함께 등록 된 cmdlet을 식별 하 고 스크립트 내에서 cmdlet을 호출 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="4d99c-135">Windows PowerShell 콘솔에서이 cmdlet을 호출 하는 경우 명령은 다음 명령과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="4d99c-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="4d99c-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="4d99c-137">Cmdlet 특성이 선언 될 때 Windows PowerShell 외부에서 리소스를 변경 하는 모든 cmdlet에는 `SupportsShouldProcess` 키워드가 포함 되어야 합니다. 이렇게 하면 cmdlet에서 해당 작업을 수행 하기 전에 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="4d99c-138">`false`를 반환 [하는 경우에는 작업](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="4d99c-139">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여 생성 된 확인 요청에 대 한 자세한 내용은 [요청 확인](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d99c-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="4d99c-140">`Confirm` 및 `WhatIf` cmdlet 매개 변수는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 지 원하는 cmdlet에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="4d99c-141">예제</span><span class="sxs-lookup"><span data-stu-id="4d99c-141">Example</span></span>

<span data-ttu-id="4d99c-142">다음 클래스 정의에서는 Cmdlet 특성을 사용 하 여 로컬 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 검색 **하는 node.js cmdlet에** 대 한 .NET Framework 클래스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d99c-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="4d99c-143">**Get-help** cmdlet에 대 한 자세한 내용은 [getproc 자습서](./getproc-tutorial.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d99c-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d99c-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d99c-144">See Also</span></span>

<span data-ttu-id="4d99c-145">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="4d99c-145">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
