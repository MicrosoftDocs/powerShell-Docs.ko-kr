---
title: 오류 정보 표시 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774578"
---
# <a name="displaying-error-information"></a><span data-ttu-id="ba463-102">오류 정보 표시</span><span class="sxs-lookup"><span data-stu-id="ba463-102">Displaying Error Information</span></span>

<span data-ttu-id="ba463-103">이 항목에서는 사용자가 오류 정보를 표시할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba463-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="ba463-104">Cmdlet에 오류가 발생 하면 오류 정보를 표시 하는 것은 기본적으로 다음 오류 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba463-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="ba463-105">그러나 사용자는 변수를로 설정 하 여 범주별로 오류를 볼 수 있습니다 `$ErrorView` `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="ba463-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="ba463-106">범주 보기에는 오류에 대 한 자유 텍스트 설명이 아닌 오류 레코드의 특정 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba463-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="ba463-107">이 보기는 검색할 오류 목록이 긴 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba463-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="ba463-108">범주 보기에서 이전 오류 메시지는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba463-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="ba463-109">오류 범주에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba463-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba463-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba463-110">See Also</span></span>

[<span data-ttu-id="ba463-111">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="ba463-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ba463-112">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ba463-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
