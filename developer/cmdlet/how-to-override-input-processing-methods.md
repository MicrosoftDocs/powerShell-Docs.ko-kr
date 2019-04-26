---
title: 입력 처리 메서드를 재정의 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067946"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="9d9b8-102">입력 처리 메서드를 재정의하는 방법</span><span class="sxs-lookup"><span data-stu-id="9d9b8-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="9d9b8-103">이러한 예제에는 입력 처리 cmdlet 내에서 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="9d9b8-104">이러한 메서드는 다음 작업을 수행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="9d9b8-105">합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드 cmdlet에서 처리 하는 모든 개체에 대 한 유효한 일회성 시작 작업을 수행 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="9d9b8-106">Windows PowerShell 런타임에이 메서드를 한 번만 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="9d9b8-107">합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet에 전달 된 개체를 처리할 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="9d9b8-108">Windows PowerShell 런타임에 cmdlet에 전달 되는 각 개체에 대 한이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="9d9b8-109">합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드는 일회성 사후 처리 작업을 수행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="9d9b8-110">Windows PowerShell 런타임에이 메서드를 한 번만 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="9d9b8-111">BeginProcessing 메서드를 재정의 하려면</span><span class="sxs-lookup"><span data-stu-id="9d9b8-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="9d9b8-112">보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="9d9b8-113">다음 클래스에는 샘플 메시지를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-113">The following class prints a sample message.</span></span> <span data-ttu-id="9d9b8-114">이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="9d9b8-115">ProcessRecord 메서드를 재정의 하려면</span><span class="sxs-lookup"><span data-stu-id="9d9b8-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="9d9b8-116">보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="9d9b8-117">다음 클래스에는 샘플 메시지를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-117">The following class prints a sample message.</span></span> <span data-ttu-id="9d9b8-118">이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="9d9b8-119">EndProcessing 메서드를 재정의 하려면</span><span class="sxs-lookup"><span data-stu-id="9d9b8-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="9d9b8-120">보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="9d9b8-121">다음 클래스는 샘플을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-121">The following class prints a sample.</span></span> <span data-ttu-id="9d9b8-122">이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="9d9b8-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="9d9b8-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d9b8-123">See Also</span></span>

[<span data-ttu-id="9d9b8-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="9d9b8-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="9d9b8-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="9d9b8-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="9d9b8-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="9d9b8-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

<span data-ttu-id="9d9b8-127">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9d9b8-127">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
