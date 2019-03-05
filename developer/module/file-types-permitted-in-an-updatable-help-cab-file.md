---
title: 도움말 CAB 파일을 업데이트할 수 있는에서 허용 하는 파일 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862839"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="2db11-102">업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식</span><span class="sxs-lookup"><span data-stu-id="2db11-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="2db11-103">이 항목 나열 하 고 업데이트할 수 있는 도움말 CAB 파일에 대 한 콘텐츠 요구 사항에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="2db11-104">업데이트 가능한 도움말 CAB 파일 요구 사항</span><span class="sxs-lookup"><span data-stu-id="2db11-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="2db11-105">압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1GB로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="2db11-106">이 한도 무시 하려면 사용자를 사용 해야 합니다 **Force** 의 매개 변수를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2db11-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>
<span data-ttu-id="2db11-107">압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1GB로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-107">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="2db11-108">이 한도 무시 하려면 사용자를 사용 해야 합니다 **Force** 의 매개 변수를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2db11-108">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="2db11-109">인터넷에서 다운로드 하는 도움말 파일의 보안을 보장 하는 업데이트 가능한 도움말 CAB 파일 아래에 나열 된 파일 형식만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-109">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="2db11-110">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 항목에서는 스키마에 대해 모든 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-110">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="2db11-111">경우는 `Update-Help` 는 유효 하지 않거나 허용 된 형식이 아닌 파일을 발견 하는 cmdlet, 잘못 된 파일을 설치 하지 않습니다 고에서 사용자의 컴퓨터에서 CAB 파일 설치를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-111">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>
<span data-ttu-id="2db11-112">인터넷에서 다운로드 하는 도움말 파일의 보안을 보장 하는 업데이트 가능한 도움말 CAB 파일 아래에 나열 된 파일 형식만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-112">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="2db11-113">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 항목에서는 스키마에 대해 모든 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-113">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="2db11-114">경우는 `Update-Help` 는 유효 하지 않거나 허용 된 형식이 아닌 파일을 발견 하는 cmdlet, 잘못 된 파일을 설치 하지 않습니다 고에서 사용자의 컴퓨터에서 CAB 파일 설치를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-114">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="2db11-115">Cmdlet에 대 한 XML 기반 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="2db11-115">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="2db11-116">스크립트 및 함수에 대 한 XML 기반 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="2db11-116">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="2db11-117">Windows PowerShell 공급자에 대 한 XML 기반 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="2db11-117">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="2db11-118">텍스트 기반 항목을 같은 항목에 대 한 도움말입니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-118">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="2db11-119">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB 압축을 풉니다 CAB 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-119">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="2db11-120">경우 `Update-Help` 업데이트할 수 있는 도움말 CAB 파일에 호환 되지 않는 파일 형식, 종료 오류를 생성 하 고 작업을 중지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-120">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="2db11-121">규정을 준수 하는 파일 형식 이더라도 CAB에서 도움말 파일을 설치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-121">It does not install any help files from the CAB, even those of compliant file types.</span></span>
<span data-ttu-id="2db11-122">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB 압축을 풉니다 CAB 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-122">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="2db11-123">경우 `Update-Help` 업데이트할 수 있는 도움말 CAB 파일에 호환 되지 않는 파일 형식, 종료 오류를 생성 하 고 작업을 중지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-123">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="2db11-124">규정을 준수 하는 파일 형식 이더라도 CAB에서 도움말 파일을 설치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db11-124">It does not install any help files from the CAB, even those of compliant file types.</span></span>