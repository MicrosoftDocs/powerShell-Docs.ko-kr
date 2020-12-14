---
ms.date: 09/13/2016
ms.topic: reference
title: 온라인 도움말 지원
description: 온라인 도움말 지원
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645426"
---
# <a name="supporting-online-help"></a><span data-ttu-id="1ba75-103">온라인 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="1ba75-103">Supporting Online Help</span></span>

<span data-ttu-id="1ba75-104">PowerShell 3.0부터 `Get-Help` powershell 명령에 대 한 온라인 기능을 지 원하는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-104">Beginning in PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for PowerShell commands.</span></span> <span data-ttu-id="1ba75-105">이 항목에서는 다양 한 명령 유형에 대해이 기능을 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-105">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="1ba75-106">온라인 도움말 정보</span><span class="sxs-lookup"><span data-stu-id="1ba75-106">About Online Help</span></span>

<span data-ttu-id="1ba75-107">온라인 도움말은 항상 PowerShell의 중요 한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-107">Online help has always been a vital part of PowerShell.</span></span> <span data-ttu-id="1ba75-108">Cmdlet은 `Get-Help` 명령 프롬프트에서 도움말 항목을 표시 하지만 많은 사용자가 커뮤니티 콘텐츠 및 wiki 기반 문서에서 색 구분, 하이퍼링크 및 아이디어 공유를 포함 하 여 온라인 읽기 환경을 선호 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-108">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="1ba75-109">가장 중요 한 점은 업데이트할 수 있는 도움말을 제공 하기 전에 온라인 도움말에서 최신 버전의 도움말 파일을 제공 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-109">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="1ba75-110">PowerShell 3.0에서 업데이트할 수 있는 도움말을 사용 하 여 온라인 도움말에서 여전히 중요 한 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-110">With the advent of Updatable Help in PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="1ba75-111">유연한 사용자 환경 외에도 온라인 도움말은 업데이트할 수 있는 도움말 항목을 다운로드 하는 데 사용할 수 없는 사용자를 위한 도움말을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-111">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="1ba75-112">Get-Help-온라인 작동 방법</span><span class="sxs-lookup"><span data-stu-id="1ba75-112">How Get-Help -Online Works</span></span>

<span data-ttu-id="1ba75-113">사용자가 명령에 대 한 온라인 도움말 항목을 찾을 수 있도록 명령에는 `Get-Help` 사용자의 기본 인터넷 브라우저에서 명령에 대 한 온라인 버전의 도움말 항목을 여는 온라인 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-113">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default internet browser.</span></span>

<span data-ttu-id="1ba75-114">예를 들어 다음 명령은 cmdlet에 대 한 온라인 도움말 항목을 엽니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-114">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="1ba75-115">을 구현 하기 위해 `Get-Help -Online` 이 `Get-Help` cmdlet은 다음 위치의 온라인 버전 도움말 항목에 대 한 URI (Uniform resource Identifier)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-115">To implement `Get-Help -Online`, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="1ba75-116">명령에 대 한 도움말 항목의 **관련 링크** 섹션에 있는 첫 번째 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-116">The first link in the **Related Links** section of the help topic for the command.</span></span> <span data-ttu-id="1ba75-117">사용자의 컴퓨터에 도움말 항목이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-117">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="1ba75-118">이 기능은 PowerShell 2.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-118">This feature was introduced in PowerShell 2.0.</span></span>

- <span data-ttu-id="1ba75-119">모든 명령의 **HelpUri** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-119">The **HelpUri** property of any command.</span></span> <span data-ttu-id="1ba75-120">**HelpUri** 속성은 사용자의 컴퓨터에 명령에 대 한 도움말 항목이 설치 되어 있지 않은 경우에도 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-120">The **HelpUri** property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="1ba75-121">이 기능은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-121">This feature was introduced in PowerShell 3.0.</span></span>

  <span data-ttu-id="1ba75-122">`Get-Help`**HelpUri** 속성 값을 가져오기 전에 **관련 링크** 섹션의 첫 번째 항목에서 URI를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-122">`Get-Help` looks for a URI in the first entry in the **Related Links** section before getting the **HelpUri** property value.</span></span> <span data-ttu-id="1ba75-123">속성 값이 잘못 되었거나 변경 된 경우 첫 번째 관련 링크에 다른 값을 입력 하 여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-123">If the property value is incorrect or has changed, you can override it by entering a different value in the first related link.</span></span> <span data-ttu-id="1ba75-124">그러나 첫 번째 관련 링크는 도움말 항목이 사용자의 컴퓨터에 설치 된 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-124">However, the first related link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="1ba75-125">명령 도움말 항목의 첫 번째 관련 링크에 URI 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-125">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="1ba75-126">`Get-Help -Online`명령에 대 한 XML 기반 도움말 항목의 **관련 링크** 섹션에 있는 첫 번째 항목에 유효한 URI를 추가 하 여 명령을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-126">You can support `Get-Help -Online` for any command by adding a valid URI to the first entry in the **Related Links** section of the XML-based help topic for the command.</span></span> <span data-ttu-id="1ba75-127">이 옵션은 XML 기반 도움말 항목에만 사용할 수 있으며 도움말 항목이 사용자의 컴퓨터에 설치 된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-127">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="1ba75-128">도움말 항목을 설치 하 고 URI를 채우면이 값이 명령의 **HelpUri** 속성 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-128">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="1ba75-129">이 기능을 지원 하려면 URI가 `maml:uri` 요소의 첫 번째 요소 아래에 있는 요소에 표시 되어야 합니다 `maml:relatedLinks/maml:navigationLink` `maml:relatedLinks` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="1ba75-130">다음 XML은 URI의 올바른 배치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="1ba75-131">`Online version:` `maml:linkText` 요소의 텍스트가 가장 좋은 방법 이지만 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-131">The `Online version:` text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="1ba75-132">명령에 HelpUri 속성 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="1ba75-133">이 섹션에서는 HelpUri 속성을 다른 형식의 명령에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="1ba75-134">Cmdlet에 HelpUri 속성 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="1ba75-135">C #으로 작성 된 cmdlet의 경우 **cmdlet** 클래스에 **HelpUri** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-135">For cmdlets written in C#, add a **HelpUri** attribute to the **Cmdlet** class.</span></span> <span data-ttu-id="1ba75-136">특성의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-136">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="1ba75-137">다음 코드에서는 cmdlet 클래스의 **HelpUri** 특성을 보여 줍니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-137">The following code shows the **HelpUri** attribute of the `Get-History` cmdlet class.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="1ba75-138">고급 함수에 HelpUri 속성 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="1ba75-139">고급 함수의 경우 **Cmdletbinding** 특성에 **HelpUri** 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="1ba75-140">속성의 값은 "http" 또는 "https"로 시작 하는 URI 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="1ba75-141">다음 코드에서는 함수의 **HelpUri** 특성을 보여 줍니다. `New-Calendar`</span><span class="sxs-lookup"><span data-stu-id="1ba75-141">The following code shows the **HelpUri** attribute of the `New-Calendar` function</span></span>

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="1ba75-142">CIM 명령에 HelpUri 특성 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="1ba75-143">CIM 명령의 경우 CDXML 파일의 **Cmdletmetadata** 요소에 **HelpUri** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span>
<span data-ttu-id="1ba75-144">특성의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-144">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="1ba75-145">다음 코드는 CIM 명령의 HelpUri 특성을 보여 줍니다. `Start-Debug`</span><span class="sxs-lookup"><span data-stu-id="1ba75-145">The following code shows the HelpUri attribute of the `Start-Debug` CIM command</span></span>

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="1ba75-146">워크플로에 HelpUri 특성 추가</span><span class="sxs-lookup"><span data-stu-id="1ba75-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="1ba75-147">PowerShell 언어로 작성 된 워크플로의 경우를 추가 **합니다.** 워크플로 코드에 대 한 ExternalHelp 주석 지시문입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-147">For workflows that are written in the PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="1ba75-148">지시문의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .</span><span class="sxs-lookup"><span data-stu-id="1ba75-148">The value of the directive must be a URI that begins with `http` or `https`.</span></span>

> [!NOTE]
> <span data-ttu-id="1ba75-149">HelpUri 속성은 PowerShell의 XAML 기반 워크플로에 대해 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-149">The HelpUri property is not supported for XAML-based workflows in PowerShell.</span></span>

<span data-ttu-id="1ba75-150">다음 코드에서는을 보여 줍니다. 워크플로 파일의 ExternalHelp 지시문입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba75-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
