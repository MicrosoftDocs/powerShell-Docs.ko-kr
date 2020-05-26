---
title: CAB 파일을 만들고 업로드 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 37b31aa77dde23c1bd57a9af67e2232ef0827005
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811762"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="82878-102">CAB 파일을 만들고 업로드하는 방법</span><span class="sxs-lookup"><span data-stu-id="82878-102">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="82878-103">이 항목에서는 업데이트할 수 있는 도움말 CAB 파일을 만들고 업데이트할 수 있는 도움말 cmdlet에서 해당 파일을 찾을 수 있는 위치에 업로드 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-103">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="82878-104">업데이트할 수 있는 도움말 CAB 파일을 만들고 업로드 하는 방법</span><span class="sxs-lookup"><span data-stu-id="82878-104">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="82878-105">업데이트할 수 있는 도움말 기능을 사용 하 여 여러 언어 및 문화권의 모듈에 대 한 새로운 또는 업데이트 된 도움말 파일을 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-105">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="82878-106">모듈에 대 한 업데이트할 수 있는 도움말 패키지는 하나의 HelpInfo XML 파일과 하나 이상의 캐비닛 ()으로 구성 됩니다. CAB) 파일.</span><span class="sxs-lookup"><span data-stu-id="82878-106">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (.CAB) files.</span></span> <span data-ttu-id="82878-107">각 CAB 파일에는 한 가지 UI 문화권의 모듈에 대 한 도움말 파일이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-107">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="82878-108">업데이트할 수 있는 도움말의 CAB 파일을 만들려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="82878-108">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="82878-109">UI 문화권에 따라 모듈에 대 한 도움말 파일을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-109">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="82878-110">각 업데이트할 수 있는 도움말 CAB 파일에는 한 가지 UI 문화권의 한 모듈에 대 한 도움말 파일이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-110">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="82878-111">각 모듈에 대해 서로 다른 UI 문화권에 대 한 여러 도움말 CAB 파일을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-111">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

2. <span data-ttu-id="82878-112">도움말 파일에 업데이트 가능한 도움말에 허용 된 파일 형식만 포함 되어 있는지 확인 하 고 도움말 파일 스키마에 대해 유효성 검사를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-112">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="82878-113">Cmdlet이 `Update-Help` 잘못 되었거나 허용 되는 형식이 아닌 파일을 발견 하는 경우 잘못 된 파일을 설치 하지 않고 CAB에서 파일 설치를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-113">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="82878-114">허용 되는 파일 형식 목록은 [업데이트할 수 있는 도움말 CAB 파일에서 허용 되는 파일 형식](./file-types-permitted-in-an-updatable-help-cab-file.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82878-114">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

3. <span data-ttu-id="82878-115">도움말 파일에 디지털 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-115">Digitally sign the help files.</span></span> <span data-ttu-id="82878-116">디지털 서명은 필요 하지 않지만 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="82878-116">Digital signatures are not required, but they are a best practice.</span></span>

4. <span data-ttu-id="82878-117">새 파일 또는 변경 된 파일 뿐만 아니라 UI 문화권의 모듈에 대 한 도움말 파일을 모두 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-117">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="82878-118">CAB 파일이 완전 하지 않은 경우 처음으로 도움말 파일을 다운로드 하거나 모든 업데이트를 다운로드 하지 않는 사용자에 게는 모듈 도움말 파일이 모두 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-118">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

5. <span data-ttu-id="82878-119">MakeCab와 같은 캐비닛 파일을 만드는 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-119">Use a utility that creates cabinet files, such as MakeCab.exe.</span></span> <span data-ttu-id="82878-120">Windows PowerShell에는 CAB 파일을 만드는 cmdlet이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-120">Windows PowerShell does not include cmdlets that create CAB files.</span></span>

6. <span data-ttu-id="82878-121">CAB 파일의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-121">Name the CAB files.</span></span> <span data-ttu-id="82878-122">자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일의 이름을 추가 하는 방법](./how-to-name-an-updatable-help-cab-file.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82878-122">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

7. <span data-ttu-id="82878-123">모듈에 대 한 HelpInfo XML 파일의 **Helpcontenturi** 요소에 지정 된 위치에 모듈의 CAB 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-123">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="82878-124">그런 다음 HelpInfo XML 파일을 모듈 매니페스트의 **HelpInfoUri** 키로 지정 된 위치에 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-124">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="82878-125">**Helpcontenturi** 및 **HelpInfoUri** 는 동일한 위치를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82878-125">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="82878-126">**HelpInfoUri** Key 및 **helpcontenturi** 요소의 값은 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-126">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with "http" or "https".</span></span> <span data-ttu-id="82878-127">값은 인터넷 위치를 나타내야 하며 파일 이름을 포함 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82878-127">The value must indicate an Internet location and it must not include a file name.</span></span>
