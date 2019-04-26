---
title: HelpInfo XML 파일을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082416"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="74110-102">HelpInfo XML 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="74110-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="74110-103">이 섹션의이 항목에서는이 만들고 일반적으로 "HelpInfo XML 파일 이라는," Windows PowerShell 업데이트할 수 있는 도움말 기능에 대 한 도움말 정보 파일을 채우는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74110-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="74110-104">HelpInfo XML 파일 개요</span><span class="sxs-lookup"><span data-stu-id="74110-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="74110-105">HelpInfo XML 파일은 모듈에 대해 업데이트할 수 있는 도움말에 대 한 정보의 기본 소스.</span><span class="sxs-lookup"><span data-stu-id="74110-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="74110-106">모듈, 지원 되는 UI 문화권을 및 버전 번호는 사용자가 최신 도움말 파일을 확인 하는 업데이트 가능한 도움말에 대 한 도움말 파일의 위치를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="74110-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="74110-107">각 모듈 모듈 여러 UI 문화권에 대 한 여러 도움말 파일을 포함 하는 경우에 하나의 HelpInfo XML 파일을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74110-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="74110-108">모듈 작성자 HelpInfo XML 파일을 생성 하 고 지정 된 인터넷 위치에 배치 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="74110-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="74110-109">모듈 도움말 파일이 업데이트 되 고 업로드, 하는 경우 모듈 작성자 HelpInfo XML 파일을 업데이트 하 여 새 버전을 사용 하 여 원래 HelpInfo XML 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="74110-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="74110-110">반드시 HelpInfo XML 파일을 신중 하 게 유지 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="74110-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="74110-111">새 파일을 업로드 해도 버전 번호를 증가 해야 하는 경우 업데이트할 수 있는 도움말 다운로드할 수 없습니다 새 파일을 사용자의 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="74110-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="74110-112">새 UI 문화권에 대 한 도움말 파일을 추가 하지만 하지 HelpInfo XML 파일을 업데이트 하거나 올바른 위치에 배치를 업데이트할 수 있는 도움말 다운로드할 수 없습니다 새 파일.</span><span class="sxs-lookup"><span data-stu-id="74110-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="74110-113">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="74110-113">In this section</span></span>

<span data-ttu-id="74110-114">이 섹션에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74110-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="74110-115">HelpInfo XML 스키마</span><span class="sxs-lookup"><span data-stu-id="74110-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="74110-116">HelpInfo XML 샘플 파일</span><span class="sxs-lookup"><span data-stu-id="74110-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="74110-117">HelpInfo XML 파일의 이름을 지정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="74110-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="74110-118">HelpInfo XML 버전 번호를 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="74110-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="74110-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74110-119">See Also</span></span>

[<span data-ttu-id="74110-120">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="74110-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)