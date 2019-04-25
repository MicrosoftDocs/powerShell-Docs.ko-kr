---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리의 FileList 기능
ms.openlocfilehash: 5f372c943c73fa8e1014657394e40eaedef5d045
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084813"
---
# <a name="filelist-feature-in-the-gallery"></a><span data-ttu-id="e1dc7-103">갤러리의 FileList 기능</span><span class="sxs-lookup"><span data-stu-id="e1dc7-103">FileList feature in the Gallery</span></span>

<span data-ttu-id="e1dc7-104">갤러리에 게시된 모든 패키지의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-104">You are able to view the contents in all packages published in the gallery.</span></span>

<span data-ttu-id="e1dc7-105">이 기능은 패키지 내의 파일 나열 및 지원되는 파일 형식에 대한 파일 내용 표시의 두 부분으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-105">This feature includes two parts: listing the files within the package, and displaying file contents for supported file types.</span></span> <span data-ttu-id="e1dc7-106">현재 파일 내용 표시가 지원되는 파일 확장명은 .ps1, .psm1, .psd1, .ps1xml, .xml 및 .txt입니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-106">Currently we support displaying the contents of the following file extensions: .ps1, .psm1, .psd1, .ps1xml, .xml and .txt.</span></span> <span data-ttu-id="e1dc7-107">이후 릴리스에서는 더 많은 파일 확장명이 지원될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-107">We will be supporting more file extensions in the next releases.</span></span>

## <a name="where-to-find-filelist"></a><span data-ttu-id="e1dc7-108">FileList를 찾을 수 있는 위치</span><span class="sxs-lookup"><span data-stu-id="e1dc7-108">Where to Find FileList</span></span>

<span data-ttu-id="e1dc7-109">각 개별 패키지 페이지에서 FileList 섹션과 **표시** 링크를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-109">On each individual package page, you will be able to find FileList section and a **Show** link.</span></span> <span data-ttu-id="e1dc7-110">표시를 클릭하면 패키지에 포함된 항목의 전체 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-110">Click on the Show and you will find a complete list of items contained in the package.</span></span>

<span data-ttu-id="e1dc7-111">지원되는 각 파일 형식이 하이퍼링크로 표시되며, 클릭하면 파일 내용이 PowerShell 구문 강조로 표시된 새 페이지로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-111">Each supported file type is displayed as a hyperlink, and clicking it will take you to a new page with file contents displayed in PowerShell syntax highlighting.</span></span> <span data-ttu-id="e1dc7-112">화면 맨 위에 표시된 패키지의 제목 또는 버전을 클릭하면 패키지 세부 정보 페이지로 다시 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e1dc7-112">Clicking on the title or the version of the package, which is displayed at the top of the screen, will bring you back to package detail page.</span></span>
