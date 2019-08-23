---
title: Cmdlet 동적 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986249"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="34744-102">Cmdlet 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="34744-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="34744-103">Cmdlet은 다른 매개 변수의 인수가 특정 값인 경우와 같이 사용자가 특별 한 조건에서 사용할 수 있는 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34744-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="34744-104">이러한 매개 변수는 런타임에 추가 되며 필요한 경우에만 추가 되므로 동적 매개 변수 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="34744-105">예를 들어 특정 스위치 매개 변수가 지정 된 경우에만 여러 매개 변수를 추가 하는 cmdlet을 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34744-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="34744-106">공급자 및 PowerShell 함수는 동적 매개 변수를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34744-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="34744-107">PowerShell cmdlet의 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="34744-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="34744-108">PowerShell은 여러 공급자 cmdlet에서 동적 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="34744-109">예를 들어, `Get-Item` 및 `Get-ChildItem` cmdlet은 **path** 매개 변수에서 **인증서** 공급자 경로를 지정 하는 경우 런타임에 **codesigningcert** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="34744-110">**Path** 매개 변수가 다른 공급자의 경로를 지정 하는 경우 **Codesigningcert** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34744-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="34744-111">다음 예에서는를 실행할 `Get-Item` 때 **codesigningcert** 매개 변수를 런타임에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34744-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="34744-112">이 예에서는 PowerShell 런타임에서 매개 변수를 추가 하 고 cmdlet이 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34744-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="34744-113">이 예제에서는 **파일 시스템** 드라이브를 지정 하 고 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34744-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="34744-114">오류 메시지는 **Codesigningcert** 매개 변수를 찾을 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34744-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="34744-115">동적 매개 변수 지원</span><span class="sxs-lookup"><span data-stu-id="34744-115">Support for dynamic parameters</span></span>

<span data-ttu-id="34744-116">동적 매개 변수를 지원 하려면 다음 요소를 cmdlet 코드에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="34744-117">인터페이스</span><span class="sxs-lookup"><span data-stu-id="34744-117">Interface</span></span>

<span data-ttu-id="34744-118">[IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)입니다.</span><span class="sxs-lookup"><span data-stu-id="34744-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="34744-119">이 인터페이스는 동적 매개 변수를 검색 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="34744-120">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="34744-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="34744-121">메서드</span><span class="sxs-lookup"><span data-stu-id="34744-121">Method</span></span>

<span data-ttu-id="34744-122">[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)</span><span class="sxs-lookup"><span data-stu-id="34744-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="34744-123">이 메서드는 동적 매개 변수 정의를 포함 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="34744-124">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="34744-124">For example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a><span data-ttu-id="34744-125">클래스</span><span class="sxs-lookup"><span data-stu-id="34744-125">Class</span></span>

<span data-ttu-id="34744-126">추가할 동적 매개 변수를 정의 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="34744-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="34744-127">이 클래스에는 각 매개 변수에 대 한 **매개 변수** 특성과 cmdlet에 필요한 선택적 **별칭** 및 **유효성 검사** 특성이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34744-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="34744-128">예:</span><span class="sxs-lookup"><span data-stu-id="34744-128">For example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="34744-129">동적 매개 변수를 지 원하는 cmdlet의 전체 예제는 [동적 매개 변수를 선언 하는 방법](./how-to-declare-dynamic-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34744-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34744-130">참고자료</span><span class="sxs-lookup"><span data-stu-id="34744-130">See also</span></span>

[<span data-ttu-id="34744-131">IDynamicParameters.</span><span class="sxs-lookup"><span data-stu-id="34744-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="34744-132">IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="34744-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="34744-133">동적 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="34744-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

<span data-ttu-id="34744-134">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="34744-134">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
