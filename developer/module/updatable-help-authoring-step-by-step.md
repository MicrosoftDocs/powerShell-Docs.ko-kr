---
title: '업데이트 가능한 도움말 작성: 단계별 | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082127"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="ebfa2-102">업데이트 가능한 도움말 작성: 단계별</span><span class="sxs-lookup"><span data-stu-id="ebfa2-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="ebfa2-103">이 문서는 업데이트할 수 있는 도움말 작성 단계를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="ebfa2-104">업데이트 가능한 도움말을 작성 합니다. 단계별</span><span class="sxs-lookup"><span data-stu-id="ebfa2-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="ebfa2-105">최종 사용자에 게 업데이트할 수 있는 도움말은 그러나 모듈 작성자가 한 많은 혜택을 제공 하 고 작성기 도움말 콘텐츠를 추가 하는 기능을 포함 하 여 오류를 수정, 여러 UI 문화권의 배달 시간 후 사용자 의견 및 요청에 응답할 합니다 모듈에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="ebfa2-106">이 항목에서는 패키지 하는 방법을 설명 하 고 사용자가 다운로드 하 고 사용 하 여 설치할 수 있도록 업로드 도움말 파일을 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="ebfa2-107">다음 단계를 업데이트할 수 있는 도움말 지원 프로세스의 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="ebfa2-108">1단계: 도움말 파일에 대해 인터넷 사이트 찾기</span><span class="sxs-lookup"><span data-stu-id="ebfa2-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="ebfa2-109">업데이트 가능한 도움말을 만드는 첫 번째 단계는 모듈의 도움말 파일에 대 한 인터넷 위치를 찾는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="ebfa2-110">실제로 두 개의 서로 다른 위치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="ebfa2-111">하나의 인터넷 위치와 다른 인터넷 위치에서 도움말 콘텐츠 CAB 파일에서 모듈의 도움말 정보 파일 (HelpInfo XML-아래에서 설명)를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="ebfa2-112">모든 도움말 콘텐츠 CAB 파일을 모듈에 대 한 동일한 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="ebfa2-113">동일한 위치에서 다른 모듈에 대 한 도움말 콘텐츠 CAB 파일을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="ebfa2-114">2단계: 프로그램 모듈 매니페스트에 HelpInfoURI 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="ebfa2-115">추가 된 **HelpInfoURI** 프로그램 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="ebfa2-116">키의 값이는 리소스 URI (Uniform Identifier) 모듈에 대 한 HelpInfo XML 정보 파일의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="ebfa2-117">보안에 대 한 주소는 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="ebfa2-118">URI는 인터넷 위치를 지정 해야 하지만 HelpInfo XML 파일 이름을 포함 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="ebfa2-119">예:</span><span class="sxs-lookup"><span data-stu-id="ebfa2-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="ebfa2-120">3단계: HelpInfo XML 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ebfa2-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="ebfa2-121">HelpInfo XML 정보 파일을 도움말 파일 및 지원 되는 각 UI 문화권의 모듈에 대 한 최신 도움말 파일의 버전 번호는 인터넷 위치의 URI를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="ebfa2-122">모든 Windows PowerShell 모듈에는 하나의 HelpInfo XML 파일을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="ebfa2-123">편집 하거나 HelpInfo XML 파일을 대체 하 여 도움말 파일을 업데이트 하면 다른 추가 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="ebfa2-124">자세한 내용은 [HelpInfo XML 파일을 만드는 방법](./how-to-create-a-helpinfo-xml-file.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="ebfa2-125">4단계: 도움말 파일에 서명</span><span class="sxs-lookup"><span data-stu-id="ebfa2-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="ebfa2-126">디지털 서명 필요 없는 되지만 모범 사례 권장 사항을 파일을 공유 하는 때마다 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="ebfa2-127">5 단계: CAB 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ebfa2-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="ebfa2-128">만들려는 MakeCab.exe 같은 캐비닛 (.cab) 파일을 만드는 도구를 사용 하 여를 합니다. 모듈에 대 한 도움말 파일이 포함 된 CAB 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="ebfa2-129">지원 되는 각 UI 문화권의 도움말 파일에 대 한 별도 CAB 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="ebfa2-130">자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일을 준비 하는 방법을](./how-to-prepare-updatable-help-cab-files.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="ebfa2-131">6 단계: 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="ebfa2-131">Step 6: Upload your files</span></span>

<span data-ttu-id="ebfa2-132">새롭거나 업데이트 된 도움말 파일을 게시 하려면 지정 된 인터넷 위치에 CAB 파일을 업로드 합니다 **HelpContentUri** HelpInfo XML 파일의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="ebfa2-133">그런 다음 값으로 지정 된 인터넷 위치로 HelpInfo XML 파일을 업로드 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
