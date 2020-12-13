---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 도움말 파일을 만드는 방법
description: Cmdlet 도움말 파일을 만드는 방법
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659094"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="45134-103">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-103">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="45134-104">이 섹션에서는 Windows PowerShell cmdlet 도움말 항목에 대 한 콘텐츠를 포함 하는 올바른 XML 파일을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-104">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="45134-105">이 섹션에서는 도움말 파일의 이름을로 하는 방법, 적절 한 XML 헤더를 추가 하는 방법 및 cmdlet 도움말 콘텐츠의 여러 섹션이 포함 될 노드를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-105">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="45134-106">도움말 파일의 전체 보기를 보려면 `dll-Help.xml` Windows PowerShell 설치 디렉터리에 있는 파일 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45134-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="45134-107">예를 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 들어 파일에는 몇 가지 PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45134-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="45134-108">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-108">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="45134-109">텍스트 파일을 만들고 UTF8 인코딩을 사용 하 여 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-109">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="45134-110">파일 이름에는 Windows PowerShell에서 cmdlet 도움말 파일로 검색할 수 있도록 다음과 같은 형식이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-110">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="45134-111">텍스트 파일에 다음 XML 헤더를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-111">Add the following XML headers to the text file.</span></span> <span data-ttu-id="45134-112">이 파일은 MAML (Microsoft 지원 마크업 언어) 스키마에 대해 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-112">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="45134-113">현재 PowerShell에서는 파일의 유효성을 검사 하는 도구를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45134-113">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="45134-114">어셈블리의 각 cmdlet에 대 한 cmdlet 도움말 파일에 **명령** 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-114">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="45134-115">**명령** 노드 내의 각 노드는 cmdlet 도움말 항목의 다른 섹션과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45134-115">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="45134-116">다음 표에는 각 노드에 대 한 XML 요소와 각 노드에 대 한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45134-116">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="45134-117">노드</span><span class="sxs-lookup"><span data-stu-id="45134-117">Node</span></span>           |                                                                                                     <span data-ttu-id="45134-118">설명</span><span class="sxs-lookup"><span data-stu-id="45134-118">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="45134-119">Cmdlet 도움말 항목의 NAME and 개요 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-119">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-120">자세한 내용은 [Cmdlet 이름 및 개요를 추가 하는 방법](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-120">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="45134-121">Cmdlet 도움말 항목의 설명 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-121">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-122">자세한 내용은 [Cmdlet 도움말 항목에 자세한 설명을 추가](./how-to-add-a-cmdlet-description.md)하는 방법을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="45134-122">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="45134-123">Cmdlet 도움말 항목의 구문 섹션에 대 한 내용을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-123">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-124">자세한 내용은 [Cmdlet 도움말 항목에 구문을 추가 하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-124">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="45134-125">Cmdlet 도움말 항목의 매개 변수 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-125">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-126">자세한 내용은 [Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법 항목](./how-to-add-parameter-information.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-126">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="45134-127">Cmdlet 도움말 항목의 입력 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-127">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-128">자세한 내용은 [Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법 항목](./how-to-add-input-types-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-128">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="45134-129">Cmdlet 도움말 항목의 출력 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-129">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-130">자세한 내용은 [Cmdlet 도움말 항목에 반환 값을 추가 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-130">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="45134-131">Cmdlet 도움말 항목의 참고 항목 섹션에 대 한 내용을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-131">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-132">자세한 내용은 [Cmdlet 도움말 항목에 메모를 추가 하는 방법 항목](./how-to-add-notes-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-132">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="45134-133">Cmdlet 도움말 항목의 예제 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-133">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-134">자세한 내용은 [Cmdlet 도움말 항목에 예를 추가 하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-134">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="45134-135">Cmdlet 도움말 항목의 관련 링크 섹션에 대 한 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="45134-135">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="45134-136">자세한 내용은 [Cmdlet 도움말 항목에 관련 링크를 추가 하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45134-136">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="45134-137">예제</span><span class="sxs-lookup"><span data-stu-id="45134-137">Example</span></span>

 <span data-ttu-id="45134-138">다음은 cmdlet 도움말 항목의 다양 한 섹션에 대 한 노드를 포함 하는 **명령** 노드의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="45134-138">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45134-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45134-139">See Also</span></span>

 [<span data-ttu-id="45134-140">Cmdlet 이름 및 개요를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-140">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-141">Cmdlet 도움말 항목에 자세한 설명을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-141">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="45134-142">Cmdlet 도움말 항목에 구문을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-142">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-143">Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-143">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="45134-144">Cmdlet 도움말 항목에 입력 형식을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-144">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-145">Cmdlet 도움말 항목에 반환 값을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-145">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-146">Cmdlet 도움말 항목에 메모를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-146">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-147">Cmdlet 도움말 항목에 예제를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-147">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-148">Cmdlet 도움말 항목에 관련 링크를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="45134-148">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="45134-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="45134-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
