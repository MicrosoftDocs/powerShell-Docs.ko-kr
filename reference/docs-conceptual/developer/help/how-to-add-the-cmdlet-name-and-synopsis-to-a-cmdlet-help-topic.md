---
title: Cmdlet 이름 및 개요를 Cmdlet 도움말 항목에 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361192"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="28192-102">Cmdlet 도움말 항목에 Cmdlet 이름 및 개요를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="28192-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="28192-103">이 섹션에서는 cmdlet 도움말의 NAME 및 개요 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="28192-104">도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28192-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="28192-105">도움말 파일의 전체 보기를 보려면 Windows PowerShell 설치 디렉터리에 있는 dll-Help 파일 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28192-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="28192-106">예를 들어 dll-Help 파일에는 몇 가지 Windows PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28192-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="28192-107">Cmdlet 이름 및 개요를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="28192-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="28192-108">Cmdlet 도움말에는 cmdlet에 대 한 두 가지 설명이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28192-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="28192-109">첫 번째 설명은 개요 이라고 하는 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="28192-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="28192-110">두 번째 설명은 [Cmdlet 도움말 항목에](./how-to-add-a-cmdlet-description.md)대 한 자세한 설명을 추가 하는 방법에서 설명 하는 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="28192-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="28192-111">두 설명을 모두 단일 단락으로 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="28192-112">개요 cmdlet 이름을 반복 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28192-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="28192-113">사용자에 게 Get Server cmdlet이 서버를 가져오지만 정보는 없다는 사실을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28192-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="28192-114">대신 동의어를 사용 하 고 설명에 세부 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="28192-115">예: "로컬 또는 원격 컴퓨터를 나타내는 개체를 가져옵니다."</span><span class="sxs-lookup"><span data-stu-id="28192-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="28192-116">개요에서 "get", "create" 및 "change"와 같은 간단한 동사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="28192-117">"Set"는 모호 하 고 "modify"와 같은 고급 단어를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="28192-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="28192-118">예: "파일의 Authenticode 서명에 대 한 정보를 가져옵니다."</span><span class="sxs-lookup"><span data-stu-id="28192-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="28192-119">활성 음성으로 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-119">Write in active voice.</span></span> <span data-ttu-id="28192-120">예: "TimeSpan 개체 사용 ..." "TimeSpan 개체를 사용할 수 있습니다." 보다 훨씬 더 명확 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="28192-121">개체를 가져오는 cmdlet을 설명할 때 동사 "display"를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28192-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="28192-122">Windows PowerShell에서 cmdlet 데이터를 표시 하지만, 사용자에 게 데이터를 표시 하지 않을 수 있는 개체 .NET Framework cmdlet이 반환 한다는 개념을 소개 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="28192-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="28192-123">표시를 강조 표시 하는 경우 사용자는 cmdlet이 표시 되지 않는 다른 많은 유용한 속성 및 메서드를 반환 했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28192-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="28192-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28192-124">See Also</span></span>

 [<span data-ttu-id="28192-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="28192-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)