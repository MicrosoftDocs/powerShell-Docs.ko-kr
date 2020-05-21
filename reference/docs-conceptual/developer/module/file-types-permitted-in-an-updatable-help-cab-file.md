---
title: 업데이트할 수 있는 도움말 CAB 파일에서 허용 되는 파일 형식 | Microsoft Docs
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
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560987"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="fcc65-102">업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식</span><span class="sxs-lookup"><span data-stu-id="fcc65-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="fcc65-103">이 항목에서는 업데이트할 수 있는 도움말 CAB 파일에 대 한 콘텐츠 요구 사항을 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="fcc65-104">업데이트할 수 있는 도움말 CAB 파일 요구 사항</span><span class="sxs-lookup"><span data-stu-id="fcc65-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="fcc65-105">압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1gb로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="fcc65-106">이 제한을 무시 하려면 사용자가 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet의 **Force** 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="fcc65-107">인터넷에서 다운로드 되는 도움말 파일의 보안을 보장 하기 위해 업데이트할 수 있는 도움말 CAB 파일에는 아래 나열 된 파일 유형만 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="fcc65-108">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet은 도움말 항목 스키마에 대 한 모든 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="fcc65-109">Cmdlet이 `Update-Help` 잘못 되었거나 허용 되는 형식이 아닌 파일을 발견 하는 경우 잘못 된 파일을 설치 하지 않고 사용자 컴퓨터의 CAB 파일 설치를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="fcc65-110">Cmdlet에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="fcc65-111">스크립트 및 함수에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="fcc65-112">Windows PowerShell 공급자에 대 한 XML 기반 도움말 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="fcc65-113">텍스트 기반 도움말 항목 (예: 정보 항목)</span><span class="sxs-lookup"><span data-stu-id="fcc65-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="fcc65-114">[업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 은 cab 파일의 압축을 풀고 cab 콘텐츠를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="fcc65-115">`Update-Help`에서 업데이트할 수 있는 도움말 CAB 파일에 비규격 파일 형식을 찾으면 종료 오류를 생성 하 고 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="fcc65-116">호환 되는 파일 형식의 경우에도 CAB에서 도움말 파일을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcc65-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>
