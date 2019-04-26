---
title: 비종료 오류 보고를 Cmdlet에 추가 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068867"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="8ec04-102">Cmdlet에 종료되지 않는 오류 보고 추가</span><span class="sxs-lookup"><span data-stu-id="8ec04-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="8ec04-103">Cmdlet를 호출 하 여 종료 되지 않는 오류를 보고할 수는 [System.Management.Automation.Cmdlet.WriteError][] 메서드 계속 해 서 추가로 들어오는 또는 현재 입력된 개체에서 작동 하 고 개체를 파이프라인.</span><span class="sxs-lookup"><span data-stu-id="8ec04-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="8ec04-104">이 섹션에는 해당 입력된 처리 메서드를 종료 되지 않는 오류를 보고 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="8ec04-105">종료 되지 않는 오류 (뿐만 아니라 종료 오류), cmdlet 통과 해야 합니다는 [System.Management.Automation.ErrorRecord][] 오류를 식별 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="8ec04-106">각 error 레코드는 "오류 식별자"를 호출 하는 고유 문자열로 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="8ec04-107">식별자 외에도 각 오류의 범주 된 정의 된 상수는 [System.Management.Automation.ErrorCategory][] 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="8ec04-108">사용자는 설정 하 여 해당 범주에 따라 오류를 볼 수는 `$ErrorView` "CategoryView" 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="8ec04-109">오류 레코드에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="8ec04-110">Cmdlet을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-110">Defining the Cmdlet</span></span>

<span data-ttu-id="8ec04-111">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="8ec04-112">이 cmdlet은 "Get" 여기에서 선택한 동사 이름 이므로 프로세스 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="8ec04-113">(거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="8ec04-114">다음은이 Get-proc cmdlet에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="8ec04-115">이 정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="8ec04-116">매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-116">Defining Parameters</span></span>

<span data-ttu-id="8ec04-117">필요한 경우 cmdlet에 입력을 처리 하는 것에 대 한 매개 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="8ec04-118">Get-proc cmdlet이 정의 **이름을** 에 설명 된 대로 매개 변수 [매개 변수는 프로세스 명령줄 입력 추가](adding-parameters-that-process-command-line-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="8ec04-119">에 대 한 매개 변수 선언은 다음과 같습니다 합니다 **이름을** 이 Get-proc cmdlet의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="8ec04-120">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="8ec04-121">모든 cmdlet 입력 처리에서 제공 하는 메서드 중 하나 이상을 재정의 해야 합니다 [System.Management.Automation.Cmdlet][] 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="8ec04-122">이러한 메서드는 나오는 [첫 번째 Cmdlet 만들기](creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ec04-123">Cmdlet에 처리 해야 하지 각 레코드 최대한 독립적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="8ec04-124">Get-proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.ProcessRecord][] 처리 하는 메서드는 **이름** 스크립트나 사용자가 제공한 입력에 대 한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="8ec04-125">이 메서드는 제공 된 이름이 없는 경우 각 요청 된 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="8ec04-126">이 재정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="8ec04-127">오류를 보고할 때 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ec04-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="8ec04-128">합니다 [System.Management.Automation.ErrorRecord][] cmdlet 전달의 핵심 예외가 필요한 오류를 작성 하는 경우는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="8ec04-129">사용 하는 예외를 결정할 때.NET 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="8ec04-130">기본적으로 오류 의미상 동일한 경우 기존 예외로, cmdlet를 사용 하거나 해당 예외에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="8ec04-131">그렇지 않은 경우 새 예외 또는 예외 계층에서 직접 파생 되어야 합니다 [System.Exception][] 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="8ec04-132">오류 식별자 (ErrorRecord 클래스의 FullyQualifiedErrorId 속성을 통해 액세스)를 만들 때 다음 사항에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="8ec04-133">생성 된 오류와 진단 목적으로 정규화 된 식별자를 검사 하는 경우 어떤 오류를 확인할 수 있습니다이 대 한 대상으로 하는 사용 하 여 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="8ec04-134">잘 구성 된 정규화 된 오류 식별자는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="8ec04-135">이전 예제에서는 오류 식별자 (첫 번째 토큰)를 지정 오류가 무엇 인지 확인 하 고 남은 부분에서 오류가 발생 한 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="8ec04-136">복잡 한 시나리오에 대 한 오류 식별자에는 검사에서 구문 분석할 수 있는 점으로 구분 된 토큰 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="8ec04-137">이 오류 식별자와 오류 범주 뿐만 아니라 오류 식별자 부분에 너무 분기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="8ec04-138">Cmdlet은 다른 코드 경로에 특정 오류 식별자를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="8ec04-139">다음 정보를 고려 오류 식별자 할당 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ec04-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="8ec04-140">오류 식별자 cmdlet 수명 주기에 걸쳐 일정 하 게 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="8ec04-141">Cmdlet 버전 간의 오류 식별자의 의미 체계를 변경 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8ec04-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="8ec04-142">상품 보고 된 오류에 해당 하는 오류 식별자에 대 한 텍스트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="8ec04-143">공백 또는 문장 부호를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8ec04-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="8ec04-144">재현할 수 있는 오류 식별자만을 생성 하는 cmdlet에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="8ec04-145">예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="8ec04-146">오류 식별자는 동일한 문제가 발생 한 다른 사용자가 표시 되는 식별자에 해당 하는 경우에 사용자에 게 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="8ec04-147">처리 되지 않은 예외 PowerShell에서 다음 조건에서 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="8ec04-148">Cmdlet에서 처리 되지 않은 예외를 throw 하는 스레드는 실행 되는 코드를 새 스레드를 만드는 경우 PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="8ec04-149">개체가 소멸자 또는 Dispose 메서드는 처리 되지 않은 예외를 발생 시킨 코드를 사용 하면 PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="8ec04-150">종료 되지 않는 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="8ec04-151">입력 처리 메서드 중 하나를 사용 하 여 출력 스트림을 종료 되지 않는 오류를 보고할 수 있습니다 합니다 [System.Management.Automation.Cmdlet.WriteError][] 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ec04-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="8ec04-152">에 대 한 호출을 보여 주는이 Get-proc cmdlet의 코드 예제는 다음과 같습니다 [System.Management.Automation.Cmdlet.WriteError][] 에서 재정의 내는 [System.Management.Automation.Cmdlet.ProcessRecord][] 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ec04-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="8ec04-153">이 경우 cmdlet은 지정 된 프로세스 식별자에 대 한 프로세스를 찾을 수 없는 경우에 호출이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="8ec04-154">종료 되지 않는 오류를 작성 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ec04-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="8ec04-155">종료 되지 않는 오류를 cmdlet에는 각 특정 입력된 개체에 대 한 특정 오류 식별자를 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="8ec04-156">Cmdlet은 자주 종료 되지 않는 오류로 인해 생성 된 PowerShell 작업을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="8ec04-157">정의 하 여이 수행할 수는 `ErrorAction` 고 `ErrorVariable` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="8ec04-158">정의 하는 경우는 `ErrorAction` 매개 변수를 cmdlet 사용자 옵션을 제공 합니다 [System.Management.Automation.ActionPreference][]를 설정 하 여 작업을 직접 조작할 수 있습니다는 `$ErrorActionPreference` 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="8ec04-159">Cmdlet을 사용 하 여 변수 종료 되지 않는 오류를 저장할 수는 `ErrorVariable` 매개 변수를 설정 하 여 영향을 받지 않는 `ErrorAction`합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="8ec04-160">오류 추가할 수 있는 기존 오류 변수는 더하기 기호 (+)를 추가 하 여 변수 이름의 맨 앞으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8ec04-161">코드 예제</span><span class="sxs-lookup"><span data-stu-id="8ec04-161">Code Sample</span></span>

<span data-ttu-id="8ec04-162">전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample04 샘플](./getprocesssample04-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="8ec04-163">개체 유형 및 서식을 정의합니다</span><span class="sxs-lookup"><span data-stu-id="8ec04-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="8ec04-164">PowerShell은.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="8ec04-165">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="8ec04-166">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="8ec04-167">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="8ec04-167">Building the Cmdlet</span></span>

<span data-ttu-id="8ec04-168">Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="8ec04-169">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="8ec04-170">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ec04-170">Testing the Cmdlet</span></span>

<span data-ttu-id="8ec04-171">PowerShell를 cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="8ec04-172">오류를 보고 하는지 여부를 확인 하려면 샘플 Get-proc cmdlet를 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="8ec04-173">PowerShell을 시작 하 고 "TEST" 라는 프로세스를 검색할 Get-proc cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="8ec04-174">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec04-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="8ec04-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ec04-175">See Also</span></span>

[<span data-ttu-id="8ec04-176">프로세스 파이프라인 입력 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="8ec04-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="8ec04-177">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="8ec04-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="8ec04-178">첫 번째 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="8ec04-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="8ec04-179">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="8ec04-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="8ec04-180">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8ec04-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="8ec04-181">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="8ec04-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="8ec04-182">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="8ec04-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
