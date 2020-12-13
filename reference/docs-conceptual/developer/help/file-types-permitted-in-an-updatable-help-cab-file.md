---
ms.date: 03/22/2012
ms.topic: reference
title: 업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식
description: 업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654743"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="14759-103">업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식</span><span class="sxs-lookup"><span data-stu-id="14759-103">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="14759-104">압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1gb로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14759-104">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="14759-105">이 제한을 무시 하려면 사용자가 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet의 **Force** 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14759-105">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="14759-106">인터넷에서 다운로드 되는 도움말 파일의 보안을 보장 하기 위해 업데이트할 수 있는 도움말 CAB 파일에는 아래 나열 된 파일 유형만 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14759-106">To assure the security of help files that are downloaded from the internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="14759-107">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet은 도움말 항목 스키마에 대 한 모든 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="14759-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="14759-108">Cmdlet이 `Update-Help` 잘못 되었거나 허용 되는 형식이 아닌 파일을 발견 하는 경우 잘못 된 파일을 설치 하지 않고 사용자 컴퓨터의 CAB 파일 설치를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="14759-108">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="14759-109">Cmdlet에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="14759-109">XML-based help topics for cmdlets.</span></span>
- <span data-ttu-id="14759-110">스크립트 및 함수에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="14759-110">XML-based help topics for scripts and functions.</span></span>
- <span data-ttu-id="14759-111">PowerShell 공급자에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="14759-111">XML-based help topics for PowerShell providers.</span></span>
- <span data-ttu-id="14759-112">텍스트 기반 도움말 항목 (예: 정보 항목)</span><span class="sxs-lookup"><span data-stu-id="14759-112">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="14759-113">[업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 은 cab 파일의 압축을 풀고 cab 콘텐츠를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="14759-113">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="14759-114">`Update-Help`에서 업데이트할 수 있는 도움말 CAB 파일에 비규격 파일 형식을 찾으면 종료 오류를 생성 하 고 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="14759-114">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="14759-115">호환 되는 파일 형식의 경우에도 CAB에서 도움말 파일을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14759-115">It does not install any help files from the CAB, even those of compliant file types.</span></span>
