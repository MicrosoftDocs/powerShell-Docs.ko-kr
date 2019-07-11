---
title: 와일드 카드 식 별칭을 추가 하 고 Cmdlet 매개 변수를 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733839"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="363ea-102">Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가</span><span class="sxs-lookup"><span data-stu-id="363ea-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="363ea-103">이 섹션에서는 와일드 카드 식 별칭을 추가 하는 방법을 설명 하 고 도움말 메시지 중지 Proc cmdlet의 매개 변수를 (에서 설명한 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="363ea-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="363ea-104">이 중지 Proc cmdlet Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하려고 합니다. (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="363ea-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="363ea-105">Cmdlet을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-105">Defining the Cmdlet</span></span>

<span data-ttu-id="363ea-106">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="363ea-107">시스템을 변경 하는 cmdlet를 작성 하는 때문에 적절 하 게 명명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="363ea-108">이 cmdlet은 시스템 프로세스를 중지, 정의한 동사 "Stop"을 사용 합니다 [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스를 "Proc" 프로세스를 나타내려면 명사를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="363ea-109">승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="363ea-110">다음 코드는이 중지 Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="363ea-111">시스템 수정에 대 한 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="363ea-112">Cmdlet는 지원 시스템 수정 및 사용자 피드백 매개 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="363ea-113">Cmdlet을 정의 해야는 `Name` 매개 변수 또는 해당 cmdlet은 식별자의 일종으로 시스템을 수정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="363ea-114">또한, cmdlet 정의 해야 합니다 `Force` 및 `PassThru` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="363ea-115">이러한 매개 변수에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="363ea-116">매개 변수 별칭을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="363ea-117">대체 이름 또는 cmdlet 매개 변수에 대해 잘 정의 된 문자 1 또는 2 자의 짧은 이름을 매개 변수 별칭을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="363ea-118">두 경우 모두 명령줄에서 사용자 입력을 단순화 하기 위해 별칭을 사용 하 여 목표가입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="363ea-119">Windows PowerShell을 통해 매개 변수 별칭을 지원 합니다 [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 의 선언 구문은 [Alias()]를 사용 하는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="363ea-120">다음 코드를 별칭은 추가 하는 방법을 보여 줍니다는 `Name` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="363ea-121">사용 하는 것 외에도 합니다 [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성에는 Windows PowerShell 런타임에 수행 부분 이름에 일치 하는 별칭 없음 지정 된 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="363ea-122">예를 들어 cmdlet에는 `FileName` 매개 변수 이며로 시작 하는 유일한 매개 변수인 `F`, 사용자가 입력할 수 `Filename`, `Filenam`, `File`, `Fi`, 또는 `F` 여전히 인식 하 고는 항목으로는 `FileName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="363ea-123">매개 변수에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="363ea-123">Creating Help for Parameters</span></span>

<span data-ttu-id="363ea-124">Windows PowerShell을 사용 하면 cmdlet 매개 변수에 대 한 도움말을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="363ea-125">시스템 수정 및 사용자 피드백에 사용 되는 매개 변수에 대해이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="363ea-126">도움말을 지원 하려면 각 매개 변수에 대해 설정할 수 있습니다 합니다 `HelpMessage` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="363ea-127">이 키워드는 매개 변수를 사용 하 여 도움이 필요 하면 사용자에 게 표시할 텍스트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="363ea-128">설정할 수도 있습니다는 `HelpMessageBaseName` 키워드를 사용 하는 메시지에 사용할 리소스의 기본 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="363ea-129">이 키워드를 사용 하도록 설정한 경우 설정 해야 합니다 `HelpMessageResourceId` 리소스 식별자를 지정 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="363ea-130">이 중지 Proc cmdlet에서 다음 코드를 정의 합니다 `HelpMessage` 특성에 대 한 키워드는 `Name` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="363ea-131">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="363ea-132">Cmdlet는 입력 처리 메서드를 재정의 해야, 가장 일반적인 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="363ea-133">시스템을 수정할 때 cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 사용자를 허용 하는 방법 변경 되기 전에 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="363ea-134">이러한 방법에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="363ea-135">와일드 카드 확장 지원</span><span class="sxs-lookup"><span data-stu-id="363ea-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="363ea-136">여러 개체의 선택에 허용 하려면 cmdlet에 사용할 수는 [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 하 고 [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 제공 하는 클래스 입력 매개 변수에 대 한 와일드 카드 확장 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="363ea-137">와일드 카드 패턴의 예는 lsa \* \*.txt 및 [a-c]\*합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="363ea-138">패턴을 그대로 사용 해야 하는 문자를 포함 하는 경우에 이스케이프 문자로 역따옴표 (')를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="363ea-139">파일 이름과 경로 와일드 카드 확장은 cmdlet을 여러 개체의 선택이 필요한 경우 지원에 대 한 경로 입력을 허용 하도록 할 수는 있는 일반적인 시나리오의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="363ea-140">현재 폴더에 있는 모든 파일을 보려면 사용자가 있는 파일 시스템의 일반적인 사례 이며</span><span class="sxs-lookup"><span data-stu-id="363ea-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="363ea-141">드물게만 사용자 지정된 와일드 카드 패턴 일치 하는 구현을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="363ea-142">이 경우 cmdlet 전체 POSIX 1003.2, 와일드 카드 확장에 대 한 3.13 사양 또는 다음 단순화 된 하위 집합을 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="363ea-143">**물음표 (?)입니다.**</span><span class="sxs-lookup"><span data-stu-id="363ea-143">**Question mark (?).**</span></span> <span data-ttu-id="363ea-144">지정된 된 위치에 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="363ea-145">**별표 (\*).**</span><span class="sxs-lookup"><span data-stu-id="363ea-145">**Asterisk (\*).**</span></span> <span data-ttu-id="363ea-146">지정된 된 위치에서 시작 하는 0 개 이상의 문자와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="363ea-147">**대괄호 ()를 엽니다.**</span><span class="sxs-lookup"><span data-stu-id="363ea-147">**Open bracket ([).**</span></span> <span data-ttu-id="363ea-148">문자 또는 문자 범위를 포함할 수 있는 패턴 대괄호 식을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="363ea-149">범위가 필요한 경우 하이픈 (-) 범위를 나타내기 위해 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="363ea-150">**닫는 대괄호 (]).**</span><span class="sxs-lookup"><span data-stu-id="363ea-150">**Close bracket (]).**</span></span> <span data-ttu-id="363ea-151">대괄호 식 패턴을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="363ea-152">**백 견적 이스케이프 문자 (').**</span><span class="sxs-lookup"><span data-stu-id="363ea-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="363ea-153">다음 문자가 문자 그대로 해석 되도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="363ea-154">프로그래밍 방식으로 지정) (아닌 명령줄에서 백 따옴표 문자를 지정할 때 백 따옴표 이스케이프 문자를 지정 해야 합니다 두 번에 유의 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="363ea-155">와일드 카드 패턴에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수에서 와일드 카드를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="363ea-156">다음 코드에서는 와일드 카드 옵션을 설정 하 고 확인 하는 데 사용 되는 와일드 카드 패턴을 정의 하는 방법을 보여 줍니다.는 `Name` 이 cmdlet에 대 한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="363ea-157">다음 코드는 프로세스 이름에 정의 된 와일드 카드 패턴 일치 하는지 여부를 테스트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="363ea-158">이 경우 프로세스 이름 패턴 일치 하지 않는 경우 cmdlet에서 계속 다음 프로세스 이름을 가져오려면 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="363ea-159">코드 예제</span><span class="sxs-lookup"><span data-stu-id="363ea-159">Code Sample</span></span>

<span data-ttu-id="363ea-160">전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample03 샘플](./stopprocesssample03-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="363ea-161">개체 유형 및 서식을 정의합니다</span><span class="sxs-lookup"><span data-stu-id="363ea-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="363ea-162">Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="363ea-163">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="363ea-164">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](/previous-versions//ms714665(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="363ea-165">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="363ea-165">Building the Cmdlet</span></span>

<span data-ttu-id="363ea-166">Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해.</span><span class="sxs-lookup"><span data-stu-id="363ea-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="363ea-167">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](/previous-versions//ms714644(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="363ea-168">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="363ea-168">Testing the Cmdlet</span></span>

<span data-ttu-id="363ea-169">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="363ea-170">샘플 프로시저 중지 cmdlet를 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="363ea-171">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="363ea-172">Windows PowerShell을 시작 및 중지 프로시저의 ProcessName 별칭을 사용 하는 프로세스를 중지 하는 데는 `Name` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="363ea-173">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="363ea-174">명령줄에서 다음 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-174">Make the following entry on the command line.</span></span> <span data-ttu-id="363ea-175">Name 매개 변수는 필수 이므로에 대 한 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="363ea-176">입력 "?"</span><span class="sxs-lookup"><span data-stu-id="363ea-176">Entering "!?"</span></span> <span data-ttu-id="363ea-177">매개 변수를 사용 하 여 연결 된 도움말 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="363ea-178">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="363ea-179">와일드 카드 패턴과 일치 하는 모든 프로세스를 중지 하려면 다음 항목을 확인 하 고 있습니다. "\* 참고\*"입니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="363ea-180">메시지가 표시 되는 패턴과 일치 하는 각 프로세스를 중지 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="363ea-181">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="363ea-182">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="363ea-183">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363ea-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="363ea-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="363ea-184">See Also</span></span>

[<span data-ttu-id="363ea-185">시스템을 수정 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="363ea-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="363ea-186">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="363ea-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="363ea-187">[확장 개체 형식 및 서식 지정](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="363ea-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="363ea-188">[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="363ea-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="363ea-189">Cmdlet 매개 변수에서 와일드 카드 지원</span><span class="sxs-lookup"><span data-stu-id="363ea-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="363ea-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="363ea-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
