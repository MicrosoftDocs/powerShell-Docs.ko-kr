---
title: Cmdlet 도움말 파일을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858979"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="8f20c-102">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="8f20c-103">이 섹션에는 Windows PowerShell cmdlet 도움말 항목에 대 한 콘텐츠를 포함 하는 유효한 XML 파일을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="8f20c-104">이 섹션에는 도움말 파일 이름 지정 방법, 적절 한 XML 헤더를 추가 하는 방법 및 다양 한 cmdlet 도움말 콘텐츠 섹션을 포함 하는 노드를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="8f20c-105">에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="8f20c-106">예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="8f20c-107">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="8f20c-108">텍스트 파일을 만들고 UTF8 인코딩을 사용 하 여 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="8f20c-109">Windows PowerShell cmdlet 도움말 파일을 검색할 수 있도록 파일 이름 형식은 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="8f20c-110">텍스트 파일에 다음 XML 헤더를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="8f20c-111">다중 에이전트 모델링 언어 (MAML) 스키마에 대해 파일을 검사할 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="8f20c-112">현재 Windows PowerShell은 파일의 유효성을 검사 하려면 도구를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="8f20c-113">어셈블리의 각 cmdlet에 대 한 cmdlet 도움말 파일을 명령 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="8f20c-114">명령 노드에 내의 각 노드는 cmdlet 도움말 항목의 다른 섹션 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="8f20c-115">다음 표에서 각 노드의 설명 뒤에 각 노드에 대 한 XML 요소를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="8f20c-116">노드</span><span class="sxs-lookup"><span data-stu-id="8f20c-116">Node</span></span>|<span data-ttu-id="8f20c-117">설명</span><span class="sxs-lookup"><span data-stu-id="8f20c-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="8f20c-118">Cmdlet 도움말 항목의 이름 및 개요 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-119">자세한 내용은 [개요와 Cmdlet 이름을 추가 하는 방법을](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="8f20c-120">Cmdlet 도움말 항목의 설명 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-121">자세한 내용은 [자세히 기술 한 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-a-cmdlet-description.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="8f20c-122">Cmdlet 도움말 항목의 구문 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-123">자세한 내용은 [구문 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-syntax-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="8f20c-124">Cmdlet 도움말 항목의 매개 변수 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-125">자세한 내용은 [추가 매개 변수는 Cmdlet 도움말 항목을 방법](./how-to-add-parameter-information.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="8f20c-126">Cmdlet 도움말 항목을 입력 부분에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-127">자세한 내용은 [Cmdlet 도움말 항목을 입력 유형을 추가 하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="8f20c-128">Cmdlet 도움말 항목의 출력 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-129">자세한 내용은 [반환 값 추가 Cmdlet 도움말 항목을 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="8f20c-130">Cmdlet 도움말 항목의 NOTES 섹션에 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-131">자세한 내용은 [추가 하는 방법에는 Cmdlet 도움말 항목에 정보](./how-to-add-notes-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="8f20c-132">Cmdlet 도움말 항목의 예 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-133">자세한 내용은 [예제 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-examples-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="8f20c-134">Cmdlet 도움말 항목의 관련 링크 섹션에 대 한 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8f20c-135">자세한 내용은 [관련 링크 추가 Cmdlet 도움말 항목을 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="8f20c-136">예제</span><span class="sxs-lookup"><span data-stu-id="8f20c-136">Example</span></span>

 <span data-ttu-id="8f20c-137">Cmdlet 도움말 항목의 여러 섹션에 대 한 노드를 포함 하는 명령 노드의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f20c-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="8f20c-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f20c-138">See Also</span></span>

 [<span data-ttu-id="8f20c-139">Cmdlet 이름 및 개요를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-140">자세한 설명은 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="8f20c-141">구문 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-142">Cmdlet 도움말 항목 매개 변수를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="8f20c-143">입력된 형식 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-144">Cmdlet 도움말 항목에 반환 값을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-145">추가 하는 방법에는 Cmdlet 도움말 항목을 참고 사항</span><span class="sxs-lookup"><span data-stu-id="8f20c-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-146">예제 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-147">관련된 링크 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f20c-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8f20c-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8f20c-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)