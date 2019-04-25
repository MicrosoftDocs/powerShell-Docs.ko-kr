---
title: Cmdlet은 동적 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068541"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="2ed9a-102">Cmdlet 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2ed9a-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="2ed9a-103">Cmdlet는 경우와 같이 다른 매개 변수 인수의 특정 값을 특수 한 상황에서 사용자에 게 사용할 수 있는 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="2ed9a-104">이러한 매개 변수는 런타임에 추가 되 고 이라고 *동적 매개 변수* 있으므로 필요할 때에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="2ed9a-105">예를 들어, 특정 스위치 매개 변수를 지정 하는 경우에 여러 매개 변수를 추가 하는 cmdlet를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="2ed9a-106">공급자 및 Windows PowerShell 함수는 동적 매개 변수를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="2ed9a-107">Windows PowerShell Cmdlet에서 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2ed9a-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="2ed9a-108">Windows PowerShell 공급자 cmdlet의 여러 동적 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="2ed9a-109">예를 들어, 합니다 `Get-Item` 및 `Get-ChildItem` cmdlet 추가 `CodeSigningCert` 런타임에 매개 변수 때를 `Path` cmdlet의 매개 변수는 인증서 공급자 경로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="2ed9a-110">경우는 `Path` 다른 공급자에 대 한 경로 지정 하는 cmdlet의 매개 변수는 `CodeSigningCert` 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="2ed9a-111">다음 예제에서는 표시 하는 방법을 `CodeSigningCert` 매개 변수는 런타임에 추가 됩니다 때를 `Get-Item` cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="2ed9a-112">첫 번째 예에서는 Windows PowerShell 런타임이 매개 변수를 추가 및 cmdlet은 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="2ed9a-113">두 번째 예제에서는 파일 시스템 드라이브를 지정 하 고 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="2ed9a-114">오류 메시지를 표시 하는 `CodeSigningCert` 매개 변수를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="2ed9a-115">동적 매개 변수에 대 한 지원</span><span class="sxs-lookup"><span data-stu-id="2ed9a-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="2ed9a-116">동적 매개 변수를 지원 하려면 cmdlet 코드는 다음과 같은 요소를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="2ed9a-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 이 인터페이스는 동적 매개 변수를 검색 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="2ed9a-118">예:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="2ed9a-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 이 메서드는 동적 매개 변수 정의 포함 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="2ed9a-120">예:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-120">Example:</span></span>

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

<span data-ttu-id="2ed9a-121">동적 매개 변수 클래스가이 클래스에 추가할 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="2ed9a-122">이 클래스는 각 매개 변수 및 cmdlet에 필요한 모든 선택적 별칭 및 유효성 검사 특성에 대 한 매개 변수 특성을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="2ed9a-123">예:</span><span class="sxs-lookup"><span data-stu-id="2ed9a-123">Example:</span></span>

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

<span data-ttu-id="2ed9a-124">동적 매개 변수를 지 원하는 cmdlet의 전체 예제를 참조 하세요 [동적 매개 변수를 선언 하는 방법을](./how-to-declare-dynamic-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed9a-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ed9a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ed9a-125">See Also</span></span>

[<span data-ttu-id="2ed9a-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="2ed9a-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="2ed9a-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="2ed9a-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="2ed9a-128">동적 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2ed9a-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

<span data-ttu-id="2ed9a-129">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="2ed9a-129">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
