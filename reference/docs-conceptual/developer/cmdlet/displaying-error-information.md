---
title: 오류 정보 표시 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369972"
---
# <a name="displaying-error-information"></a><span data-ttu-id="f4524-102">오류 정보 표시</span><span class="sxs-lookup"><span data-stu-id="f4524-102">Displaying Error Information</span></span>

<span data-ttu-id="f4524-103">이 항목에서는 사용자가 오류 정보를 표시할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="f4524-104">Cmdlet에 오류가 발생 하면 오류 정보를 표시 하는 것은 기본적으로 다음 오류 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="f4524-105">그러나 사용자는 `$ErrorView` 변수를 `"CategoryView"`으로 설정 하 여 범주별로 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="f4524-106">범주 보기에는 오류에 대 한 자유 텍스트 설명이 아닌 오류 레코드의 특정 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="f4524-107">이 보기는 검색할 오류 목록이 긴 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="f4524-108">범주 보기에서 이전 오류 메시지는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4524-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="f4524-109">오류 범주에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4524-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4524-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4524-110">See Also</span></span>

[<span data-ttu-id="f4524-111">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="f4524-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="f4524-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f4524-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
