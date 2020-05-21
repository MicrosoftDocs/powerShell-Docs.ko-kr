---
title: 별칭, 와일드 카드 확장 및 Cmdlet 매개 변수에 대 한 도움말 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 7c4098c6c670f22253fe7d463b33e45208d00790
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560001"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="763c3-102">Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가</span><span class="sxs-lookup"><span data-stu-id="763c3-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="763c3-103">이 섹션에서는 진단, 와일드 카드 확장 및 도움말 메시지를 Stop Proc cmdlet의 매개 변수에 추가 하는 방법에 대해 설명 합니다 ( [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)참조).</span><span class="sxs-lookup"><span data-stu-id="763c3-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="763c3-104">이 Stop Proc cmdlet은 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 것 처럼 Get-proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="763c3-105">Cmdlet 정의</span><span class="sxs-lookup"><span data-stu-id="763c3-105">Defining the Cmdlet</span></span>

<span data-ttu-id="763c3-106">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="763c3-107">시스템을 변경 하는 cmdlet을 작성 하 고 있으므로 이름을 적절 하 게 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="763c3-108">이 cmdlet은 시스템 프로세스를 중지 하므로 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스에 정의 된 동사 "Stop"을 사용 하 여 프로세스를 나타내는 명사 "Proc"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="763c3-109">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="763c3-110">다음 코드는이 Stop Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="763c3-111">시스템 수정 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="763c3-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="763c3-112">Cmdlet은 시스템 수정과 사용자 피드백을 지 원하는 매개 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="763c3-113">Cmdlet은 매개 변수를 정의 해야 합니다 `Name` . 이렇게 하면 cmdlet이 일종의 식별자로 시스템을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="763c3-114">또한 cmdlet은 `Force` 및 매개 변수를 정의 해야 합니다 `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="763c3-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="763c3-115">이러한 매개 변수에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="763c3-116">매개 변수 별칭 정의</span><span class="sxs-lookup"><span data-stu-id="763c3-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="763c3-117">매개 변수 별칭은 cmdlet 매개 변수에 대 한 대체 이름 또는 잘 정의 된 1 자 또는 2 자 짧은 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="763c3-118">두 경우 모두 별칭을 사용 하는 것은 명령줄에서 사용자 입력을 단순화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="763c3-119">Windows PowerShell은 선언 구문 [Alias ()]를 사용 하는 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성을 통해 매개 변수 별칭을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="763c3-120">다음 코드는 매개 변수에 별칭을 추가 하는 방법을 보여 줍니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="763c3-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="763c3-121">[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성을 사용 하는 것 외에도 Windows PowerShell 런타임은 별칭이 지정 되지 않은 경우에도 부분 이름 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="763c3-122">예를 들어 cmdlet에 `FileName` 매개 변수가 있고로 시작 하는 유일한 매개 변수인 경우 `F` 사용자는,,, 또는를 입력 하 여 해당 `Filename` `Filenam` 항목을 `File` `Fi` `F` `FileName` 매개 변수로 계속 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="763c3-123">매개 변수에 대 한 도움말 만들기</span><span class="sxs-lookup"><span data-stu-id="763c3-123">Creating Help for Parameters</span></span>

<span data-ttu-id="763c3-124">Windows PowerShell을 사용 하 여 cmdlet 매개 변수에 대 한 도움말을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="763c3-125">시스템 수정 및 사용자 의견에 사용 되는 매개 변수에 대해이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="763c3-126">도움말을 지 원하는 각 매개 변수에 대해 `HelpMessage` [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언에서 attribute 키워드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="763c3-127">이 키워드는 매개 변수를 사용할 때 사용자에 게 표시 되는 텍스트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="763c3-128">또한 키워드를 설정 `HelpMessageBaseName` 하 여 메시지에 사용할 리소스의 기본 이름을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="763c3-129">이 키워드를 설정 하는 경우 키워드를 설정 `HelpMessageResourceId` 하 여 리소스 식별자도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="763c3-130">이 Stop Proc cmdlet의 다음 코드는 `HelpMessage` 매개 변수에 대 한 attribute 키워드를 정의 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="763c3-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="763c3-131">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="763c3-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="763c3-132">Cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 대부분은 일반적으로 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)입니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="763c3-133">시스템을 수정 하는 경우 cmdlet은 변경 전에 사용자에 게 피드백을 제공할 수 있도록 [system.web](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .. n a m a. a m [a.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="763c3-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="763c3-134">이러한 메서드에 대 한 자세한 내용은 시스템을 [수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="763c3-135">와일드 카드 확장 지원</span><span class="sxs-lookup"><span data-stu-id="763c3-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="763c3-136">여러 개체를 선택할 수 있도록 cmdlet은 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 및 [Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 클래스를 사용 하 여 매개 변수 입력에 대 한 와일드 카드 확장 지원을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="763c3-137">와일드 카드 패턴의 예로는 lsa \*, \* .txt 및 [a-c]가 있습니다 \* .</span><span class="sxs-lookup"><span data-stu-id="763c3-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="763c3-138">패턴에 리터럴로 사용 해야 하는 문자가 포함 된 경우에는 백슬래시 문자 (')를 이스케이프 문자로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="763c3-139">파일 및 경로 이름의 와일드 카드 확장은 여러 개체를 선택 해야 하는 경우 cmdlet이 경로 입력 지원을 허용 하려는 일반적인 시나리오의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="763c3-140">일반적인 경우는 사용자가 현재 폴더에 있는 모든 파일을 확인 하려는 파일 시스템에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="763c3-141">거의 사용자 지정 된 와일드 카드 패턴 일치 구현이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="763c3-142">이 경우 cmdlet은 와일드 카드 확장 또는 다음 단순화 된 하위 집합에 대 한 전체 POSIX 1003.2, 3.13 사양을 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="763c3-143">**물음표 (?)를 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="763c3-143">**Question mark (?).**</span></span> <span data-ttu-id="763c3-144">지정 된 위치에 있는 모든 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="763c3-145">**별표 ( \* ).**</span><span class="sxs-lookup"><span data-stu-id="763c3-145">**Asterisk (\*).**</span></span> <span data-ttu-id="763c3-146">지정 된 위치에서 시작 하 여 0 개 이상의 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="763c3-147">**여는 대괄호 ([).**</span><span class="sxs-lookup"><span data-stu-id="763c3-147">**Open bracket ([).**</span></span> <span data-ttu-id="763c3-148">문자 또는 문자 범위를 포함할 수 있는 패턴 대괄호 식을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="763c3-149">범위가 필요한 경우 범위를 나타내는 데 하이픈 (-)이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="763c3-150">**닫는 대괄호 (])입니다.**</span><span class="sxs-lookup"><span data-stu-id="763c3-150">**Close bracket (]).**</span></span> <span data-ttu-id="763c3-151">패턴 대괄호 식을 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="763c3-152">**백슬래시 이스케이프 문자 (')입니다.**</span><span class="sxs-lookup"><span data-stu-id="763c3-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="763c3-153">는 다음 문자를 문자 그대로 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="763c3-154">명령줄에서 백슬래시 문자를 지정 하는 경우 (프로그래밍 방식으로 지정 하는 것과 반대), 백슬래시 이스케이프 문자를 두 번 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="763c3-155">와일드 카드 패턴에 대 한 자세한 내용은 [Cmdlet 매개 변수에서 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="763c3-156">다음 코드에서는 와일드 카드 옵션을 설정 하 고 `Name` 이 cmdlet의 매개 변수를 확인 하는 데 사용 되는 와일드 카드 패턴을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="763c3-157">다음 코드에서는 프로세스 이름이 정의 된 와일드 카드 패턴과 일치 하는지 여부를 테스트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="763c3-158">이 경우 프로세스 이름이 패턴과 일치 하지 않으면 cmdlet은 계속 해 서 다음 프로세스 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="763c3-159">코드 예제</span><span class="sxs-lookup"><span data-stu-id="763c3-159">Code Sample</span></span>

<span data-ttu-id="763c3-160">전체 c # 샘플 코드는 [StopProcessSample03 샘플](./stopprocesssample03-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="763c3-161">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="763c3-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="763c3-162">Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="763c3-163">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="763c3-164">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="763c3-165">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="763c3-165">Building the Cmdlet</span></span>

<span data-ttu-id="763c3-166">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="763c3-167">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="763c3-168">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="763c3-168">Testing the Cmdlet</span></span>

<span data-ttu-id="763c3-169">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="763c3-170">샘플 중지-프로시저 cmdlet을 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="763c3-171">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="763c3-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="763c3-172">Windows PowerShell을 시작 하 고 ProcessName 별칭을 사용 하 여 매개 변수에 대 한 프로세스를 중지 하려면 Stop Proc를 사용 `Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="763c3-173">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="763c3-174">명령줄에 다음 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-174">Make the following entry on the command line.</span></span> <span data-ttu-id="763c3-175">Name 매개 변수는 필수 매개 변수 이므로 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="763c3-176">"!?"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-176">Entering "!?"</span></span> <span data-ttu-id="763c3-177">매개 변수와 연결 된 도움말 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="763c3-178">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="763c3-179">이제 와일드 카드 패턴 "\* note"와 일치 하는 모든 프로세스를 중지 하기 위해 다음 항목을 만듭니다 \* .</span><span class="sxs-lookup"><span data-stu-id="763c3-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="763c3-180">패턴과 일치 하는 각 프로세스를 중지 하기 전에 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="763c3-181">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="763c3-182">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="763c3-183">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="763c3-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="763c3-184">See Also</span></span>

[<span data-ttu-id="763c3-185">시스템을 수정 하는 Cmdlet을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="763c3-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="763c3-186">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="763c3-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="763c3-187">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="763c3-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="763c3-188">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="763c3-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="763c3-189">Cmdlet 매개 변수에 와일드 카드 지원</span><span class="sxs-lookup"><span data-stu-id="763c3-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="763c3-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="763c3-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
