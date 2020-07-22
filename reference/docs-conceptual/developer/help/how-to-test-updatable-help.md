---
title: 업데이트 가능한 도움말을 테스트하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892968"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="83018-102">업데이트 가능한 도움말을 테스트하는 방법</span><span class="sxs-lookup"><span data-stu-id="83018-102">How to Test Updatable Help</span></span>

<span data-ttu-id="83018-103">이 항목에서는 모듈에 대해 업데이트할 수 있는 도움말을 테스트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="83018-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="83018-104">자세한 정보를 사용 하 여 오류 검색</span><span class="sxs-lookup"><span data-stu-id="83018-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="83018-105">모듈에 대 한 HelpInfo XML 파일 및 CAB 파일을 업로드 한 후 **Verbose** 매개 변수를 사용 하 여 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 명령을 실행 하 여 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="83018-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="83018-106">**Verbose** 매개 변수는 `Update-Help` 모듈 매니페스트의 **HelpInfoUri** 키를 읽고, 압축을 푼 CAB 파일의 파일 형식에 대 한 유효성을 검사 하 고, 파일을 언어별 모듈 디렉터리에 배치 하는 작업의 중요 한 단계를 보고 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83018-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="83018-107">모든 자세한 정보 메시지가 확인 되 면 `Update-Help` **Debug** 매개 변수를 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83018-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="83018-108">이 매개 변수는 업데이트할 수 있는 도움말 파일의 나머지 문제를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="83018-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
