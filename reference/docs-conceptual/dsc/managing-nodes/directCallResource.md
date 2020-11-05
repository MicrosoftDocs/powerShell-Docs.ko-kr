---
ms.date: 08/11/2020
keywords: dsc,powershell,configuration,setup
title: DSC 리소스 메서드를 직접 호출
description: Invoke-DscResource cmdlet을 사용하여 DSC 리소스의 함수 또는 메서드를 호출할 수 있습니다. 이 기능은 DSC 리소스를 사용하려는 타사에서, 또는 리소스를 개발하는 유용한 도구로 사용될 수 있습니다.
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650998"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="befa4-105">DSC 리소스 메서드를 직접 호출</span><span class="sxs-lookup"><span data-stu-id="befa4-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="befa4-106">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="befa4-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="befa4-107">[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet을 사용해 DSC 리소스의 함수 또는 메서드(MOF 기반 리소스의 `Get-TargetResource`, `Set-TargetResource` 및 `Test-TargetResource` 함수 또는 클래스 기반 리소스의 **Get** , **Set** 및 **Test** 메서드)를 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="befa4-108">이 기능은 DSC 리소스를 사용하려는 타사에서, 또는 리소스를 개발하는 유용한 도구로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="befa4-109">PowerShell 7.0 이상에서 `Invoke-DscResource`는 더 이상 WMI DSC 리소스 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="befa4-110">여기에는 **PSDesiredStateConfiguration** 의 **File** 및 **Log** 리소스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="befa4-111">일반적으로 이 cmdlet은 메타구성 속성 `refreshMode = 'Disabled'`와 함께 사용되지만 **refreshMode** 의 설정과 관계없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="befa4-112">`Invoke-DscResource` cmdlet을 호출하는 경우 **Method** 매개 변수를 사용해 호출할 메서드 또는 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="befa4-113">해시 테이블을 **Property** 매개 변수 값으로 전달해 리소스의 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="befa4-114">다음은 리소스 메서드를 직접 호출하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="befa4-115">파일이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="befa4-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="befa4-116">파일이 있는지 테스트</span><span class="sxs-lookup"><span data-stu-id="befa4-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="befa4-117">파일의 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="befa4-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="befa4-118">복합 리소스 메서드를 직접 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="befa4-119">대신 복합 리소스를 구성하는 기본 리소스의 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="befa4-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="befa4-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="befa4-120">See Also</span></span>

- [<span data-ttu-id="befa4-121">MOF를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="befa4-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="befa4-122">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="befa4-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="befa4-123">DSC 리소스 디버그</span><span class="sxs-lookup"><span data-stu-id="befa4-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
