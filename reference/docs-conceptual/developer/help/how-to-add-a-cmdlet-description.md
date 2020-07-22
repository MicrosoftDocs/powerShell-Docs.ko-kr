---
title: Cmdlet 설명을 추가하는 방법
ms.date: 09/13/2016
ms.openlocfilehash: 2b98c4cefc3a55eccfeb7eba5a290e7d93a6088b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893240"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="e3116-102">Cmdlet 설명을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="e3116-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="e3116-103">이 섹션에서는 cmdlet 도움말의 **설명** 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-103">This section describes how to add content that is displayed in the **DESCRIPTION** section of the cmdlet Help.</span></span> <span data-ttu-id="e3116-104">도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 **명령** 노드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-104">In the Help file, this content is added to the **Command** node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e3116-105">도움말 파일의 전체 보기를 보려면 `dll-Help.xml` PowerShell 설치 디렉터리에 있는 파일 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-105">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="e3116-106">예를 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 들어 파일에는 몇 가지 PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-106">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="e3116-107">설명을 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="e3116-107">To Add a Description</span></span>

- <span data-ttu-id="e3116-108">먼저 cmdlet의 기본 기능에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="e3116-109">대부분의 경우 cmdlet 이름에 사용 되는 용어를 설명 하 고 예제를 사용 하 여 익숙하지 않은 개념을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="e3116-110">예를 들어 cmdlet이 파일에 데이터를 추가 하는 경우 기존 파일의 끝에 데이터를 추가 함을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="e3116-111">Cmdlet의 모든 기능을 찾으려면 매개 변수 목록을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="e3116-112">Cmdlet의 기본 기능을 설명 하 고 다른 함수 및 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="e3116-113">예를 들어 cmdlet의 main 함수가 하나의 속성을 변경 하는 것 이지만이 cmdlet은 자세한 설명에서 모든 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="e3116-114">Cmdlet 매개 변수를 사용 하 여 사용자가 다른 방법으로 정보를 요청 하는 경우 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="e3116-115">사용자가이 cmdlet을 사용할 수 있는 방법 뿐만 아니라 명확한 사용 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="e3116-116">예를 들어, cmdlet이 검색 하는 개체를 사용 하 여 `Get-Host` Windows PowerShell 명령 창의 텍스트 색을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="e3116-117">예: " `Get-Acl` Cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-117">Example: "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="e3116-118">보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="e3116-119">ACL은 사용자 및 사용자 그룹이 리소스에 액세스 해야 하는 권한을 지정 합니다. "</span><span class="sxs-lookup"><span data-stu-id="e3116-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="e3116-120">자세한 설명은 cmdlet에 대해 설명 하지만 cmdlet에서 사용 하는 개념을 설명 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="e3116-121">추가 참고 사항에 개념 정의를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3116-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3116-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3116-122">See Also</span></span>

[<span data-ttu-id="e3116-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e3116-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
