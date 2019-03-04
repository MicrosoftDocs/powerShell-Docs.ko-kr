---
title: 도움말 파일을 업데이트 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855529"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="90c49-102">도움말 파일을 업데이트하는 방법</span><span class="sxs-lookup"><span data-stu-id="90c49-102">How to Update Help Files</span></span>

<span data-ttu-id="90c49-103">이 항목에서는 업데이트 가능한 도움말을 지 원하는 모듈에 대 한 도움말 파일을 업데이트 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="90c49-104">도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="90c49-104">Updating Help Files</span></span>

<span data-ttu-id="90c49-105">오류를 수정, 개념을 명확히, 자주 묻는 질문에 답하려면, 새 파일을 추가 또는 새롭고 더 나은 예제 추가 같은 도움말 파일을 업데이트 하는 방법은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="90c49-106">도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-106">To update a help file:</span></span>

1. <span data-ttu-id="90c49-107">파일을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-107">Change the files.</span></span>

2. <span data-ttu-id="90c49-108">다른 UI 문화권으로 파일을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="90c49-109">각 UI 문화권의 모듈에 대 한 모든 도움말 파일 (새, 변경 및 변경 되지 않은)를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="90c49-110">XML 스키마에 대해 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="90c49-111">각 UI 문화권에 대 한 CAB 파일을 다시 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="90c49-112">HelpInfo XML 파일에서 각 UI 문화권에 대 한 CAB 파일의 버전 번호를 하나씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="90c49-113">값으로 지정 된 위치에 새 CAB 파일을 업로드 합니다 **HelpContentUri** HelpInfo XML 파일의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="90c49-114">새 CAB 파일을 사용 하 여 오래 된 CAB 파일을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="90c49-115">지정 된 위치에 업데이트 된 HelpInfo XML 파일을 업로드 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="90c49-116">새 파일을 사용 하 여 이전 HelpInfo XML 파일을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c49-116">Replace the older HelpInfo XML file with the new file.</span></span>