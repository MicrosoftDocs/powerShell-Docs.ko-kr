---
title: 업데이트 가능한 도움말을 테스트 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854739"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="184f9-102">업데이트 가능한 도움말을 테스트하는 방법</span><span class="sxs-lookup"><span data-stu-id="184f9-102">How to Test Updatable Help</span></span>

<span data-ttu-id="184f9-103">이 항목에서는 모듈의 업데이트할 수 있는 도움말을 테스트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="184f9-104">오류를 검색 하는 자세한 정보를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="184f9-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="184f9-105">HelpInfo XML 파일 및 모듈에 대 한 CAB 파일을 업로드 한 후 파일을 실행 하 여 테스트를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 명령에 **Verbose** 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="184f9-106">합니다 **Verbose** 매개 변수는 지시 `Update-Help` 읽기에서 해당 작업의 중요 한 단계를 보고 하는 **HelpInfoUri** 압축 푼된 CAB 파일의 파일 형식을 확인을 위해 모듈 매니페스트 키 및 언어별 모듈 디렉터리에 파일을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="184f9-107">HelpInfo XML 파일 및 모듈에 대 한 CAB 파일을 업로드 한 후 파일을 실행 하 여 테스트를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 명령에 **Verbose** 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="184f9-108">합니다 **Verbose** 매개 변수는 지시 `Update-Help` 읽기에서 해당 작업의 중요 한 단계를 보고 하는 **HelpInfoUri** 압축 푼된 CAB 파일의 파일 형식을 확인을 위해 모듈 매니페스트 키 및 언어별 모듈 디렉터리에 파일을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="184f9-109">모든 세부 정보 표시 메시지를 해결 하는 경우 실행을 `Update-Help` 명령에 **디버그** 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="184f9-110">이 매개 변수는 업데이트할 수 있는 도움말 파일을 사용 하 여 나머지 문제를 감지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="184f9-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>