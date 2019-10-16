---
title: 형식 지정 파일 (. types.ps1xml)을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363622"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="0c069-102">형식 지정 파일(.format.ps1xml)을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="0c069-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="0c069-103">이 항목에서는 형식 지정 파일 (. types.ps1xml)을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="0c069-104">Windows PowerShell에서 제공 하는 파일 중 하나를 복사 하 여 서식 파일을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="0c069-105">기존 파일의 복사본을 만드는 경우 기존 디지털 서명을 삭제 하 고 새 파일에 고유한 서명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="0c069-106">. Types.ps1xml 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="0c069-107">메모장과 같은 텍스트 편집기를 사용 하 여 텍스트 파일 (.txt)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="0c069-108">다음 줄을 서식 파일에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="0c069-109">@No__t-0 구성 > \</구성 > 태그는 루트 `Configuration` 노드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="0c069-110">모든 추가 XML 태그는이 노드 내에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="0c069-111">태그 <ViewDefinitions></ViewDefinitions> 는 `ViewDefinitions` 노드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="0c069-112">모든 뷰는이 노드 내에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="0c069-113">Windows PowerShell 설치 폴더, 모듈 폴더 또는 모듈 폴더의 하위 폴더에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="0c069-114">파일을 저장할 때 다음 이름 형식을 사용 합니다. `MyFile.format.ps1xml`</span><span class="sxs-lookup"><span data-stu-id="0c069-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="0c069-115">서식 파일은 `.format.ps1xml` 확장을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="0c069-116">이제 서식 파일에 뷰를 추가할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="0c069-117">서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="0c069-118">각 개체에 대해 단일 뷰를 추가 하거나, 동일한 개체에 대 한 여러 뷰를 추가 하거나, 여러 개체에서 사용 하는 단일 뷰를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c069-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c069-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c069-119">See Also</span></span>

[<span data-ttu-id="0c069-120">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0c069-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
