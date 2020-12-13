---
ms.date: 09/12/2016
ms.topic: reference
title: 도움말 파일을 업데이트하는 방법
description: 도움말 파일을 업데이트하는 방법
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649595"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="01076-103">도움말 파일을 업데이트하는 방법</span><span class="sxs-lookup"><span data-stu-id="01076-103">How to Update Help Files</span></span>

<span data-ttu-id="01076-104">이 항목에서는 업데이트할 수 있는 도움말을 지 원하는 모듈에 대 한 도움말 파일을 업데이트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-104">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="01076-105">도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="01076-105">Updating Help Files</span></span>

<span data-ttu-id="01076-106">오류 수정, 개념을 명확 하 게 하기, 자주 묻는 질문에 대 한 답변, 새 파일 추가, 새 예제 추가 등의 여러 가지 이유로 도움말 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01076-106">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="01076-107">도움말 파일을 업데이트 하려면:</span><span class="sxs-lookup"><span data-stu-id="01076-107">To update a help file:</span></span>

1. <span data-ttu-id="01076-108">파일을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-108">Change the files.</span></span>
1. <span data-ttu-id="01076-109">다른 UI 문화권으로 파일을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-109">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="01076-110">각 UI 문화권의 모듈에 대 한 모든 도움말 파일 (새로운, 변경 및 변경 되지 않음)을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-110">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="01076-111">XML 스키마에 대해 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-111">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="01076-112">각 UI 문화권에 대 한 CAB 파일을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-112">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="01076-113">HelpInfo XML 파일에서 각 UI 문화권에 대 한 CAB 파일의 버전 번호를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="01076-113">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="01076-114">HelpInfo XML 파일에서 **Helpcontenturi** 요소의 값으로 지정 된 위치에 새 CAB 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-114">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="01076-115">이전 CAB 파일을 새 CAB 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="01076-115">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="01076-116">모듈 매니페스트에서 **HelpInfoUri** 키로 지정 된 위치에 업데이트 된 HelpInfo XML 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="01076-116">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="01076-117">이전 HelpInfo XML 파일을 새 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="01076-117">Replace the older HelpInfo XML file with the new file.</span></span>
