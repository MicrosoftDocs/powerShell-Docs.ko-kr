---
ms.date: 09/13/2016
ms.topic: reference
title: HelpInfo XML 파일을 만드는 방법
description: HelpInfo XML 파일을 만드는 방법
ms.openlocfilehash: d5a24306aa6488fdefad0b7b1ea9e2978a93a7b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647715"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="775c7-103">HelpInfo XML 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="775c7-103">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="775c7-104">이 섹션의이 항목에서는 PowerShell 업데이트할 수 있는 도움말 기능에 대 한 도움말 정보 파일 (일반적으로 "HelpInfo XML file" 이라고 함)을 만들고 채우는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-104">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="775c7-105">HelpInfo XML 파일 개요</span><span class="sxs-lookup"><span data-stu-id="775c7-105">HelpInfo XML File Overview</span></span>

<span data-ttu-id="775c7-106">HelpInfo XML 파일은 모듈에 대 한 업데이트할 수 있는 도움말에 대 한 정보의 기본 출처입니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-106">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="775c7-107">여기에는 모듈에 대 한 도움말 파일의 위치, 지원 되는 UI 문화권 및 사용자에 게 최신 도움말 파일이 있는지 여부를 확인 하는 데 사용할 수 있는 버전 번호가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-107">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="775c7-108">모듈에 여러 UI 문화권에 대 한 여러 도움말 파일이 포함 되어 있는 경우에도 각 모듈에는 HelpInfo XML 파일이 하나 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-108">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="775c7-109">모듈 작성자는 HelpInfo XML 파일을 만들고 모듈 매니페스트의 **HelpInfoUri** 키로 지정 된 인터넷 위치에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-109">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="775c7-110">모듈 도움말 파일을 업데이트 및 업로드 하면 모듈 작성자가 HelpInfo XML 파일을 업데이트 하 고 원래 HelpInfo XML 파일을 새 버전으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-110">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="775c7-111">HelpInfo XML 파일을 신중 하 게 유지 관리 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-111">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="775c7-112">새 파일을 업로드 하 고 버전 번호를 늘리는 경우 업데이트할 수 있는 도움말은 사용자의 컴퓨터에 새 파일을 다운로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-112">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="775c7-113">새 UI 문화권에 대 한 도움말 파일을 추가 하지만 HelpInfo XML 파일을 업데이트 하지 않거나 올바른 위치에 배치 하지 않으면 업데이트할 수 있는 도움말이 새 파일을 다운로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-113">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="775c7-114">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="775c7-114">In this section</span></span>

<span data-ttu-id="775c7-115">이 섹션에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="775c7-115">This section includes the following topics.</span></span>

- [<span data-ttu-id="775c7-116">HelpInfo XML 스키마</span><span class="sxs-lookup"><span data-stu-id="775c7-116">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="775c7-117">HelpInfo XML 샘플 파일</span><span class="sxs-lookup"><span data-stu-id="775c7-117">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="775c7-118">HelpInfo XML 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="775c7-118">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="775c7-119">HelpInfo XML 버전 번호를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="775c7-119">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="775c7-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="775c7-120">See Also</span></span>

[<span data-ttu-id="775c7-121">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="775c7-121">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
