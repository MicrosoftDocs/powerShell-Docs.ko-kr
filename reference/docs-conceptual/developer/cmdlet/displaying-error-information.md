---
ms.date: 09/13/2016
ms.topic: reference
title: 오류 정보 표시
description: 오류 정보 표시
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653054"
---
# <a name="displaying-error-information"></a><span data-ttu-id="d9ebf-103">오류 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d9ebf-103">Displaying Error Information</span></span>

<span data-ttu-id="d9ebf-104">이 항목에서는 사용자가 오류 정보를 표시할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-104">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="d9ebf-105">Cmdlet에 오류가 발생 하면 오류 정보를 표시 하는 것은 기본적으로 다음 오류 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-105">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="d9ebf-106">그러나 사용자는 변수를로 설정 하 여 범주별로 오류를 볼 수 있습니다 `$ErrorView` `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="d9ebf-106">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="d9ebf-107">범주 보기에는 오류에 대 한 자유 텍스트 설명이 아닌 오류 레코드의 특정 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-107">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="d9ebf-108">이 보기는 검색할 오류 목록이 긴 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-108">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="d9ebf-109">범주 보기에서 이전 오류 메시지는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-109">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="d9ebf-110">오류 범주에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-110">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ebf-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9ebf-111">See Also</span></span>

[<span data-ttu-id="d9ebf-112">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="d9ebf-112">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="d9ebf-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d9ebf-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
