---
title: Cmdlet에 종료 되지 않는 오류 보고 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364612"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="7ac6a-102">Cmdlet에 종료되지 않는 오류 보고 추가</span><span class="sxs-lookup"><span data-stu-id="7ac6a-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="7ac6a-103">Cmdlet은 [WriteError입니다.][] 메서드를 호출 하 여 종료 되지 않는 오류를 보고할 수 있으며, 계속 해 서 현재 입력 개체 또는 추가로 들어오는 파이프라인 개체에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="7ac6a-104">이 섹션에서는 입력 처리 방법에서 종료 되지 않는 오류를 보고 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="7ac6a-105">종료 오류 (및 종료 오류)의 경우 cmdlet은 오류를 식별 하는 [ErrorRecord.][] 개체를 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="7ac6a-106">각 오류 레코드는 "오류 식별자" 라는 고유한 문자열로 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="7ac6a-107">식별자 외에도 각 오류의 범주는 [ErrorCategory.][] 열거형에 정의 된 상수로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="7ac6a-108">사용자는 `$ErrorView` 변수를 "CategoryView"로 설정 하 여 해당 범주에 따라 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="7ac6a-109">오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="7ac6a-110">Cmdlet 정의</span><span class="sxs-lookup"><span data-stu-id="7ac6a-110">Defining the Cmdlet</span></span>

<span data-ttu-id="7ac6a-111">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="7ac6a-112">이 cmdlet은 프로세스 정보를 검색 하므로 여기에서 선택한 동사 이름은 "Get"입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="7ac6a-113">정보를 검색할 수 있는 거의 모든 종류의 cmdlet은 명령줄 입력을 처리할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="7ac6a-114">다음은이 In-proc cmdlet에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="7ac6a-115">이 정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](creating-a-cmdlet-without-parameters.md)때 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="7ac6a-116">매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="7ac6a-116">Defining Parameters</span></span>

<span data-ttu-id="7ac6a-117">필요한 경우 cmdlet은 입력 처리를 위한 매개 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="7ac6a-118">이 cmdlet은 [명령줄 입력을 처리 하는 매개 변수 추가](adding-parameters-that-process-command-line-input.md)에 설명 된 대로 **Name** 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="7ac6a-119">다음은이 In-proc cmdlet의 **Name** 매개 변수에 대 한 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="7ac6a-120">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="7ac6a-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="7ac6a-121">모든 cmdlet은 [System.object.][] 클래스에서 제공 하는 입력 처리 메서드를 하나 이상 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="7ac6a-122">이러한 방법은 [첫 번째 Cmdlet 만들기](creating-a-cmdlet-without-parameters.md)에서 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7ac6a-123">Cmdlet은 각 레코드를 가능한 한 독립적으로 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="7ac6a-124">이 Get-Proc cmdlet 메서드는 사용자 또는 스크립트에서 제공하는 입력에 대한 **Name** 매개 변수를 처리하기 위해 [ProcessRecord입니다.][] 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="7ac6a-125">이 메서드는 요청 된 각 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 이름이 제공 되지 않은 경우에는입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="7ac6a-126">이 재정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](creating-a-cmdlet-without-parameters.md)때 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="7ac6a-127">오류를 보고할 때 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="7ac6a-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="7ac6a-128">오류를 기록할 때 cmdlet이 전달 하는 [ErrorRecord.][] 개체에는 코어의 예외가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="7ac6a-129">사용할 예외를 결정할 때 .NET 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="7ac6a-130">기본적으로 오류가 기존 예외와 의미상 동일 하면 cmdlet은 해당 예외를 사용 하거나이를 파생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="7ac6a-131">그렇지 않은 경우에는 [system.object][] 클래스에서 직접 새 예외 또는 예외 계층 구조를 파생 시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="7ac6a-132">ErrorRecord 클래스의 FullyQualifiedErrorId 속성을 통해 액세스 되는 오류 식별자를 만들 때 다음 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="7ac6a-133">진단 목적으로 대상으로 지정 된 문자열을 사용 하 여 정규화 된 식별자를 검사할 때 오류가 발생 한 위치와 오류가 발생 한 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="7ac6a-134">잘 구성 된 정규화 된 오류 식별자는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="7ac6a-135">앞의 예제에서 오류 식별자 (첫 번째 토큰)는 오류가 무엇 인지를 지정 하 고 나머지 부분은 오류가 발생 한 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="7ac6a-136">더 복잡 한 시나리오의 경우 오류 식별자는 검사 시 구문 분석할 수 있는 점으로 구분 된 토큰이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="7ac6a-137">이를 통해 오류 식별자 및 오류 범주에 대 한 오류 식별자 부분을 너무 분기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="7ac6a-138">Cmdlet은 특정 오류 식별자를 다른 코드 경로에 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="7ac6a-139">오류 식별자 할당에 대 한 다음 정보를 염두에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="7ac6a-140">오류 식별자는 cmdlet 수명 주기 전체에서 일정 하 게 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="7ac6a-141">Cmdlet 버전 간에 오류 식별자의 의미 체계를 변경 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="7ac6a-142">보고 되는 오류에 해당 하는 오류 식별자에 tersely 텍스트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="7ac6a-143">공백 또는 문장 부호를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="7ac6a-144">Cmdlet에서 재현 가능한 오류 식별자만 생성 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="7ac6a-145">예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="7ac6a-146">오류 식별자는 동일한 문제가 발생 한 다른 사용자에 게 표시 되는 식별자에 해당 하는 경우에만 사용자에 게 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="7ac6a-147">처리 되지 않은 예외는 다음 조건에서 PowerShell에 의해 catch 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="7ac6a-148">Cmdlet이 새 스레드를 만들고 해당 스레드에서 실행 중인 코드가 처리 되지 않은 예외를 throw 하는 경우 PowerShell은 오류를 catch 하지 않고 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="7ac6a-149">개체의 소멸자 나 처리 되지 않은 예외를 발생 시키는 Dispose 메서드에 코드가 있으면 PowerShell에서 오류를 catch 하지 않고 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="7ac6a-150">종료 되지 않는 오류 보고</span><span class="sxs-lookup"><span data-stu-id="7ac6a-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="7ac6a-151">입력 처리 방법 중 하나는 [WriteError입니다.][] 메서드를 사용 하 여 출력 스트림에 종료 되지 않는 오류를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="7ac6a-152">[ProcessRecord입니다.][] 메서드 재정의 내에서 [WriteError입니다.][]에 대한 호출을 보여 주는이 Get-Proc cmdlet의 코드 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="7ac6a-153">이 경우 cmdlet에서 지정 된 프로세스 식별자에 대 한 프로세스를 찾을 수 없는 경우 호출이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="7ac6a-154">종료 되지 않는 오류를 기록 하는 방법에 대해 알아야 할 사항</span><span class="sxs-lookup"><span data-stu-id="7ac6a-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="7ac6a-155">종료 되지 않는 오류의 경우 cmdlet은 각 특정 입력 개체에 대해 특정 오류 식별자를 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="7ac6a-156">Cmdlet은 종료 되지 않는 오류에 의해 생성 된 PowerShell 작업을 수정 해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="7ac6a-157">@No__t_0 및 `ErrorVariable` 매개 변수를 정의 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="7ac6a-158">@No__t_0 매개 변수를 정의 하는 경우 cmdlet은 [System.object 기본 설정][], `$ErrorActionPreference` 변수를 설정 하 여 작업에 직접 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="7ac6a-159">Cmdlet은 `ErrorAction` 설정의 영향을 받지 않는 `ErrorVariable` 매개 변수를 사용 하 여 종료 되지 않는 오류를 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="7ac6a-160">변수 이름 앞에 더하기 기호 (+)를 추가 하 여 기존 오류 변수에 오류를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7ac6a-161">코드 예제</span><span class="sxs-lookup"><span data-stu-id="7ac6a-161">Code Sample</span></span>

<span data-ttu-id="7ac6a-162">전체 C# 샘플 코드는 [GetProcessSample04 샘플](./getprocesssample04-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="7ac6a-163">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="7ac6a-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="7ac6a-164">PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="7ac6a-165">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="7ac6a-166">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="7ac6a-167">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="7ac6a-167">Building the Cmdlet</span></span>

<span data-ttu-id="7ac6a-168">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="7ac6a-169">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="7ac6a-170">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="7ac6a-170">Testing the Cmdlet</span></span>

<span data-ttu-id="7ac6a-171">PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="7ac6a-172">샘플 cmdlet을 테스트 하 여 오류를 보고 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="7ac6a-173">PowerShell을 시작 하 고, Get-help cmdlet을 사용 하 여 "TEST" 라는 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="7ac6a-174">다음 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac6a-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="7ac6a-175">관련 항목</span><span class="sxs-lookup"><span data-stu-id="7ac6a-175">See Also</span></span>

[<span data-ttu-id="7ac6a-176">파이프라인 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="7ac6a-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="7ac6a-177">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="7ac6a-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="7ac6a-178">첫 번째 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="7ac6a-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="7ac6a-179">개체 형식 및 서식 확장</span><span class="sxs-lookup"><span data-stu-id="7ac6a-179">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="7ac6a-180">Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="7ac6a-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="7ac6a-181">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="7ac6a-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="7ac6a-182">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="7ac6a-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[system.object]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System.object 기본 설정]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[ProcessRecord입니다.]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[WriteError입니다.]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.object.]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[ErrorCategory.]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[ErrorRecord.]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
