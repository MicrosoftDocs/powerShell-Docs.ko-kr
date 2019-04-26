---
title: Cmdlet 설명을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083521"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="9b847-102">Cmdlet 설명을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="9b847-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="9b847-103">이 섹션에는 cmdlet 도움말의 설명 섹션에 표시 되는 콘텐츠를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="9b847-104">도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9b847-105">에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="9b847-106">예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="9b847-107">설명을 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="9b847-107">To Add a Description</span></span>

- <span data-ttu-id="9b847-108">자세히 cmdlet의 기본 기능을 설명 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="9b847-109">대부분의 경우 cmdlet 이름에 사용 된 용어를 설명 하 고 예제를 사용 하 여 알 수 없는 개념을 설명 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="9b847-110">예를 들어, cmdlet은 데이터 파일에 추가 하는 경우 기존 파일의 끝에 데이터를 추가 하는 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="9b847-111">모든 cmdlet의 기능을 찾으려면 매개 변수 목록을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="9b847-112">Cmdlet의 기본 기능을 설명 하 고 다른 함수 및 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="9b847-113">예를 들어, cmdlet의 주요 함수 하나의 속성을 변경 하는 cmdlet의 모든 속성을 변경할 수 있지만 경우 그렇게 말할 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="9b847-114">Cmdlet 매개 변수를 다른 방법으로 정보를 요청할 수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="9b847-115">사용자가 분명 사용 하는 것 외에도 cmdlet을 사용할 수 있는 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="9b847-116">예를 들어 개체를 사용할 수 있습니다 하는 `Get-Host` cmdlet은 Windows PowerShell 명령 창에서 텍스트의 색을 변경 하는 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="9b847-117">예:  "는 `Get-Acl` cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="9b847-118">보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="9b847-119">ACL 지정 권한이 있는 사용자 및 사용자 그룹 리소스에 액세스할 수 있습니다. "</span><span class="sxs-lookup"><span data-stu-id="9b847-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="9b847-120">자세히 기술 한 cmdlet 설명 해야 하지만 cmdlet을 사용 하는 개념을 설명 하지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="9b847-121">추가 정보에 개념 정의 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b847-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b847-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b847-122">See Also</span></span>

[<span data-ttu-id="9b847-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9b847-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
