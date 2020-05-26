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
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811652"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="e4f58-102">도움말 파일을 업데이트하는 방법</span><span class="sxs-lookup"><span data-stu-id="e4f58-102">How to Update Help Files</span></span>

<span data-ttu-id="e4f58-103">이 항목에서는 업데이트할 수 있는 도움말을 지 원하는 모듈에 대 한 도움말 파일을 업데이트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="e4f58-104">도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="e4f58-104">Updating Help Files</span></span>

<span data-ttu-id="e4f58-105">오류 수정, 개념을 명확 하 게 하기, 자주 묻는 질문에 대 한 답변, 새 파일 추가, 새 예제 추가 등의 여러 가지 이유로 도움말 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="e4f58-106">도움말 파일을 업데이트 하려면:</span><span class="sxs-lookup"><span data-stu-id="e4f58-106">To update a help file:</span></span>

1. <span data-ttu-id="e4f58-107">파일을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-107">Change the files.</span></span>

2. <span data-ttu-id="e4f58-108">다른 UI 문화권으로 파일을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="e4f58-109">각 UI 문화권의 모듈에 대 한 모든 도움말 파일 (새로운, 변경 및 변경 되지 않음)을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="e4f58-110">XML 스키마에 대해 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="e4f58-111">각 UI 문화권에 대 한 CAB 파일을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="e4f58-112">HelpInfo XML 파일에서 각 UI 문화권에 대 한 CAB 파일의 버전 번호를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="e4f58-113">HelpInfo XML 파일에서 **Helpcontenturi** 요소의 값으로 지정 된 위치에 새 CAB 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="e4f58-114">이전 CAB 파일을 새 CAB 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="e4f58-115">모듈 매니페스트에서 **HelpInfoUri** 키로 지정 된 위치에 업데이트 된 HelpInfo XML 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="e4f58-116">이전 HelpInfo XML 파일을 새 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e4f58-116">Replace the older HelpInfo XML file with the new file.</span></span>
